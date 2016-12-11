# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "debian/contrib-jessie64"
  config.vm.hostname = ENV["VM_HOSTNAME"] || "jessie64-caff"

  if Vagrant.has_plugin?("vagrant-cachier")
    config.cache.scope = :box
  end

  config.vm.synced_folder "#{Dir.home}/.gnupg", "/home/.gnupg"

  config.vm.provider 'virtualbox' do |vb|
    vb.memory = 1024
    vb.cpus = 2
    vb.customize ['modifyvm', :id, '--nictype1', 'virtio']
    vb.customize [
      'modifyvm', :id,
      '--hwvirtex', 'on',
      '--nestedpaging', 'on',
      '--largepages', 'on',
      '--ioapic', 'on',
      '--pae', 'on',
      '--paravirtprovider', 'kvm',
    ]
  end

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "provision/playbook.yml"
    unless ENV["VM_SKIP_GALAXY"]
      ansible.galaxy_role_file = "provision/requirements.txt"
    end
    ansible.verbose = ENV["VM_ANSIBLE_VERBOSE"]
  end
end

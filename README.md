# caff (signing-party) environment in vagrant

## usage

- copy from `provision/google.yml.example` to `provision/google.yml` and edit
- `vagrant up`
- `vagrant ssh`
- `gpg-agent --daemon /bin/bash`
- `caff <keyid> [<keyid> ...]`

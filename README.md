# caff (signing-party) environment in vagrant

## usage

- copy from `provision/config.yml.example` to `provision/config.yml` and edit
- `vagrant up`
- `vagrant ssh`
- `gpg-agent --daemon /bin/bash`
- `caff <keyid> [<keyid> ...]`

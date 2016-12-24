# Automated Server Setup (Please don't acronym this)
By Jason Yao

## Description
This repo contains my automated setup script to take care of the
tedious tasks that need to always be setup for newly provisioned
*nix  servers.

Specifically, this repo sets up an opinionated, security-focused
automated setup approach that will do the following:
- Updates & upgrades
- Sets up non-root user creation, dotfiles installation, and SSH key setup
- Secures SSH access to the host (non-standard port, disabling non-root access, etc.)
- Sets up package auto-update
- Sets up firewall (`ufw`), & automated ip-ban (`fail2ban`) for SSH access
- Secures shared memory access
- Secures `su` privileges
- Secures networking (IP spoofing protection, source packet routing disabling, etc.)
- Monitoring subscription (monit if single host, kubernetes if part of docker cloud)

**NOTE**: It is assumed that the user of this script
has the necessary permissions. Basically, if you're
the default user once you SSH into a fresh instance
(e.g. `pi` for Raspbian, `root` for DO, `ubuntu` for
vagrant, etc. etc.), then this script is guarenteed
to work on these supported platforms.

## Supported Platforms
- Vagrant ubuntu 16.04 LTS server
- Digital Ocean ubuntu 16.04 LTS server
- AWS ubuntu 16.04 LTS server
- Raspberry Pi Raspbian

## Flow
The following flow can be achieved with the one-liner provided below.
- Download script
- Run script
- Validate script outcomes
- Delete script

## Install
The following one-liner will setup initial requirements before
running through a normal install via the [start script](start.sh)
```sh
wget https://raw.githubusercontent.com/JasonYao/server-setup/master/start.sh &> /dev/null && bash start.sh; rm -rf start.sh
```

## License
This repo is licensed under the terms of the GNU GPL v3, a copy of which may be found [here](LICENSE)

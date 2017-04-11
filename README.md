# Automated Server Setup (Please don't acronym this)
By [Jason Yao](https://github.com/JasonYao)

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
- [INCOMPLETE] Monitoring subscription (monit if single host, kubernetes if part of docker cloud)

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

## Install
The following one-liner should be used normally,
due to "sane" defaults already set (password should
be changed though).
```sh
curl -s https://raw.githubusercontent.com/JasonYao/server-setup/master/start | bash
```

## Customisation
This install script was built to have overridable defaults,
and can have the following settings overridden:
- User name (default is `jason`)
- User password
- User default shell (defaults to `bash`, some potential ones are `zsh`, `ksh`, etc.) *
- User dotfiles location (defaults to `~/.dotfiles`)
- User SSH public key value

* NOTE: The overridden shell should first be installed
on the host, otherwise the user's `SHELL` will simply
be set to `sh`.

### Changing the user and password
```sh
wget https://raw.githubusercontent.com/JasonYao/server-setup/master/start &> /dev/null && username="YOUR NAME HERE" password="YOUR PASSWORD HERE" bash start; rm -rf start
```

### Changing the user's default shell, dotfiles directory, and SSH key
```sh
wget https://raw.githubusercontent.com/JasonYao/server-setup/master/start &> /dev/null && defaultShell="zsh" dotfilesDirectory="/home/jason/.other_dir" sshPublicKey="ssh-ed25519 blahblahblahblah" bash start; rm -rf start
```

### Changing everything
Just fork this repo and change the default,
why bother overriding values at this point?

## Forking Note
If you plan on using this setup script,
my personal recommendation is to simply
fork this repo, and change the hard-coded
defaults in the script.

The defaults are located at lines `10`
through `14`, and should be self-explanatory
on how to change.

## License
This repo is licensed under the terms of the GNU GPL v3, a copy of which may be found [here](LICENSE).

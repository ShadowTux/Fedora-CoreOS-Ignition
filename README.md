# Fedora-CoreOS-Ignition
Ignition configurations for Fedora CoreOS<br />

# Notes
1. These are the configs I personally use on my systems. You **MUST** edit the files before you use them. At the very least, you should add your SSH keys or password hash.<br />
2. Only ED25519 SSH keys are accepted with the SSHD hardening configuration. If you do not use ED25519 keys, you will need to edit the `ExecStart=/usr/bin/curl https://raw.githubusercontent.com/TommyTran732/Linux-Setup-Scripts/main/etc/ssh/sshd_config/10-custom.conf -o /etc/ssh/sshd_config.d/10-custom.conf` accordingly.
3. If you create a passwordless user that requires administrative privileges, ensure that it is part of the `sudo` group (CoreOS allows this group to use sudo without a password) as the configs will disable empty password system authentication.
4. These configurations are made with a VPS in mind. You should adapt it for a bare metal deployment if that is what you are using (adding additional kernel parameters, configuring drive encryption, configuring storage, etc). You should also change the tuned profile from `virtual-guest` appropriately.
5. In most of these configs, the timezone is set to `America/New_York` and the automatic reboot time is set at 12 AM on Sunday. Watchtower will kick in 5-10 minutes after the reboot to update and redeploy the containers. You should change it according to your needs. The Docker-Compose.yml file does not include Watchtower.
6. The auto-updater.service could be put in `/etc/systemd/system` and enable to have automatic updates for your docker-compose and its containers. Please make sure that the `WorkingDir` is appropriate.

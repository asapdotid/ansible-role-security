<p align="center"> <img src="https://user-images.githubusercontent.com/34257858/129839002-15e3f2c7-3f75-46d4-afae-0fd207d7fdde.png" width="100" height="100"></p>

<h1 align="center">
    Ansible Role Security (Basic)
</h1>

<p align="center" style="font-size: 1.2rem;">
    This ansible role setup Security On Ubuntu, CentOS. Your servers' security is <i>*your*</i> responsibility.
</p>

<p align="center">

<a href="https://www.ansible.com">
  <img src="https://img.shields.io/badge/Ansible-2.10-green?style=flat&logo=ansible" alt="Ansible">
</a>
<a href="LICENSE.md">
  <img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="Licence">
</a>
<a href="https://ubuntu.com/">
  <img src="https://img.shields.io/badge/ubuntu-20.x-orange?style=flat&logo=ubuntu" alt="Distribution">
</a>
<a href="https://www.centos.org/">
  <img src="https://img.shields.io/badge/CentOS-8-green?style=flat&logo=centos" alt="Distribution">
</a>

## Requirements

For obvious reasons, `sudo` must be installed if you want to manage the sudoers file with this role.

On RedHat/CentOS systems, make sure you have the EPEL repository installed (you can include the `geerlingguy.repo-epel` role to get it installed).

No special requirements for Debian/Ubuntu systems.

## Role Variables

A list of users who should be added to the sudoers file so they can run any command as root (via `sudo`) either without a password or requiring a password for each command, respectively.

    security_autoupdate_enabled: true

Whether to install/enable `yum-cron` (RedHat-based systems) or `unattended-upgrades` (Debian-based systems). System restarts will not happen automatically in any case, and automatic upgrades are no excuse for sloppy patch and package management, but automatic updates can be helpful as yet another security measure.

    security_autoupdate_blacklist: []

(Debian/Ubuntu only) A listing of packages that should not be automatically updated.

    security_autoupdate_reboot: false

(Debian/Ubuntu only) Whether to reboot when needed during unattended upgrades.

    security_autoupdate_reboot_time: "03:00"

(Debian/Ubuntu only) The time to trigger a reboot, when needed, if `security_autoupdate_reboot` is set to `true`. In 24h "hh:mm" clock format.

    security_autoupdate_mail_to: ""
    security_autoupdate_mail_on_error: true

(Debian/Ubuntu only) If `security_autoupdate_mail_to` is set to an non empty value, unattended upgrades will send an e-mail to that address when some error occurs. You may either set this to a full email: `ops@example.com` or to something like `root`, which will use `/etc/aliases` to route the message. If you set `security_autoupdate_mail_on_error` to `false` you'll get an email after every package install.

## Dependencies

None.

## Example Playbook

```yaml
- hosts: servers

  roles:
    - { role: asapdotid.security }
```

## License

MIT (Expat) / BSD

## Author Information

This role was created in 2014 by [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).

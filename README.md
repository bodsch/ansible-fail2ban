

An Ansible Role that installs and configure fail2ban 2.x on Debian/Ubuntu, RHEL/CentOS, ArchLinux and ArtixLinux (mabybe also on Gentoo based Systemes).


[![GitHub Workflow Status](https://img.shields.io/github/workflow/status/bodsch/ansible-fail2ban/CI)][ci]
[![GitHub issues](https://img.shields.io/github/issues/bodsch/ansible-fail2ban)][issues]
[![GitHub release (latest by date)](https://img.shields.io/github/v/release/bodsch/ansible-fail2ban)][releases]

[ci]: https://github.com/bodsch/ansible-fail2ban/actions
[issues]: https://github.com/bodsch/ansible-fail2ban/issues?q=is%3Aopen+is%3Aissue
[releases]: https://github.com/bodsch/ansible-fail2ban/releases


## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

`fail2ban_ignoreips`

can be an IP address, a CIDR mask or a DNS host.

`fail2ban_conf`

`fail2ban_jail`

`fail2ban_path_definitions`

`fail2ban_jails`

`fail2ban_jail`


## Dependencies

None.

## Example Playbook

```
fail2ban_ignoreips:
  - 127.0.0.1/8
  - 192.168.0.0/24

fail2ban_conf:
  default:
    dbpurgeage: 5d

fail2ban_jail:
  default:
    bantime: 3200

fail2ban_jails:
  - name: ssh
    enabled: true
    port: ssh
    filter: sshd
    logpath: /var/log/authlog.log
    findtime: 12h
    bantime: 2w
    maxretry: 2
  - name: ssh-breakin
    enabled: true
    port: ssh
    filter: sshd-break-in
    logpath: /var/log/authlog.log
    maxretry: 2
  - name: ssh-ddos
    enabled: true
    port: ssh
    filter: sshd-ddos
    logpath: /var/log/authlog.log
    maxretry: 2
```

## License

Apache License 2.0

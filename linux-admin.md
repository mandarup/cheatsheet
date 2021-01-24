


- Security Audit

```sh
# reference: https://www.2daygeek.com/check-track-successful-failed-login-attempts-linux/

# install auditd
$ sudo apt-get install auditd

# By default the audit daemon will start, if not use the following commands to kikstart.
$ sudo systemctl start auditd

# then collect event summary using, e.g.
# success logins
$ aureport -l --success --summary -i | more
# failed logins
$ aureport -l --failed | more
$ aureport -l --failed --summary -i | more
$ aureport -l --failed --summary -i | tail
$ aureport -l --failed  -i | tail

```


# fail2ban

Ref: 
- https://github.com/BetterWayElectronics/secure-wireguard-implementation
- https://www.vultr.com/docs/how-to-further-secure-ssh-with-a-port-knocking-sequence-on-ubuntu-18-04
- https://help.ubuntu.com/community/PortKnocking

```sh
$sudo apt install  fail2ban
# confirm service has started
$systemctl status fail2ban.service
# check status
$sudo fail2ban-client status sshd
```






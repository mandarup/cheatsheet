


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

```

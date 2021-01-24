


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
- 
- 

```sh
$sudo apt install  fail2ban
# confirm service has started
$systemctl status fail2ban.service
# check status
$sudo fail2ban-client status sshd
```


# knockd port-knocking
References
- https://www.techrepublic.com/article/how-to-obscure-open-ports-with-knockd/
- https://www.vultr.com/docs/how-to-further-secure-ssh-with-a-port-knocking-sequence-on-ubuntu-18-04
- https://help.ubuntu.com/community/PortKnocking

```sh
$apt-get install knockd

# add knocking sequence in this file
$sudo nano /etc/knockd.conf

# se the service to start at boot
$sudo nano /etc/default/knockd
START_KNOCKD=1
KNOCKD_OPTS="-i ens3"
# in this case ens3 is the ethernet interface, verify what's yours via ifconfig or ip a
```



# Firewall

If working with iptbles instead of ufw,
** here is a FOR argument in favor of iptables https://spyhce.com/blog/using-iptables-instead-ufw-basic-server-setup
To be fair, if you do decide to use iptables in the initial configuration of your server, please bear in mind these two other commands which you need. First of all, and before configuring anything, make sure you don't lock yourself out of your connection by accepting the current established connection with this command: sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT. Then, whenever you have finished defining rules for your incoming connections, block everything else: sudo iptables -A INPUT -j DROP. This appends a rule to ignore all connections that don't fall into one of the filters specified before in the rules chain for INPUT.



## Making UFW work with Docker
References
- https://medium.com/@bitaps.com/ubuntu-ufw-and-docker-security-e840f772e2b4
- https://spyhce.com/blog/using-iptables-instead-ufw-basic-server-setup

- Problem

- Solution 
First way: do not expose ports, use --net=host options for containers

Second way: disable this Docker behaviour by creating or modifying /etc/docker/daemon.json
```sh
$sudo nano /etc/docker/daemon.json
{ "iptables": false }
$sudo service docker restart
```


# UFW
 If run into issue, start with reset
```
 sudo ufw reset
 sudo ufw default deny incoming
 sudo ufw default deny outgoing
 sudo ufw limit ssh
 sudo ufw allow out 53
 sudo ufw logging on
 sudo ufw enable


# vpn seems to work with just these rules.

# not sure why below http/s aren’t needed
 sudo ufw allow out http
 sudo ufw allow in http 
 sudo ufw allow out https
 sudo ufw allow in https

#sudo ufw allow svn
 #sudo ufw allow git
 sudo ufw disable && sudo ufw enable
 
 
#Ufw logging
$sudo ls /var/log/ufw*
# to watch 
$sudo tail -f /var/log/ufw*
# or just see las n
$sudo tail  /var/log/ufw*

```

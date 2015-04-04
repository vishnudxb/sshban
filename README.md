# sshban
# Allow ssh logins only from your preferred countries. 

* The main reason for this script is to block all ssh logins excpet from some countries. In this script I am allowing only US and INDIA for SSH Logins.

* You need to install geoip-bin & geoip-database.


```
$ sudo apt-get install geoip-bin geoip-database

```
* Make sure it works by doing
```
$ sudo geoiplookup 8.8.8.8

```
* Copy this script to your  /usr/local/bin/
* Then use your /etc/hosts.deny and /etc/hosts.allow to control your SSHD.
* In /etc/hosts.deny add the below line
```
sshd: ALL

```
* In /etc/hosts.allow add the below line
```
sshd: ALL: aclexec /usr/local/bin/sshban.sh %a

```
* For testing the scipt, Run the below command
```
/usr/local/bin/sshban.sh 202.176.195.17

```
* Here if the IP is from US and INDIA, it will allow ssh connection, if its from any other country, it won't and
you can see the logs on /var/log/messages or /var/log/syslog like below

```
Apr 05 11:59:54 pi logger: DENY sshd connection from 202.176.195.17 (SG)

``` 
	


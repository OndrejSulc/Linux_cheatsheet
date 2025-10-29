# Fail 2 ban

Install
```
sudo apt install fail2ban
```

-------------------
#### Check count of jails (only sshd is enabled by default)
```
fail2ban-client status
```
output:
> Status  
> |- Number of jail:	1  
> `- Jail list:	sshd

------------
#### Check specific jail status (sshd)
```
fail2ban-client status sshd
```
output:
```
  Status for the jail: sshd
  |- Filter
  |  |- Currently failed:	1
  |  |- Total failed:	68
  |  `- Journal matches:	_SYSTEMD_UNIT=ssh.service + _COMM=sshd
  `- Actions
     |- Currently banned:	3
     |- Total banned:	10
     `- Banned IP list:	2.57.121.25 2.57.121.112 165.154.233.77
```


------------------------------
#### List of IP addresses which attempted to login

```
journalctl -u ssh.service | grep -E "Accepted|Failed" | grep -oE '[0-9]+\.[0-9]+\.[0-9]+\.[0-9]+' | sort | uniq -c | sort -nr
```
output:
```
476 165.154.233.77
307 206.189.110.212
240 41.94.88.219
106 45.135.232.92
```


----------------------------------
#### Ban IP
```
fail2ban-client set sshd banip 165.154.233.77
```


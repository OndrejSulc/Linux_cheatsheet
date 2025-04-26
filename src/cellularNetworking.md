# Cellular Networking

There is system daemon "ModemManager" with "mmcli" as client that is
used by NetworkManager

 
Modify config
```
vi /lib/systemd/system/ModemManager.service
```
```
ModemManager --help
```
## Review connected modem

1) scan modems
```
mmcli --scan-modems
```

2) list available modems
```
mmcli --list-modems
```
From output, get ID of mode. following modem has ID = 1
> /org/freedesktop/ModemManager1/Modem/1 [huawei] E3372


3) check modem is healthy (change ID according to previous step)
```
mmcli --modem=1
```

## Connect
simple connect with t-mobile sim (might not be supported by device)
```
mmcli -m 0 --simple-connect="apn=internet.t-mobile.cz"
```

check modem is healthy (change ID according to previous step)  
It should show that status = connected
It should also contain bearer
```
mmcli --modem=1
```

check bearer
```
mmcli --modem=1 --bearer=0
```


## If connection is not settled

DHCP config
```
udhcpc -q -f -n -i wwan0
```


## Old way 

get signal 
qmicli -d /dev/cdc-wdm0 --nas-get-signal-info

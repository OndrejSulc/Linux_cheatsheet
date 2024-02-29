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
## Connection

connect with t-mobile sim
```
mmcli -m 0 --simple-connect="apn=internet.t-mobile.cz"
```

DHCP config
```
udhcpc -q -f -n -i wwan0
```


## Old way 

get signal 
qmicli -d /dev/cdc-wdm0 --nas-get-signal-info

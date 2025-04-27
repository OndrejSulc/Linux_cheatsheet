# Network manager

list all registered network devices
```
nmcli device
```

Add new ethernet connection bound to inteface eth1
```
nmcli connection add type ethernet con-name my_ethernet1 ifname eth1
```

Add new wwan0 connection
```
nmcli connection add type gsm ifname wwan0 con-name my_wwan0
```

## Configuration files
connections are stored in `/etc/NetworkManager/system-connections/<file>.nmconnection` files


#### /etc/NetworkManager/NetworkManager.conf
Main manager config file

ifupdown means it will cover interfaces form /etc/network/interface
```
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true
```


## Manually created GSM connection

```
nmcli connection edit type gsm con-name "My GSM Connection"
```

```
#(Inside the config tool)
set gsm.apn internet.t-mobile.cz
```



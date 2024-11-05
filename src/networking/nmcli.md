# Network manager

list all registered network devices
```
nmcli device
```

Add new ethernet connection bound to inteface eth1
```
nmcli connection add type ethernet con-name my_ethernet1 ifname eth1
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

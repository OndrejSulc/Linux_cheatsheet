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

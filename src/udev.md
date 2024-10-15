# udev

udev is manager for devices that are under /dev directory
on linux it is running as `systemd-udevd.service`

## new devices
kernel 
```
dmesg
```

list udev events and get `path`
```
udevadm monitor
```

get device info based on path
```
udevadm info --attribute-walk --path=... e.g. /devices/pci0000:00/0000:00:14.0/usb1/1-2
```

udev info about current /dev/** device
```
udevadm info
udevadm info --attribute-walk --name /dev/ttyUSB0
udevadm info -q all -n /dev/ttyUSB0
```


list usb devices
```
lsusb
```




## rules
udev rules are usually in directory `/etc/udev/rules.d `
when new device is connected, udev go

into file 

```
SUBSYSTEM=="tty", ATTRS{serial}=="A800dRam", SYMLINK+="usbrelay0"
or 
SUBSYSTEM=="tty", ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6001", SYMLINK+="tty%E{ID_MODEL}"
```

## after changes
```
udevadm control --reload
reboot
```

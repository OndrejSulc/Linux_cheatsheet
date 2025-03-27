# Qemu

`/dev/kvm` kernel virtualization api


## Installation
Install qemu
```
sudo apt install qemu-utils qemu-system-x86 qemu-system-gui
```

Install virt-manager - UI for managing qemu instances
```
sudo apt install virt-manager
```

## New device
https://wiki.debian.org/QEMU

Create hard disk image
```
$ qemu-img create debian.img 2G
```


Run image
```
qemu-system-x86_64 -hda debian.img -m 4G
```

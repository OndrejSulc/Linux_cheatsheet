# chroot
## Create chroot jail for testing on linux

```bash
mkdir chroot-jail
sudo apt install debootstrap
sudo debootstrap bookworm chroot-jail
```


## Start chroot jail

```bash
sudo chroot chroot-jail /bin/bash
```

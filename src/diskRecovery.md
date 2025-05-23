# Disk recovery

## Sources
https://wiki.archlinux.org/title/File_recovery

## Backup and restore

compressed disk copy (assuming healthy disk - otherwise use ddrescue)
```
dd if=/dev/INPUT/DEVICE-NAME-HERE conv=sync,noerror bs=64K | gzip -c > /path/to/my-disk.image.gz
```

write back
```
gunzip -c IMAGE.HERE-GZ | dd of=/dev/OUTPUT/DEVICE-HERE
```

send image to remote storage
```
dd if=/dev/INPUT conv=sync,noerror bs=64K | gzip -c | ssh <user>@<ip> 'dd of=myimage.image.gz'
```

create disk image from disk on remote server
(note `sudo`) - might be needed to temporarily set passwordless sudo
```
ssh <user>@<ip> "sudo dd if=/dev/INPUT conv=sync,noerror bs=64K | gzip -c" > myimage.image.gz
```


## Analysis

Install SMART monitoring tools
```
sudo apt-get install smartmontools
```

Print disk info
```
smartctl -x /dev/sdd
```

## Carving
https://wiki.archlinux.org/title/Foremost

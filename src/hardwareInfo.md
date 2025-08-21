# Hardware information and management

Device manager equivalent + benchmarking software
```
hardinfo
```

Disk usage (general overview)
```
df -H
```

Directory size
```
du -sh <directory>
```

List top 5 directories with the most disk usage to depth 1 (in the entire system - `/`)
```
du -BM --max-depth=1 / | sort -n | tail -n 5 
```

List top 10 directories in current dir (`.`) subdir with the most disk usage to depth 3 (use in `/var` - useful for docker)
```
du -BM --max-depth=3 . | sort -n | tail -n 5 
```

Display messages in kernel ring buffer
```
dmesg
```

Display some hardware info
```
cat /proc/<provided option>

# examples
cat /proc/cpuinfo # Display CPU information
cat /proc/meminfo # Display memory information
```

Print the file name of the terminal connected to standard input
```
tty
```

Display free and used RAM memory ( -h for human readable, -m for MB, -g for GB.)
```
free -h
```

Display PCI devices
```
lspci -tv
```

Display USB devices
```
lsusb -tv
```

Display DMI/SMBIOS  (The DMI table describes what the system is currently made of)  
see `man dmidecode`
```
dmidecode
```

Test for unreadable blocks on disk sda
```
badblocks -s /dev/sda
```


Show info about ATA disk (/dev/sda)
```
hdparm -i /dev/sda
```

## Temperature
Check CPU temperature without 3rd party software (58000 = 58°C)
```
cat /sys/class/thermal/thermal_zone*/temp
```

Perform a read speed test on disk sda
```
hdparm -tT /dev/sda
```



## Move /var to bigger partition
1) `fdisk` to create new partition in free space
2) `mkfs.ext4 /dev/sdaX` to format it
3) `mount /dev/sdaX /mnt` to mount it
4) `cp /var /mnt -r` copy content of var
5) `blkid /dev/sdaX` get UUID of partition
6) edit `/etc/fstab` so /var is always mounted correctly
```
UUID=uuid-from-blkid   /var   ext4   defaults   0   2
```




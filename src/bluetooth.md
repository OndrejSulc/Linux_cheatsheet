## Bluetooth debug

Usefull tools:

- hcitool
- hciconfig
- hcidump
- bluetoothctl

Bluetooth rssi
```
hcitool cc <MAC> && hcitool rssi <MAC> && hcitool dc <MAC>
```

Dump for wireshark
```
hcidump -i <bt interface> --save-dump=file.pcap
```


## Bluetooth debug

Usefull tools:

- hcitool
- hciconfig
- hcidump
- bluetoothctl

Install:
- bluez (C library for bluetooth)
- pybluez (python wrapper for bluez)
- bluez-hcidump
  

List bluetooth interfaces
```
hcitool devices
```

Bluetooth rssi
```
hcitool cc <MAC> && hcitool rssi <MAC> && hcitool dc <MAC>
```

Dump for wireshark
```
hcidump -i <bt interface> --save-dump=file.pcap
```


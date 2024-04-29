## Wireguard VPN
Tools 

- wireguard
- wireguard-tools
- wg-quick

```
sudo apt install wireguard wireguard-tools iproute2 -y
```

Generate key pair
```
wg genkey | tee privatekey | wg pubkey > publickey
```

Default path
```
/etc/wireguard/wg0.conf
```

Connect to VPN with config file:
```
wg-quick up ./wg0.conf
```

Auto setup after reboot
```
systemctl enable wg-quick@wg0.service
```


Config file wg0.conf (name of file determines name of created network interface)
```
[Interface]
Address = <assigned address with CIDR>
PrivateKey = <your private key>

[Peer]
PublicKey = <server public vpn key>
AllowedIPs = 10.0.0.0/16 #which ip addresses
Endpoint = 10.20.30.40:51820 #endpoint with VPN server
PersistentKeepalive = 25 (optional for endpoint devices to ping every 25s to keep connection active)
```

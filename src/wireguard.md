## Wireguard VPN
Tools 

- wireguard
- wireguard-tools


Generate key pair
```
wg genkey | tee privatekey | wg pubkey > publickey
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

Connect to VPN with config file:
```
wg-quick up ./wg0.conf
```


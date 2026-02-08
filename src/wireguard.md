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


Peer behind NAT config file wg0.conf (name of file determines name of created network interface)
```
[Interface]
Address = <assigned address with CIDR> #192.168.10.2/32
PrivateKey = <your private key>

[Peer]
PublicKey = <server public vpn key> 
AllowedIPs = 192.168.10.0/24 #which ip addresses
Endpoint = 10.20.30.40:<server port> #public endpoint with VPN server
PersistentKeepalive = 25 (optional for endpoint devices to ping every 25s to keep connection active)
```

Peer with public IP
```
[Interface]
Address = 192.168.10.1/32
SaveConfig = true
ListenPort = <server port>
PrivateKey = <server public vpn key> 
# Some PostUp and PreDown rules should be added.

[Peer]
PublicKey = <peer pub key>
AllowedIPs = 192.168.10.3/32
Endpoint = 10.20.30.41:<server port> #public endpoint with VPN server

[Peer]
PublicKey = <peer pub key>
AllowedIPs = 192.168.10.2/32
PersistentKeepalive = 25 # just in case other side forgot it
```


Firewall routing on server
```
sudo ufw route allow in on wg0 out on wg0
```


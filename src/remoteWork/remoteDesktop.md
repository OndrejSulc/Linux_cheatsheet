# Remote desktop


## Setup server

XRDP server is free & opensource.

Install
```
sudo apt install xrdp xorg xorgxrdp xfce4 xfce4-goodies dbus-x11 x11-xserver-utils -y
```


Config
```
sudo nano /etc/xrdp/xrdp.ini
sudo nano /etc/xrdp/sesman.ini
```


Sesman is default session manager for xrdp. It uses group `tsusers` to authorize which users can use remote desktop
```
sudo groupadd tsusers
sudo usermod -a -G tsusers user

sudo groupadd tsadmins
sudo usermod -a -G tsadmins user
```


Setup xrdp to use XFCE
```
echo "xfce4-session" > ~/.xsession
```


Finish
```
sudo systemctl restart xrdp
sudo systemctl enable xrdp
```

## Setup client

Remmina is default client for remote desktop.

Config:
- protocol: RDP - Remote Desktop Protocol
- Server: 10.8.0.xxx:3389 (3389 is default XRDP server port)
- username: username just like ssh
- password: just like ssh

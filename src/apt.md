# APT - management of packages

## Commands

List installed packages
```
apt list --installed
```

List manually installed packages
```
apt list --installed | grep -v automatic
```

## Files

files are stored in `/etc/apt/` directory

### keys
- /etc/apt/trusted.gpg - old way where to store keys
- /etc/apt/trusted.gpg.d/

### sources
- /etc/apt/sources.list - old way where to store keys
- /etc/apt/sources.list.d/

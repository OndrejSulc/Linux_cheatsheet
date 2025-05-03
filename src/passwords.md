# Passwords

Generate easy to remember and type password (10 is lenght)
```
pwgen -cn1 10
```

Generate safer password (good for copy paste)
```
pwgen -cns1v 20
```



### Passwords management:

- "Passwords" (GNOME Keyring data) are stored in ~/.local/share/keyrings
- "Secure Shell" data (SSH keys) are stored in ~/.ssh
- "PGP Keys" (including GPG keys) are stored in ~/.gnupg

# System audit and logs

## Login tracking and user activity

### Important files
Following files can be reviewed with `last`
```
sudo last /var/run/utmp
```
`/var/log/btmp` records failed login attempts

`/var/run/utmp` allows one to discover information about who is **currently** using the system.
This file will contain information on a user's logins: on which terminals, logouts,
system events and the current status of the system, system boot time (used by uptime) etc.`

`/var/log/wtmp` provides an **historical** record of `utmp` data.

### Log ~/.bash_history

If you want to review what does the user type in the shell (but not what the result of that is) you can setup
a system-wide /etc/profile that configures the environment so that all commands are saved into a
history file. 

```
HISTFILE=~/.bash_history
HISTSIZE=10000
HISTFILESIZE=999999
# Don't let the users enter commands that are ignored
# in the history file
HISTIGNORE=""
HISTCONTROL=""
readonly HISTFILE
readonly HISTSIZE
readonly HISTFILESIZE
readonly HISTIGNORE
readonly HISTCONTROL
export HISTFILE HISTSIZE HISTFILESIZE HISTIGNORE HISTCONTROL
```

You need also to set the append-only option using chattr program for .bash_history for all users otherwise they can wipe history with `> .bash_history`
```
chattr -a ~/.bash_history
```

Verify with
```
lsattr ~/.bash_history
```


## System journal
Debian uses either systemd's journald or Rsyslog. Both support sending logged messages to remote.

### systemd-journald

There are additional `systemd-journal-x` services called `upload`(client) and `remote`(server)
```
journalctl
```

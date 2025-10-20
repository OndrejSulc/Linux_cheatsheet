# Xorg

--------------
```
cd /home/kiosk/.local/share/xorg/
root@podium:/home/kiosk/.local/share/xorg# ls
Xorg.0.log           Xorg.0.log.old       Xorg.0.log.segfault
```

--------------------
```
cd /usr/share/X11/xorg.conf.d/
root@podium:/usr/share/X11/xorg.conf.d# ls
10-evdev.conf      10-quirks.conf     40-libinput.conf   99-tpk-touch.conf
```

------------------------------

```
root@podium:/etc/udev/rules.d# ls  
99-tpk-touchscreen.rules  touchscreen.rules
root@podium:/etc/udev/rules.d# cat 99-tpk-touchscreen.rules 
ATTRS{name}=="TPK USA LLC Touch Fusion 4.", ENV{ID_INPUT_TOUCHSCREEN}="1", ENV{ID_INPUT_KEYBOARD}="0"

root@podium:/etc/udev/rules.d# cat touchscreen.rules 
# There are a number of modifiers that are allowed to be used in some
# of the different fields. They provide the following subsitutions:
#
# %n the "kernel number" of the device.
#    For example, 'sda3' has a "kernel number" of '3'
# %e the smallest number for that name which does not matches an existing node
# %k the kernel name for the device
# %M the kernel major number for the device
# %m the kernel minor number for the device
# %b the bus id for the device
# %c the string returned by the PROGRAM
# %s{filename} the content of a sysfs attribute
# %% the '%' char itself
#

# Create a symlink to any touchscreen input device

```
SUBSYSTEM=="input", KERNEL=="event[0-9]*", ATTRS{modalias}=="input:*-e0*,3,*a0,1,*18,*", SYMLINK+="input/touchscreen0"
SUBSYSTEM=="input", KERNEL=="event[0-9]*", ATTRS{modalias}=="ads7846", SYMLINK+="input/touchscreen

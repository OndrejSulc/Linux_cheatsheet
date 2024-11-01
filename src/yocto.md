# Yocto
```
kas shell <kas config path> -c "bitbake virtual-kernel:do_configure -f"
```


## Kernel configuration

virtual-kernel is replaced by BSP - for example linux-ktn

```
bitbake virtual-kernel:do_menuconfig
bitbake virtual-kernel:do_savedefconfig
```

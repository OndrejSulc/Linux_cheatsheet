# Yocto
```
kas shell <kas config path> -c "bitbake virtual-kernel:do_configure -f"
```


## Kernel configuration

(virtual/kernel is automatically replaced by used kernel)

Start modifying Kernel
```
kas shell config_file.yml -c "bitbake virtual/kernel:do_menuconfig"
```

Save created modifications of Kernel
```
kas shell config_file.yml -c "bitbake virtual/kernel:do_savedefconfig"
```

Lock git subrepos checkouts
```
kas lock config_file.yml
```

Show recipes available in KAS config
```
kas shell config_file.yml -c "bitbake-layers show-recipes"
```

see how specific recipe is built
```
kas shell config_file.yml  -c "bitbake -c compile -v chromium-x11"
```

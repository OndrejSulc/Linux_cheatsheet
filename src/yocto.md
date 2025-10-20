# Yocto
```
kas shell <kas config path> -c "bitbake virtual-kernel:do_configure -f"
```

## File watches
```
echo "165536" | sudo tee /proc/sys/fs/inotify/max_user_watches
```

## bmap tools
1) umount the device first but do not eject so it still appears in `lsblk`
2) use bmap tool to copy image to the device
```
sudo bmaptool copy image.hddimg --nobmap /dev/sdc
sudo bmaptool copy image.img --bmap image.bmap /dev/sdX
```

## Build KAS config
add to `local_conf_header:`
```
  quicker: |
    # What SSTATE_DIR should be used (use your own path instead)
    SSTATE_DIR ?= "/media/ondra/dalsimisto/lgmc-edge-images/lgmc-edge-images/sstate-cache"

    # Limit BitBake to 10 parallel tasks
    BB_NUMBER_THREADS = "9"

    # Limit make (used during compilation) to 10 threads
    PARALLEL_MAKE = "-j9"
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

Show layers available in KAS config
```
kas shell config_file.yml -c "bitbake-layers show-layers"
```

see how specific recipe is built
```
kas shell config_file.yml  -c "bitbake -c compile -v chromium-x11"
```

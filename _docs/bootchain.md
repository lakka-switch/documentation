---
title: Current boot chain
permalink: /docs/bootchain/
---

0. Switch is in RCM
1. Exploit is triggered, hekate runs
2. hekate loads and runs coreboot through `coreboot.rom` 
3. coreboot loads and runs u-boot
4. u-boot mounts the SD card and runs the `lakka/boot/boot.scr` boot script
    1. loads the kernel and device tree from the SD card
    2. sets the kernel boot arguments
    3. resets USB and boots the kernel
5. The kernel is packed with an init ramdisk - the init script :
    1. Checks and mounts the SD card in `/flash`
    2. Bind mounts `/flash/lakka/storage` as `/storage`
    3. Mounts the `/flash/lakka/SYSTEM` squashfs image as root filesystem

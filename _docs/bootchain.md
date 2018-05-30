---
title: Current boot chain
permalink: /docs/bootchain/
---

0. Switch is in RCM
1. Exploit is triggered, CBFS is sent over USB
2. The CBFS payload requests coreboot, which is loaded
3. coreboot loads u-boot with `run distro_bootcmd` as a boot command
4. u-boot loads `boot.scr` from the FAT32 partition of the SD card
5. From `boot.scr`, u-boot :
    1. loads the kernel and device tree from the SD card
    2. sets the kernel boot arguments
    3. resets USB and boots the kernel
6. The kernel is packed with an init ramdisk - the init script :
    1. Checks and mounts both partitions of the SD card
        * FAT32 partition in `/flash`
        * ext4 partition in `/storage`
    2. Mounts the `/flash/SYSTEM` squashfs image as root filesystem

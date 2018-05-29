---
title: Installing Lakka on your Switch
layout: page
---

{% include disclaimer.html %}

## Step 0 : what you need

* A first generation Switch
* A spare SD card of at least 2Gb, formatted in FAT32
* A way to put your Switch into RCM [(see this guide)](https://xghostboyx.github.io/RCM-Guide/)
* A host PC to setup the SD card
* A way to run the exploit : 
    * A PC on Windows or Linux
    * A Mac
    * An Android device with USB OTG
    
## Step 1 : preparing the SD card

### The easy way (recommended, formats your SD card)

1. Download the latest compressed image from [here](https://natinusala.cheats-inc.org/natinusala/lakka-switch/archives/images/) (use your brain to grab the latest)
2. Extract the image using the archiver of your choice (7-Zip wink wink)
3. Burn the image to the SD card (**everything will be erased**)
    * Either by using [Etcher](https://etcher.io/)
    * Or by using the `dd` command directly
    
### The hard way (manual partitioning)

1. Download the latest archive from [here](https://natinusala.cheats-inc.org/natinusala/lakka-switch/archives/updates/) (use your brain to grab the latest)
2. Make sure that the first partition is FAT32 formatted
3. Add an ext4 partition to your SD card with size of your choice - this will be the storage partition
4. Extract the right files from the archive to the root of the **FAT32 partition** (replace everything) :
    * `KERNEL`, `KERNEL.md5`, `SYSTEM` and `SYSTEM.md5` (contains the read-only system partition and the kernel)
    * the content of the directory `3rdparty/bootloader` (contains the boot script and device tree)
5. (advanced) If you want to set _another_ partition as storage, remake `boot/boot.scr` using `mkimage` and change the `disk` variable of the boot command

## Step 2 : booting Lakka

Once your SD card is set up, put it back in your Switch.

{% include first_boot.html %}

## Booting from Windows

## Booting from Linux & Mac OS

## Booting from an Android device



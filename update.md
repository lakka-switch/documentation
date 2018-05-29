---
title: Updating Lakka
layout: page
---

## Automatic update

1. Download the **latest** archive from [this repository](https://natinusala.cheats-inc.org/natinusala/lakka-switch/archives/updates/) (use your brain to grab the latest)
2. Using a method of your choice, copy the archive to the `.update` directory of the **storage partition**
3. The next (re)boot will automatically update your installation

## Manual update

1. Download the **latest** archive from [this repository](https://natinusala.cheats-inc.org/natinusala/lakka-switch/archives/updates/) (use your brain to grab the latest)
2. Using a method of your choice, extract the right files from the archive to the root of the **FAT32 partition** (replace everything) :
    * `KERNEL`, `KERNEL.md5`, `SYSTEM` and `SYSTEM.md5` (contains the read-only system partition and the kernel)
    * the content of the directory `3rdparty/bootloader` (contains the boot script and device tree)

---
title: Updating Lakka
layout: page
---

## How to update

**TL;DR** The same as you did to install it : download the tarball and extract it

1. Download the latest archive from [here](https://natinusala.cheats-inc.org/natinusala/lakka-switch/releases/) (use your brain to grab the latest)
2. Extract the content of the directory in the archive to the root of your SD card
    * Windows users can use 7-Zip
    * You should have updated two folders, `boot` and `lakka`
    
## Migrating from an old installation (new partitions layout)

The 04/07/18 update changed the partitions layout - the "storage partition" is no longer an ext4 partition, as it has been replaced by a directory in the FAT32 partition. This allows everything to be centralized in one partition, and allows files to be modified from Windows more easily.

When applying this update, you will want to remove the now unused ext4 partition. Here is a quick guide depending on how you want to do it :

### Cleaning up the old installation

First, start by deleting those files :
* `KERNEL`
* `KERNEL.md5`
* `SYSTEM`
* `SYSTEM.md5`

### If you don't care about saving your data

Warning : your Lakka installation will be reset and you will loose everything (games, saves, configuration...) !

* If you know how to use a partition manager, just remove the ext4 partition and resize the FAT32 partition at your convenience
* If you don't know how to use a partition manager :
    1. Backup everything on your FAT32 partition
    2. Format the entire card to FAT32 (use [SDFormatter](https://www.sdcard.org/downloads/formatter_4/))
    3. Put your files back

Then, you can [install the new Lakka](https://lakka-switch.github.io/documentation/installation.html).
    
### If you care about saving your data

1. Backup everything on your storage partition
2. Remove it :
    * If you know how to use a partition manager, just remove the ext4 partition and resize the FAT32 partition at your convenience
    * If you don't know how to use a partition manager :
        1. Backup everything on your FAT32 partition
        2. Format the entire card to FAT32 (use [SDFormatter](https://www.sdcard.org/downloads/formatter_4/))
        3. Put your FAT32 files back
3. [Install the new Lakka](https://lakka-switch.github.io/documentation/installation.html)
4. Restore the storage partition content : files should be put in `lakka/storage`
5. **Delete `lakka/storage/.config/retroarch/retroarch.cfg` !**

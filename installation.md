---
title: Installing Lakka on your Switch
layout: page
---

{% include disclaimer.html %}

## Step 0 : what you need

* A fusée gelée vulnerable Switch
* A SD card of at least 2Gb, formatted in FAT32
    
## Step 1 : preparing the SD card

0. Make sure that your SD card is FAT32 formatted, _exFAT will not work_
1. Download the latest stable archive from [here]({% include download_link.html %}) (use your brain to grab the latest)
2. Extract the content of the directory in the archive to the root of your SD card
    * Windows users can use 7-Zip
    * You should have two folders, `lakka` and `bootloader`

## Step 2 : booting Lakka

To boot Lakka, you need a working installation of [hekate](https://github.com/CTCaer/hekate/releases) 4.0 (or later) on the Switch. We won't cover this topic here, as there are multiple guides already existing.

Here are some softwares you can use :
  * Windows : [TegraRcmSmash](https://github.com/rajkosto/TegraRcmSmash), [fusee-launcher](https://github.com/Cease-and-DeSwitch/fusee-launcher)
  * Linux, Mac OS : [fusee-launcher](https://github.com/Cease-and-DeSwitch/fusee-launcher)
  * Android : [NXLoader](https://github.com/DavidBuchanan314/NXLoader/releases), [Rekado](https://github.com/MenosGrante/Rekado) _(don't use the Lakka launcher)_
  * iOS : [NXBoot](https://mologie.github.io/nxboot/)

Once hekate is running on your Switch, you can boot Lakka by going to `Launch > More configs > Lakka`.

## Autoboot

If going through the menu each time annoys you, you can ask hekate to autoboot Lakka by going to to `Launch options > Auto boot > More configs > Lakka`.

## Now what ?

I suggest you read the FAQ, especially on how to access the storage partition and copy games. Actually, while you're here, read everything. Enjoy !

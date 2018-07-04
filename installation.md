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
* An USB cable to plug the Switch in and run the exploit (USB C-to-C or C-to-A)
    
## Step 1 : preparing the SD card

0. Make sure that your SD card is FAT32 formatted, _exFAT will not work_
1. Download the latest archive from [here](https://natinusala.cheats-inc.org/natinusala/lakka-switch/releases/) (use your brain to grab the latest)
2. Extract the content of the directory in the archive to the root of your SD card
    * Windows users can use 7-Zip
    * You should have two folders, `boot` and `lakka`

## Step 2 : booting Lakka

Once your SD card is set up, put it back in your Switch.

### Booting from Windows

**Preparation work**

You will first need to install the required driver :

1. Get your Switch in RCM mode and plug it into your PC
    * It should appear as "APX" in Windows
2. Download and run the Zadig Driver Installer from here : https://zadig.akeo.ie/ 
3. In the list, choose the device "APX"
    * If it's not showing up, check "List all devices" in the options
4. At the right end of the green arrow, choose "libusbK (v3.0.7.0)"
5. Click on the big "Install driver" button

**Booting**

1. Download and extract [this archive](https://github.com/lakka-switch/boot-scripts/archive/master.zip)
2. Put your Switch into RCM
3. Run `windows-boot.bat` (or `windows-win32-boot.bat` on a 32bit machine)

### Booting from Linux or Mac OS

**Preparation work**

Install Python 3 (usually already installed). Open a terminal to install the required package : `pip3 install pyusb==1.0.0`. I let you deal with permissions issues.

**Booting**

1. Download and extract [this archive](https://github.com/lakka-switch/boot-scripts/archive/master.zip)
2. Put your Switch into RCM
3. Run the `linux-macos-boot.sh` script from this repository's folder. Again, I let you deal with permissions issues (if it cannot find the module `usb` it means that you have insufficient permissions).

### Booting from an Android device

**Preparation work**

1. Download and install the latest release of [this app](https://github.com/lakka-switch/switch_linux_launcher/releases/latest)
2. Run it - it will tell you that some files are missing, remember the folder in the dialog, it should look like one of these :
    * `/storage/emulated/0/Android/data/io.mrarm.switchlinuxlauncher.noimx/files/shofel2`
    * `/sdcard/Android/data/io.mrarm.switchlinuxlauncher.noimx/files/shofel2`
4. Exit the app (if you can close the task using the multitask button it's better)
5. From the `payloads` folder of [this repository](https://github.com/lakka-switch/boot-scripts), copy the `cbfs.bin` and `coreboot.rom` files to the `shofel2` folder on your Android device (the folder of the previous step)
6. Run the app again - if the dialog doesn't show up then you can go on, otherwise you did something wrong
7. (Optional) Depending on your device, you might need to enable "OTG" or "OTG Storage" in the Android settings

**Booting**

1. Plug your Switch in your Android device
    * If the Switch is charging from your phone, you can go on
    * If your phone is charging from the Switch, try to reverse the cabling so that your phone charges the Switch instead
    * If nothing happens, I'm afraid your phone doesn't have OTG (or it's not enabled) - the exploit might not work
2. Put your Switch in RCM mode
3. Done !

## Now what ?

I suggest you read the FAQ, especially on how to access the storage partition and copy games. Actually, while you're here, read everything. Enjoy !

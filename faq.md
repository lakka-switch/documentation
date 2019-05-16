---
title: Frequently Asked Questions
layout: page
---

Here is a list of frequently asked questions and, obviously, an answer to each of them. What you want may already be listed on the [official Lakka FAQ](http://www.lakka.tv/doc/FAQ/) so check it out aswell.

&nbsp;
> **How stable and safe is Linux to use ?**

***

The battery bug has been fixed as of the 02/07/2018 update. Be sure to apply the fix from Hekate 3.0 first !

The known side-effects of using Linux on your Switch are :
* RTC (Real-Time Clock) desynchronization - this will break the date and time in Horizon. To fix that, just stay online in Horizon or reset the time manually after each time you run Lakka.
* Possible unsafe SD Card unmounting ; your PC will ask for a repair (or mount the SD Card read only), do it if you want. If `REC` files appear on the root of the card, it means that some files were corrupted. Avoid force shutting down the system (always go back to RCM first) to prevent that from happening.

&nbsp;
> **Will it brick my Switch ? Will it replace the official operating system ?**

***

**No.** Lakka boots from the SD card, it never touches the NAND of the console. It's a "dual boot", if you prefer.

&nbsp;
> **What currently works ? What doesn't ?**

***

See this tiny table for a summary of what works and what doesn't :

| Works                          | Doesn't work      |
|:------------------------------:|:-----------------:|
| Wi-Fi                                                              | Wireless Joy-Cons  |
| Audio through internal speakers, headphones and AirPlay           | Sleep mode        |
| Touch screen                                                      | Bluetooth (so no Bluetooth audio, no wireless controllers) |
| Full speed GPU driver (nvgpu) with OpenGL and Vulkan              | Dock isn't enabled due to missing wireless Joy-Cons driver     |
| Wired Joy-Cons (it means attached to the console)                |  exFAT formatted SD cards     |
| Full speed CPU, GPU and RAM (with overclock GUI)                  | Unofficial Joy-Cons (such as the Hori ones)   |
| Wireless services: SSH, SMB                       |                   |
| All types of SD Cards
| Graceful shutdown  | |
| Screen brightness control | |
| USB Device (gadget): serial console | | 

&nbsp;
> **How do I enable Vulkan ?**

***

Go to Settings > User Interface and enable Advanced Settings. Now, go back to the top of the Settings list and go to Drivers. Here, you can change the video driver from `gl` (OpenGL) to `vulkan`, or the opposite. Then, restart RetroArch for the change to take effect.

**Warning:** Do NOT set any of the drivers to `null` before restarting RetroArch! If you do so, you will need to edit the config file manually to fix it.

&nbsp;
> **Which cores support Vulkan?**

***

- All 2D / software rendered cores (PCSX ReARMed counts as software rendered)
- Beetle PSX HW
- Dolphin

Please go back to OpenGL for any core that's not in this list.

&nbsp;
> **How do I change my Wi-Fi MAC Address ?**

***

The MAC Address should be written in the chip in the factory, but for some reason Nintendo didn't do that. As a result, the MAC Address is software controlled, which means that Horizon has to manually set the address... and Lakka too. As we cannot pull the Horizon MAC from the NAND for now, Lakka uses a random address and writes it to `/storage/.config/macaddress`. If you want to use the same address as Horizon, you can by editing this file and rebooting.

&nbsp;
> **Where can I see the IP address of the Switch on my network ?**

***

From your Switch, you can see this in the first tab, Information > Network Information. From your host PC, various methods are listed [there](http://www.lakka.tv/doc/Finding-the-IP-of-your-Lakka-box/).

&nbsp;
> **How do I add games to the system ?**

***

You need to copy your games to the `lakka/storage/roms/downloads` directory on your SD card.

Once your games are copied, go to the tab which icon is a plus sign (on Lakka, on the Switch) and scan the directory where you added your game (you can just scan the top-level directory, it will go through everything recursively). If your games were recognized, new tabs will appear (one for each console) with them listed inside. If not, you can still load the game manually from the first tab.

&nbsp;
> **How do I setup Bluetooth audio ?**

***

**Please note that Bluetooth is currently broken. Do not bother trying this as it will not work.**

1. Enable Bluetooth in Services
2. Pair your headset using SSH : (use Putty on Windows, credentials are `root` and `root`)
    1. `bluetoothctl`
    2. `agent on`
    3. `scan on`
    4. Wait for your headset to show up and see its MAC address
    5. `pair XX:XX:XX:XX:XX:XX`, put the correct MAC address (protip : use tab-completion)
    6. `trust XX:XX:XX:XX:XX:XX`
    7. `connect XX:XX:XX:XX:XX:XX`
3. If the audio is choppy, make sure to update the boot/tegra210-nintendo-switch.dtb file on your SD card (take the one from the latest update archive). If it doesn't work at all, make sure that Audio driver is set to pulse and Audio and Audio sync are enabled.

&nbsp;
> **How do I setup AirPlay audio ? (thanks to @rd for this guide)**

***

Open SSH and run the command `pactl load-module module-raop-discover`. This will discover all AirPlay receivers on your network and add them as PulseAudio sinks. Then, use `pactl` to select the sink corresponding to the desired receiver. You can also use the module `module-raop-sink` to directly connect to the right receiver, given its IP (see full command below).

You can use your Android device as an AirPlay receiver by using the [AirBubble](https://play.google.com/store/apps/details?id=com.bubblesoft.android.airbubble&hl=fr) app. 

If you want to use your Android device's own hotspot with AirPlay, you will need to use this command :

`pactl load-module module-raop-sink server=[192.168.43.1]:5000  protocol=UDP encryption=RSA codec=ALAC channels=2 format=16 rate=44100 latency_msec=2000`

Where `192.168.43.1` is the IP of your Android device. You shouldn't need to change this, as all Android devices have the same local IP on their own hotspot : 192.168.43.1. Should it not be valid, use `ip route` on Lakka : the default gateway IP will be the one to use (assuming you're connected to your hotspot).

&nbsp;
> **How do I shutdown my Switch from Lakka ?**

***

Short answer : you can't, you have to reboot to Horizon then shutdown. Long answer : the shutdown option in Lakka was removed for safety reasons ; to shutdown, reboot to RCM then press the POWER button for twelve seconds. It is a good idea to boot in Horizon to shutdown properly from here.

&nbsp;
> **My Switch doesn't turn on anymore / won't turn on unless it's docked / it's bricked**

***

Don't worry, your Switch is not bricked. You most probably left it in RCM mode for a prolonged period and it ran out of battery. Plus, the calibration may be wrong.

First, hold the POWER button for twelve seconds to make sure that the Switch if off, then place it on the dock and wait for it to charge at 100%. Don't forget that the battery is decalibrated !

&nbsp;
> **I don't have any icons, the font is ugly and nothing works**

***

Your RetroArch configuration file somehow got corrupted. Delete the `lakka/storage/.config/retroarch/retroarch.cfg` file on your SD card and try again. If doing it over SSH, don't forget to stop RetroArch first : `systemctl stop retroarch && rm -f /storage/.config/retroarch/retroarch.cfg && systemctl start retroarch`.

Next time you power off your Switch from Lakka, remember to reboot to RCM first !

&nbsp;
> **My games are always freezing**

***

Enable Advanced settings in User Interface then disable Threaded Video in Video settings. It may enable itself again in the future so be careful.

&nbsp;
> **I have a black screen when trying to boot (hekate works)**

***

It happens sometimes : it boots but the LCD stays black. When it happens, wait a bit for RetroArch to launch (to prevent corrupting the configuration file) and force shutdown by holding the POWER button for twelve seconds. Try to boot again. If it _still_ happens, reboot to Horizon before trying again.

Sometimes however it will not boot at all, giving a black screen everytime you try. This is a know issue, and there is currently no known solution.

&nbsp;
> **How can I get boot logs?**

***

Lakka can use USB as serial output to gather boot and shutdown logs from your PC. This only works if the backlight is on (if your copy of Lakka crashes before turning the backlight on, don't bother trying).

1. On your SD card, go to /lakka/boot, remove boot.scr and rename boot_usb.scr to boot.scr.
2. Boot Lakka
3. Plug the Switch to your PC (using an USB-C cable)
4. If you're using Windows, go to the device manager and check the COM port corresponding to the Switch (warning: it will change it you change the USB port you plug the cable into)
5. You can now use PuTTY (or similar) to get the logs on the COM port you got in the previous step

Now to gather boot logs:
1. Boot hekate
2. Plug the Switch to your PC
3. Open PuTTY, don't open the COM port yet
4. Boot Lakka
5. As soon as the Switch is connected to your PC (Windows will chime), open the COM port in PuTTY (chad Linux can use a udev rule to open a terminal automatically instead)
6. You will drop a few early boot messages but most useful stuff will be there (late kernel boot + systemd userland logs).

&nbsp;
> **Do my Joy-Cons charge when using Lakka ?**

***

Short answer : no. Long answer : while the driver is currently not capable of charging Joy-Cons, this is a feature that's being worked on.

&nbsp;
> **How do I overclock or underclock the GPU ? What is the GPU profile setting in the first tab ?**

***

This setting allows you to underclock or overclock the GPU of the Switch. At each reboot, the non-docked profile is applied. 

While underclocking the GPU can allow the battery to drain slower, be aware that higher profiles may cause power failures when the Switch is not docked. Plus, the Switch was not made to exceed the docked profile : use at your own risk.

&nbsp;
> **How can I see the logs of RetroArch ? How can I troubleshoot Lakka ?**

***

See [the official Lakka documentation](http://www.lakka.tv/doc/Troubleshooting-Lakka/) for a guide on how to access RetroArch logs from SSH (among others).

&nbsp;
> **The time and date are wrong, how can I fix that ?**

***

See [the official Lakka documentation](http://www.lakka.tv/doc/Timezone-settings/) for a guide on how to set the correct timezone in Lakka.

&nbsp;
> **How to resume playing after I got back to the menu with the HOME button ?**

***

The Resume option can be reached in two ways :
1. First tab > Quick menu
2. Current game entry in your playlists (aka "console" tabs)

&nbsp;
> **Lakka is slower than usual / video is choppy while it normally isn't**

***

Just reboot then !


&nbsp;
> **PPSSPP (PSP emulator) doesn't work / displays a black screen**

***

To make PPSSPP work you first need to copy the assets in the system directory :

1. Download [this archive](https://github.com/hrydgard/ppsspp/archive/master.zip)
2. Using the method of your choice, extract all the content of the `assets` directory in the `lakka/storage/system/PPSSPP` directory on your SD card (create it if it doesn't exist)

&nbsp;
> **reicast (Dreamcast emulator) doesn't work / displays a black screen**

***

You need to place the Dreamcast BIOS files in the `lakka/storage/system/DC` directory on your SD card (create it if it doesn't exist).

&nbsp;
> **Touchscreen doesn't work in DeSmuME (DS emulator) / games are slow**

***

Press HOME, open the core options and set the pointer type to touch. While you're at it, set frameskip to 1 and CPU cores to 4.

&nbsp;
> **Can my console be banned because I used Lakka ?**

***

¯\\\_(ツ)\_/¯

&nbsp;
> **Can I update my console and still use Lakka ?**

***

Can you ? Yes. Should you ? No.

&nbsp;
> **Where can I donate ? Can I buy you a beer ?**

***

Don't buy _me_ a beer. [Buy _libretro_ a beer.](https://www.patreon.com/libretro)

&nbsp;
> **I can't access the Online Updater on Lakka, why ?**

***

There is no need to use the Online Updater, so it's disabled to avoid breaking things.

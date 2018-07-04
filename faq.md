---
title: Frequently Asked Questions
layout: page
---

Here is a list of frequently asked questions and, obviously, an answer to each of them. What you want may already be listed on the [official Lakka FAQ](http://www.lakka.tv/doc/FAQ/) so check it out aswell.

&nbsp;
> **Does Lakka still have [insert standard Linux issues here] ?**

***

The battery bug has been fixed as of the 02/07/2018 update. Be sure to apply the fix from Hekate 3.0 first !

&nbsp;
> **Will it brick my Switch ? Will it replace my system ?**

***

**No.** Lakka boots from the SD card, it never touches the NAND of the console. It's a "dual boot", if you prefer. However, using Lakka does have side effects, listed in the above question.

&nbsp;
> **What currently works ? What doesn't ?**

***

See this tiny table for a summary of what works and what doesn't :

| Works                          | Doesn't work      |
|:------------------------------:|:-----------------:|
| Wi-Fi (after a reboot)         | Internal speakers & jack port |
| Bluetooth (partially)          | Sleep mode        |
| Touch screen                   | Graceful shutdown |
| Hardware graphics acceleration | USB Host          |
| Wired Joy-Cons (it means attached to the console)                | Dock support      |
| GPU Profile Selection          | Wireless Joy-Cons |
| SSH, SMB                       |                   |
| SDXC cards
| Bluetooth Audio (AD2P) | |
| Screen brightness control | |

&nbsp;
> **Which consoles and systems are currently supported ?**

***

{% include consoles_list.html %}

&nbsp;
> **Which standalone games are currently included ?**

***

* 2048
* cannonball
* Cave Story
* Dinotharw
* PrBoom (Doom 1 rewrite)
* Mr.Boom (Bomberman clone)
* TyrQuake (Quake 1 rewrite)
* XRick (Rick Dangerous rewrite)

&nbsp;
> **Which miscellaneous cores are currently included ?**

***

* ChaiLove (2D game framework)
* Game Music Emu (video games music player)
* Lutro (LUA game engine)
* PocketCDG (karaoke music player)
* EasyRPG (RPG Maker 2000/2003 engine)
* Remote RetroPad (use your Switch as a joypad for your PC)

&nbsp;
> **Why doesn't Wi-Fi Work ?**

***

Wi-Fi won't work on a cold boot of the system. Therefore, you need to reboot at least once into RCM and run the exploit again to fix Wi-Fi connectivity.

&nbsp;
> **Where can I see the IP address of the Switch on my network ?**

***

From your Switch, you can see this in the first tab, Information > Network Information. From your host PC, various methods are listed [there](http://www.lakka.tv/doc/Finding-the-IP-of-your-Lakka-box/).

&nbsp;
> **How do I add games to the system ?**

***

You need to copy your games to the `lakka/storage/roms` directory on your SD card.

Once your games are copied, go to the tab which icon is a plus sign (on Lakka, on the Switch) and scan the directory where you added your game (you can just scan the top-level directory, it will go through everything recursively). If your games were recognized, new tabs will appear (one for each console) with them listed inside. If not, you can still load the game manually from the first tab.

&nbsp;
> **How do I setup Bluetooth audio ?**

***

1. Make sure that Audio driver is set to pulse and Audio and Audio sync are enabled
2. Enable Bluetooth in Services
3. Pair your headset using SSH and `bluetoothctl` (use Putty on Windows)
    1. `agent on`
    2. `scan on`
    3. Wait for your headset to show up and see its MAC address
    4. `pair XX:XX:XX:XX:XX:XX`, put the correct MAC address (protip : use tab-completion)
    5. `trust XX:XX:XX:XX:XX:XX`
    6. `connect XX:XX:XX:XX:XX:XX`
4. If the audio is choppy, make sure to update the boot/tegra210-nintendo-switch.dtb file on your SD card (take the one from the latest update archive)
5. After a reboot, it should autoconnect to your device if it's available and still paired

&nbsp;
> **How do I shutdown my Switch from Lakka ?**

***

Short answer : you can't, reboot to Horizon then shutdown. Long answer : the shutdown option in Lakka was removed for safety reasons ; to shutdown, reboot to RCM then press the POWER button for twelve seconds. It is a good idea to boot in Horizon to shutdown properly from here.

&nbsp;
> **My Switch doesn't turn on anymore / won't turn on unless it's docked / it's bricked**

***

Don't worry, your Switch is not bricked. You most probably left it in RCM mode for a prolonged period and it ran out of battery. Plus, the calibration may be wrong.

First, hold the POWER button for twelve seconds to make sure that the Switch if off, then place it on the dock and wait for it to charge at 100%. Don't forget that the battery is decalibrated !

&nbsp;
> **I have black squares everywhere, the font is ugly and nothing works**

***

Your RetroArch configuration file somehow got corrupted. Delete the `lakka/storage/.config/retroarch/retroarch.cfg` file on your SD card and try again. If doing it over SSH, don't forget to stop RetroArch first : `systemctl stop retroarch && rm -f /storage/.config/retroarch/retroarch.cfg && systemctl start retroarch`.

Next time you power off your Switch from Lakka, remember to reboot to RCM first !

&nbsp;
> **My games are always freezing**

***

Enable Advanced settings in User Interface then disable Threaded Video in Video settings. It may enable itself again in the future so be careful.

&nbsp;
> **Sometimes the exploit works but nothing happens on my Switch**

***

It happens sometimes : it boots but the LCD stays black. When it happens, wait a bit for RetroArch to launch (to prevent corrupting the configuration file) and force shutdown by holding the POWER button for twelve seconds. Try to boot again. If it _still_ happens, reboot to Horizon before trying again.

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

See [the official Lakka documentation](http://www.lakka.tv/doc/Troubleshooting-Lakka/) for a guide on how to set the correct timezone in Lakka.

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

Lakka on Switch is not upsreamed yet so the buildbot is not configured for the Online Updater. It will be added back if / when the Switch project is merged with the original Lakka repository.

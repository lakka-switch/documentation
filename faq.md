---
title: Frequently Asked Questions
layout: page
---

Here is a list of frequently asked questions and, obviously, an answer to each of them. What you want may already be listed on the [official Lakka FAQ](http://www.lakka.tv/doc/FAQ/) so check it out aswell.

&nbsp;
> **Does Lakka still have [insert standard Linux issues here] ?**

***

**Yes.** Lakka **will** desynchronize your battery and your internal clock. Lakka **will** cause screen burn-ins if you let it on the menu for too long.

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
| Wi-Fi (after a reboot)         | Audio             |
| Bluetooth (partially)          | Sleep mode        |
| Touch screen                   | Graceful shutdown |
| Hardware graphics acceleration | USB Host          |
| Wired Joy-Cons                 | Dock support      |
| GPU Profile Selection          | SDXC cards        |
| SSH, SMB                       |                   |

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

You need to copy your games to the `roms` directory of the storage partition. You have three ways of achieving that, depending on your host operating system : see [this guide](http://www.lakka.tv/doc/Accessing-Lakka-filesystem/) to know how.

Once your games are copied, go to the tab which icon is a plus sign (on Lakka, on the Switch) and scan the directory where you added your game (you can just scan the top-level directory, it will go through everything recursively). If your games were recognized, new tabs will appear (one for each console) with them listed inside. If not, you can still load the game manually from the first tab.

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
> **How do I update Lakka ?**

***

**Automatic update**

1. Download the **latest** archive from [this repository](https://natinusala.cheats-inc.org/natinusala/lakka-switch/archives/updates/) (use your brain to grab the latest)
2. Using a method of your choice, copy the archive to the `.update` directory of the **storage partition**
3. The next (re)boot will automatically update your installation

**Manual update**

1. Download the **latest** archive from [this repository](https://natinusala.cheats-inc.org/natinusala/lakka-switch/archives/updates/) (use your brain to grab the latest)
2. Using a method of your choice, extract the right files from the archive to the root of the **FAT32 partition** (replace everything) :
    * `KERNEL`, `KERNEL.md5`, `SYSTEM` and `SYSTEM.md5` to the root (contains the read-only system partition and the kernel)
    * the content of the directory `3rdparty/bootloader` (contains the boot script and device tree)

&nbsp;
> **Do my Joy-Cons charge when using Lakka ?**

***

Short answer : no. Long answer : while the driver is currently not capable of charging Joy-Cons, this is a feature that's being worked on.

&nbsp;
> **How can I see the logs of RetroArch ? How can I troubleshoot Lakka ?**

***

See [the official Lakka documentation](http://www.lakka.tv/doc/Troubleshooting-Lakka/) for a guide on how to access RetroArch logs from SSH (among others).

&nbsp;
> **The timezone is wrong, how can I fix that ?**

***

See [the official Lakka documentation](http://www.lakka.tv/doc/Troubleshooting-Lakka/) for a guide on how to set the correct timezone in Lakka.

&nbsp;
> **How to resume playing after I got back to the menu with the HOME button ?**

***

The Resume option can be reached in two ways :
1. First tab > Quick menu
2. Current game entry in your playlists (aka "console" tabs)

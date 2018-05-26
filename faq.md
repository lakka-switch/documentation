---
title: Frequently Asked Questions
layout: page
---

Here is a list of frequently asked questions and, obviously, an answer to each of them. What you want may already be listed on the [official Lakka FAQ](http://www.lakka.tv/doc/FAQ/) so check it out aswell.

> **Which consoles and systems are currently supported ?**

***

{% include consoles_list.html %}

&nbsp;
> **Which standalone games are currently included ?**

***

* 2048
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
> **Why doesn't Wi-Fi Work ? Why is `[]` the only Wi-Fi network ?**

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

Once your games are copied, go to the very last tab on Lakka and scan the directory where you added your game (you can just scan the top-level directory, it will go through everything recursively). If your games were recognized, new tabs will appear (one for each console) with them listed inside. If not, you can still load the game manually from the first tab.

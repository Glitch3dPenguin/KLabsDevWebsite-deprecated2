---
title: Make Transmission WEB-UI Beautiful
date: 2022-10-17
categories: [Home Lab, Torrent, Transmission]
tags: [transmission web interface,torrenting,torrent,seed box,transmission,transmission-daemon,web-ui]
image:
  path: /klabsdev/thumbs/TransmissionToTransmissionic.png
---

## Introduction
After years of building my collection of Linux ISOs I have used a solid collection of Torring software. Everything from uTorrent, Transmission, BitTorrent, qBittorrent, and more! Each software comes with its own suite of features - some better than others. After building out my home lab, I have been looking for the ultimate setup allowing me to quickly and conveniently use magnet links to add .torrents to my seed box. By far the best option that I found is Transmission's Web Daemon.
 
In my opinion the only downside is the dated and blinding web interface. I spend some time digging around in the server files and online to see if there are any 3rd party options for a better UI. Through trial and error, I feel I have found the best option for a Beautiful Transmission web interface!
 
It's called [Transmisionic](https://github.com/6c65726f79/Transmissionic) by [Samuel Leroy](https://github.com/6c65726f79)!
 
## Installation 
Getting this web overlay installed is very easy! So Let’s get started! 
 
**Step 1:** 
<br>
Start by downloading the latest release of Transmisionic from Github. The latest release can be found [here](https://github.com/6c65726f79/Transmissionic/releases/tag/v1.7.0).
 
**Step 2:** 
<br>
Unzip it and replace the ``web`` folder of Transmission. On Ubuntu server, you can find that folder in 
```console
/usr/share/transmission/web
```

![Transmission UI Light Mode](https://cdn.klabsdev.com/klabsdev/images/trans-light.png)
![Transmission UI Dark Mode](https://cdn.klabsdev.com/klabsdev/images/trans-dark.png)

## Conclusion
All that is left to do is refresh the page and enjoy your new Transmission User Interface!
 
Thanks for reading!
 
Written By: Max Kulik


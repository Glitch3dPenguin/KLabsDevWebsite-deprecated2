---
title: My Home Lab | Update 1
date: 2022-06-04
categories: [Home Lab, Hardware]
tags: [home lab,hardware]
---
## Introduction
 I use my server to host some of my movies, game servers, and websites. I will be going over some of the current hardware that will be going into the machine and some of the future plans. I am looking for some feedback on my storage structure plans and the build overall.

 I have been using Proxmox for almost 10 years now and I started with used old hardware and I have finally retired all of my old nodes for this new server. The last 2 that I had built were based on bulldozer architecture.

## SPECS:

**Mobo:** ASUS X99-A II

**CPU:** XEON E5-2697AV4 16 cores/3.6GHz Boost

**RAM:** 4x Kingston KVR24E17D8 16GB/ECC

**GPU:** GTX 1060 (maybe video encode for plex?)

**Boot Drive:** 1TB SK Hynix NVME drive (No RAID)

**VM Storage:** 3x 1TB SK Hynix SSD (RAIDZ on Proxmox)

**NIC:** TRENDnet 2.5 gigabit (Will be used by VM's)

**NIC:** Chelsio T420-BT Dural 10 Gigabit (Passthorugh for pfSence)

**HBA:** Dell H200 SAS

**NAS Storage:** HBA w/4x 4TB HDDs on a RAIDZ vdev - I plan on using this for NAS storage. The HBA will be forwarded to a TrueNAS VM.

![Choose file type in program](/klabsdev/images/HomeLab1.png)
![Choose file type in program](/klabsdev/images/HomeLab2.png)
![Choose file type in program](/klabsdev/images/HomeLab3.png)

I will be looking into finding a new case soon. This case was used from one of my old servers and I need to find something that has more HDD bays. If I can't find a decent tower case I may end up rack mounting my system. 

Join the conversation over on [Reddit](https://www.reddit.com/r/homelab/comments/sqa6fw/my_newest_home_lab_went_live_today/)!

Thanks for reading!

Written By: Max Kulik
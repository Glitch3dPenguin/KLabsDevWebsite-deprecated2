---
title: Transmission Killswitch Script 
date: 2023-08-07
categories: [Home Lab,Torrent,Transmission]
tags: [Home Lab,Torrent,script,Transmission]
image:
  path: /klabsdev/images/Killswitch.png
---

## Introduction: 

I collect most of my “linux ISO’s” using Transmission’s transmission-daemon. I will normally log into the web interface in order to manage my torrent files. However I do also run an OpenVPN instance on that machine connected to my PIA VPN in order to mask that traffic and keep my ISP off my back. 

The risk involved I wanted to manage is making sure that if something happens to the OpenVPN connection, Transmission doesn’t continue to download anything using the non VPN network. In order to do this I have made a very simple and configurable killswitch script. 

For fun, I have also set up a configuration option on this script to post messages to a Discord server in case the killswitch runs. This will allow alerts to be sent out if the VPN server has been disconnected for some reason and if the container needs to be rebooted. 


## Requirements:

In order for this script to work there are a few things that will need to be set up first. I will not be going over this here but in the future I plan to. I will update this post when I get posts made for the requirements. 

- Requirement 1
  + You will need to have a Ubuntu container set up on Proxmox. 
- Requirement 2
  + You will need OpenVPN set up and configured to use a static IP from whatever VPN provider you are using. In my case I use PIA. 
- Requirement 3
  + The container will need to have transmission-daemon already installed and configured.
- Requirement 4
  + Both OpenVPN and transmission-daemon need to be running when this script is run for the first time. If it is not running, there is a chance the script could fail to install. 

## How to Use: 

1. Ensure that you have met the above requirements and that you are running this script inside of a Ubuntu LXC container. This has been untested to work inside of a VM. Their file structures are different and could cause issues. 
2. Run the one-line installer command that I have created: ```wget https://raw.githubusercontent.com/Glitch3dPenguin/Transmission-KillSwitch/main/installer.sh && chmod +x installer.sh && sudo ./installer.sh```
3. Then, once the script has finished you can edit transmission-killswitch/config in order to get the script ready. 
4. Finally we can go ahead and start up the killswitch `sudo service killswitch start`

## Conclusion: 

The killswitch is now ready to use and has been started. The script installer will also set itself up to start on boot. 

If you would like to contribute to this project or check for updates, feel free to view the [github repo](https://github.com/Glitch3dPenguin/Transmission-KillSwitch). 

Thanks for reading!

Written By: Max Kulik
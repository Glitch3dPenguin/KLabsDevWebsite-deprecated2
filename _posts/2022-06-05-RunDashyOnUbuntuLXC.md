---
title: Install Dashy on Ubuntu LXC in Proxmox
date: 2022-06-05
categories: [Home Lab, Proxmox, Dashy, Tutorial]
tags: [home lab,dashy,proxmox,dashy,heimdall,helper script]
---
## Introduction
I was doing some research on trying to find a good personal dashboard to use in a container on Proxmox. I ended up using Dashy over Heimdall. Dashy, however is mostly supported for running on Docker. So I set out to create a one-liner helper script that will install it start to finish.

TLDR - This is a way standalone way to install Dashy on a Proxmox Ubuntu LXC container. 

## Requirements:
- Proxmox LXC Container (Script Does NOT support Proxmox VM yet)
- 4096mb of memory allocated (deflate to 1024mb after script)
- 2 virtual cores (deflate to 1 after script) 

## Tested LXC Containers:

|                   LXC Template              |    Support   |
| ------------------------------------------- | ------------ |
| ubuntu-18.04-standard_18.04.1-1_amd64       | Working      |
| ubuntu-22.04-standard_22.04-1_amd64 (Focal) | Working      |
| ubuntu-22.04-standard_22.04-1_amd64 (Jammy) | Working      |
| ubuntu-22.10-standard_22.10-1_amd64         | Broken       |

## How to Use
**Step 1)** 
```console
nano install-dashy.sh
```

**Step 2)**
```bash
#!/bin/bash

#Let's stop the script if anything errors out. 
set -o errexit

#~~~~~~~~~~~~~~~~~~~~~~~~~~~~
#READ ME FIRST: This script is intended to be directly run on a ubuntu 20.10 LXC privileged container.
#I have only tested on that but I would imagine you could run this on any Ubuntu machine as long as you 
#edit the directories used to fit your needs.
#~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#Let's start by making sure we are up to date
sudo apt update && sudo apt upgrade
#Downloading and installing dependencies for getting packages dependent software - Git, Curl, and net-tools for printing local IP at the end.
sudo apt-get install git curl net-tools
#Now that we have Curl, lets add the corect version of NodeJS
wget -qO- https://deb.nodesource.com/setup_16.x | bash -
#We need to refresh the apt repositories now
sudo apt-get update
sudo apt-get install -y nodejs
sudo apt-get update && sudo apt-get upgrade -y
#This may look redundant but I promise it needs to be done this way!
#"yarn" is used by a program called cmdtest. If this process is not done like this it will 
#always fail due to cmdtest being installed. If you know a better way please let me know! 
sudo apt-get remove cmdtest
sudo apt-get autoremove
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt-get update
sudo apt-get install yarn
echo
echo
#Print versions of Yarn and NodeJS
echo Yarn Version:
yarn --version 
echo Node Version:
node -v
echo
echo If you did not get a version of both Yarn and NodeJS then something did not work.
echo 
#Time to download Dashy
git clone https://github.com/Lissy93/dashy.git
cd /root/dashy/
yarn # Install dependencies
#Yarn will run out of memory when trying to build. This next command will allow 
#NodeJS to build with a max size of 1000mb of memory. It will fail without it. 
export NODE_OPTIONS=--max-old-space-size=1000
#Build Yarn
yarn build # Build the app

#Let's make Dashy run on system startup
#Create simple launch script for Dashy
cat <<EOF > /root/dashy/start.sh
#!/bin/bash 
cd /root/dashy/
yarn start #start the app
EOF
#Allow the to run
chmod +x /root/dashy/start.sh
#Create the service ID file to launch dashy on container boot
cat <<EOF > /etc/systemd/system/dashy.service
[Unit]
Description=dashy
Before=motd-news.service

[Service]
Type=oneshot
ExecStart=/root/dashy/start.sh
StandardOutput=journal+console

[Install]
WantedBy=multi-user.target
EOF
#Enabled the service for systemctl
sudo systemctl enable dashy
#Script is finished! Fingers crossed this works first try!
echo If you see this message everything worked!
echo Reboot container and launch
ifconfig | grep -Eo 'inet (addr:)?([0-9]*\.){3}[0-9]*' | grep -Eo '([0-9]*\.){3}[0-9]*' | grep -v '127.0.0.1'
echo on port 4000
```

**Step 3)** Allow it to be executed
```console
chmod +x install-dashy.sh
```

**Step 4)** Run the installer you just created!
```console
sudo bash install-dashy.sh
```

**Step 5)** Now it's time to reboot your container
```console
reboot
```
## Conclusion

You can now go to your container's IP address in a browser and view your Dashy!

xxx.xxx.xxx.xxx:4000 is default.


The most up-to-date version of the script can be found over on my [GitHub](https://github.com/Glitch3dPenguin/DashyDashboardForLXC). You can also join the conversation on [Reddit](https://www.reddit.com/r/selfhosted/comments/sz9nz9/run_dashy_on_ubuntu_2010_lxc_in_proxmox/)!

> Post updated on `5/25/2023`.
{: .prompt-info }

Thanks for reading!

Written By: Max Kulik

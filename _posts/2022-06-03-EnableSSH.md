---
title: Enable Remote SSH on Proxmox LXC
date: 2022-06-03
categories: [Proxmox, LXC]
tags: [proxmox,lxc,ssh,homelab,virtualization]
---
## Introduction
By default, Debian-based LXC containers on Proxmox do not have Remote Password Authentication enabled. They use Public Key-based Authentication. The best way to access the container is to load up the web interface and simply open the shell for the container you would like to make changes to. However, if you're like me, you'd rather just have that server added to your favorite SSH client and be able to access the shell from any computer on the same network that way. 

Here is a step by step walkthrough to enable Remote SSH on any LXC container::

>Enabling Password Authentication on your LXC container has the potential to open security vulnerabilities. Proceed at your own risk.
{: .prompt-danger }

## Allow Remote SSH Login
1) First, log into your Promox web panel and select the Container that you would like to enable Remote SSH on. 

2) Next you will need to edit the sshd config file.
```console
nano /etc/ssh/sshd_config
```
3) use `CTRL` + `W` to open the "Where Is" prompt and type `PermitRootLogin`. Once you have found that line you'll want to change it to the following:

Before: `PermitRootLogin without-password`

After: `PermitRootLogin yes`

4) Now that the change has been made use `CTRL` + `X` to close Nano. You will be prompted to save your changes with `Y` and `ENTER`.

5) Restart the sshd service for the changes to take effect. 
```console
service ssh restart
```
You now have the ability to Remote SSH into the LXC container directly within the same network using the container's IP address.
>If you do not know the IP address of the LXC container, you can run `ifconfig`.
{: .prompt-tip }

## Conclusion
As mentioned before adjusting the LXC container does hold the potential to open some security vulnerabilities within your home lab. As long as you are not exposing port 22 to WAN you should be fine. If you need to gain SSH access to an LXC container for the greater internet, I would suggest using a self-hosted OpenVPN server or Apache Guacamole.

Thanks for reading!
Written By: Max Kulik
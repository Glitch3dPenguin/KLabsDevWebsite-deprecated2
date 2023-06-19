---
title: Install Nginx Proxy Manager on Proxmox LXC & Alpine Linux
date: 2023-05-15
categories: [Proxmox,Home Lab,LXC]
tags: [Nginx Proxy Manager,Home Lab,LXC,LXC Container,Alpine Linux]
---

## Introduction: 
Currently the only supported way to install Nginx Proxy Manager is to run it inside of a Docker container. However, for someone like me, using Proxmox, I like to utilize LXC for my containerization. This guide will step anyone through the process of Installing Nginx Proxy Manager on a Proxmox LXC Container. 

## Preparation & Prerequisites 

1) Download the Alpine 3.16 container.

![Download Alpine Linux](/klabsdev/images/NginxProxyManager/NginxProxyManager1.png)

> DO NOT USE Alpine 3.17 - Installer Will Fail Later
{: .prompt-warning }

2) Create a new LXC container using the downloaded Alpine 3.16 template. 

3) Log into the newly created container. Then update and upgrade the container. 

`apk update` 
`apk upgrade`

4) Next create an "npm" user on the container. It will be needed for the install script. 

`adduser npm`

5) Now run the install script. 

```
wget --no-cache -qO - https://raw.githubusercontent.com/ej52/proxmox/main/lxc/nginx-proxy-manager/setup.sh | sh
```

6) After the install script runs you will be prompted with the login URL:

![Download Alpine Linux](/klabsdev/images/NginxProxyManager/NginxProxyManager2.png)

Save this URL and port number for later as you will need it to access the web management panel. 

7) Next, using your text editor of choice edit `/usr/local/openresty/nginx/conf/nginx.conf`

```
nano /usr/local/openresty/nginx/conf/nginx.conf 
```

You will need to comment out this line 
`pid /run/nginx/nginx.pid;`
to
`# pid /run/nginx/nginx.pid;`

Save and close the file. 

8)Reboot the container 

```
reboot
```

9) Enter the provided IP address in a browser and use the default login: 

```
E-Mail: admin@example.com
Password: changeme
```

10) Once logged in, you will be asked to change the default admin login. Use the previously provided default login as the last login option.

Nginx Proxy Manager is now installed! 

## Sources: 

- Install script created by [**Elton Renda**](https://github.com/ej52). Further documentation for other containers and other operating systems are listed [**here**](https://github.com/ej52/proxmox-scripts/blob/main/lxc/nginx-proxy-manager/README.md).
- Broken support for Alpine Linux 3.17 documented on [**Issue #118**](https://github.com/ej52/proxmox-scripts/issues/118).
- Script does not create the "npm" user by default and it is not documented outside of [**Issue #117**](https://github.com/ej52/proxmox-scripts/issues/117).


> This post has been updated on 6/19/2023.
{: .prompt-info }

Thanks for reading!

Written By: Max Kulik
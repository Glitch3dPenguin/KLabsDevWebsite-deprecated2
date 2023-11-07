---
title: Proxmox Dark Mode
date: 2022-06-17
categories: [Proxmox, Home Lab, Tutorial]
tags: [home lab,dark mode,proxmox,]
---

![Desktop View](/klabsdev/images/ProxmoxExample.png){: width="972" height="589" }
_My Dashboard With PVE Discord Dark_

> This article is now obsolete. First party dark mode has been included since [Proxmox 7.4](https://www.proxmox.com/en/about/press-releases/proxmox-virtual-environment-7-4).
{: .prompt-info }

## Introduction
Poxmox’s UI is informational, functional, and looks great! The only problem is that it’s also blinding. When I am up late working on a project for hours, the worst thing is going from my dark themed terminal, web browser, windows machine to a flashbang like Proxmox panel. Now with only a few lines in the terminal, we can solve that problem! 

## Installation
**Step 1:** Open your Proxmox web panel and connect to the node shell to start the Dark Mode install!

**Step 2:** Start by heading over to [Weilbyte’s Github](https://github.com/Weilbyte/PVEDiscordDark) and star the amazing project there! Then we need to download the CLI utility:
```console
wget https://raw.githubusercontent.com/Weilbyte/PVEDiscordDark/master/PVEDiscordDark.sh
```

**Step 3:** Next we will need to mark the downloaded file as executable:
```console
chmod u+x PVEDiscordDark.sh
```

**Step 4:** Now we run it!
```console
bash PVEDiscordDark.sh install
```


## Conclusion
Welcome to the dark side! PVE Discord Dark is now installed and you can now enjoy working within your Proxmox panel without hurting your eyes!

Thanks for reading!
<br>
Written By: Max Kulik


Sources:
<br>
Welbyte Github - [https://github.com/Weilbyte/PVEDiscordDark](https://github.com/Weilbyte/PVEDiscordDark)

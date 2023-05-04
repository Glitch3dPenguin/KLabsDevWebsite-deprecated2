---
title: Allow Read/Write Permissions to Wordpress
date: 2022-07-04
categories: [Home Lab, Apache 2, Web Server]
tags: [home lab,apache 2,wordpress,permissions]
---

![Desktop View](/klabsdev/images/ApacheReadWrite.png){: width="972" height="589" }
_Screenshot of Top showing apache 2 using the www-data user_

## Introduction
Apache 2 - when installed to a Ubuntu server using the apt repository reads and writes using the `www-data` user. When manually installing a Wordpress site, Apache will try to read and write files using that user and if the owner is not set properly you will not be able to make any meaningful changes to the Wordpress website. The following is how to set the proper folder permissions in Ubuntu for a manual Wordpress installation. 

## Set Folder Owner
First we are going to assume you have Apache 2 installed and have Virtual Hosts already pointing to the Wordpress folder. I have another article explaining this process from start to finish. For this example I will be using `/var/www/wordpress`.

**Step 1:** We need to navigate to the www directory that Apache will be using.
```console
cd /var/www/ 
```

**Step 2:** Now we will recursively set the folder owner and group using chown. This command using the `-R` argument will make sure to make any file and folder inside of the wordpress folder owned by `www-data` as well. 
```console
sudo chown -R www-data:www-data wordpress
```

**Step 3:** The final step is checking to make sure the owner has been set properly. We can simply use the ls command with an argument to do this:
```console
ls -l
```

## Conclusion
This process is not very hard nor time consuming but it’s a step I have to take every time I add a new Wordpress website to my web server.

Thanks for reading!
<br>
Written By: Max Kulik
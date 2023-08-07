---
title: Install PNPM on Alpine Linux 3.17
date: 2023-06-09
categories: [Proxmox,LXC,Home Lab,Alpine Linux]
tags: [PNPM,LXC,Alpine Linux,home lab]
image:
  path: /klabsdev/thumbs/AlpineLinuxLogo.png
---

## Introduction: 
PNPM is often times used alongside NPM when building a project. Then typical way to install PNPM would be to add it via apk. However it does not seem there is a working package that has been added for Alpine 3.17. However, you can manually install it. These steps are assume you are using Alpine 3.17 on a Proxmox LXC container. 

## Installation

1) First you will need to install Curl. 

```
apk add curl 
```

2) After that you can run the provided PNPM installer script

```
curl -L https://unpkg.com/@pnpm/self-installer | node
```

3) Check that it has been installed
```
pnpm --version
```

## Sources: 

- PNPM Github [**Issue #784**](https://github.com/pnpm/pnpm/issues/784).


Thanks for reading!

Written By: Max Kulik
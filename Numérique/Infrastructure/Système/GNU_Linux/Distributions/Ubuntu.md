---
title: Ubuntu
description: 
published: true
date: 2024-05-21T11:22:18.097Z
tags: 
editor: markdown
dateCreated: 2024-05-21T11:22:18.097Z
---

# Ubuntu

## Invité KVM (guest KVM)

### QEMU guest agent

```bash
apt -y install qemu-guest-agent
# reboot
```

### Activer serveur serial

`/etc/default/grub` :

```txt
GRUB_CMDLINE_LINUX="console=tty0 console=ttyS0,115200"

GRUB_TERMINAL="console serial"

GRUB_SERIAL_COMMAND="serial --speed=115200"
```

```bash
sudo update-grub
```
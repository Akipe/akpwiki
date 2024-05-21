---
title: Secure Boot
description: 
published: true
date: 2024-05-21T12:45:59.134Z
tags: 
editor: markdown
dateCreated: 2024-05-21T12:45:59.134Z
---

# Secure Boot

## sbctl (Archlinux)

### Prepare UEFI bios

- Reset & remove current keys
- Enable custom keys

### Prepare system

```bash
pacman -S sbctl
```

Check if system is ok :

```bash
sbctl status
```

```
==> WARNING: Setup Mode: Enabled
==> WARNING: Secure Boot: Disabled
```

### Generate keys

```bash
sbctl create-keys
```

### Sign EFI binaries

Check current EFI binaries sign:

```bash
sbctl verify
```

Sign a binary :

```bash
sbctl sign -s /efi/EFI/BOOT/BOOTX64.EFI
```

### Enroll key to UEFI bios

Enroll key with Microsoft key to :

```bash
sudo sbctl enroll-keys --microsoft
```

Enroll only the generate key :

```bash
sudo sbctl enroll-keys
```

But warning message :
> Found OptionROM in the bootchain. This means we should not enroll keys into UEFI without some precautions.  
There are three flags that can be used:  
    --microsoft: Enroll the Microsoft OEM certificates into the signature database.  
    --tpm-eventlog: Enroll OpRom checksums into the signature database (experimental!).  
    --yes-this-might-brick-my-machine: Ignore this warning and continue regardless.  
Please read the FAQ for more information: <https://github.com/Foxboron/sbctl/wiki/FAQ#option-rom>

Reboot the computer and enable secure boot.

Check if it is working :

```bash
sbctl status
```

### Ressources

- <https://lunaryorn.com/secure-boot-on-arch-linux-with-sbctl-and-dracut>
- <https://www.reddit.com/r/archlinux/comments/ji0be6/simple_way_to_set_up_secure_boot/>

---
title: Image VHD
description: 
published: true
date: 2024-05-21T18:49:18.666Z
tags: 
editor: markdown
dateCreated: 2024-05-21T18:49:18.666Z
---

# Image VHD

## Image VHD depuis Linux

```bash
dd if=/dev/zero of=windows.raw bs=1M count=120000
mkntfs -F windows.raw
qemu-img convert -f raw -O vpc -o subformat=fixed,force_size windows.raw windows.vhd
```
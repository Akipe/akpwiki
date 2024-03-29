---
title: NixOS
description: 
published: true
date: 2024-03-29T23:42:50.530Z
tags: 
editor: markdown
dateCreated: 2024-03-04T12:54:30.573Z
---

# NixOS

## Installation

### Image template LXC Proxmox

- <https://mtlynch.io/notes/nixos-proxmox/>
- <https://hydra.nixos.org/job/nixos/trunk-combined/nixos.lxdContainerImage.x86_64-linux>

Renommer en `nixos-2023-09-21-lxdContainerImage.x86_64-linux.tar.xz`.

## Maintenance

```shell
nix-store --verify --check-contents --repair
```
---
title: Windows dans Docker
description: 
published: true
date: 2024-06-12T17:08:55.161Z
tags: 
editor: markdown
dateCreated: 2024-06-12T17:08:55.161Z
---

# Windows dans Docker

Windows inside a Docker container.

<https://github.com/dockur/windows>

```yml
services:
  windows:
    image: dockurr/windows
    container_name: windows
    environment:
      VERSION: "win11"
    devices:
      - /dev/kvm
    cap_add:
      - NET_ADMIN
    ports:
      - 8006:8006
      - 3389:3389/tcp
      - 3389:3389/udp
    stop_grace_period: 2m
```
---
title: NetworkManager
description: 
published: true
date: 2024-05-21T19:08:23.461Z
tags: 
editor: markdown
dateCreated: 2024-05-21T19:08:23.461Z
---

# NetworkManager

## Commands

There is two way to configure NetworkManager :

- `nmcli` for command line interface
- `nmtui` for curses-based interface

### Management

#### Reload configuration

```bash
nmcli general reload
```

### Wifi

- <https://wiki.salo.pe/archlinux/internet.html>

#### Connection with WPS

- <https://gitlab.freedesktop.org/NetworkManager/NetworkManager/-/issues/925>

Within 2 minutes of pushing the WPS button in the AP :

```shell
nmcli dev wifi connect <SSID>
```

#### List SSID

```bash
nmcli device wifi list
```

#### Set state of Wi-Fi

Turn on :

```bash
nmcli radio wifi on
```

Turn off :

```bash
nmcli radio wifi off
```

### Inteface

#### Disconnect an interface

```bash
nmcli device disconnect ifname eth0
```

### Connection

A connection is a configuration for an interface.

#### Get connection informations

```bash
nmcli connection show
```

#### Activate connection

```bash
nmcli connection up name_or_uuid
```

#### Delete connection

```bash
nmcli connection delete name_or_uuid
```

### Device

#### List network devices and some information

```bash
nmcli device
```
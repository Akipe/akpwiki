---
title: Raspberry Pi
description: 
published: true
date: 2024-04-19T17:06:24.959Z
tags: 
editor: markdown
dateCreated: 2024-04-19T17:06:24.959Z
---

# Raspberry Pi

## Materiel

### Raspberry pi zero

#### IdéesIdées

- <https://techsystem.fr/axzez-interceptor-carrier-board/>
- <https://learn.pimoroni.com/article/getting-started-with-pirate-audio>
- <https://retropie.org.uk/>
- <https://uk.pi-supply.com/a/l/fr/products/naturebytes-wildlife-camera-case>
- keybowmini
- ecran az-touch - <https://magmi.cc/aztouch>
- <https://magpi.cc/moodlight>
- octoprint
- <https://magpi.cc/lamp>
- <https://magpi.cc/donotdisturbed>
- <https://magpi.cc/multiroomaudio>
- <https://magpi.cc/zerokeyring>
- <https://magpi.cc/polapizero>
- <https://magpi.cc/passwordkeeper>
- <https://magpi.cc/riotbrick>
- <https://magpi.cc/stickpc>
- <https://magpi.cc/boseberrypi>
- <https://magpi.cc/puitar>
- <https://magpi.cc/tunergitlab>
- <https://github.com/stacksmashing/pico-light-arcade/>
- <https://magpi.cc/keybow2040>
- <https://magpi.cc/keybowbuild>
- <https://magpi.cc/fliczero>
- <https://magpi.cc/fridgemonitor>
- <https://magpi.cc/whashbearypi>
- <https://magpi.cc/thermos>pi
- <https://magpi.cc/waterdispenser>
- <https://magpi.cc/babycam>
- <https://magpi.cc/uberhome>
- <https://magpi.cc/smartbike>
- <https://magpi.cc/guitarpedalyt>
- picosystem

### OS

- risc os pi
- libreelec
- osmc
- retropie
- lakka
- motioneyeos
- Octo pie
- dietpie
- https://magpi.cc/chromiumos
- emteria.os
- picoreplayer
- Pimusicbox
- slitaz

## Achat

### Où trouver des stocks pour achat

<https://rpilocator.com/>

### Format

#### Tablet

- <https://cutiepi.io/>
- <https://www.diskiopi.com/shop/fr/>
- <https://raspad.com/>

## Configuration

### EEPROM

It is supported only for the Raspberry Pi v4.

Other Raspberry Pi use the file `bootcode.bin` on the boot filesystem.

For Archlinux ARM, `vcgencmd` is accessible with path `/opt/vc/bin/vcgencmd`.

#### Configure

Read the current config :

```bash
rpi-eeprom-config
```

Or :

```bash
vcgencmd bootloader_config
```

Change the configuration :

```bash
rpi-eeprom-config --edit
```
You need to reboot to validate the modification.

#### Update

Get the current version :

```bash
vcgencmd bootloader_version
```

Check if an update is available :

```bash
rpi-eeprom-update
```

Install the latest version available :

```bash
rpi-eeprom-update -a
```

The new EEPROM will be flash on system restarting.

To cancel the pending update :

```bash
rpi-eeprom-update -r
```

#### Ressources

- <https://www.raspberrypi.com/documentation/computers/raspberry-pi.html>
- Bootloader configuration : <https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#raspberry-pi-4-bootloader-configuration>
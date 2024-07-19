---
title: Debian
description: 
published: true
date: 2024-07-19T18:14:13.113Z
tags: 
editor: markdown
dateCreated: 2024-07-19T18:14:13.113Z
---

# Debian

## Configuration

### Microcode CPU

#### Intel CPU

- <https://cyrusyip.org/en/post/2023/01/31/install-microcode-on-proxmox/>

```bash
echo "deb http://deb.debian.org/debian/ unstable non-free-firmware" > /etc/apt/sources.list.d/debian-unstable.list
```

```ini
# /etc/apt/preferences.d/unstable-repo
# lower the priority of all packages in the unstable repository
Package: *
Pin: release o=Debian,a=unstable
Pin-Priority: 10

# allow upgrading microcode from the unstable repository
Package: intel-microcode
Pin: release o=Debian,a=unstable
Pin-Priority: 500

Package: amd64-microcode
Pin: release o=Debian,a=unstable
Pin-Priority: 500
```

```shell
apt update && apt list --upgradable
```

```shell
# Intel CPU
apt install intel-microcode
# AMD CPU
apt install amd64-microcode
```

remove file : `/etc/modprobe.d/intel-microcode-blacklist.conf`

To remove :

```shell
# remove microcode
apt purge amd64-microcode intel-microcode
apt autoremove
# make sure there is no installed package from the unstable repository
apt list --installed | grep '/unstable'
# remove unstable repo and config
rm /etc/apt/sources.list.d/debian-unstable.list /etc/apt/preferences.d/unstable-repo
# reboot
reboot
# check microcode, you should see "No entries"
journalctl -k --grep="microcode updated early to"
```

### Gestionnaire de paquets APT

#### Ajout du support du PPA et de `add-apt-repository`

```shell
apt install software-properties-common
```

#### Mise à jour automatique

<https://guide.ubuntu-fr.org/server/automatic-updates.html>

#### Dépôt

##### Pacstall

Un AUR like pour les distributions Debian ou basé Debian.

https://pacstall.dev/

##### MPR makedeb

https://mpr.makedeb.org/

### Watchdog

#### IPMI Watchdog

```bash
apt install ipmitool
```

`/etc/default/pve-ha-manager`:

```ini
WATCHDOG_MODULE=ipmi_watchdog
```

`/etc/modprobe.d/ipmi_watchdog.conf`:

```ini
options ipmi_watchdog action=power_cycle panic_wdt_timeout=10
```

Check if working :

```bash
ipmitool mc watchdog get
```

```
Watchdog Timer Use:     SMS/OS (0x44)
Watchdog Timer Is:      Started/Running
Watchdog Timer Actions: Power Cycle (0x03)
Pre-timeout interval:   0 seconds
Timer Expiration Flags: 0x10
Initial Countdown:      10 sec
Present Countdown:      10 sec
```

Test if working (carefull, it will reboot your computer) :

```bash
lsof /dev/watchdog
# COMMAND   PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
# watchdog- 833 root    3w   CHR 10,130      0t0  566 /dev/watchdog
kill -9 833 # set same PID
```


#### Watchdog classique

Vérifier qu'il y a un appareil de disponible :

```shell
ls -al /dev/watchdo*
```

### Gestion de la mise en veille sur pc portable

#### Désactiver la mise en veille lorsque on ferme le pc portable

`/etc/systemd/logind.conf` :

```ini
HandleLidSwitch=ignore
HandleLidSwitchExternalPower=ignore
HandleLidSwitchDocked=ignore
```

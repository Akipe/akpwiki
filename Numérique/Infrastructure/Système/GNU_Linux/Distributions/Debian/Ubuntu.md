---
title: Ubuntu
description: 
published: true
date: 2024-07-19T18:29:30.302Z
tags: 
editor: markdown
dateCreated: 2024-07-19T18:29:30.302Z
---

# Ubuntu

## Configuration

### Mise à jour automatiques

- <https://guide.ubuntu-fr.org/server/automatic-updates.html> 

```shell
apt install unattended-upgrades

dpkg-reconfigure -plow unattended-upgrades
```

`/etc/apt/apt.conf.d/20auto-upgrades` & `/etc/apt/apt.conf.d/50unattended-upgrades` & `systemctl status apt-daily.timer`

Outils : <https://github.com/abhigenie92/unattended_upgrades_repos>

```shell
wget https://github.com/abhigenie92/unattended_upgrades_repos/raw/master/unattended_upgrades_repos.py
python3 ./unattended_upgrades_repos.py
```

```
Add repos:
"Ubuntu:xenial";
"LP-PPA-kubuntu-ppa-backports:xenial";
"LP-PPA-tuxonice:xenial";
"LP-PPA-webupd8team-sublime-text-3:xenial";

Skipping files due to not present origin or suite. Or origin being a url.:
packagecloud.io_slacktechnologies_slack_debian_dists_jessie_InRelease
tiliado.eu_nuvolaplayer_repository_deb_dists_xenial_InRelease
```

`/etc/apt/apt.conf.d/50unattended-upgrades`

```conf
Unattended-Upgrade::Allowed-Origins {
	"${distro_id}:${distro_codename}-security";
	"${distro_id}:${distro_codename}-updates";
	"${distro_id}:${distro_codename}-proposed";
	"${distro_id}:${distro_codename}-backports";
  "Ubuntu:xenial";
  "LP-PPA-kubuntu-ppa-backports:xenial";
  "LP-PPA-tuxonice:xenial";
  "LP-PPA-webupd8team-sublime-text-3:xenial";
};
```

```shell
sudo unattended-upgrade --dry-run --debug
```

One line command :

```shell
apt install unattended-upgrades -y && \
	dpkg-reconfigure -plow unattended-upgrades && \
	apt install python3-distro -y && \
	mkdir /tmp/apt && \
	cd /tmp/apt && \
	wget https://github.com/abhigenie92/unattended_upgrades_repos/raw/master/unattended_upgrades_repos.py && \
	python3 ./unattended_upgrades_repos.py && \
	sleep 10 && \
	vim /etc/apt/apt.conf.d/50unattended-upgrades && \
	apt purge python3-distro -y && \
	unattended-upgrade --dry-run --debug
```

### Invité KVM (guest KVM)

#### QEMU guest agent

```bash
apt -y install qemu-guest-agent
# reboot
```

#### Activer serveur serial

`/etc/default/grub` :

```txt
GRUB_CMDLINE_LINUX="console=tty0 console=ttyS0,115200"

GRUB_TERMINAL="console serial"

GRUB_SERIAL_COMMAND="serial --speed=115200"
```

```bash
sudo update-grub
```

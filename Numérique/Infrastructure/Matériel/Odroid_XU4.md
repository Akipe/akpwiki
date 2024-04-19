---
title: Odroid XU4
description: 
published: true
date: 2024-04-19T17:08:40.974Z
tags: 
editor: markdown
dateCreated: 2024-04-19T17:08:40.974Z
---

# Odroid XU4

## Archlinux ARM

### Installation

On va installer le système :

- /boot sur l'accessoire EMCC
- / sur le disque dur branché en USB

Brancher le module emmc à l'adaptateur micro SD, puis :

```bash
lsblk
# EMMC sera /dev/sdb
# Disque USB sera /dev/sdc

sudo fdisk /dev/sdb
# "o" puis "p" pour vérifier qu'il n'y a plus de partitions
# "n" puis "p" puis "1" puis "4096" pour le premier secteur
# puis "+4G" pour allouer 8 giga
# enfin "w"
sudo mkfs.ext4 -L sysboot /dev/sdb1

sudo fdisk /dev/sdc
# "o" puis "p" pour vérifier qu'il n'y a plus de partitions
# "n" puis "p" puis "1" puis "2048" pour le premier secteur
# puis "+396G" correspond à Total-0.15*Total
# enfin "w"
sudo mkfs.ext4 -L sysroot /dev/sdc1


mkdir /tmp/root
sudo mount /dev/sdc1 /tmp/root
sudo mkdir /tmp/root/boot
sudo mount /dev/sdb1 /tmp/root/boot

wget http://os.archlinuxarm.org/os/ArchLinuxARM-odroid-xu3-latest.tar.gz
sudo bsdtar -xpf ArchLinuxARM-odroid-xu3-latest.tar.gz -C /tmp/root

lsblk -f
cp /boot/boot.txt /boot/boot.txt.bak
vim /boot/boot.txt
# root=PARTUUID=e139ce78-9841-40fe-8823-96a304a09859 boot_delay=32 rootwait
vim /etc/fstab
# UUID=3f2acc4f-3e52-4703-a1c0-033a53cdb0ad / ext4 errors=remount-ro,noatime 0 1
# UUID=9143f05a-70e7-46b7-ad96-728e12bdf6eb /boot errors=remount-ro,noatime defaults 0 1
pacman -S uboot-tools
sudo /tmp/root/boot/mkscr
sudo /tmp/root/boot/sd_fusing.sh /dev/sdb

cd /
sync && sudo sync
sudo umount -R /tmp/root
```


Ensuite il faut brancher le module EMMC sur la carte, activer le boot sur la carte EMMC et la mettre sous tension.

### Mise en service de base

On se connecte en SSH avec l'identifiant *alarm* et le mot de passe *alarm*. Le mot de passe root est par défaut *root*.

```bash
pacman-key --init
pacman-key --populate archlinuxarm
pacman -Syu
reboot
```

```bash
pacman -S linux-armv7 linux-armv7-headers
```

## Boot Process

- boot files :
	- **bl1.bin** *sign* : Also referred to as fwbl1, this is the first-stage bootloader. It is provided by Samsung as is, so we don't have many details. It is signed by Samsung, and encrypted. They really don't want you reverse engineering this :laughing:.
    - **bl2.bin** *sign* : This is the second-stage bootloader, aka the secondary program loader (SPL) or the MMC Loader (MLO). This is actually part of U-boot and can be extracted from your own personally compiled u-boot.bin using the mkexynosspl tool in the tools directory. However, it must be signed by the ODROID people (requests can be made on the ODROID forum) for the board to actually run it, so if you aren't making changes it would be much easier to just use the provided blob.
    - **u-boot.bin** *not sign*: This is the U-boot image that we can build ourselves. It does not have to be signed, so we can make changes easily.
    - **tzsw.bin** *sign* : This is "TrustZone Software", provided by Samsung/ARM. It seems like this shouldn't be kept as opaque as bl1, but I haven't been able to dig up much information about it on the ODROID wiki and forum. According to the mods, you cannot boot without it (I can confirm, without tzsw.bin the fan will spin up but U-boot will not reach it's interactive menu), and it is signed by Samsung. It is not open source, but there is an open source attempt to reconstruct it (Technically this is for an older entry in the ODROID-XU series). The mods are willing to sign a modified tzsw.bin, but modifying it would be quite difficult for the aforementioned reasons.

- where to find binaries :
	- https://github.com/hardkernel/u-boot/tree/odroidxu4-v2017.05
	- old https://github.com/hardkernel/u-boot/tree/odroidxu3-v2012.07/sd_fuse/


- MBR/DOS style partition table 
- create primary partition, stgart at 3072 and take all space
- (for using binary) uboot fork for odroid-xu4 : git clone https://github.com/hardkernel/u-boot.git -b odroidxu4-v2017.05
- cd sd_fuse
- sudo ./sd_fushing.sh /dev/#### (path of sdcard or emmc)

- for using sources uboot (hardkernel) :
	- https://github.com/hardkernel/u-boot.git -b odroidxu4-v2017.05
	- root path : make odroid-xu4_defconfig
    - env : export ARCH=arm
			export CROSS_COMPILE=arm-linux-gnueabi-
    - make / make -j #
    - The resulting binary will be called u-boot-dtb.bin. Move it to the sd_fuse directory. You can now run sd_fusing.sh like normal to flash the sd card. The script is smart enough to use your u-boot-dtb.bin, assuming you don't change the name, and only uses the precompiled hardkernel version of uboot if it can't find any other version in the sd_fuse directory.

- uboot (mainline sources) : (https://aur.archlinux.org/cgit/aur.git/tree/PKGBUILD?h=uboot-odroid-xu3-mainline)
	- git clone https://github.com/u-boot/u-boot && cd u-boot
	- get defconfig (exemple : https://aur.archlinux.org/cgit/aur.git/tree/odroid-xu3_defconfig?h=uboot-odroid-xu3-mainline ) to uboot/configs
    - unset CFLAGS CXXFLAGS CPPFLAGS
    - make odroid-xu3_config
    
- cp u-boot-dtb.bin /boot (generate with uboot)
- cp {{bl{1,2},tzsw}.bin,sd_fusing.sh} /boot
- chmod +x "/boot/sd_fusing.sh
- tools/mkimage -A arm -O linux -T script -C none -n "U-Boot boot script" -d /boot.txt "${pkgdir}"/boot/boot.scr
- cp /{boot.txt,mkscr} /boot

### Install to SD Card

- dd if=/dev/zero of=/dev/sdX bs=1M count=8 # clean sd card
- fdisk /dev/sdX
- At the fdisk prompt, create the new partition:
    Type o. This will clear out any partitions on the drive.
    Type p to list partitions. There should be no partitions left.
    Type n, then p for primary, 1 for the first partition on the drive, 4096 for the first sector, and then press ENTER to accept the default last sector.
    Write the partition table and exit by typing w.

###  Links

- <https://github.com/ku-sldg/stairCASE/wiki/Deploying-to-the-ODROID-XU4>
- <https://github.com/ku-sldg/stairCASE/wiki/ODROID-XU4-Boot-Details>
- <https://lastlog.de/blog/posts/odroid_xu4_with_nixos.html>
- <https://aur.archlinux.org/packages/uboot-odroid-xu3-mainline>
- <https://wiki.gentoo.org/wiki/Odroid-XU4>
- <https://github.com/ARM-software/u-boot/blob/master/doc/README.odroid>
- <https://wiki.tizen.org/Quick_guide_for_odroidxu4>
- <https://wiki.odroid.com/odroid-xu4/software/building_u-boot_mainline>
- <https://github.com/ARM-software/u-boot/blob/master/doc/README.odroid>
- <https://wiki.odroid.com/odroid-xu4/software/building_u-boot_mainline>
- <https://odroid.com/dokuwiki/doku.php?id=en:xu3_building_u-boot#installation>
- <https://github.com/hardkernel/u-boot/blob/u-boot_v2020.01/doc/README.odroid>
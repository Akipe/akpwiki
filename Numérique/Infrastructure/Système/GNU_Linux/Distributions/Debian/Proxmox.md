---
title: Proxmox
description: 
published: true
date: 2024-07-19T18:24:21.177Z
tags: 
editor: markdown
dateCreated: 2024-07-19T17:23:48.143Z
---

# Proxmox

## Host

### Commandes

#### Machines virtuelles Qemu

##### Uploader une image

```shell
scp PATH/vzdump-qemu.vma.zst USER@PROXMOX:/var/lib/vz/dump/
```

#### Containers LXC

##### Changer nom du container

```shell
pct set <VMID> --hostname <newname>
```

### Configuration

#### Changement du hostname

Changer les fichiers suivants :

- `/etc/hosts`
- `/etc/hostname`
- `/etc/mailname`
- `/etc/postfix/main.cf`

#### Définir le VLAN

Par exemple pour le VLAN *100* et pour l'appareil *enp2* :

```conf
# /etc/network/interfaces

# ...
auto vmbr0
iface vmbr0 inet static
        bridge-ports enp2 # A changer
        bridge-stp off
        bridge-fd 0
        bridge-vlan-aware yes
        bridge-vids 2-4094

auto vmbr0.100
iface vmbr0.100 inet static
        address 10.0.0.100/24
        gateway 10.0.0.1
# ...
```

#### Power

<https://wiki.archlinux.org/title/CPU_frequency_scaling>

```shell
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver
cat /sys/devices/system/cpu/cpu*/cpufreq/energy_performance_available_preferences

> # /etc/tmpfiles.d/energy.conf
w /sys/devices/system/cpu/cpufreq/policy*/scaling_governor - - - - powersave
w /sys/devices/system/cpu/cpufreq/policy*/energy_performance_preference - - - - balance_performance

w /sys/devices/system/cpu/cpufreq/policy*/scaling_governor - - - - conservative
w /sys/devices/system/cpu/cpufreq/conservative/sampling_down_factor - - - - 2
w /sys/devices/system/cpu/cpufreq/conservative/up_threshold - - - - 75
w /sys/devices/system/cpu/cpufreq/conservative/down_threshold - - - - 10
w /sys/devices/system/cpu/cpufreq/conservative/freq_step - - - - 10
w /sys/devices/system/cpu/cpufreq/conservative/ignore_nice_load - - - - 1
```

#### ZFS

##### Réduire la quantité de RAM alloué

- <https://wiki.archlinux.org/title/ZFS#ZFS_is_using_too_much_RAM>
- <https://www.admin-magazine.com/mobile/HPC/Articles/Tuning-ZFS-for-Speed-on-Linux>

```shell
# A definir dans grub comme paramètre de démarage du noyau
zfs.zfs_arc_max=536870912 # (for 512MiB)
zfs.zfs_arc_min=268435456 # (for 256MiB, needs to be lower than zfs.zfs_arc_max)
zfs.zfs_arc_max=536870912 zfs.zfs_arc_min=268435456
```

#### Watchdog

##### Host (node)

- <https://pve.proxmox.com/wiki/High_Availability_Cluster_4.x#Hardware_Watchdogs>

```shell
modprobe iTCO-wdt
dmesg | grep -i wdt # iTCO_wdt iTCO_wdt.1.auto: Found a ...
```

Modificier `/etc/default/pve-ha-manager` :

```ini
WATCHDOG_MODULE=iTCO_wdt
```

Si un watchdog matériel défini :

```ini
# /etc/kernel/cmdline ou 
nmi_watchdog=0
```

```shell
proxmox-boot-tool refresh
```

Pour vérifier que celà fonctionne :

```shell
dmesg | grep iTCO
```

Pour tester :

```shell
# Attention ! Génére un kernel panic,
# Sauvegarder et arréter les services avant d'executer la commande
echo c > /proc/sysrq-trigger
```

##### VM (qemu)

Ajouter dans la configuration de la VM :

```shell
# /etc/pve/qemu-server/[server_id].conf
watchdog: model=i6300esb,action=reset
```

Configurer la VM :

```shell
apt install watchdog
```

Editer la config :

```ini
# /etc/watchdog.conf
watchdog-device = /dev/watchdog
log-dir =  /var/log/watchdog
realtime = yes
priority = 1
```

Par défaut `i6300esb` est blacklisté, pour l'autoriser, modifier `/etc/default/watchdog` et définir `watchdog_module` à `i6300esb`.

Activer le service :

```shell
systemctl enable watchdog
```

Redémarrer la VM.

Pour vérifier que celà fonctionne :

```shell
dmesg | grep i6300 # i6300ESB timer 0000:00:04.0: initialized. heartbeat=30 sec (nowayout=0)
```

Pour tester :

```shell
# Attention ! Génére un kernel panic,
# Sauvegarder et arréter les services avant d'executer la commande
echo c > /proc/sysrq-trigger
```

### Qemu VM

#### Configuration

##### PCI Passthrough

- <https://pve.proxmox.com/wiki/PCI(e)_Passthrough>
- <https://pve.proxmox.com/wiki/PCI_Passthrough>
- <https://leduccc.medium.com/improving-the-performance-of-a-windows-10-guest-on-qemu-a5b3f54d9cf5>
- <https://asded.gitlab.io/post/2023-07-01-pci-passthrough-proxmox-04/>

##### SR-IOV

##### Vérifier support materiel

```shell
lspci -vvv -s 02:00.0 | grep -A 9 SR-IOV
```

Example :

```shell
lspci -vvv -s 02:00.0 | grep -A 9 SR-IOV
    Capabilities: [160 v1] Single Root I/O Virtualization (SR-IOV)
            IOVCap: Migration-, Interrupt Message Number: 000
            IOVCtl: Enable+ Migration- Interrupt- MSE+ ARIHierarchy+
            IOVSta: Migration-
            Initial VFs: 32, Total VFs: 32, Number of VFs: 7, Function Dependency Link: 00
            VF offset: 16, stride: 1, Device ID: 154c
            Supported Page Size: 00000553, System Page Size: 00000001
            Region 0: Memory at 0000000090400000 (64-bit, prefetchable)
            Region 3: Memory at 0000000092c20000 (64-bit, prefetchable)
            VF Migration: offset: 00000000, BIR: 0
```

#### Problèmatiques

##### kvm: Hyper-V enlightened VMCS (hv-evmcs) requires Hyper-V virtual APIC (hv-vapic)

- <https://forum.proxmox.com/threads/nested-virtualization-stopped-working-pve-6-1-5.64316/>

Pour CPU Intel, ajouter au fichier :

```ini
args: -cpu host,+vmx
```

Exemple :

```ini
bootdisk: scsi0
cores: 8
args: -cpu host,+svm
cpu: kvm64,flags=+hv-evmcs;+aes
ide2: local:iso/proxmox-ve_6.1-1.iso,media=cdrom
memory: 16384
name: vm2
net0: virtio=BA:CA:13:CE:4A:E9,bridge=vmbr0,firewall=1
numa: 0
ostype: l26
scsi0: Pve8:vm-5001-disk-0,size=200G
scsihw: virtio-scsi-pci
smbios1: uuid=6bca378f-dc6f-41b4-9b13-e526da7702a0
sockets: 1
vmgenid: f3a42be1-b6c9-4979-969b-eac838aa6c9f
```

### LXC container

#### Attach USB device

##### Get device informations

Sur l’hôte, utiliser l’utilitaire lsusb pour lister les devices connectés. Récupérer les nombres Bus et Device (ici 001 et 003) pour en déduire le chemin vers le fichier spécial du device.

```shell
lsusb
```

```shell
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Récupérer le major number et le minor number du fichier spécial /dev/bus/usb/{{Bus}}/{{Device}} (ici 189 pour le major et 2 pour le minor)

```shell
ls -al /dev/bus/usb/001/003
```

```shell
crw-rw-r-- 1 root root 189, 2 Jul 24 09:46 /dev/bus/usb/001/003
```

##### Configure LXC container

Maintenant qu’on a les 4 nombres, éditer le fichier de configuration du container 101. Le major+minor sert pour autoriser le container à manipuler le device et le chemin vers le fichier spécial doit être monté exactement au même endroit dans le container LXC

```shell
vi /etc/pve/nodes/host01/lxc/101.conf
```

```ini
lxc.cgroup.devices.allow: c 189:2 rwm
lxc.mount.entry: /dev/bus/usb/001/003 dev/bus/usb/001/003 none bind,optional,create=file
```

Rebooter le container. Normalement le device USB est bien présent.

Pour vérifier, on peut installer usbutils dans le container pour vérifier que la clé est bien disponible avec lsusb.

```shell
apt install usbutils
```

```shell
lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

### A ajouter dans ansible

```ini
# grub config
GRUB_CMDLINE_LINUX="$GRUB_CMDLINE_LINUX intel_iommu=on iommu=pt"
GRUB_CMDLINE_LINUX="$GRUB_CMDLINE_LINUX intel_iommu=on iommu=pt kvm_intel.ept=Y  kvm_intel.nested=Y" ?
GRUB_CMDLINE_LINUX="$GRUB_CMDLINE_LINUX isolcpus=1-7,9-15 nohz_full=1-7,9-15 rcu_nocbs=1-7,9-15" ?
GRUB_CMDLINE_LINUX="$GRUB_CMDLINE_LINUX hugepagesz=1G hugepages=48" ?
GRUB_CMDLINE_LINUX="$GRUB_CMDLINE_LINUX cgroup_enable=memory swapaccount=1" ?
GRUB_CMDLINE_LINUX="$GRUB_CMDLINE_LINUX intel_pstate=disable" ?
GRUB_CMDLINE_LINUX="$GRUB_CMDLINE_LINUX pci=noaer pcie_acs_override=downstream,multifunction" ?
```

puis

```shell
update-grub
```

```
# /etc/modprobe.d/kvm.conf

options kvm ignore_msrs=1 report_ignored_msrs=0
```

```
# /etc/modules-load.d/vfio.conf
vfio
vfio_iommu_type1
vfio_pci
vfio_virqfd
```

puis

```shell
update-initramfs -u -k all
```

```
# /etc/modprobe.d/vfio.conf
# Nvidia
options vfio-pci ids=10de:1e87,10de:10f8,10de:1ad8,10de:1ad9

# AMD RX580
options vfio-pci ids=1002:67df,1002:aaf0

# Fresco USB
options vfio-pci 1b73:1100

# Wifi
options vfio-pci 14e4:43a0
```

### Changer le hostname

Editer les fichiers `/etc/hosts`, `/etc/hostname`, `/etc/mailname` et `/etc/postfix/main.cf`

## Installation

### Raspberry Pi

Utiliser une version maintenu par la communauté appelé **Pimox** : <https://github.com/pimox/pimox7>

## Outils et extensions

### Edge kernel

Proxmox Edge kernels : <https://github.com/fabianishere/pve-edge-kernel>

### Scripts

- <https://tteck.github.io/Proxmox/>

## Ressources

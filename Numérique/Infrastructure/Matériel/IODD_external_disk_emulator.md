---
title: IODD external disk emulator
description: 
published: true
date: 2024-04-19T17:15:15.544Z
tags: 
editor: markdown
dateCreated: 2024-04-19T17:15:15.544Z
---

# IODD external disk emulator

## Commun

- <https://help.iodd.kr/>
- <https://www.iodd.shop/mediafiles/downloads/IODD_2541_QuickGuide_EN.pdf>
- <http://en.iodd.kr/wiki/index.php/Main_Page>

### File tree

```
J(IODD internal Drive) (32 file/folder limits)
├─ _ISO (32 file/folder Limits)
│  │  Hiren’s BootCD 15.2.iso
│  │  ubuntu-14.04.4-desktop-amd64.iso
│  │  Windows 10.iso
│  │  Windows XP sp3.iso
│  │  (max 32 files or subfolders in a folder)
│  │  
│  ├─IMA for Floppy (32 file/folder limits)
│  │      Bios updater.ima
│  │      MS-DOS 6.0.ima
│  │      Symantec Ghost.ima
│  │      
│  ├─RMD Files (32 file/folder limits)
│  │      Win 7Ent_x86_x64+8.1Pro+10Pro vol2.RMD
│  │      Win7_Ult_SP1_Russian_x64.RMD
│  │      Windows 10.RMD
│  │      
│  └─VHD Files (32 file limits)
│      │  linuxmint-17.3-cinnamon-32bit.vhd
│      │  Windows 10 Win2Go.vhd
│      │  Windows 7 OS Booting.vhd
│      │  
│      └─Nested Subfolders is allowed
├─Your Folder 01 (no limits)
├─Your Folder 02 (no limits)
├─Your Folder 99 (no limits)
```

### Firmware

- <https://help.iodd.kr/troubleshooting/firmware-update>
- <http://dir.iodd.kr/iodd_firmware_updater/>

### VHD

- <https://help.iodd.kr/bootable-virtual-drive/virtual-drive-vhd/creat-vhd-file-with-vhd-tools>


## IODD 2541

### Boutons

#### Short press

| Key | Action
|---|---
| `1` | Rescan root folder
| `2` | File/item list Up
| `3` | Display VBUS minimum voltage
| `4` | Go to parent folder.
| `5` | View file information.
| `6` | Select a file or Enter to a folder.
| `7` | Eject the latest virtual hard drive or virtual CD
| `8` | file/item list Down
| `9` | Save Loading Status
| `settings` | Enter to Menu. (or Exit)
| `0` | View Help
| `enter` | Select a file or 

#### Long press (3 seconds)

| Key | Action
|---|---
| `1` | Reconnected.
| `3` | Reconnected with Write-Protection.
| `4` | View Partition list. Default partition can be selected.
| `7` | Reconnected with all virtual drives detached.
| `9` | USB connection is detached with sleep mode.
| `0` | Reconnected with temporarily Write Protection disabled.


#### Startup press

| Key | Action
|---|---
| `1` | Reset to factory settings.
| `3` | Start with Write Protection.
| `5` | Start without connecting to PC
| `7` | Start with all virtual drive unmounted.
| `settings` | Enter to menu without connecting to PC. Finish all settings and reconnect or disconnect.
| `0` | Displays startup key information without connecting to PC. Press and hold the corresponding startup key to reconnect with that function. Pressing any other key will reconnect without the startup key function.

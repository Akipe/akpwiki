---
title: Sunshine et Moonlight
description: 
published: true
date: 2024-06-06T16:48:00.753Z
tags: 
editor: markdown
dateCreated: 2024-06-06T16:41:04.214Z
---

# Sunshine et Moonlight

Moonlight utilise à la base le protocole *Nvidia Gamestream*.
<https://moonlight-stream.org/>

Sunshine is an open source application for replace Nvidia Geforce Experience.

<https://github.com/LizardByte/Sunshine>

It can be used with other vendor (Intel, Amd...) and support Windows, macOS & GNU/Linux.

## Connection from Internet

There is two way to do it :
- use the application *Moonlight Internet Hosting Tool*
- manualy allow ports and set port forwarding with IPv4

### Ports

Port :
- TCP 47984, 47989, 48010
- UDP 47998, 47999, 48000, 48002, 48010

## Keyboard shortcuts

| Keys | Action
|---|---
| `Ctrl` + `Alt` + `↑ Shift` + `Q` | **Quit** the streaming session (game is still running)
| `Ctrl` + `Alt` + `↑ Shift` + `Z` | Toggle mouse and keyboard capture
| `Ctrl` + `Alt` + `↑ Shift` + `X` | Toggle between full-screen and windowed mode
| `Ctrl` + `Alt` + `↑ Shift` + `S` | Open performance **stats** overlay
| `Ctrl` + `Alt` + `↑ Shift` + `M` | Toggle **mouse** mode (pointer capture or direct control)
| `Ctrl` + `Alt` + `↑ Shift` + `V` | Type clipboard text on the host
| `Ctrl` + `Alt` + `↑ Shift` + `D` | Minimize the stream window
| `Ctrl` + `Alt` + `↑ Shift` + `C` | Toggle local **cursor** display in remote desktop mouse mode (remote cursor will always show up due to GameStream limitations)
| `Ctrl` + `Alt` + `↑ Shift` + `L` | Toggle **locking** the mouse pointer to the video area (requires "Optimize mouse for remote desktop instead of games" checkbox enabled)
| `CTRL` + `ALT` + `SHIFT` + `N` | (Sunshine) Hide/Unhide the cursor (This may be useful for Remote Desktop Mode for Moonlight)
| `CTRL` + `ALT` + `SHIFT` + `F1/F12` | (Sunshine) Switch to different monitor for Streaming

## Astuces

### Changement configuration multi écran

Raccourcie pour changer la configuration des écrans : ```Windows + P```

Puis faire "Fleche bas" pour choisir la configuration :

![moonlight_gestion_multi_ecran.webp](/numerique/application/moonlight_gestion_multi_ecran.webp)

## Erreurs

### Wrong screen stream

1. Ensure your primary monitor is the BIOS primary display (the one the logo appears on on boot.
1. (Suggested) Make a windows restore point, just in case.
1. Unplug every monitor except your primary display.
1. Open Registry Editor.
1. Navigate to HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GraphicsDrivers\Configuration.
1. Delete all sub-items under Configuration.
1. Reboot your machine.
1. Reconnect your other monitors.
1. Profit.

> <https://github.com/moonlight-stream/nvidia-gamestream-issues/issues/22#issuecomment-1010348630>

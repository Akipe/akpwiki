---
title: Wine
description: 
published: true
date: 2024-05-21T19:00:20.053Z
tags: 
editor: markdown
dateCreated: 2024-05-21T19:00:20.053Z
---

# Wine

## Utilisation

### Préfixe

Préfixe Wine : `WINEPREFIX`.

Par défaut : `~/.wine`

#### Préfixe par défaut

```shell
env WINEPREFIX=~/.wine/win64 wineboot -u
```

#### Création

```shell
WINEARCH=win64 WINEPREFIX=~/.wine/win64 wine winecfg
WINEARCH=win32 WINEPREFIX=~/.wine/win32 wine winecfg
```

### Executer une application

```shell
WINEPREFIX=~/.wine/win64 wine application.exe
```

## Proton

<https://cheatsheets.stephane.plus/games/steam/#proton>

## Proton Glorious Egroll (Proton-GE)

<https://github.com/GloriousEggroll/proton-ge-custom>

## Ressources

- <https://github.com/ValveSoftware/Proton/#runtime-config-options>
- <https://cheatsheets.stephane.plus/games/steam/>

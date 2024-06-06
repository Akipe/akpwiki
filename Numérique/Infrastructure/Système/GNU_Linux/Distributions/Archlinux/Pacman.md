---
title: Pacman
description: 
published: true
date: 2024-06-06T16:29:05.076Z
tags: 
editor: markdown
dateCreated: 2024-06-06T16:29:05.076Z
---

# Pacman

Pacakge manager for Archlinux.

# Commandes

## Search

In repositories :

```bash
pacman -Ss <package-name>
```

Can use `pacsearch` too :

```bash
pacsearch -n ^fire
```

## Installation

```bash
sudo pacman -S <package-name>
```

Do not reinstall a package if already intalled

```bash
sudo pacman -S --needed <package-name>
```

Build package from source

```bash
sudo pacman -U <package-file>
```

Install without check or install dependencies

```bash
sudo pacman -S -d <package-name>
```

## Updating

Check new versions of packages

```bash
sudo pacman -Syy
```

Upgrade system

```bash
sudo pacman -Syu
```

## Installed

Listing all installed packages :

```bash
pacman -Q
```

Get information about a package :

```bash
pacman -Qi <package-name>
```

## Remove

Remove only a package without dependencies

```bash
pacman -R <package-name>
```

Remove package with dependecies

```bash
pacman -Rcns <package-name>
```

### Orphaned dependencies

List all

```bash
pacman -Qdt
```

List all without informations

```bash
pacman -Qdtq
```

Remove all

```bash
pacman -R $(pacman -Qdtq)
```

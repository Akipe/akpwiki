---
title: XFCE
description: 
published: true
date: 2024-06-06T16:34:53.911Z
tags: 
editor: markdown
dateCreated: 2024-06-06T16:34:53.911Z
---

# XFCE

## Correction de problèmes

### Demande de mot de passe avec Chromium

This problem has a long history and you can fiddle around with gnome-keyring if you want, but I found that the easier solution is to set that prompt's password to blank, such that it won't ask you anymore:

1. `rm ~/.local/share/keyrings/*` (you may want to check/backup these files first, if you're not on a fresh install, e.g., `cp -r ~/.local/share/keyrings ~/keyrings-backup`)
1. Restart Chrome
1. When prompted to create a keyring, continue without entering a password. (Turns out you would have been okay if you did this the first time.)

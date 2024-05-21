---
title: GnuPG
description: 
published: true
date: 2024-05-21T12:27:25.343Z
tags: 
editor: markdown
dateCreated: 2024-05-21T12:27:25.343Z
---

# GnuPG

## Configuration

### Web Key Directory (WKD)

Auto-héberger la découverte de clé publique GnuPG.

- <https://gist.github.com/kafene/0a6e259996862d35845784e6e5dbfc79>
- <https://gnupg.org/blog/20161027-hosting-a-web-key-directory.html>

## Yubikey

### Initier un appareil avec une clée existante

```bash
gpg --card-status
gpg --edit-card # puis "fetch"
> fetch
gpg --list-secret-keys # Récupérer l'id : "sec# rsa4096/$ID"
gpg --edit-key $KEYID
> trust
> 5
> o
> quit
```

### Problèmes de compatibilité avec CCID & PCSC-Lite

<https://ludovicrousseau.blogspot.com/2019/06/gnupg-and-pcsc-conflicts.html>

```conf
# ~/.gnupg/scdaemon.conf
disable-ccid
```

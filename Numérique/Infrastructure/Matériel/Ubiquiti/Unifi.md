---
title: Unifi
description: 
published: true
date: 2024-07-22T11:34:45.550Z
tags: 
editor: markdown
dateCreated: 2024-07-22T11:33:07.481Z
---

# Unifi

## Controleur

## Appareils

### Mots de passe par défaut

- `ubnt` et `ubnt`

### Informer le controleur de son adresse

```shell
ssh ubnt@192.168.1.142 # Connect to the device
set-inform http://192.168.1.1:8080/inform # Change IP to the controller machine
```
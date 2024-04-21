---
title: Gestion Énergie
description: 
published: true
date: 2024-04-21T14:55:35.352Z
tags: 
editor: markdown
dateCreated: 2024-04-21T14:55:35.352Z
---

# Gestion Énergie

## Veille prolongé
La veille prolongé est également appelé *hibernation* permet de consomme encore moins d'énergie que la vise en veille.

<https://lecrabeinfo.net/activer-la-mise-en-veille-prolongee-windows.html>

### Activation

#### Terminal

En administrateur :
```
powercfg -hibernate on
```

Redémarrer l'ordinateur

#### Panneau de configuration

Options d’alimentation > Options d’alimentation > Modifier des paramètres actuellement non disponibles. > Veille prolongée

#### Raccourcie

Créer un fichier `hibernate.bat` et définir son contenu comme suivant :
```bat
rundll32.exe powrprof.dll,SetSuspendState
```

### Désactiver

```
powercfg -h off
```

## Ressources
- <https://lecrabeinfo.net/activer-la-mise-en-veille-prolongee-windows.html>

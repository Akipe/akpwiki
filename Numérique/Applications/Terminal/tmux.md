---
title: tmux
description: 
published: true
date: 2024-03-04T12:14:00.920Z
tags: 
editor: markdown
dateCreated: 2024-03-04T12:14:00.920Z
---

# tmux

## Info
Les différents niveaux
**sessions > fenêtres > panes (=carreaux)**
Raccourcie avant chaque commandes
```CTRL + b```
Exécuter des commandes depuis tmux (à la vim)
```CTRL + b puis :```
Sélectionner du texte pour ensuite copier/coller :
```SHIFT + selection avec la souris```

## Commande de base
Lancement avec nouvelle session
```tmux```
Lancement d'une nouvelle session avec nomage
```tmux new -s $NOM_SESSION```
Lancement sur la dernière session existante *(attach)*
```tmux a|at|attach```
Lancement sur une session existante nomé
```tmux a|at|attach -t $NOM_SESSION```
Lister les sessions
```tmux ls```
Terminer une session
```tmux kill-session -t $NOM_SESSION```
Forcer l'arret du serveur tmux :
```tmux kill-server```

# Les niveaux
## Sessions
Créer une nouvelle session
```CTRL + b puis :new```
Renommer la session courante
```CTRL + b puis $```
Lister les sessions
```CTRL + b puis s```
Quitter la session *(detach)*
```CTRL + b puis d```

## Fenêtres
Créer une nouvelle fenêtre *(create)*
```CTRL + b puis c```
Renommer la fenêtre courante
```CTRL + b puis ,```
Basculer entre les fenêtres *(next)*
```CTRL + b puis n```
Lister l'ensemble des fenêtres *(windows)*
```CTRL + b puis w```
Déplacer la fenêtre courante
```CTRL + b puis .```
Chercher une fenêtre *(find)*
```CTRL + b puis f```
Supprimer la fenêtre courante
```CTRL + b puis &```

## Panes / Carreaux
Diviser horizontalement
```CTRL + B puis %```
Diviser verticalement
```CTRL + B puis "```
Afficher les ID des panes
```CTRL + b puis q```
Déplacer des panes
...

Supprimer le panel courant
```CTRL + B puis x```

## Autre
Afficher l'aide
```CTRL + b puis ?```
Afficher l'heure sur un pane *(time)*
```CTRL + b puis t```

# Plugins
- Tmux Plugin Manager (tpm)
  - Installer les plugins : ```CTRL + B puis I```
 
- Tmux resurrect
  - Sauvegarder environement : ```CTRL + B puis CTRL + s```
  - Restaurer environement : ```CTRL + B puis CTRL + r```



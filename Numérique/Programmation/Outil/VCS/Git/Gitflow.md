---
title: Gitflow
description: 
published: true
date: 2024-05-21T15:12:56.235Z
tags: 
editor: markdown
dateCreated: 2024-05-21T15:12:56.235Z
---

# Gitflow

Gitflow est une méthodologie pour utiliser plus efficacement git pou réaliser un projet avec plusieurs développeurs.

Pour ce faire, on défini des conventions pour la gestion de branches.

Pour chaque nouvelle fonctionnalité, on va créer une branche à partir de l'état courant.

Gitflow n'est pas le plus adapté pour de l'integration continue, il existe une autre méthodologie appelé *développement basé sur le tronc*.

## Workflow pour le travaille en équipe

1. On crée une branch à partir de `develop`.

```bash
git checkout develop # On se positionne sur la branche develop
git checkout -b nouvelle_branch # On créer la branche et on se positionne dessus
```

2. On crée les commits sur cette nouvelle branche.
3. Une fois la fonctionnalité finalisée, on propose un pull request (requete de tirrage) sur la branch `develop`.
4. Une fois la branche intégré, on peut supprimer la branche créer précédament.

## Droit des branches

- branche interdite : main et develop

on créer un branche qui contient les modif, (requete de tirrage = pull request)

Dans la branch main et develop :
activer protection de la branche et vérification de code apr les pair dans github.

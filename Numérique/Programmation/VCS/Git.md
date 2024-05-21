---
title: Git
description: 
published: true
date: 2024-05-21T15:09:31.732Z
tags: 
editor: markdown
dateCreated: 2024-05-21T15:09:31.732Z
---

# Git

- <https://jbuget.fr/posts/qu-est-ce-qu-un-bon-commit-git>
- <https://gdevops.gitlab.io/tuto_git/_downloads/ff11bc9f353dcc59720470099fbcf5da/froggit_git_antiseche.pdf>
- <https://blog.microlinux.fr/formation-git-02-installation-configuration/>
- <https://www.atlassian.com/git/tutorials/atlassian-git-cheatsheet>
- <http://git-cheatsheet.com/>
- <https://training.github.com/>
- <https://training.github.com/downloads/fr/github-git-cheat-sheet/>
- <https://dev.to/uttarasriya/leveling-up-your-git-skills-game-inspired-guide-to-git-commands-36gl>

## Installation

## Configuration

### Convention retour à ligne

- <https://docs.github.com/fr/get-started/getting-started-with-git/configuring-git-to-handle-line-endings>

Dans un fichier `.gitattributes` à la racine du projet :

```ini
# .gitattributes

# Set the default behavior, in case people don't have core.autocrlf set.
* text=auto

# Explicitly declare text files you want to always be normalized and converted
# to native line endings on checkout.
*.c text
*.h text

# Declare files that will always have CRLF line endings on checkout.
*.sln text eol=crlf

# Denote all files that are truly binary and should not be modified.
*.png binary
*.jpg binary
```

Il faut ensuite ajouter ce fichier dans l'historique git :

```bash
git add . -u
git commit -m "Saving files before refreshing line endings"
```

On peut ensuite normaliser tous les fichiers :

```bash
git add --renormalize .
```

Pour ensuite sauvegarder sous git :

```bash
git status
git commit -m "Normalize all the line endings"
```

#### Retour à la ligne de type Linux pour tous fichiers

```ini
# .gitattributes

* text eol=lf
```

### Profiles multiples

- <https://vmaerten.io/posts/comment-avoir-plusieurs-profils-git/>

## Commandes

### Informations

- `git status`
- `git diff HASH_COMMIT_1 HASH_COMMIT_2`
- `git log HASH_`

## Sources d'inspirations

Contenu à découvrir :
<https://mediashare.fr/post/procedure-de-merge-request>

## Commandes terminal de déplacement

## Se déplacer

```bash
## "ChangeDirectory"
cd NOM_DU_DOSSIER

## Chemin absolut
cd /CHEMIN/DES/DOSSIER

## Chemin relatif, à partir du dossier courant
pwd # Récupérer le dossier courant
cd CHEMIN/DES/DOSSIER
# ou
cd ./CHEMIN/DES/DOSSIER
```

## Créer un dossier

```bash
## "MakeDIRectory"
mkdir NOM_DU_DOSSIER
```

## Créer un fichier vide

```bash
touch NOM_FICHIER
```

## Configuration

Configuration minimal pour utiliser git :

```bash
# Nom de l'auteur des commits à afficher
git config --global user.name "NOM D'UTILISATEUR"
# Email de l'auteur des commit à afficher 
git config --global user.email email@nom.com
```

Liste de la configuration actuel :

```bash
git config --list
```

## Gérer un dépôt (repository)

**Attention !** Lorsqu'on est sur la derrière ligne d'un fichier, si l'on rajoute une nouvelle ligne, le caractère invisible "\n" est ajouté. 
Git concidère donc qu'on a modifier la ligne précédante, même si la modification à l'air invisible.

### Workflow d'utilisation

```bash
# On vérifie qu'on n'a pas déjà des modifications en attente
git status

# On ajout un fichier pour notre prochain commit
git add FICHIER

# On vérifie l'état de notre workflow git
git status

# On valide notre commit
git commit -m "Message explicite sur les modifications apportés"
```

### Explications détaillé

#### Initialisation d'un dépôt

```bash
cd DOSSIER_NOUVEAU_REPO
git init
```

#### Ajout de fichiers pour un commit

```bash
git add FICHIER
git add .
git add -A # --all, tous les fichiers
```

#### Les commits

```bash
git commit -m "Message explicite sur les modifications apportés"
git commit -m "Premiere ligne" -m "Deuxième ligne"
```

#### Avoir des informations

```bash
git status
```

#### Annuler des modifications

```bash
git restore FICHIER_A_RESTORER
git checkout -- FICHIER # Annuler les changement
```

#### Branches

L'utilité des branches dans Git :
- gérer plusieurs versions du code
- collaborer à plusieurs sur le même projet

##### Conventions sur les branches

- *Master* : Version final.
- *Hotfix* : Modifications directe de la branche *master*.
- *Release* : Version Release Candidate (RC), sensé permettre de vérifier si tout fonctionne comme on le veut.
- *Develop* : Version béta, sensé être sans bug.
- *Feature* : Lorsqu'on veut ajouter de fonctionnalités. Il faut la synchroniser régulièrement avec le reste du code.

##### Commandes

```bash
# Lister les branches existantes
git branch
# Exemple de résultat :
  develop
* master   # L'étoile détermine quelle branche est afficher

# Créer une branche
git branch NOM_NOUVELLE_BRANCH

# Changer la branche affiché
git checkout NOM_BRANCHE

# Suppression d'une branche
git branch -d NOM_BRANCHE
git branch --delete NOM_BRANCHE
```

## Conseilles

### Nom des commits

<https://cbea.ms/git-commit/>

## Conventions

- <https://github.com/streamich/git-cz>

## Éviter les conflits

- <https://jbuget.fr/posts/comment-eviter-les-conflits-dans-git/>

## Astuces

### Mettre à jour un repo fork depuis le repo d'origine

1. Ajouter le dépot d'origine comme remote :
```bash
git remote add upstream $URL_REPO
```

2. Récupérer les données du dépot d'origine :
```bash
git fetch --all
```

3. Synchroniser la branche avec le dépot d'origine :
```bash
git rebase upstream/main # branche "main" par exemple
```

4. Optionnel : envoyer les modifications au serveur :
```bash
git push origin
```

## gitignore

- <https://www.toptal.com/developers/gitignore>

## Problèmes

### Solutions aux problèmes classiques

- <https://ohshitgit.com/fr>

## Outils

### pre-commit

<https://pre-commit.com/>

### git-crypt

<https://github.com/AGWA/git-crypt>

## Ressources

- <https://delicious-insights.com/fr/articles/git-branches/>
- <https://delicious-insights.com/fr/articles/glossaire-git/>
- <https://hupstream.com/git-cheat-sheet/>
- <https://cheatsheets.stephane.plus/versioning/git/#git-config>
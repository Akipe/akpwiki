---
title: NeoVim
description: 
published: true
date: 2024-05-21T18:55:22.893Z
tags: 
editor: markdown
dateCreated: 2024-05-21T18:55:22.893Z
---

# NeoVim

- <https://vim.avec.une-tasse-de.cafe/#1>

## Cheatsheet

- <https://vim.rtorr.com/>

## Tuto

Pour lancer l'apprentissage integré à vim, il faut :

- lancer `vimtutor` ou `vimtutor  directement
- ou depuis vim : `:help tutor`

Il existe également beaucoup de tutoriels :

- <https://vim-adventures.com/>
- <https://danielmiessler.com/study/vim/>
- <https://www.openvim.com/>
- <https://www.systutorials.com/vim-tutorial-beginners-vimtutor/>
- <https://www.w3schools.io/editor/vim-tutorials/>
- <https://linuxhint.com/vim-tutorial/>
- <https://linuxconfig.org/vim-tutorial>
- <https://www.tutorialspoint.com/vim/index.htm>
- <https://github.com/iggredible/Learn-Vim>
- <https://www.youtube.com/watch?v=I-iDGGqYf30&t=27>

## Base

Vim permet d'éditer des fichiers.

Vim utilise différents modes :

- **insertion** : i
- **insertion en début de ligne**: I
- **ajout de caractère après le curseur**: a
- **ajout de caractère en fin de ligne**: A


### Commandes globales

```vim
# Enregistrer un fichier
:w # "Write"
# Enregistrer un fichier sous
:w /CHEMIN/NOUVEAU/FICHIER
# Quitter
:q # "Quit"
:q! # Quitter sans sauvegarder

# Ouvrir un dossier
:e FILEPATH
```

#### Déplacement

Entre les lignes :

```vim
:1 # Première ligne, début du fichier
:$ # Dérnière ligne, fin du fichier
:15 # aller à la 15ième ligne
```

Sur une ligne :

```vim
$ # Aller à la fin de la ligne
```

#### Copier / couper / coller

```vim
Y # Copier une ligne
10Y # Copier 10 lignes
dd # Couper/supprimer une ligne
d10 # Couper/supprimer 10 lignes
dw # Couper/supprimer un mot
p # Coller - "Pasteé
```

#### Annuler / Refaire une action

```vim
u # Annuler
. # Refaire
```

#### Rechercher

```vim
/MOT # Rechercher le texte "MOT" vers le bas
?MOT # Rechercher le texte "MOT" vers le haut
n # Aller à l'occurence suivante - "Next"
? + <Entrer> # Aller à l'occurance précédante 
```

### Modes

#### Visuel

```vim
v #  selection de texte
<Ctrl> + v # selection de bloc de texte
```

### Explorer mode

```vim
# Explorer mode : explorateur de documents
:Sexplore
# ou
:Vexplore

# Executer des commandes shell
:! touch mon_fichier.txt
:! mkdir test

# Create directory
d
# Create file
%
```

## Astuces

### Activer la souris

```vim
:set mouse=a
```

### Executer une commande shell

```vim
:! ls
:! mkdir TEST
:! git status
```

### Gérer l'affichage des numéros de lignes

```vim
:set nu # afficher les numéros de lignes
:set nu! # masquer les numéros de lignes
```

### Activer la coloration syntaxique

```vim
:syntax on
```

### Utilisation de regex

#### Remplacer du texte

```vim
:s/test/texte/g  ## On remplace test par texte
```

Si on veut remplacer les séparateur `/` :

```vim
:s@/test/test@/texte/texte@g
```

Pour spécifier sur quelles lignes effectuer les traitemants :

```vim
:10,20 s/test/texte/g
```

## Extension

## Ressources
- <https://zestedesavoir.com/billets/4328/petite-lecon-de-vim-apprendre-a-gerer-ses-motions/>
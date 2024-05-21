---
title: Logseq
description: 
published: true
date: 2024-05-21T18:59:00.602Z
tags: 
editor: markdown
dateCreated: 2024-05-21T18:59:00.602Z
---

# Logseq

Logseq est un logiciel de prise de note non linéaire.

- <https://logseq.com/>

## Principe

### Les bloc

Un bloc est le plus petit élément dans Logseq. Il dispose d'un point au début.

Un bloc peut contenir des sous blocs.

#### Références

On peut les référencer de plusieurs manière :
- Copying their address
- Click-dragging them
- Searching for them
- In an alias

<https://discuss.logseq.com/t/the-basics-of-logseq-block-references/8458>

### Les pages

Les pages sont constitué de blocs et de sous blocs.

Ils sont sauvegardé sur l'ordinateur en tant que fichier.

Le graphe des connaissances (*the knowledge graph*) représente par défaut que les liens entre les pages.

## Syntaxe

Voir la syntaxe du [Markdown](https://wiki.akipe.fr///books/developpement-informatique/page/markdown).

On peut commencer par écrire `/` pour avoir la liste de syntaxes possibles.

### Références

#### Références vers une note

```
- Je vais m'occuper de [[Mon Jardin]]
```

#### Références vers un bloc

```
- Je vais m'occuper de ((mon bloc))
```

#### Références de date

En anglais.

Choisir le `date picker` :

```
/date
```

```
- [[Now 1st, 2020]]
  - Je devrais faire quelque chose
```

### Liste de choses à faire (todo)

```
- TODO
  - TODO faire quelque chose
  - TODO faire autre chose
  - TODO encore ...
```

### Afficher plus de formats de synxtaxes

```
<
```

## Raccourcies clavier

### Commandes de base

Raccourcie | Action
---|---
<kbd>shift</kbd> + <kbd>left click</kbd> | Ouvrir le lien dans la barre latérale
<kbd>ctrl</kbd> + <kbd>`[`</kbd> | Backwards
<kbd>ctrl</kbd> + <kbd>`]`</kbd> | Forwards
<kbd>ctrl</kbd> + <kbd>k</kbd> | Recherche sur l'ensemble des notes
<kbd>ctrl</kbd> + <kbd>shift</kbd> + <kbd>k</kbd> | Recherche sur la page actuelle
<kbd>ctrl</kbd> + <kbd>z</kbd> | Annuler
<kbd>ctrl</kbd> + <kbd>y</kbd> ou <kbd>ctrl</kbd> + <kbd>shift</kbd> + <kbd>z</kbd> | Refaire

### Navigation

Raccourcie | Action
---|---
<kbd>g</kbd> + <kbd>h</kbd> | Go to home
g j | Go to journals
g a | Go to all pages
g g | Go to graph view
g f | Go to flashcards
g t | Go to tomorrow
g n | Go to next journal entry
g p | Go to previous journal entry
g s | Go to keyboard shortcuts

### Basculer / toggle

Raccourcie | Action
---|---
? | Toggle help
t o | Toggle open blocks
t w | Toggle wide mode
t c | Toggle cards
t d | Toggle Document Mode
ctrl+c ctrl+b | Toggle display brackets
t t | Toggle Dark/Light mode
t l | Toggle left sidebar
t r | Toggle right sidebar
t s | Toggle settings
alt+sh­ift+c | Toggle contents in sidebar

### Block navigation

#### Mode edition

Raccourcie | Action
---|---
Enter ou click | Enter edit mode
ESC | Exit edit mode
Flêche haut | Up a line
Flêche bas | Down a line
alt+Flêche droite | Zoom into block
alt+Flêche gauche | Zoom out editing block

#### Mode block

Raccourcie | Action
---|---
ESC | Go to block mode
Enter | Go to edit mode
Flêche haut | Up a block
Flêche bas | Down a block
alt+Flêche droite | Backwards
alt+Flêche gauche | Forwards

### Déplacement de block

Raccourcie | Action
---|---
tab | Indent block
shift+tab | Outdent block
alt+shift+Flêche haut | Move block up
alt+shift+Flêche bas | Move block down

### Selection de texte

Raccourcie | Action
---|---
click & drag | Select text
double click & drag | Select words
triple click & drag | Select lines
shift+­arrow | Select text
ctrl+s­hif­t+arrow | Select words
ctrl+a | Select full line in edit mode
ctrl+a | Select full page in block mode

### Raccourcies spéciaux

Raccourcie | Action
---|---
ctrl+s­hift+p | Open command palette
ctrl+s­hift+j | Open todays page in sidebar
ctrl+c ctrl+c | Clear right sidebar
ctrl+d ctrl+a | Open file in default app
ctrl+d ctrl+i | Open file in parent directory
ctrl+c ctrl+s | Rebuild search index
ctrl+s­hift+f | Add/Remove favorites
ctrl+s­hift+y | Insert youtube timestamp
ctrl+s­hift+1 | Run git command

## Requetes

### Requetes simples

Raccourcie | Action
---|---
/query | Start Query
(and A B) | Both need to be true
(or A B) | One needs to be true
(not A) | A should not be true
(task A B) | Get all tasks with state A or B
(task TODO) | Find all tasks TODO
(namespace A) | Get everything from namespace A
(page-­pro­perty A) | page property A exists
(page-­pro­perty A B) | page property A equals B
(property A) | Find anything with property A
(priority A) | Filter on priority A
(page-tags A) | Filter on page tags A
(between :-1d :-3d) | Filter journal entries between yesterday and 3 days ago
(block­-co­ntent abc) | Does a block contain the string abc
(page abc) | Get page abc
(page-ref abc) | All blocks that refer to page abc

### Requêtes favorites

Get all tasks that are open en tagged with ABC

```
{{query (and (task TODO DOING) [[ABC]]) }}
```

Query subsection of a page

```
{{query (and (page <% current page %>) [[tag]] )}}
```

Find all templates

```
{{query (property template) }}
```

All tasks related to current page

```
{{query (and <% current page %> (task TODO DOING DONE) )}}
```

## Ressources

- <https://github.com/logseq/logseq>
- <https://github.com/logseq/awesome-logseq>
- <https://www.youtube.com/watch?v=KfMx0a6mb18&list=PLwpUQg3DhPIrx0mTZNjg3u5WdYyG0a0m4>

### Documentation

- <https://docs.logseq.com/>
- <https://github.com/logseq/docs>
- <https://github.com/logseq/awesome-logseq#-guides-and-how-tos>
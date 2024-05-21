---
title: Commits Conventionnels
description: 
published: true
date: 2024-05-21T17:18:30.490Z
tags: 
editor: markdown
dateCreated: 2024-05-21T17:18:30.490Z
---

# Commits Conventionnels

Une spécification ajoutant une signification lisible pour l'humain et pour la machine dans les messages des commits.

La spécification de Commits Conventionnels est une convention basique pour des messages de commit propres. Elle fournit un ensemble simple de règles pour créer un historique de commit explicite, ce qui facilite l’écriture d’outils automatisés. Cette convention suit SemVer, en décrivant les fonctionnalités, les correctifs et les modifications importantes apportées aux messages de commit.

Le message du commit doit être structuré comme suit :

```txt
<type>[étendue optionnelle]: <description>

[corps optionnel]

[pied optionnel]
```

Le commit contient les éléments structurels suivants, permettant de communiquer à l’intention des consommateurs de votre API :

1. **fix**: un commit de *type* `fix` corrige un bogue dans le code (cela est en corrélation avec `PATCH` en gestion sémantique de versions).
2. **feat**: un commit de *type* `feat` introduit une nouvelle fonctionnalité dans le code (cela est en corrélation avec `MINOR` en gestion sémantique de versions).
3. **BREAKING CHANGE**: un commit qui contient dans son pied le mot-clé `BREAKING CHANGE:`, ou dont le *type/étendue* est suffixé d’un `!`, introduit une rupture de compatibilité dans l’API (cela est en corrélation avec `MAJOR` en gestion sémantique de versions). Un BREAKING CHANGE peut faire partie des commits de n’importe quel *type*.
4. Les *types* autre que `fix:` et `feat:` sont autorisés; par exemple, [@commitlint/config-conventional](https://github.com/conventional-changelog/commitlint/tree/master/%40commitlint/config-conventional) (basé sur [the Angular convention](https://github.com/angular/angular/blob/22b96b9/CONTRIBUTING.md#-commit-message-guidelines)) recommande `build:`, `chore:`, `ci:`, `docs:`, `style:`, `refactor:`, `perf:`, `test:`, etc.
5. Les *pieds* autres que `BREAKING CHANGE: <description>` peuvent être fournis et suivre une convention similaire à [git trailer format](https://git-scm.com/docs/git-interpret-trailers).

Les types supplémentaires ne sont pas prescrits par la spécification de Commits Conventionnels et n’ont aucun effet implicite dans la gestion des versions sémantiques (à moins qu’ils ne comportent un BREAKING CHANGE). Une étendue peut être fournie au type d’un commit pour fournir des informations contextuelles supplémentaires. Elle est indiquée entre parenthèses, par exemple, feat(parser): add the ability to parse arrays.

- <https://www.conventionalcommits.org/fr/v1.0.0/>
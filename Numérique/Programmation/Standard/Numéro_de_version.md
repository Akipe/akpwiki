---
title: Numéro de version
description: 
published: true
date: 2024-05-21T17:12:59.665Z
tags: 
editor: markdown
dateCreated: 2024-05-21T14:17:47.892Z
---

# Numéro de version

## Standard ***courant***

`w.x.y.z`, exemple : `3.2.1:4`

- `w` : version majeur, c'est à dire risque de cassure avec l'ancienne version
- `x` : version mineur, ajout de fonctionnalité
- `y` : fixe, correction de bogues et de sécurité
- `z` : numéro de compilations, optionnelle.

## Standard ***Semantic Versioning***

Given a version number MAJOR.MINOR.PATCH, increment the:

1. MAJOR version when you make incompatible API changes
2. MINOR version when you add functionality in a backward compatible manner
3. PATCH version when you make backward compatible bug fixes

Additional labels for pre-release and build metadata are available as extensions to the MAJOR.MINOR.PATCH format.

- <https://semver.org/>

### semantic-release

**semantic-release** automates the whole package release workflow including: determining the next version number, generating the release notes, and publishing the package.

This removes the immediate connection between human emotions and version numbers, strictly following the **Semantic Versioning** specification and communicating the impact of changes to consumers.

- <https://semantic-release.gitbook.io/semantic-release>
- <https://github.com/semantic-release/semantic-release>
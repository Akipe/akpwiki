---
title: Marp
description: 
published: true
date: 2024-05-21T18:33:24.997Z
tags: 
editor: markdown
dateCreated: 2024-05-21T18:33:24.997Z
---

# Marp

Marp est une application/langage/extension vscode qui permet de faire des présentations visuels comme Microsoft PowerPoint.

- <https://marp.app/>
- <https://github.com/marp-team/marp>
- <https://github.com/marp-team/marp-core>

Il utilise la version ***CommonMark*** du Markdown.

## Exemple

```markdown
---
marp: true
theme: gaia
author: Prénom Nom
paginate: true
transition: fade
---

<style>
img[alt~="center"] {
  display: block;
  margin: 0 auto;
}
</style>

# **Nom du projet**

1. Réalisations *de la semaine*
1. Organisation du projet
1. Feuille de route
1. Fonctionnalités obsolètes

---

# Réalisation : base de donnée

![width:1200px center](./img/bdd_mld_ancien.png)

---

# Réalisation : base de donnée

![width:1200px center](./img/bdd_mld_nouveau.png)

---

# Réalisation : développement


Meilleures cohésion entre les développeurs

![width:300px](./img/logo_docker.png)

---

# Organisation du projet

- Méthode Scrum

* Cycle d'avancement : *2 semaines (à étudier), 7 fois*
* Demo à chaque cycle : *si possible & pertinent*
* Réunion fin cycle : *retours, points bloquants & questions*

---

# Feuille de route

Version 0.1 *(xxx)* : initialisation du projet

![width:1200px center](./img/roadmap_1.png)

---

# Feuille de route

Version 0.2 *(courant xxx)* : implémentation obsolescence

![width:1200px center](./img/roadmap_2.png)

---

# Fonctionnalités obsolètes

- nanan
* *Autres points ?*

```

## Compilateurs

### VSCode

Installer l'extension **Marp for VS Code**
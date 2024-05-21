---
title: Chromium
description: 
published: true
date: 2024-05-21T19:40:17.146Z
tags: 
editor: markdown
dateCreated: 2024-05-21T19:40:17.146Z
---

# Chromium

## Installation

### **ungoogled-chromium**

Modifications de Chromium pour améliorer la vie privé.

<https://github.com/ungoogled-software/ungoogled-chromium>

```url
chrome://ungoogled-first-run/
```

#### Autorisation de l'ajout d'extensions

1. `chrome://flags`
2. `#extension-mime-request-handling` to `Always prompt for install`
3. Installer l'extensions **chromium-web-store** : <https://github.com/NeverDecaf/chromium-web-store/releases/latest>

> If you do not see the Add to Chromium button in the web store, you can use the context menu option instead: Right click > Add to Chromium.

### Utilitaire **chrlauncher**

Outil permetant la mise à jour automatique de différentes versions de Chromium (notamment *ungoogled-chromium*).

<https://github.com/henrypp/chrlauncher>

## Configuration

### Ungoogled chromium

Information sur les options : <https://github.com/ungoogled-software/ungoogled-chromium/blob/master/docs/flags.md>

#### Activer les extensions à installer depuis le store

1. Ouvrir <chrome://flags/#extension-mime-request-handling> et définir à `Always prompt for install`
2. Télécharger l'extension `Chromium.Web.Store.crx` depuis <https://github.com/NeverDecaf/chromium-web-store/releases>

### Accès aux composants de chromium

`chrome://components`

### Accès aux configurations avancés

`chrome://flags`


## Extensions

### Développement

- <https://github.com/ANG13T/designr>

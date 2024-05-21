---
title: Failles de Sécurité
description: 
published: true
date: 2024-05-21T12:37:08.785Z
tags: 
editor: markdown
dateCreated: 2024-05-21T12:37:08.785Z
---

# Failles de Sécurité

## Alertes

- <https://www.cert.ssi.gouv.fr/>

## Nomenclature CVE

Gérer par l'entreprise **MITRE Corporation**.

Elle s'occupe de référencer les différents CVE :

> CVE : Common Vulnerabilities and Exposures

Une CVE se nomme comme ceci : *ANNÉE-INDEX_FAILLE_DE_L_ANNÉE*

Exemple : 2028-124 *(124ème faille de l'année 2028)*.

## Types de Failles

| Type | Nom | Description |
|---|---|---
| LFI | Local File Inclusion | Lire ou executer un fichier sans avoir besoin de s'authentifier.

## Liste de failles connus

- <https://www.exploit-db.com/>

## Recherche de failles

### `searchsploit`

<https://www.it-connect.fr/recherche-rapide-dans-la-base-exploit-db-avec-searchsploit/>

## Test d'intrusion
<https://www.metasploit.com/>

## Scanneur de vunérabilité

### nuclei

Outil pour automatiser la recherche de vulnérabilité à partir de "recttes" au format yaml et à partir de config de la communautée.

### Wappalyzer

<https://addons.mozilla.org/fr/firefox/addon/wappalyzer/>

### nikto

Analyseur pour applications web.

- <https://github.com/sullo/nikto>
- <https://memo-linux.com/nikto-outil-scanner-de-securite-serveur-web/>

### wpscan

Analyseur pour application web Wordpress

<https://github.com/wpscanteam/wpscan>

### BurpSuite

Analyse de requette http en proxy. Utilisation de FoxyProxy pour faire passer les requetes.

### ZAP OWASP

Scan de vulnérabilité utilisant les régles de l'OWASP.

### Wapiti

Scanner de vunérabilité.

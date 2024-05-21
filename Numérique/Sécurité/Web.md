---
title: Web
description: 
published: true
date: 2024-05-21T12:34:22.059Z
tags: 
editor: markdown
dateCreated: 2024-05-21T12:34:22.059Z
---

# Web

## Bonnes pratiques

### OWASP

<https://owasp.org/>

## Informations sur le serveur

```bash
curl -I http://IP_ADRESS/
```

## Trouver des pages cachées

> **Attention ! Le simple faite de scanner une page web est une infraction à la loi dans de nombreux pays !**

Un scan laisse de nombreuses traces dans les fichiers de journalisations.

### Scan avec `dirb`

`dirb` va essayer d'acceder automatiquement à un ensemble de fichiers fréquement utilisé sur les serveurs. Il affichera les adresses existantes.

```bash
dirb http://IP_ADDRESS -X .php
```

## Requete POST à la main

Exemple de requete POST réalisé soit même :

```http
POST http://ADRESSE HTTP/1.1
Host: IP_ENVOYEUR
Content-Type: application/x-www-form-urlencoded
Content-Length: 27

NOM_CHAMP=VALEUR
```

## L'Injection de commandes

Si un formulaire est mal protégé, on peut s'en servir pour faire executer des commandes au serveur.

Exemple : un champ de formulaire où l'on peut entrer un nombre entre 1 à 4 pour choisir une action à réaliser.

Le serveur executera la commande `./autodiag.sh 1` si l'on rentre `1` dans le champ du formulaire.

On peut modifier notre champs par `1; ls` ce qui fera executer au serveur la commande `./autodiag.sh 1; ls`.

## Certificats SSL

### Création d'une autorité de certification

- <https://tech.kibatic.com/ops/https-en-dev/>
- <https://cert-manager.io/docs/configuration/selfsigned/>
- <https://jamielinux.com/docs/openssl-certificate-authority/introduction.html>

Outils :

- <https://github.com/smallstep/certificates>
- <https://github.com/dogtagpki/pki>
- <https://github.com/rabbitmq/tls-gen>
- <https://github.com/minio/certgen>
- <https://github.com/bertrandmartel/ssl-cert-dashboard>
- <https://medium.com/@duhruh/trusting-your-docker-apps-setting-up-your-own-certificate-authority-7d1dbfb7dc4>
- <https://smallstep.com/blog/automate-docker-ssl-tls-certificates/>

### Test de configuration SSL

- <https://ssl-config.mozilla.org/>
- <https://www.ssllabs.com/>
- <https://tls.imirhil.fr/>

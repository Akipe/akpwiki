---
title: Synology
description: 
published: true
date: 2024-05-21T19:52:24.226Z
tags: 
editor: markdown
dateCreated: 2024-05-21T11:42:56.426Z
---

# Synology

## Installation

### Periphérique officiel

### Xpenology

- <https://xpenology.com/forum/>
- <https://xpenology.net/en/introduction/>
- <https://xpenology.org/>
- <https://xpenology.club/>
- <https://www.reddit.com/r/Xpenology/>

## Configuration

### Sécurité

<https://www.youtube.com/watch?v=b37lkIlowNA>

### Certificats SSL

#### ACME et DNS 01

- <https://lippertmarkus.com/2020/03/14/synology-le-dns-auto-renew/>

Créer un compte utilisateur dans le groupe `administrators`.

Lui retirer tous les droits.

```shell
wget -O /tmp/acme.sh.zip https://github.com/acmesh-official/acme.sh/archive/master.zip && \
sudo 7z x -o/usr/local/share /tmp/acme.sh.zip && \
rm /tmp/acme.sh.zip && \
sudo mv /usr/local/share/acme.sh-master/ /usr/local/share/acme.sh && \
sudo chown -R $NOM_UTILISATEUR:users /usr/local/share/acme.sh/
```

```shell
cd /usr/local/share/acme.sh
sudo su $NOM_UTILISATEUR

export INFOMANIAK_API_TOKEN="$TOKEN" && \
./acme.sh --issue --dns dns_infomaniak -d $DOMAINE.COM -d *.$DOMAINE.COM --server letsencrypt --home $PWD
```

```shell
export SYNO_Create=1 && \
export SYNO_Username="$NOM_UTILISATEUR" && \
export SYNO_Password="$MOT_DE_PASSE_UTILISATEUR" && \
export SYNO_Scheme="https" && \
export SYNO_Hostname="$URL_AVEC_NOM_DOMAINE" && \
export SYNO_Port="5001" && \
./acme.sh --insecure --deploy --deploy-hook synology_dsm -d $DOMAINE.COM -d *.$DOMAINE.COM --home $PWD
```

Ensuite naviguer dans DSM : Panneau de configuration > Planificateur de taches

Créer une nouvelle tache : créer -> tache planifier > Script utilisateur

- Tache : Renouveler tous les certificats via acme
- Utilisateur : $NOM_UTILISATEUR
- Tous les premiers du mois (lundi, mardi, mecredi... dimanche), chaque mois, à 10h
- script utilisateur :
```shell
/usr/local/share/acme.sh/acme.sh --cron --home /usr/local/share/acme.sh
```

## Astuces

### Démarrer depuis n'importe où

<https://www.youtube.com/watch?v=BFm44HxgW8ww>

## Applications

### Depot officiel

<https://www.synology.com/en-us/dsm/packages>

### Depot tiers

Moteur de recherche de paquet multi dépot : <https://synopackage.com/home>

Nom | Adresse | Web | Informations
---|---|---|---
`SynoCommunity` | `https://packages.synocommunity.com/` | <https://synocommunity.com/>
`digitalboxdsm7` | `https://digitalbox.go.zd.fr/` | <https://digitalbox.go.zd.fr/>

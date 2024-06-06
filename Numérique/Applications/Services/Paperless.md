---
title: Paperless
description: 
published: true
date: 2024-06-06T17:30:15.340Z
tags: 
editor: markdown
dateCreated: 2024-06-06T17:30:15.340Z
---

# Paperless

## Installation

### Paperless-NGX

## Configuration et utilisation

### Archive Serial Numbers (ASN)

C'est un identifiant unique pour chaque document qui permet une meilleure organisation des documents physiques.

Le principe est de ranger, par ordre croissant ASN, chaque document dans un même support.

Comme ceci, on disposera par exemple :
- d'un classeur contenant les documents classés par ASN de 0 à 50
- puis d'un autre classeur contenant les documents par ASN de 51 à 100
- et d'un autre de 101 à 150...

On fera attention de bien noté sur le support la plage du plus petit et plus grand ASN contenu

> exemple : ASN 0000 à 0041

### Organisation des nom des fichiers

> Attention ! Ne modifier jamais à la main les nom des fichiers, sinon Paperless ne sera plus où il est.

On doit créer un nouveau *storage path* en ajoutant la configuration des noms de fichier :

- {asn}: The archive serial number of the document, or "none".
- {correspondent}: The name of the correspondent, or "none".
- {document_type}: The name of the document type, or "none".
- {tag_list}: A comma separated list of all tags assigned to the document.
- {title}: The title of the document.
- {created}: The full date (ISO format) the document was created.
- {created_year}: Year created only, formatted as the year with century.
- {created_year_short}: Year created only, formatted as the year without century, zero padded.
- {created_month}: Month created only (number 01-12).
- {created_month_name}: Month created name, as per locale
- {created_month_name_short}: Month created abbreviated name, as per locale
- {created_day}: Day created only (number 01-31).
- {added}: The full date (ISO format) the document was added to paperless.
- {added_year}: Year added only.
- {added_year_short}: Year added only, formatted as the year without century, zero padded.
- {added_month}: Month added only (number 01-12).
- {added_month_name}: Month added name, as per locale
- {added_month_name_short}: Month added abbreviated name, as per locale
- {added_day}: Day added only (number 01-31).

<https://docs.paperless-ngx.com/advanced_usage/?ref=skerritt.blog#file-name-handling>

### Ajout de documents par mail

### Ajout automatique depuis appareil HP

Voir le logiciel *node-hp-scan-to* depuis [Imprimante HP](https://wiki.akipe.fr///books/infrastructure-numerique/page/imprimante-hp).

### Organisation des tags, type, etc

<https://www.reddit.com/r/selfhosted/comments/sdv0rr/paperless_ng_which_tags_document_types/>

## Ressources

- <https://skerritt.blog/how-i-store-physical-documents/>
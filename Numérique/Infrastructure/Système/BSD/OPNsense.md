---
title: OPNsense
description: 
published: true
date: 2024-03-25T13:53:31.168Z
tags: 
editor: markdown
dateCreated: 2024-03-25T13:49:44.252Z
---

# OPNsense

## Configuration

### Blocage d'adresses IP

Il faut créer un ALIAS de type `URL Table (IPs)` et ajouter l'URL de la liste.

Si nécessaire il faut augmenter le nombre d'entrées autorisés. Pour ce faire il faut aller dans `Firewall` > `Settings` > `Advanced` et définir dans `Firewall Maximum Table Entries` le nombre maximum d'éléments autorisés.

#### Sources

##### BE.CYBER Community

<https://github.com/duggytuxy/malicious_ip_addresses>

- `https://raw.githubusercontent.com/duggytuxy/malicious_ip_addresses/main/botnets_zombies_scanner_spam_ips.txt`
- `https://raw.githubusercontent.com/duggytuxy/malicious_ip_addresses/main/botnets_zombies_scanner_spam_ips_ipv6.txt`
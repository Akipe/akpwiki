---
title: IPv6
description: 
published: true
date: 2024-03-04T12:17:47.289Z
tags: 
editor: markdown
dateCreated: 2024-03-04T12:17:47.289Z
---

# IPv6

## Raccourci d'adresses
Les `0` en début sont optionnels.
Quand ils y a plusieurs octes de `0`, on peut remplacer par `::` mais une seul fois.

```
2001:0DB8:0000:0000:0010:ABCD:DEF1:1234
2001:DB8:0:0:10:ABCD:DEF1:1234
2001:DB8::10:ABCD:DEF1:1234
```

## Prefix
```
2001:DB8:0:BA3::/60
```

Préfix pour la doc (non utilisable) : `2001:0DB8/32`

### Type d'adresse
Unspecified | 0000...0 (128 bits) | ::/128 |
---
Loopback | 0000...1 (128 bits) | ::1/128 |
---
Multicast | 1111 1111 | FF00::/8 |
---
Link-local unicast | 1111 1110 10 | FE80::/10 |
---
Unique Local Unicast | 1111 1100 et 1111 1101 | FC00::/7 |
---
Global unicast | tout le reste | tout le reste | routable reseau et internet & unique dans le monde

#### Adresse Unicast
Adresse la plus classique, dédigne interface unique en IPv6.

n bits | 128 -n bits
---
Prefix sous-réseau | Interface ID

`Interface ID`: plupart du temps 64 bits & adresse MAC

##### Global Unicast
Adresse unique dans le monde & routable sur l'ensemble du réseau Internet & privé.

n bits | m bits | 128-n-m bits
---


##### Link-local Unicast
Routable uniquement en local (ressemble notions adresse privé IPv4 en RFC 1918).
Routeurs ne doivent pas router ses interfaces.
FE80::/10

10 bits | 54 bits | 64 bits
---
1111 1110 10 | 0 | Interface ID

##### Unique Local Unicast
Adresse routable dans réseau privé (1 ou plusieurs sites), mais pas sur Internet.
Pour générer ces adresses, besoin algorithlme (web)
FC00::/7 | FD00::/7

7 bits | 1 | 40 bits | 16 bits | 64 bits
---
Préfix | L | Global ID | Subnet ID | Interface ID
0 | 0 | ID du Reseau global | Réseau | Machine

#### Adresse Multicast
Tout paquet envoyé est reçu et traité par l'ensemble des interfaces.

#### Adresse Anycast
Adresse pouvant être détenue par plusieurs interfaces (même ou différent hardware). Paquet traité par une de ces interfaces, souvent la + proche topologiquement.
Impossiblebde distinguer d'après syntaxe, et seul interfaces assignées sont conscientes de leur nature Anycast.

##### subnet-router anycast
Adresse permettant de s'addresser à n'importe quel routeur du sous réseau

n bits | 128 -n bits
---
Préfixe sous réseau | 000...000

#### Adresse Multicast
Défini un groupe d'interface. Ne peut 

8 bits | 4 bits | 4 bits | 112 bits
---
1111 1111 | flags | scope | groupe ID

FF00::/8

Par exemple, on défini le groupe hexa 123 pour un service NTP :
`FF01::123` : serveurs NTP même interface que l'expediteur.
`FF02::123` : serveurs NTP même lien réseau que l'expediteur.
`FF05::123` : serveurs NTP même site que l'expediteur
`FF0E::123` : serveurs NTP du réseau Internet

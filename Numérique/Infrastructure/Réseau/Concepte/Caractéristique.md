---
title: Caractéristique
description: 
published: true
date: 2024-03-04T12:17:15.902Z
tags: 
editor: markdown
dateCreated: 2024-03-04T12:17:15.902Z
---

# Caractéristique

- topologie 
  - physique : agencement cable, equipement réseau et éléments en bout de chaine
  - logique : chemin utilisé par les données pour naviguer
- vitesse : bits/s :
  - 100 mb/s
  - 1000 mb/s
  - ...
- cout de mise en place, maintenance etc
- sécurité : comment le réseau est protégé
- disponibilité :
  - calculé entre le temps ou il est disponible DIVISÉ temps total d'une année MULTIPLIÉ par 100 pour avoir % (99,9971%)
- evolutivité : est t'il évoluable dans le temps, par exemple avec l'ajout de personnes ?
- fiabilité : composant du réseau sont t'il fiable pour éviter les pannes ?

# Topologie Réseau

## LAN / WAN

### LAN

Se limite souvent à un secteur physique.

### WAN

Un regroupement de LAN. Pour pouvoir communiquer sur internet, le LAN doit pouvoir communiqué au travers du WAN.

## Topologie

### Physique

#### Par bus

Tous les postes sont connécté directement à tous les autres.

```
    *   *
    |   |
--------------
  |   |    |
  *   *    *
```

#### En anneaux (ring)

Les postes ont deux voisins chacun.

```
   *
  / \
 /   \
*     *
 \   /
  \ /
   *
```

#### En étoile (star)

La plus fréquente. Le péripherique central est souvent un composant du réseau, comme un switch.

```
  * * *
   \|/
 *--*--*
   /|\
  * * *
```

#### Maillé (mesh)

Chaque poste est connecté aux autres, permet une meilleur redondance et donc une meilleure fiabilité.

```
   *
  /|\
 / | \
*--|--*
 \ | /
  \|/
   *
```

## Diagramme réseau

Lorsque créer d'un réseau, il faut créer une carte détaillé (avec un diagramme).

Légende :

- S = interface série
- FA = Fast Ethernet
- GI = Gigabit Ethernet
- 192.168.1.0 = adresse réseau
- /24 = masque sous réseau

## Impacte des applications sur réseau

### Applications par lot

Enchaine de suite de commandes sans intervention humaine (comme FTP et TFTP).

### Applications interactive

Application qui attendent une réponse d'un utilisateur.

### Applications en temps réel

Nécéssite une intervention humaine, et bande passante très critique.
Pour ce type d'application, on utilise le **QOS** (Quality of service ou qualité de service).

- QOS = permet de donner des priorité, comme pour la VOIP.

## modèle OSI

OSI : Open System Interconnection, ou interconnexion de systèmes ouverts, mise en place par l'ISO. Permet la mise en place de programmes compatibles entre eux.

Il existe 7 couches de réseaux :

7. APPLICATIONS
   Assure l'interface avec les applications. C'est le niveau le plus proche des utilisateurs.

8. PRESENTATION
   Chargé du codage des données applicatives.

9. SESSIONS
   Gére l'ouverture et la fermeture de sessions de communication entre les machines du réseau.

10. TRANSPORT
    Charge de transport des paquet, c'est à dire de découper en paquet, et de gérer les erreurs de transmissions.

11. RESEAU (Network)
    Gére l'adressage et le routage des données, c'est à dire l'acheminement via le réseau.

12. LIAISON DE DONNÉES (Data link)
    Gére les communications entre 2 machines, directement connecté entre elle, connecté par un commutateur.

13. PHYSIQUE
    Défini comment les données sont physiquement converties en signaux numérique sur le media de communication.
    Exemple : impulsions electrique sur un cable RJ45 ou modulation de lumières sur fibre optique.

Moyens mémotechnique :

- Pour Le Réseau Tout Se Passe Automatiquement
- Après Plusieurs Semaines Tout Respire La Paix

## Protocole TCP/IP

Ce sont deux protocoles différents mais lier.

- TCP
  Protocole de Controle de Transmission.
- IP
  Protocol Internet

### Comparaison avec le modèle OSI

Uniquement 4 couches :

4. APPLICATION
   Equivalent couche 5 (session) 6 (presentation) et 7 (application) OSI.

5. TRANSPORT
   Equivalent couche 4 (transport) OSI.

6. INTERNET
   Permet acheminer les données de la source à la destination. Couche où le protocole IP fonctionne.
   Equivalent couche 3 (réseau) OSI.

7. LIAISON (link)
   Couche d'accès au réseau.
   Équivalent couche 1 (physique) et 2 (liaison de donnée) OSI.

## Communication Peer-to-Peer

```
Envoyeur                        Receveur

(De haut en bas)   PDU         (De bas en haut)
Applications ---- Data    ---- Applications
Transport    ---- Segment ---- Transport
Internet     ---- Packet  ---- Internet
Link         ---- Frame   ---- Link
```

Peer-to-peer = paire à paire, donc d'objets égaux.
Donc chaques couche doit pouvoir communiquer avec son égale de l'autre coté.
Donc les procotoles de chaques couches s'échangent des paquets.

- Paquets d'informations = PDU (Protocole Data Unit)

## Encapsulation et décapsulation

Les données sont encapsulé à l'envois et décapsulé à la récéption.
Analogie des poupées russes.

### Encapsulation

1. Données d'une application sont envoyé à la couche Application (1).
2. La couche transport ajoute une entéte de couche 4 et transmet à la couche internet.
3. La couche internet ajoute une entéte de couche 3 et transmet à la couche link.
4. La couche link ajoute son entéte de couche 2 et finalise avec le champs FCS.

FCS (Frame check sequence) = permet de détécté si les données sont éronné.

### Décapsulation

La même chose mais en sens inverse.

1. Commence par vérifier les données avec FCS, si non valide redemande le paquet.

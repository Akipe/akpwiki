---
title: Information Technology Infrastructure Library ITIL
description: 
published: true
date: 2024-09-08T18:41:40.771Z
tags: 
editor: markdown
dateCreated: 2024-09-08T15:11:41.834Z
---

# Information Technology Infrastructure Library, ITIL

## Introduction

ITIL est un modèle d'organisation à l'échelle d'une entreprise orienté sur la gestion de service informatique.

Les versions de ITIL sont :

- ...
- 2011
- V3
- V4 (dernière en date)


### Normes ISO

La norme ISO 20000 correspond à la normalisation du processus ITIL. Il reprend les bonne pratiques des version V3 et 2011 de ITIL

Il existe d'autres normes ISO intéressantes :

- ISO 2000 : SMS
- ISO 9001 : prendre en compte la qualité et la satisfaction client. Celà passe par la gestion des incidents utilisateurs, les outils, les process, les délais, et les solutions prévus. Par exemple gérer la réinitialisation de mot de passe.
- ISO 14 001 : sur la gestion de l'image écologique renvoyer par la structure.
- ISO 27 001 : sur la gestion des risque sur l'ensemble du domaine du numérique
	1. Sécurité operationnel (avoir un RSI, responsable sécurité physique, etc)
  2. Sécurité du personnel (clause de confidentialité, politique de gestion de mot de passe en fin de carrière etc)
  3. Sécurité physique
  4. Sécurité technologique (Gestion des mises à jour, pen test (PDCA))
- ISO 27 001 : c'est un guide pour aider la mise en place de la norme ISO 27 000
- ISO 45 000 : concerne la santé et la sécurité au travail 
- ISO 45 001

On peut se servir des normes ISO de deux manière :

1. Soit en s'inspirant des méthodes et prérequis de ceux ci.
2. Soit en appliquant à la lettre la norme et en passant un audit pour certifier la structure.

Les normes ISO sont payantes, notamment les documents documentants celles-ci. Elles sont géré entre autre par l'AFNOR Internaionnal Standard.

On peut réaliser 2 types d'audit pour vérifier la bonne application des normes :

1. Les audits internes. On les réalise au préalable aux audits de certification. Elle servent à montrer les points bloquants et les process à améliorer.
1. Les audits de certification. Valable pendant 3 ans mais avec un audit de vérification chaque année.

### Roue de Deming

![processus-pdca.jpg](/numerique/processus-pdca.jpg)

1. Plan - Plannifier
2. Do - Faire
3. Check - Vérifier
4. Acte - Agir, faire le point sur comment ça c'est passer et prendre des décisions pour la prochaine fois

Le tout en répétant en continue.

## Organisation

Il existe 64 modules dans ITIL. Il aide notamment à organiser l'organigramme de l'entreprise, ou à le comprendre.

### Les entreprises

Les entreprises sont des ensembles d'éléments interdépendant coordonnées en vue d'assurer une mission de production et de vente pour faire du profil.

Les entreprise sont composés de sous systèmes.

Les entreprises peuvent être interconnecté de plusieurs manières :

- en amont par des fournisseur de produit "semi fini"
- en aval par les distributeurs
- par des échangent divers et varié à l'aide d'entreprise de transport

#### Dans l'entreprise

Au sein de l'entreprise, on peut organiser comme ceci :

1. Les taches sont les actions que réalise les employés
2. Les postes sont occupé par les employés. Chaque poste réalise un certain nombre de taches
3. Les unités regroupe un certain nombre de postes. Elle sont organisé de manière à regrouper les types de postes et de taches commune. Par exemple le Service de Ressources Humaines est une unité.
4. Les flux concernent les échanges entre les unités, les postes et les taches.

Pour mieux organiser une entreprise, on peut réaliser un certain nombre d'opérations :

- la division : on divise des taches en plusieurs tache, des poste en plusieurs poste, des unités en plusieurs unités
- le regroupement : on peut regrouper des taches, des postes, des unités
- la coordination : on organise le flux entre différentes taches, postes, et unités.

Lors de la réorganisation, il faut éviter de chercher à trop "découper" les taches et les postes. Car celà va robotiser les taches à réaliser pour un poste, ce qui va démotiver l'employer et augmenter le risque d'un accident.

Pendant la réorganisation, il faut se poser ces questions :

- L'efficacité -> les objectif et les résultat
- L'efficence -> les moyens et les résultat
- La pertinence -> les objectif et les moyens

Plusieurs techniques existes :

1. Spécialisation horizontal : permet la spécialisation des postes

> *Divise "résoude des appel" pour un service client en "prendre l'appel", "qualifier l'appel" et "agir"

2. Spécialisation vertical
	- Permet d'associer des postes avec des compétences spécifiques pour chaqu'une des taches.
  - Permet de discocier la conception à réaliser qu'une seul fois à l'execution qui doit être réalisé plusieurs fois et/ou de manière réguliére

3. Le couplage : regrouper plusieurs taches en un poste.

Il existe plusieurs types de couplages :

- Couplage séquentiel : taches à réaliser à la suite du premier au dernier.
- Couplage réciproque : le flux de réalisation des taches peuvent être dans les deux sens
- Couplage de communauté : Regroupe les taches en fonction de contraintes, comme par exemple dans le cadre d'un SPOC. Par exemple le service d'accueil dans une banque : on réalise à la fois la gestion des appel, ainsi que de la gestion des clients physiques et pourquoi pas la gestion de divers taches.

### Sous système d'une entreprise

#### Système physique

Celà concerne les locaux, les équipement de l'entreprise et les flux physiques.

On peut aborder des problématiques d'optimisation de flux physique.

"Supply chain management" : la logistique inter-entreprise.

#### Système social

Celà concerne le partage de la même culture et de la même vision stratégique de l'entreprise par ses employés.

> Par exemple, la vision d'une entreprise pourrait être de venir le leader de son secteur d'ici 1 an.

#### Système de pouvoir

Il existe plusieurs type de pouvoir :

- Pouvoir légitime et formel : il est caractérisé par l'organigramme.
- Pouvoir légitime et informel : c'est par exemple un employé qui a de bonnes connaissance et les capacités à proposer des solutions, et dont les autres employés vont appliquer celle-ci.
- Pouvoir illégitime : celà peut être le chantage, la corruption, etc.

#### Système d'information

Celà concerne tout ce qui touche au numérique, mais pas que : tout type de donnée et d'informations non numérique font également partie du système d'information de l'entreprise.

Pour la partie numérique, celà concerne :

- L'infrastructure
- les applications

### Les mécanismes de coordinations

#### Supervision direct

Le responsable dirgie directement les employés en donnant un ordre directe.

Avantage :

- Guidé
- Apprantissage par la réalisation

Inconvénients :

- Peu de liberté
- déresponsabilisation

#### Ajustement mutuel

Les employer se coordonnent entre eux sans avoir besoin de l'explicité ("du bon sens").

> À LIDL, un client arrive en caisse, un employé dans les rayons arréte sa tache et va en caisse.

Avantage :

- Resonsabilisation
- initiative
- réactivité
- flexibilité

Désavantage :

- Divergence des acteurs
- absence de controle

#### Standardisation des procédés

On réalise la liste des procédure à l'avance à réaliser, et on demande à l'employer de les réaliser.

Avantage :

- Normalisation
- Checklist
- Conformité des résultat
- Productivité

Désavantage :

- Rigidité
- Perte d'initiative
- Bureaucratie
- Gestion des cas non prévu

#### Standardisation des résultat

On défini un certain nombre d'objectif voulu et on laisse la liberté à l'employer de trouver le moyen d'y arriver.

> Un élève à l'école doit travailler à sa manière pour avoir une bonne note.

Avantage :

- Initiative de moyen et d'objectif
- Engagement sur le résultat

Désavantage

- Stresse
- Risque de non conformité détéctable uniquement à la fin

#### Standardisation des qualifications

On spécifie les compétences necessaire à un poste, qui serviront à recruter un employé qui saura appliquer les bonnes actions en lien avec ces compétences.

> Un médecin peut pratiquer car il sait soigné grace aux connaissances apprises lors de sa formation.

Avantage :

- Garantie de compétences
- Engagement de moyen

Désavantage :

- Normalisation des profils
- Pas de remise en cause
- Corporatisme
- Risque de faux CV

### Paramètres de regroupement en unité

#### Paramètre de taille

Si on souhaite une supérvision directe, alors on aura un nombre d'unité subordonnées réduite.

Si on souhaite adopter une standardisation, alors on aura un nombre de subordonnées plus grand.

L'ajustement mutuel nécéssite un petit nombre d'employé dans une unité.

#### Paramètre de pouvoir

Est ce que le pouvoir est centralisé ou non ?

Si aucune (centralisation) alors tous les services dépendent du service stratégique. Celà augmente la charge de travail de ce service et réduit la productivité et l'adaptabilité des autres.

Si limité ou selective, alors on aura une organisation en arbre, avec la délégation de certain déscision à des unités intérmédiaire (*par exemple en autorisant les employés d'un service à dépenser une certain somme d'argent dans le cadre de leur mission*).

Si global, alors on a une répartition pur avec une liberté presque total des unités.

#### Paramètre de commandement

Une unité mets en commun la supervision, les ressources et les objectifs.

Quelques critères de regroupement :

- Par compétences : regroupé par leur fonction
- Par produit et marché : regroupé par divisions
- Par zone géographique

Il faut trouver le bon compromi entre décentralisation et coordination

### Type de structures

#### Structure fonctionnelle

Orienté regroupement par compétences qui mets en avant la logique de spécialisation.

On retrouve cette organisation souvent dans les entreprises :

- taille moyenne
- mono produit
- peu complexe

#### Structure divisionnelle

Orienté regroupement par produit qui mets en avant la logique de diversification.

Souvent organisé dans les entreprises :

- grandes entreprise ayant une large gamme et des divisions géographiques

#### Structure matricielle

Intégre les approches fonctionnelles et divisionnelles.

Dans les entreprise :

- avec un impératif de stabilité et de flexibilité
- pour accélerer l'inovation par produit

#### Structure Staff & Line

Mets en avant les services (unités) sur-spécialisé de "conseille" pour les restes des unités de l'entreprise.

Pour les entreprises :

- dans un environnement complexe et fluctuant

### Modèle Mintzberg : modèle de catégorisation des services et de leur rapport de force

![th-699203402.jpg](/numerique/th-699203402.jpg)

> Dans le graphique il manque la "ligne hiérarchie" qui doit être dans le triangle et relié le sommet stratégique au centre opérationnel.

Ce modèle permet d'avoir une vision d'organisation de manière hiérarchique par rapport aux missions de l'entreprise :

1. Sommet stratégique
2. Ligne hiérarchique
3. Centre opérationnel

Avec des parties complémentaires, qui peuvent être non présente ou externalisés :

1. Les techno-structures : toutes les unités qui aide à la structuration de l'entreprise et qui ne sont pas lié directement aux services proposé par l'entreprise.
	- Bureau des méthodes
  - audit interne
  - comptabilité
  - gestion du recrutement
  - ressources humaines
  - ...
2. Le **support** logistique : ce sont toutes les ressources necessaire à l'entreprise mais qui ne sont pas directement lié aux mission de l'entreprise.
	- restaurant d'entreprise
  - service courrier
  - ...

Le modèle de Mintzberg peut être appliqué à l'échelle de l'entreprise, dans les divisions ou bien à l'intérieur des département fonctionnelles (appelé également unités).

#### Rapport de force

Chacune des partie va essayer de mettre en place un rapport de force par rapport aux autres parties. Ces rapports de force vont influer la manière dont l'entreprise sera organisé.

##### Somme stratégie

Coordination principale (ou directe) : supervision directe

Force prépondérante : centralisation

Configuration structurelle : structure simple

Avantage :

Inconvénients : 

##### Techno-structure

Coordination principale (ou directe) : Standardisation des procédés

Force prépondérante : Standardisation

Configuration structurelle : Bureaucratie

Avantage :

Inconvénients : 

##### Ligne hiérarchique

Coordination principale (ou directe) : Standardisation des résultats

Force prépondérante : Balkanisation - guerre entre les structures et elles deviennent trop indépendantes.

Configuration structurelle : Structure divisionnalisée

Avantage :

Inconvénients : 

##### Centre opérationnel

Coordination principale (ou directe) : Standardisation des qualifications

Force prépondérante : Professionnalisation

Configuration structurelle : Bureaucration professionnelle

Avantage :

Inconvénients : 

##### Support logistique

Coordination principale (ou directe) : Ajustement mutuel

Force prépondérante : Collaboration

Configuration structurelle : Adhocratie (gestion de projets), similaire aux ESN (le chef de projet est dominant et qui vont collaborer avec les développeurs).

Avantage :

Inconvénients : 

#### Les facteurs d'influences

##### Externes

Ce sont des facteurs qui sont extérieur à l'entreprise.

- L'environnement
	- Stable ou dynamique : *si stable, standardisation des données, sinon bureaucratie mecaniste*
  - Compléxité : *si les déscisions sur le terrain son complexe, alors il faut des gens compétents et donc on standardise les qualitifactions*
  - Homogénéité et hétérogénéité : *si hétérogéne, il y aura une structure divisionnel divisé pour chaque marché*.
- Culture nationnal : chaque culture a des préférences
	- *France et Japon : plutôt standardisation des procédés*
  - *Allemands : plutôt standardisation des compétences avec la sur-important du diplome de docteur*
  - *Anglo-saxon : Standardisation des résultats avec la mise en avant des contrats, les préstataires et les sous traitant*

##### Interne

- L'age de l'entreprise : si agé, elle sera plus enclin à la standardisation, sinon elle adoptera plutôt une organisation simple.
- la taille : si l'entreprise est grande, elle adoptera une organisation plus structuré
- le système technique : si le système est fait sur mesure, il n'y aura pas besoin de standardiser les données, si le système technique est standard, alors il faudra standardiser les procédés.
- la statégie : s'il faut par exemple se diversifier, l'entreprise adoptera une structure de type divisionnelle.
- le pouvoir : en fonction de la Direction Général (DG), l'entreprise adoptera une organisation plutôt centralisé ou décentralisé.

### Modèle Greiner : modèle d'évolution de l'organisation de l'entreprise en fonction de sa croissance.

![modele-des-cinq-phases-de-croissance-greiner-1972-traduit-et-adapte.png](/numerique/modele-des-cinq-phases-de-croissance-greiner-1972-traduit-et-adapte.png)

Les entreprises ont tendances à évoluer de la sorte :

1. Crativité - structure simple
2. Direction - fonction
3. Délégation - divisions
4. Coordination - Technostructure
5. Collaboration - Adhoc
6. Renouveau

### La chronologies des organisation

Voici une chronologie de l'histoire de l'organisation des entreprise par Richard Scott :

1. Taylorisme (1900 - 1930), avec la surspécialisation des taches pour optimiser la production.
2. Le management RH (1930 - 1960), pour améliorer les conditions de travail, en adoptant une politique d'entreprise plus social.
3. Contingence (1960 - 1970), introduite par la concurence japonaise. Les entreprise devaient produire en fonction du marché internationnal. Il fallait planifier ce qu'on pouvait produire et vendre.
4. Toyotisme (1970 - 1995), remobilise les employé dans la vie de l'entrepris et met en avant la culture et les projets d'entreprise.

### La DSI

L'organisation de l'importance des valeurs que doit prendre en compte la DSI :

1. Chaine de valeurs (du produit)
2. Métier, qui représanté les processus de production dans les autres unités.
3. Services
4. Applications
5. Infrastructure

Le DSI a un double role de MOE et aMO.

Sa mission est d'apporter les ressources, les informations pertinantes, pour le pilotage et la réalisation des objectif de l'entreprise.

Il peut être composé de 3 unités d'activité :

- Développement : étude des besoins
- Technique : conception des solutions
- Production : execution des missions

Il doit gérer le SI et le co-piloter.

#### Historique de l'évolution du DSI

1. 1960 à 1989 : système central
	- Réduction des cout
  - Responsabilité du directeur (DAF)
  - Uniquement dans certaines unités
  	- gestion des comptes
    - gestion de la paye
    - gestion de la production assisté par ordinateur (GPAO)
  - architecture
  	- fonctionnel
    - materiel
    -structurel
  - les informaticiens sont privilégiés
  - avantages
  	- la puissance de calcul
  - désavantage
  	- les délais
    - les couts
    - la dépendance du service informatique
2. 1980 à 1990 : Élargissement du rayon d'action et micro-ordinateur
	- élargissement de l'informatique
  - des outils réalisé par d'autre entreprises sont produites et vendu pour être moins dépendant des service informatique
  - gestion des services
  	- logistiques
    - de gestion
  - architecture
  	- serveur centraux
    - infocentre
    - bureautique (ressources hétérogénes)
  - Organisation
  	- DOI mais relation complexe
    - Mode projet apparaissent mais ne sont pas encore fiables (cout, temps, faisabilité)
    - caractèrisé pra le réseau et le partage des ressources numériques (imprimante etc)
3. 1995 à 2000 : SI étendu
	- Choix d'utiliser des ERP au lieu de le développer en interne en plus d'utiliser les bonnes pratiques
  - De nouveau projets d'entreprise pour adopter de nouvelles normes :
  	- ERP/PCI
    - SCM
    - Y2K (bug de l'an 2000)
    - le passage à l'euro
  - architecture technique
  	- staff & line
    - utilisation de techno ouverte
    - utilisation de standard pour limité d'être bloqué
  - méthode de gestion de projet
  	- Gestion de projet amélioré mais avec encore des contraintes de budget et de temps
4. 2000 à 2005 : marché mondial avec internet et le service SI
	- Site web : marché mondial et évolution relation client, transport, gestion des stocks
  - technique : libération des dépendances constructeurs
  - structure : staff & line avec unité Qualité, Sécurité et PMO
  - Apparition d'ITIL
  - SLA : convention et contrat avec les clients
  - manque de cohérence entre la gestion du support clientel et le développement.
5. À partir de 2005 : SI stratégique
	- Préssion et menage lié aux couts de la part de la direction, avec un risque de sous traitance par l'infogérance (tiers maintenance, SASS). Nécéssité de pouvé l'utilité par des métrique comme le ROI (Retour Sur investissement, prendre en compte tous les couts numérique diviser par nombre de poste), démontrer le TCO (Total Cost of Ownership). Benchmarking par des cabinet externe.
  - Pression de la part des services métier, nécessité de prendre des engagements en fonction des moyens.
  - Pression de la pars des fournisseur (et du marché) par les vendeur de logiciel. Ce risque est accentué par le risque de l'obsolécence des logiciels en interne, par le manque de veille technique, par le manque de R&D avec de PoC (Proof of Concept) et par le manque de plan d'évolution technique.
  - Le personnel du DSI veulent rester compétent sur les dernière technologies et être formé pour ne pas risquer une perte d'employabilité. Il faudra proposer des formations.
  
  
## Lexique

- Risk based : basé sur les risque
- SMSI : System Management System Information
- ISO SMQ : System Management Quality
- QSE
- "Supply chain management" : la logistique inter-entreprise.
- SPOC : Single Point Of Contact
- DG : Direction Générale
- DSI
- MOE
- aMO
- SI : Système d'Information
- gestion de la production assisté par ordinateur (GPAO)
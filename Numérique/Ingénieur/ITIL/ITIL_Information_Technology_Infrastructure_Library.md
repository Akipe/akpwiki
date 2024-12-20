---
title: ITIL
description: 
published: true
date: 2024-10-15T15:08:02.443Z
tags: 
editor: markdown
dateCreated: 2024-09-08T15:11:41.834Z
---

# ITIL, Information Technology Infrastructure Library

## Introduction

ITIL est une bibliothèque de bonne pratique orienté à l'origine sur les métier de l'infra mais à présent sur le service informatique de l'entreprise.

ITIL ne permet de ne certifier que des individus, il existe la norme 20000 (ITIL v3) pour normaliser les entreprises.

### Historique

Agence gouvernementale anglais (Tatcher) qui défini un référentiel pour sous traiter les SI des administration.

- V1 (fin année 80) :
	- se base sur les référenciel et de nombres bonnes pratiques de la sous traitance de l'administration anglaise.
- V2 (2000) :
	- sensibiliser la notion de service
  - intégrer les projets au cycle de vie
  - structures de support et de conseil
- V3 (2007) :
	- Garder ITIL en phase avec l'entreprise (moins langage informatique)
  	- stratégie
    - transition
    - marketing
    - conception
    - amélioration
    - ...
  - reprend la compatibilité de ma V2 et ISO 20000
  - plus orienté métier et client
  - ajout de modules (5 modules), processus et de fonctions
- V2011 :
	- très proche de la version V3
	- On passe de 3 activités à 3 processus
- V4 (2019) :
	- basé sur la version V2011

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
  
---
q: fonction & poste ?

Un poste peut avoir un ou plusieurs fonctions - principe indépendance : poste ne ddevrais pas avoir plusieurs fonction du même domaine (développeur et teseur, RSSI et auditeur)
---
## Familles de Métier SI

Rapport publié par le Cigref qui propose des postes (fonctions) regroupé par famille.

Le modèle à tendance à se spécialisé.

Fonctions regroupé en 4 couches :

1. Architecture Processus Métier : exprime les besoins et pris en compte par management et le pilotage
2. Architecture SI Service (SOA)
3. Architecture Applications (AA)
4. Architecture (AT) Technique

### Pilotage

Evaluer les opportunée avec les Business Case (utilisé dans Prince2, et utilisé tout au long du cycle de vie du service/solution)

> Si la priorité de l'entreprise est la gestion des clients : mettre en place un CRM. Y'en a t-il un ? Mettre cette demande dans un document de Business Case.
> Le chef de projet va prendre ce document et réaliser ou pas ce projet
> On va garder et mettre à jour le business case tout au long du projet et même à sa fin.

---
q : comment s'articule le Business case par rapport au cahier des charges et les spec technique/fonctionnelle ?

business case : démontrer que la solution proposé / conseillé une solution qui répond aux exicences du cahier des charges. Peut exister plusieurs business case pour un cahier des charges, ce qui permttra de les comparer.
---

- Consultant SI
- Urbaniste SI
- Responsable domaine : relation avec métier
- Chargé affaire : un des cateurs pour processus gestion contrat de serrvice


### Management Projet

#### Chef de projet (métier) MOA

Ses missions :

- Il réalise le cahier des charges du projet pour exprimer les besoins du client.
- Il participe aux choix du projet avec le MOE.
- Il gére les évolutions et les avenants
- Coordonne les moyens (tests, mise en service et accompagnement) du projet coté métier
- Faire circulter les informations et définir les indicateurs/métriques.
- Recette en conformité avec le CDC

#### Chef de projet MOE

Ses missions :

- Réalise le projet en respectant les consigne du MOA - maitre d'ouvrage

Ses activités sont :

- Maitriser les risque et planifier le projet (avancement des KPI)
- Organise et coordone les ressources
- Détaille les specifications fonctionnelles
- Gére la **stratégie** de test et gére les anomalies
- Communique avec le MOA et propose des avenants 
- Déploie et accompagne le projet
- propose la recette au MOA et fait son bilan pour les prochains projets
- Demande de clarification avec le MOA sur les CdC

### Cycle applications

#### Développeur / Paramètreur

!!! Cétagorie de poste Applicatif, à vérifier si dans la bonne catégorie !!!

Mission : développer et paramètrer le projet

Activité :

- analyse les specification fonctionnelles
- réaliser la conception du projet
- réalise les modules du logiciel
- réalise les tests unitaire et traite les anomalies
- élabore les jeux d'essais pour les tests
- gére les dépendances et biliothéques
- réalise une documentation technique

#### Intégrateur d'application

Intégre et installe l'application ainsi que des composants (base de données, application auxilliaires, etc).

### MCO (Maintien en Condition Opérationnel) Infrastructure



### Support et assistance

- Technicien centre service (help desk) : technicien de support de premier niveau (dans le SPOC)
- assistant fonctionnel : correspond utilisateurs / Q user
- Expert qualité méthodologie

### Sécurité

### Management

Orienté vers les ressources humaines et les compétences de leur équipes.

## Lexique

- DPO : ?, souvent en lien avec la RGPD
- RGPD : ?
- HDS : Hébergement données de santé (norme ISO 27001) : si héberger en externe, obligation prestataire d'être HDS
- MOA : Maitre d'ouvrage, réalise le cahier des charges
- dette technique : baisse de maintenabilité lié à la technique (sur un ancien ou un nouveau projet). On peut analyser cette dette avec des outils comme par exemple SonarQube
- MOE : Maitre d'oeuvre, Chef de projet de réalisation
- Product Owner :
- KPI (gestion de projet) : Key Process (ou Project) Indicator (avec SonarQube par exemple)
- CdC : Cahier des Charges
- MCO : Maintien en Condition Opérationnel

## Modèle ITIL

Basé sur les processus.

### Contexte

Organisation vertical (hiérarchique).

Mais peut également utilisé en complémentaire des modules transverses organisé de la sorte :

- Processus de Direction
- Processus de réalisation (étude de marché, recherche du produit, vente, produit, etc), coeur du métier
- Processus de support (tout ce qui touche aux ressources : humaine, materiel, données)

SI est dans le processus de support.

Ce mode d'organisation se focalise sur les besoins du client.

Besoins clients -> {organisation transversal} -> résultat

L'unité organisationnel est organisé en poste sigref.

Est ce que l'unité SI doit adopter organisation transverse ? Celà peut aider au SI à mieux prendre en compte les clients.

Les directions informatiques sont de plus en plus indispensable notamment pour la gestions des besoins clients.

Le risque de ne pas adopter un mode d'organisation ITIL peut induire ceci :

- cout exorbitant
- ça ne marche pas / disfonctionnement
- trop de temps

Et ceux sans pouvoir expliquer les raisons. Mais si ça ne marche pas c'est qu'on a pas pu pouvoir définir les moyens (les mesurer) nécessaires qui n'ont donc pas pu être donné.

ITIL permet de définir clairement :

- Ce que l'ont fait
- pouvoir s'engager sur les services proposés
- des couts
- des cas pris en compte et ceux qui ne le sont pas
- des ressources necessaires

Pour mesurer le délais du service client par exemple : T initial (récéption de l'appel) et T fini (cloture de la résolution du problème), est ce que le contrat de temps est respecté ?

ITIL a permit de mettre en place cette structure pour calculer le délais. ITIL permet donc de professionnalisé le service SI en prenant des engagements.

### Mission et périmétre DSI

(p57 du diaporama)

Utilisation du modèle en 4 couches :

1. Métiers -> processus en direction des unités apportant de la valeur au client
2. Services SI
3. Applications
4. Technologies

### Organisation de la DSI

Organisation en silos :

```
          DSI
           |
    |-------------------|
  Etude             Production
    |                   |
    |   (regroupement)  |
    |                   |
  ERP,CRM,       PC, NET, Serveur,
  WEB, DWH       SGBD
    |                   |
  (en amont)         (en aval)
    |                   |
  Projets,  -------> Services
  Solutions ------->    |
    |                   |
  (méth. Prince2)    (méth ITIL)
```

ITIL ne prend pas en compte la gestion de projet, mais fait le lien avec les méthodes de gestion de projet.

Les spécialistes sont spécifique à leur silos, ce qui induit les risques :

- Manque de communication (services ne sont pas au courant des services/logiciels et donc ne peut comprendre les problèmes induites par eux).
- manque d'anticipation
- Les roles sont dispérser

La structuration :

- Partie projets et solutions
	- Représente 30% du budget
  - objectif
  	- productivité
    - créer de la valeur
- Partie production
	- représente 70% du budget

Exemple de question à se poser Est ce qu'on utilise bien tous les logiciels ? A quoi servent t'il ? Politique de gestion des licences ?)

### Caractérisation de la production

```
Activité technique (supersision) -> SAN de donnée -> réseau -> Cloud services
                                                         |---> Infrastructure interne (PC fixe, imprimante...)
```
                                   
Cloud services :

- SaaS : Software as a Service
- PaaS : Platforme as a Service
- IaaS : Infrastructure as a Service

Si externalisation du SI, est-ce necessaire d'utiliser ITIL ?

Oui car il permet :

- de bien se comprendre (partage du langage et du vocabulaire)
- de bien organiser pour les communications entre les unités interne et externe (prestataire) 
- de pouvoir organiser la sous traitance (quels services, quel contrat, etc)

ITIL permet une approche ITSM.

Logiciel de ticketing :

- LanDesk
- Isilog
- Service center
- EasyVista

Egalement possibilité de chercher des outils *ITIL compliant*.

Il faudra définir des contrats de service (SLA) ou des conventions de service avec les services internes pour ensuite demander un certain nombre d'obligation auprès des préstataire *(ISO 20000-1)* à l'aide du processus ITIL.

SI : activité de service qui induit un certain noimbre de caractéristique (immatériel, simultanée (produit et consomme en même temps) et relationnel (intéractions humaines)) engeandrant des risque de variabilités du niveau de service. *Exemple: service client : on peut tomber sur une personne expérimenté ou non par appel.*

#### Risques

Ces risque nécéssite des actions préventives à l'aide de système de management (pour limiter les variabilité) en mettant en place les processus et les ressources nécessaire. Ce service va mettre en place un SMS comme ITIL.

- Immatériel
- Simultané
- Relationnel

##### Service immateriel

Possibilités de problèmes :

- objets flou, difficulté à le définir ou à le borner
- caractéristique peu perceptibles
- résultat, cout, besoin difficile à décrire et à mesurer

Risques de :

- Préstation inadapté
- subjectivité d'appréciation -> insatisfaction percçu

Solution :

- matérialise l'offre de service (on informe clairement les services proposé ainsi que des options, en prévenant des risque et tout autre information utile)
- personnaliser et spécialiser les services (par exemple envoyer en cas de panne pour le client des pc de sauvegarde)

##### Service simultané

Il peut y avoir un pic de consommation par exemple pour la gestion du support utilisateur, ou lors de la gestion de traitement si tous les utilisateurs le lance en même temps, on risque de saturer le service (denie de service).

Risque :

- denie de service
- désiquilbre entre les demande et les moyen

Donc délais ou couts suplémentaire

Solutions :

- Prévisions des besoins et volume
- Modéliser le procesus du parcours client
- systémématiser (et automatiser) l'enchainement des activités
- standardisation et mutualisation des ressources

> *ON standardise un modèle de PC utilisé par tous les employés, et gardant un petit stock en cas où il serait necessaire de remplacer un des PC*

##### Service relationnel

Problème :

- Doit être bien utilisé par l'utilisateur : manque de compétence et risque de saturation du support utilisateur
- contact direct avec le prestataire

Risque :

- hétérogénétité des compétence et attitudes

Qui entrainera une instabilité du niveau de service

> *Risque de saturation du support utilisateur*

Solution : 

- former les utilisateurs
- Industrialiser, automatiser les processus

> *Mise en place d'un portail d'aide ou de FAQ, ou lors de la création d'un incident on récupére automatiquement les informations de l'utilisateur (type de poste, info technique et personnelle...)*

### Modèle d'organisation

Liste de modèles d'organisation (par l'entreprise *Gartner*).

> !!! image modèle gartner

CMMI : utilisé pour le développement

Plus le modèle est concret, mieux c'est.

> *ITIL 2 mets en avant la gestion du service client, qui est déjà connu par les professionnels du secteur*

Etude sur l'utilisation des méthodes de gestion de management : ITIL est utilisé en entier ou en partie dans 80% des entreprise (*Axelos Benchmarking ITSM 2017*).

Liste de d'autres méthodes (des plus utilisés au moins) :

- PMBOK (projet)
- Prince2 (projet)
- Scrum (projet)
- DevOps
- Lean (enchainer les activité de manière la plus performance possible)
- ISO 20000
- Six Sigma (basé sur les statistiques)

ITIL est dit *"holistique"* (global) : c'est une boite à outil de bonnes pratiques dans laquel on peut prendre ce que l'on veut. Sa mise en place peut être mise en place progressivement et peut être complémentaire. Elle peut être utilisé pour gérer "globalement" l'organisation du SI.

## Les processus ITIL

Graphique ITILv2 (p67)
Graphique ITILv2011 (p68)

Stratégie -> intégre étude opportunité et gestion des risques

Conception -> étudie service & architechture technique

Service Transition -> gére mise en production

Service opération -> gérer la production et le support

CSI -> aide à atteindre le niveau service attendu

Service informatique -> client : services métier -> client : clients entreprise.

SI va aider à gérer les

#### ITIL 2011

##### Services

Apporte de la valeur au client sans la résponsabilité des couts et des services.

##### Gestion de service

Apporter un savoir faire sur l'organisation de l'entreprise pour apporter de la valeurs aux clients sous forme de service.

##### Processus

Activités coordonées (aptitudes et ressources) ammenant à des résultat apportant de la valeur au client (directement ou indirectement).

> Réparer les machines ou application vendu au client, ou avoir un listing des configurations des machines.

##### Risque

Evenements potentiels indésirable empéchant d'atteindre les objectifs.

> PC portable pouvant être volé -> empéche de réaliser la mission de l'employé.

- Action corrective : résoudre les problèmes.
- Action préventive : éviter les risques.

On va gérer les risque par :

- l'impact -> ex : chiffrer le disque dur, réduire le nombre de données sur un pc, assurance pour le pc portable
- la probabilité

### Service Stratégie (SS)

Partie direction et concepteur de valeur à apporte aux clients.

> Valeur : composé d'une notion **d'utilité** et de **garantie** de bon fonctionnement.

Utilité :

- fonctionnalités

Garantie (niveau de service garantie) :

- service fonctionne
- performance correcte
- réalise correctement les taches (bug ou mauvais traitement du service)

DSI s'organise en tant que préstataire de service en interne dans l'entreprise :

- soit elle s'aligne sur la stratégie de l'entreprise
- elle "impulse" la stratégie de l'entreprise à l'aide des connaissances numérique

> *Le DSI du groupe Accord propose la mise en ligne des disponibilités des chambres des hotels en ligne*

### Service Design (SD)

La partie contrat : portefeuille de services et d'actif de service.

Associe les différents services à la réalisation de nouvelles fonctionnalités.

3 Niveau :

1. Préparation du service (offre en préparation)
2. Mise du service en catalogue (offre visible)
	- quelles compétences ?
  - quelles ressources ?
3. Obsoléscence du service (offre retiré)
	- retrait du service
  
> Remplacement d'un ERP : remplacement des accès à ceux ci pour le nouveau ERP

Permet de décliner des offres en fonction des services et vérifier si le service proposé correspond bien à la valeur que l'on souhaite proposé au client.

Activité de coordination, SLM (Service Level Management), service de gestion de catalogue, gestion de la disponibilité et autres garanties lié à l'infrastructure et à l'application (gestion du risque), gestion de la sécurité, gestion des fournisseurs.

SLM va gérer les contrat SLA

> Questionnement : est ce qu'on heberge le service en interne ? Plan de continuité ? Quel procédure de sécurité ?

*Business case service* est gérer par ce service, pendant la gestion de projet il devient un *business case project* (gérer dans service transition) qui lui n'existe que dans la phase de gestion de projet.

SLA : élément de garantie du service

### Service Transition (ST)

Module assure déploiement du service pour transitionnement sur l'opérationnel.

Il sert également à controler le bon fonctionnement d'un service ou d'un changement d'un service.

Il fait le lien avec les projets et peut déborder du cadre "classique" du workflow d'un service (par exemple lors d'une RFC qui doit être réalisé au plus tôt)

Périmétre :

- gestion des changements (RFC : Request For Change)
- Gestion des mises à jour des configuration & des connaissances (doc, faq, etc)
- Vérifie si les tests sont réalisé et s'il corresonde aux garanties défini du service

> On se rend compte qu'on utilise une appli qui utilise la BDD Oracle : Service Transition doit faire une RFC, pour :
> - mettre en place la BDD
> - avoir les compétences
> Et ainsi prévoir en amont les besoins d'un projet et par au dernier moment

Plusieurs processus :

- évaluation 
- planification
- gestion control
- bilan

Il protége l'environement de production pour limité les risques de variabilités (instabilités), les équipe opérationnel prendront en charge correctement le service.

### Service Opération (SO)         

Ce qui touche au plus près les utilisateurs. C'est la valeur ajouté la plus importante pour le client.

> On peut décider de réorganiser le module SO en premiers car on verra rapidement un changement positif dans l'entreprise (Quick Wins) ce qui aidera à la réorganisation de d'autres services dans un second temps qui prendront plus de temps à être perçu.

Doit gérer l'équilibre entre :

- Vue métier <-> Vue interne

> Dire oui systèmatique au métier <-> S'occuper des partie non métier comme mises à jour technique

- Evolutivité <-> Stabilité

> Beaucoup de demande de changement <-> peu de demande de changement

- Qualité <-> Couts

> Faire une application très qualitative qui va donc couté très chère <-> réduire au maximum les couts au détriment de la qualités

- Réactivité <-> Pro activité

> Géstion des incidents, traiter les incidents sans s'occuper des causes (toujours résoudre les même problèmes) <-> Gestion des problèmes, chercher uniquement les causes sans s'occuper de traiter les incidents


Il est le *service provider* (MOE) :

- Va gérer les événement (*ex: matériel passe de status fonctionnel à non fonctionnel)
- Gérer les incidents (si incident répétitif, devient un problème qui doit être résolut en trouvant la cause)
- Géstion des demandes et accès au service
- gestion "opérations communes" : sauvegarde, surveillance (monitoring), ordonancement (batch de nuit)

#### Centre de Service

Se rapproche de la gestion des incidents : c'est le SPOC pour la gestion des incidents, de niveau 1.

Il facilite la communication avec les utilisateur (un seul contact) pour :

- Les incidents
- les demandes

> *Couplage de communauté* : on regroupe sur le centre de service la gestion des incidents et demandes

Objectif :

- recevoir, enregistrer et gérer les appels
- assurer leur prise en compte et le traitement
- informer, relancer les acteurs internes et externes (support niveau 2 et 3)
- gérer satisfaction utilisteur

> Mauvaise pratique : si lors d'un appel d'un centre de service pour suivre l'avancement d'un projet, si le service ne peut pas répondre à la question car "on a pas accès au dossier" ou "ce n'est pas nous qui avons gérer ça" alors il y a un problème.

Indicateurs :

- volumes d'appele
	- reçu
  - attente
  - ratés
- demande résolut
	- total
  - en ligne
  - délai
- incidents mal orientés et réouvertur
- taux de satisfaction

Responsabilité :

p79

- enregistrer demande & incients
- Assurer une partie de la gestion des incidents
- suit les dossiers de bout en bout

Le centre de service va "escalader" l'appel : envoyer l'incident au service de niveau 2.

Egalement appelé "escalade fonctionnel" car le support niveau 2 est concidéré comme une fonction, donc on "escalade" de fonction en fonction.

Niveau 0 : assistant fonctionnelle, sur les sites clients, qui vont faire l'interface avec le centre de service.

(Niveau 0) -> Niveau 1 (centre de service ) <-> Niveau 2 <-> Niveau 3

Le centre de service gére la création et la fermeture du ticket.

Plusieurs formats :

1. Call Center
	- reçois les appels
  - les enregistre
  - ne resoud PAS les incidents
2. Help Desk
	- résoudre certain incidents
3. Centre de services
	- On devient le SPOC
  
Difficultés :

- resistance au changement à cause du changement d'habitude
- ressources / compétences mal adapté
- communication insuffisante de la mise en place (mal compris flux entre niveau 1 et 2)
- etc

Question test :

> Dans les activités ci-dessous, qu’est-ce qui n’est pas du
domaine du service desk :
> A. Fournir un support aux utilisateurs.
> B. Rechercher les causes des incidents.
> C. Être l’interface entre les utilisateurs et le service
informatique.
> D. Suivre la résolution des incidents.

#### Gestion des incidents

Réduire au maximum les effets des incidents. S'il le faut, il proposera des solutions de contournement (workaround)

> Si une imprimante ne fonctione pas, on va donner accès à une autre imprimante pour ne s'occuper de réparer l'imprimante dans un second temps

objectif :

- rétablir le service au plus vite
- escalader l'incident
- suivre l'incident
- proposer des solutions de workaround à un incident

Indicateurs :

- Backlog (incidents en cours) : age du backlog
- delais résolution, pourcentage de délais

Incident : événement non planifier qui pourrait provoqué une intéruption de service ou une dégradation de service.

Si c'est planifier : on appelle ça un changement (planifiable dans la gestion des changements).

```
Impact = fonction(nombre utilisateur impacté)
Urgence = fonction(degré de blocage)

Fort/moyen/faible

i(mpact) : 5,3,1
u(rgence) : 5,3,1
e(ffort) : 4,2,1

effort : plus ça demande d'effort, plus le chiffre est petit
```

Niveau priorité | Priorité | Délai de résolution
--|--|--
1 (100 à 50) | Majeur | 2h
2 (49 à 19) | Elevé | 4h ouvrées
3 (18 à 8) | Moyenne | 8h ouvrées
4 (7 à 1) | basse | 24h ouvrées

Scénario « standard » | I(mpact) | U(rgence) | E(ffort) | P(riorité) | D(urée)
--|--|--|--|--|--
Perte de mot de passe SSO | 3 | 5 | 4 | 1 | 2h
Indisponibilité ERP | 5 | 5 | 2 | 1 | 2h

```
3 * 5 * 4 * 1 = 60 
60 > 50 donc impact Majeur est donc intervention en moins de 2h
```

L'incidence majeur va demander une cellule de crise (plan de communication, en interne, en externe, le tout préparer en amont) (en interne : escalade hiérarchique, mobilisation de ressource, PRA (Plan Reprise Activité)

Role et responsabilité :

- Incident manager (également taches commun aux pilotes de processus)
	- défini le processus et les moyen
  - mesure et pilote la performance
  - améliore résultat et compétences
- Service desk (niveau 1)
- Support technique (niveau 2-3)

Un incident réseau affecte 200 utilisateurs. Au même
moment, l’imprimante du directeur tombe en
panne. Il doit imprimer un document important et
c’est urgent. Qu’en déduisez-vous :
A. Je n’ai pas assez d’information pour déterminer
quel incident traiter en premier.
B. Je traite en premier l’imprimante du directeur,
car c’est un « VIP ».
C. Les deux incidents sont de priorité égale.
D. L’incident réseau est plus important car il affecte
davantage de personnes.

Explication | I | U | E | P
--|--|--|--|--
Incident réseau | 5 | 5 | 2 | 50
(autre cas possible) | 5 | 3 | 2 | 30
VIP | 3 | 5 | 4 | 60
(autre cas possible) | 3 | 5 | 1 | 15

#### Gestion des problèmes

Le but est de réduire l'impact des incident en corrigeant les causes.

> incident / probléme : les incidents sont géré par les pompiers et les problèmes sont géré en amont pour éviter les pompier de s'éppuiser

Objectif :

- réduire l'impact des incidents
- supprimer les causes des incidents
- améliorer la productivité des équipes de support
- gérer les problèmes et erreurs connues

WorkAround : WA

diagramme p91

Strucuration de la recherche des causes à l'aide du doagramme (diagramme de cause à effet, l'arréte c'est les causes et le derniers points c'est l'effet)

p92

Familles de cause 5M :

- **Méthode** : Procédure, ficher d'instruction, consigne, organisation...
- **Moyen** : équipement, outils, maintenance...
- **Main d'oeuvre** : formation, compétences, comportement...
- **Matière** : entrées/sorties, flux d'information, communication, controles, mesures
- **Milieu** : environnement externe, conditions de travail

#### Gestion des événements

Surveillé les événements significatif de l'infratructure IT pour tout type d'opérations.

CI : Configuration Item - composant informatique - élément de configuration (ordinateur, serveur, imprimante, etc)

Objectif :

- fournir base de controle de l'exploitation
- détecter les événement, les analyser et définir des actions
- automatiser les procédures d'exploitation

> Evenement : changement état significatif d'un CI ou d'un service IT
> ex: Un ordinateur passe de l'état "en marche" à "éteinds"

> Alerte : message de changement d'état pour :
> - information
> - avertissement
> - erreur
> Ex: saturation réseau : erreur
> Ex: utilisation intensif du réseau : warning : si un ping ne reviens pas : un warning, si deux ping concécutif : erreur

On peut définir/identifier des paramètres et des seuil pour définir des alertes / changement d'état.

> Si le débit moyen du réseau descend à x Ko/s : warning / si descend à un second seuil : error
> Utilisation du load balancing

diagramme p97

#### Exécution des demandes

Egalement appelé *Request Fulfilment*.

C'est ce processus qui va traiter les demande simple et récurrente dans un processus spécialisé (demande simple et catalogue). On peut les délégué à des personnes moins expérimenté ou à des automates

> Dans les gare, si la demande est simple, on peut directement aller à la borne. Si la demande est plus complexe, alors on va au guichet. L'interet est de libérer le guichet.

Objectif :

- fournir canal rapide de prise en charge et de réalisation demande standard
- fournir information sur la disponibilité des services & procédure de demande (lien avec centre de service)
- acheter les composants et fournir le service

> **Demande de service** : demmande utilisateur sur un changement standard ; installation de logiciel, création de compte, accès VPN...

> **Changement standard** : changement simple (modèle prédéfini) pouvant définir facilement les étapes, les acteurs de réalisation, les délais...

> **Catalogue** : liste de service interne (ou externe) de l'entreprise. Par exemple, définir qu'il faut 2 jours pour créer un compte pour un nouveau employé fait partie des services du catalogue de l'entreprise.

diagramme p99

#### Gestion des accès

Gérer les droit d'accès aux utilisateurs.

finalité : autorisé ou non l'utilisateur à accéder à des services standard du catalogue.

CID: Confidentialité, Intégrité et Disponibilité des Données

> CID : qui à le droit d'accés ou de modifier des données (angle confidentialité)

Gérer au niveau des droits utilisateurs :

1. Identités : *identité d'un individus : m Dupond Jean*
2. Profil : *utilisateur normale ou utilisateur expérimenté ou un administrateur*, correspondant à son profile
3. Accés: *accès uax services et applications*
4. Droits : *droit de modification, de lecture, de suppression*

ACL: Access Control List

diagramme p 101

### Module CSI

Correspond à l'amélioration (continue) de tous les autres processus et tous les modules.

Processus : élément d'entré génére grace :

- aux ressources
- compétences et Roles
- d'activité (diviser en instruction (standardisation de procédé) à appliquer à des étapes clés)
- au travers de mesures

Qui vont générer des élément de sortie.

> *Des mail et données en entrée, savoir faire opérationnel va gérer les demande de support au niveau 1, 2, 3 pour au final donner en sortie la résolution du problème.*

Le product owner (pilote du processus) va controler le processus :

- Piloter
- vérifier les objectif son atteinds et avoir tableau de bord

Le pilote (product owner) n'a pas d'autorité hiérarchique mais une autorité du service, module et en définition du résultat du processus. On donne 

Ensuite le product Owner organise le module et les missions en catégories :

- Les activités
- Les instructions
- Les roles
- et il va réaliser une métrique pour avoir une idée des performances

Il sera aidé par des contributeurs :

- Ressources
- Aptitutes

> Résoudre les problèmes du support client en 8h, il faudra peut être revoir l'organisation des activités, des instruction et des roles pour réduire le temps de résolution d'un problème

> Equipe support : responsable service (management individus et ressource, hiérarchique, rh) et pilote procecus (orienté service, résultat, management de processus) définir un processus, processus de gestion incident

## Résumé

### Service opération

Commencé par QuickWins - résultat rapides

#### Centre de service

SPOC de la structure informatique (single point of contact)

Couplage de communauté (regroupement  de taches)

indicateurs :

- volume appels
- demande résolues
- incident mal orientés ou réouverture
- taux satisfaction

plusieurs type d'organisation :

- mutualisation du support niveau 1 pour plusieurs sites ou 1 centre de service par site

Escalade :

- fonctionnel, besoin de fonctions

Besoin de retours du niveau 1 par les autres niveau (delais prévisionnelles)

3 étapes :

1. Call center (centre d'appelle): prise d'appelle (que enregistré)
2. Help desk (centre de support) (enregistre et traite incident niveau 1)
3. Centre de service (enregistrement, traitement incident et gerer demande utilisateur)

Garenties à apporter :

- prise en compte avec enregistrement de la demande

#### Gestion des incidents

Evenement non planifié -> intérruption de service

Support initial avec WA (Work Around) avec des solutions de contournement géré par le centre de service. (ex: ecran bleu : faire redémarrer l'utilisateur.

##### Classification

- impact(pour métier)
- Urgence (de l'utilisateur)
- Effort (de résolution)

Multiplication des 3 facteurs avec définition de niveau de priorité

Niveau priorité | priorité | délais résolution
---|---|---
1 (100 à 50) | majeur | 2h
2 (49 à 19) | Elevée | 4h ouvré


Scénario standard | i | u | e | p | d
---|---|---|---|---|---
Perte mot de passe SSO | 3 | 5 | 4 | 1 | 2h

Incident majeur :

- instruction communication interne/externe (ajout message au téléphone), réduire saturation des demandes
- escalade hiérarchique, mobilisation ressources, PRA

### Processus

Il y a un pilote par processus.

4 

- définir le processus et les moyens (Plan)
- déploit de dispositif (fait appliquer la manière de procédé) (Do)
- mesure indicateur (Check)
- amélioration / réfléchir actions correctives (Act)

#### Gestion des problèmes

Gérer les problèmes une fois que les incidents sont traitées.

Analyse des causes de l'incident : solution de contournement pour aider processus incident 

Une fois problème défini et trouvé cause : proposer la modification par une demande de changement par la Gestion des changement (RFC, request for changement)

Problème (PB) : cause inconnue d'un incident

Erreur connue (KE) est un incident dont la cause est connue mais la solution définitive pas implémentée

- Processus "Problem control" : va détecter le problème et trouver des solutions de contournement (devient erreur connue)
- Processus "Error control" : fait suite au Problem control, permet de gérer l'erreur connue, rechercher une solution et implémenter la solution

Diagramme Ischikawa pour trouver cause à effets : pourquoi problème arrivé ?

5 familles :

- pb méthode
	- doc technique
  - mode opératoire
- pb moyen
- pb de milieu
- pb matières
- pb de main d'oeuvre

(ITIL : Gestion Problèmes 3/5 diapo)

process owner / pilote de processus :

- analyse technique de l'erreur connue


#### Gestion des événements

- surveiller les événement significatifs
- detecter ces événements
- analyser ces événements
- définir seuilles
- action automatique

#### Gestion des demandes

Demande de changement simple et récurrente :
- équipement
- ressources

plusieurs types demande :

- demande de services
- demande standard (défini et approuvé une première fois)

#### Gestion des accès

donen droit d'accès aux utilisateurs

matrice des droits ou justification

### Service Transition (ST)

Eviter les incidents lors de modifications : ne rien modifier n'est pas la solution.

Trouver un équilibre entre modification et stabilité.

Service transition va aider aux services sources de changement.

#### Gestion changement

Eviter les incidents lié aux changements.

> Mise en place BDD Oracle n'impacte pas les autres applications

- maitriser modification composants SI (CI : Configuration Item, ressource numérique)
- définir si changement vaut le coup
- agilité / adaptation pour la mise en place de changement
- réaliser les changement réussi du première coup (préparer le changement)

hidden change : changement caché : changement constaté à postériori, changement déployé sans demande et donc sans autorisation.

Changement : Ajout Modification Suppression de CI (composant) du Si

Possible d'utiliser le système de ticketing pour définir les changements.

Si un changement est simple et répétitif, impact faible et maitrisé : peut devenir standard si défini par les services.

CAB : Change Advisory Board : commité consultative des changements : change manager va interrargir avec des spécialiste du domaine à changer pour valider ou non un demande de changement

Change manager : personne seul qui peut décider de changement ayant un faible impacte

- mineur : change manager
- significatif : cab
- majeur : DSI (commité directeur avec DSI)

Toujours avec l'accord du Change Manager quel que soit le niveau

indicateur :

- degré d'urgence (par exemple win11 important car bientôt plus de support maj)
- niveau de ressources (par exemple un cout élevé pour Win11 car changer de pc materiel)

pour chacun des indicateur, 2 point de vue :

- métier
- 

Aller retours entre Processus de Mise en production et processus Gestion de changement.

Deployement en big bang : changement partout d'un coup, parfois necessaire (ex: changement de la BDD, obliger de changer toute l'application).

PIR : Post Implementation Review : 


CAB EC : Change Advisory Board Emergency Change


### Service Design (SD)

#### Gestion niveau de service

Accord de service entre fournisseur interne (DSI) et les métiers utilisateurs (clients internes)

Mettre en place un catalogue de service (lié aux demandes standard + SLA (contrat de services))

Contrat de service interne en entreprise == convention de service

Relation Client et le DSI

Comprendre les besoins et les ajuster en fonction coûts

Objectivé fourniture de services (savoir combien la DSI rapporte avec indicateurs objectif qui mesure qualité de service produit)

Indicateurs :

- indicateur de volume : % de couverture des métier par SLM
- nombre de revues - rapport suivi accords

Catalogue : tronc commun de services proposé

Conditions particulière dans catalogue de service : personnalisé services pour certains clients

SLA : applicable également entre ESN et clients

SLR : définir le niveau de service proposé (critères d'un SLA)

Etude de solutions pour SLR :

- capacité : infrastructure, équipement apportant réponse ?
- disponibilité (fault tolerant) : dupliquer équipement ?
- continuité: redémarrage lors de problèmes
- sécurité
- fournisseur
- financière (fait partie Service Stratégique)

Deux types de contrat :

- SLA : avec client
  - se base sur préstation
    - interne
    - externe (opérateur télécome : si plusieurs site, obligation) : capacité, délais d'intervention, etc : UC car externe

Cannal de communication :

- Canal com niveau client : SLM (Gestion Niveau de service) 
  - définir l'engagement du support
- canal de com niveau utilisateur : Centre de service : spoc (avec utilisateurs)
  - réaliser le support par rapport à l'engagement qu'on à défini

- Centre de profil : refacturation
- centre de coup : cout assumer par SI

Refacturation : permet de définir des couts par support (définir dans la SLA, qui sera tarrifié par Unité d'Oeuvre)

Contenu SLA :

- Partie (le fournisseur représenté par ... le client représenté par ...)
- Périmètre : fonction/métier concerné, site, durée
- Validité
- description
- tarif
- place de service
  - horaires
  - conditions spécial (fin de mois)
- disponibilités
- sécurité
- performance
- assistance
- tableau de bord (graphique)

Best effort (service de base) : engagement de moyen que de résultat

Le Service Level Manager peut représenter le DSI

Catalogue de service permet de définir des engagement (temps, ressources, etc) car changement standard

Server level manager :

- PDCA (plan do check act)

Description orienté client (pas 99.9% mais support sous 4h par ex)

### Gestion des capacités

Assurer ressources IT correspondent besoins acutels et future au meilleur cout.

#### Activités

Quotidiennement : (pour les deux dernière capacité, service et ressource)

- surveillance (monitoring)
  - outils mesure
  - définir seil
  - programmer alertes

- analyse performances
  - alertes
  - tendances
  - recherche causes

- amélioration (tuning)
  - rééquilibrage charge
  - répartition ressources

#### Type de capacités

##### Métier

conception configuration infrastructure

capacity plan : quels composants à ajouter sur la période à venir (et profiter opportunité pour achat avec bonus suite à cette prévision)

1 à 3 fois par an - prévision avec métier (espace stockage, puissance calcul...)

##### Service

opérationnel

Orienté service (service paye)

quotidienne

##### Ressources

opérationnel

quotidienne

## Structure de processus

Voir  p 75

module != processus (qu'est ce chacun ?)

- processus : organisation utilisé par ITIL
- module : 
- fonction :

Couleurs :

- Noir : disponible dans le coeur d'ITIL V2, bonne base d'organisation pour petite et moyenne enterprise.
- Gris : 
- Bleu : 
- à droite en vert et dans le cercle : fonctions
	- support probatoire : gestion lors de la mise en place de nouvelle applis, gérer les problèmes de transitions, documentation, formation, gestion des mécontentement des utilisateurs (Early Life Support)

### Processus

### Fonctions

Favorise la mise en place du modèle ITIL

## Déploiement ITIL

## Gestion des licences

- Vérifier les logiciels
- Vérifier licence
- Vérifier le nombre de licence correspond au nombre d'instance


## Ressources

### Web

- <https://www.atlassian.com/fr/itsm/itil>

### Livre

- <https://www.editions-eni.fr/livre/itil-4-comprendre-la-demarche-et-adopter-les-bonnes-pratiques-3e-edition-9782409045868>
- <https://www.editions-eni.fr/livre/itil-4-preparation-a-la-certification-itil-4-foundation-2e-edition-9782409039362>

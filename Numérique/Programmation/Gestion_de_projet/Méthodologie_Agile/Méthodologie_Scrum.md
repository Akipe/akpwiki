---
title: Méthodologie Scrum
description: 
published: true
date: 2024-05-21T15:21:16.117Z
tags: 
editor: markdown
dateCreated: 2024-05-21T15:21:16.117Z
---

# Méthodologie Scrum

## Présentation

La methodologie de gestion de projet Scrum est une methode qui respecte assez bien [la phylosophie Agile](https://wiki.akipe.fr///books/formation-cda/page/philosophie-agile).
Elle permet de gérer n'importe quel projet, que se soit un projet informatique ou autre.

Cette méthodologie est adapté aux projets dont on n'est pas sûr de ce que l'on doit faire, et/ou que l'on va devoir échanger régulierement avec le client.

Elle permet également de mieux chiffrer les cout et définir un temps aproximatif pour la réalisation du projet.

Cette méthodologie implique que l'on va devoir livrer réguliérement, avec des tests et des retours du client. Il faut également être flexible avec lui, en étant prêt à modifier les spécifications, tant que ça ne coute pas plus chère au projet.

Le client (seul ou avec un Product Owner) doit donc accepter de participer activement au projet.

> Le terme Scrum vient du rugby : lorsque l'équipe doit doit collaborer pour avancer jusqu'à l'objectif.

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/Ju3Eo84ykQSiZ73o-image-1665495762148.jpg)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/Ju3Eo84ykQSiZ73o-image-1665495762148.jpg)

La méthode Scrum se base sur le faite qu'on ne connait pas le résultat du projet.

On doit donc réaliser un ensemble d'itérations, qui sont appelées "sprints". Une itération dure en moyenne 1 mois, mais peut dépendre du projet. Mais elle doit par contre être respecté une fois défini.

Chaque sprint implique un certains nombre de réunions et de choses à réaliser.

Une équipe ne doit dans l'idéale ne pas dépasser 8 personnes.

Il existe également des méthodologies concurrente au Scrum :

- Le Test Driven Developpment (TDD).
- L'Extreme Programming.
- La méthode "traditionnelle".

### Type de modèle

C'est un modèle de développement **itératif et évolutif** :

- On peut ajouter des fonctionnalités tout au long du projet.
- On génére plusieurs itérations avant la version définitive.
- On construit le système en plusieurs fois.

Il reprent l'ensemble des étapes de développement de la méthodologie Processus Unifié :

1. Spécifications initiales
1. Analyse
1. Conception
1. Implémentation
1. Test

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/5ebYStYu2cpQq2wQ-image-1665485295194.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/5ebYStYu2cpQq2wQ-image-1665485295194.png)

## Étapes de la méthode Scrum

1. Défini le **Product Owner** et le **Scrum Master**, ainsi que l'équipe.
	- Le product owner est un représentant de l'entreprise client (maitre d'ouvrage, MOA)
    - Le Scrum master n'est **PAS** un chef d'équipe. Son rôle est de vérifier si la méthode Scrum est bien appliqué par l'ensemble de l'équipe, d'organiser la méthode Scrum, et de veiller aux bonnes conditions de travail de l'équipe.
	- L'équipes peut changer entre chaque sprint, mais pas pendant
1. Production du backlog générale entre le Product Owner et le Scrum Master.
	- Il va représenter l'ensemble des taches (ou User Story) à réaliser pour le projet. Il peuvent être technique ou pas.
    - Chaque User Story ne doit pas être trop petit ou trop grand.
    - On défini une User Story comme ceci :
		1. Définition *(ou nom, il représente ce qu'ont doit faire)* : `En tant que { X }, je veux { Y } afin de { Z }`
    	1. Commentaires *(précisions plus détaillé)*
    	1. Test d'acceptances *(en notation Ghuerkins, elle permetra de vérifier si on l'aura correctement réalisé)* : `Etant donne que ... lorsque ... alors ...`
1. Faire une première estimation de la charge de travail de chaque User Story
	- On pourra ensuite déterminer une date prévisionnelle de livraison final.
	- On déterminera également le prix prévisionnelle (point d'histoires -> jour idéal)
1. Determiner la capacité de travail de l'equipe
	- On calcul cette capacité de travail pour un sprint, de durée constante `X`, tout au long du projet.
    - On défini un taux de concentration à 0.7 pour le premier sprint pour calculer le nombre de jours réelles.
1. Pour chacun des sprints :
	1. Faire un backlog du sprint.
	1. Faire la réunion de planification
    	1. Première partie : avec l'équipe au complet, le scrum master et le product owner.
        	- L'objectif est de poser toutes les questions au client qui seront nécessaires pour réaliser les User Stories du backlog du sprint.
    	1. Seconde partie : avec l'équipe au complet et le scrum master.
    		- On découpe les User Stories en taches et on réajuste l'estimation du temps pour chaque taches.
    1. Préparer le Backlog du Sprint, le tableau blanc et le burndown chart par le scrum master.
    1. Pour chaque jour du sprint :
    	- On fait la réunion Daily Scrum quotidienne de 15 minutes, le Scrum Master pose les 3 questions suivantes :
        	1. Qu'as tu fais hier ?
            1. Que vas-tu faire aujourd'hui ?
            1. Rencontre tu actuellement des problèmes ?
        - On met à jour le burndown chart à chaque réunion daily Scrum.
    	- On réalise les taches du tableau blanc.
    1. A la fin du sprint, on réalise une réunion de revue de sprint, avec l'équipe au complet, le scrum master et le product owner.
        - L'objectif est de montrer au client l'incrément logiciel et de voir avec le client s'il valide le travail effectué.
    1. On réalise la réunion post-mortem avec l'équipe au complet et le scrum master.
        - L'objectif est de faire le point sur ce qui c'est bien passé, mal passé, et comment améliorer l'efficacité de travail.
    1. Après le premier sprint, on recalcule le taux de concentration de l'équipe et on refait le planning.
    	- On compare le nombre d'heure/points d'histoire qui devaient être fait et qui ont été fait. *Par exemple, si on devait réaliser 20H et qu'on en a réalisé 10h. On a un taux de concentration de 0.5 (10/20). Le taux de concentration total sera donc de `0.5 * 0.7 = 0.35`*.
    1. On défini la release en fonction du niveau d'importance voulu par le client.
    	- Par exemple, si le client veut une importance de 60 avant une release, à la fin du sprint donnant au moins 60, on effectue une release.
        - Le client peut demander plusieurs releases.

## Etapes détaillés

### Définir les rôles des individus

| Nom | Role | Informations
|---|---|---
| Product Owner | Représentant de l'entreprise client | Egalement appelé MOA (maitre d'ouvrage).
| Scrum Master | Verifier si la méthode Scrum est bien appliqué | Il n'est PAS le chef d'équipe.
| L'equipe de développement | Elle développe le système | L'équipe peut changer entre chaque Sprint; mais pas pendant.

### Production du Backlog produit

Il est réaliser avec le Product Owner et le Scrum Master.

Le Backlog produit représente l'ensemble des Users Stories à réaliser pour le projet.

Un User Story ne doit ni être trop long à réaliser, ni trop court.

On défini un Backlog produit et des Users Stories comme ceci :

| ID | Titre | Importance | Estimation | Démonstration de la fonctionnalité | Commentaires
|---|---|---|---|---|---
| *Index de l'User Story* | *Définition de l'user story rédifé en : <br />**en tant que** ... **je veux** .. **afin de*** | *Estimation défini en nombre de point d'histoire ou d'heures* | *Importance défini avec le Product Owner* | *Test d'acceptance en notation de **Gherkins** rédifé en :<br /> **Etant que** ... **lorsque** ... **alors** ...* | *Précisions supplémentaire sur l'User Story*
| 1 | **En tant que** client, **je veux** ajouter un article dans le panier **afin de** pouvoir acheter un produit | 30 | 3 | **En tant que** client, **lorsque** j'ajoute un article parmi une liste de produit dans le panier, **alors** je peux le visualiser dans le contenu de mon panier. | Nécessite un diagramme de séquence UML

### Réaliser une estimation de la charge de travail

On réalise une estimation de la charge de travail pour chaque User Story, ce qui nous donnera également la charge de travail pour l'ensemble du projet.

On aura donc une date prévisionnelle à donenr au Product Owner, même si cette date reste à être validé après le premier Sprint.

La date prévisionnelle donnera également le prix prévisionnelle du projet.

Le nombre de point d'histoire défini donnera le nombre de jour idéals.

### Déterminer la capacité de travail de l'équipe

- On calcul cette capacité de travail pour un sprint, de durée constante X, tout au long du projet.
- On défini un taux de concentration à 0.7 pour le premier sprint pour calculer le nombre de jours réelles.

### Pour chaque itération de Sprints

#### Réalise un Backlog du Sprint

---

# Old

## Etapes

1. Réunion avec le client pour élaborer une spec ou un backlog de base
	- définir les besoins
    - estimer le temps
    - estimer le cout
1. Rediger le backlog
1. Définir la productivite de l'equipe

# Principes clés

- Auto-organisation et pouvoir de décision à l'équipe
Elle est responsable des descision et ne peut se dédoigner des consequences
- Sprints en isolement
Il est important qu'en réunion les questions doivent être posé pour résoudre les futures problèmatiques, car pendant le sprint on doit travailler seul
- Délais fixe
On doit respecter les délais, sinon "on dériver".
- Réunion quotifienne de 15 minutes avec une liste de questions prédifini
3 questions à répondre.
- Démonstration du résultat du sprint
A chaque fin de sprint, une démo est présenté par une de personnes de l'équipe.
- Planning adaptatif
A chaque fin de sprint, on redéfini avec le client des priorités.

# Comparaison avec la poule et le cochon
> Un jour, une poule et un cochon se promènent ensemble. Soudain, la poule dit au cochon : « Ouvrons un restaurant ensemble. Qu'en penses-tu ? ». Le cochon réfléchit un instant puis lui répond enthousiaste : « C'est une excellente idée. Comment l'appellerais-tu ? ». La poule lui dit « Jambon et oeufs ». Le cochon lui répond alors : « Non merci ! Je serais impliqué alors que toi tu serais seulement concernée. 

- cochon est impliqué : equipe, scrummaster et product owner (représentant du client)
	- le product owner
    	- (représentant du client, souvent employé par l'entreprise client)
    	- finance projet
        - responsable des besoins initiaux (avec le scrum master)
        - responsable du bénéfice financier du projet
        - décide des release
        - responsable de la gestion des fonctionnalités et des ajouts
        - représentant les backlog produit (l'ensemble des besoins nécéssaire du produit, représente les "use cases") et de leur priorités
        - il n'y a pas que les besoin du logiciel, mais de tous les besoins globale lié au projet (formation des équipes, etc).
    - le scrummaster
    	- on peut le traduire comme "maitre de la mélé", ou bien l'arbitre, il n'est pas le supérieur de l'équipe, mais c'est lui qui vérifie la méthodologie scrum est bien respecté par tous, et il doit convaintre le product owner que le scrum est la bonne méthodologie (s'il n'est pas convaincu, il est impossible d'appliquer cette méthodo). Il n'a aucune autorité sur l'équipe (il doit faire attention à la communication lors des rappelles des régles), il est un catalyser du projet.
        - son role :
        	- isoler l'équipe des pertubations extérieurs en cours de sprint
            - apprendre la méthode Scrum à l'équipe
            - s'assuer que l'équipe respecte bien la méthode (pas aller vers l'ancienne méthode)
            - répondre aux besoins de l'équipe
            - faire cadrer scrum dans la culture d'entreprise
            - travailler avec le product owner pour l'influencer sur les besoins primordiale sur le projet. Il est autant responsable que l'équipe à la réussite du projet.
    - l'équipe : il a la résponsabilité et le pouvoir descision du chef de projet.
    	- Développer les fonctionnalités : elle transforme les besoin en fonctionnalités logiciel
        - Elle est autogéré et auto organisé (elle gére quelle ménière de gérer le code par ex)
        - est multidisciplinaire : chaque membre a une specialité. Mais on décide du temps du projet par en fonction du spécialiste mais du temps moyen par n'importe qui.
        - est résponsable du succés ou non de chaque iération, et est solidaire
        
Les poules  est concerné :
	- les utilisateurs
    - le management
    - etc...
    
# Certifications

# Organisation de la production

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/rjYmnKDu1TJb4CLA-image-1665561263765.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/rjYmnKDu1TJb4CLA-image-1665561263765.png)

## Vue d'ensemble de Scrum

### Product backlog

Travail entre le scrummaster et le product owner : on fait un point au début de la possibilté de réalisation du projet en fonction du temps et des finances.

On vérifie si c'est ok, première estimation financiere et de temps.

### Sprint

Est réaliser sur une période en générale d'un mois, ou de 15 jours en fonction du projet.

A la fin de chaque sprint des fonctionnalités sont ajouté, ou bien on réalise différentes taches du projet qui ne sont pas lié à la programmation.

A chaque sprint on réalise une présentation avec le client. C'est un peu un test d'acceptation pour le client.

A chaque sprint, le client va payer (il paye réguliérement).

Si le product owner demande à un développeur une nouvelle fonctionnalité, il faut rédiger cette demande au scrummaster qui va prendre en compte cette demande dans l'ensemble du processuce.

On répetes les sprints jusqu'à une version de l'application et du projet que le client aura validé.

### Fin du projet

C'est le client qui décidera de la fin du projet.

La fin du projet ne correspond pas forcément à l'objectif de base.

Par exemple : à 80% du projet, le client a payé 50%, et il se rend compte que les 20% derniers pourcent ne sont pas si nécessaire : le client peut décider d'arréter.

On peut décider d'arreter si

- le projet à atteinds le objectif fixé
- client ne veut plus financer le projet
- client considére que le logiciel délivre assez de fonctionnalité

Dans tous les cas l'entreprise développant ne perd plus d'argent.

Mais l'entreprise qui développe ne sera pas pérdante parce que le client aura payé réguliérement.

Si des nouvelles fonctionnalités sont demandé, il faut soit les refuser, soit 

## Gestion des objectif

Triptyque de la gestion de projet :

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/RPwMmgHyhkAEKDDZ-image-1665565201477.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/RPwMmgHyhkAEKDDZ-image-1665565201477.png)

## Backlog produit

Un exemple de backlog produit :  

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/dRZlArwYPtCnekoz-image-1665565293071.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/dRZlArwYPtCnekoz-image-1665565293071.png)

Ce sont une liste de taches, qui pourront être redécoupé en tâches.

La *démonstration de la fonctionnalité* peut être un scénario rédigé lors du [Processus Unifié](https://wiki.akipe.fr///books/formation-cda/page/processus-unifie).

C'est surement le scrummaster qui rédige ce document. Il faut ensuite estimer le temps pour rédiger les backlog.

On peut utiliser le nombre de jour par homme pour chaque fonctionnalités (jour/homme). Il faut donc savoir combien coute une personne par temps.

Ensuite on défini le cout des fonctionnalités.

Il faut expliquer au client que le cout n'est pas forcément lié aux backlog (avec un contrat qui est adapté).

Pour réaliser un Backlog produit, on défini les besoins (peut être avec les cas d'utilisation du [Processus Unifié](https://wiki.akipe.fr///books/formation-cda/page/processus-unifie).

### Methodologie d'estimation du temps

#### En jours idéaux

Déterminer le nombre de temps nécessaire pour faire une tache (pour une personne), en considérant une productivité de 100% à toutes les heures : pas de réunion, aucune intéruption...

#### En points d'histoire

On défini à quoi correspond un point d'histoire. Chacun de l'equipe doit estimer le nombre de point à utiliser pour réaliser la tache.

On défini des cartes ayant des valeurs (qui représente la suite de Fibonacci) et les personnes doivent choisir la carte ayant la valeur la plus proche (si entre deux, prendre la plus haute) en nombre de points d'histoire.

Ensuite, on compare le nombre de point d'histoire de chacun. 

Ceux qui on défini les extrémes doivent justifier leur nombre.

On refait un tour de table pour que chacun fasse un nouvelle estimation.

On débat des arguments de chacun pour ensuite décider tous ensemble le nombre de points que l'équipe décide d'appliquer.

Tant qu'un nombre de point d'histoire n'est aps décidé par tous, on le refait des tour de table d'estimation.

Par exemple :  
Si servir un café correspond un point d'histoire, combient coute en point d'histoire de préparer et servir du café pour 8 personnes.

Cette methodologie permet de casser le rapport de chacun au temps et de mieux partager cette notions dans le groupe.

#### Astuce pour l'estimation du temps

Lorsqu'on nous demande un temps, et qu'on a une estimation, **il vaut mieux donner le temps estimé multiplié par deux**.

### Les sprints

#### Réunion de début de sprint

Suite au scrummaster et product owner selectionne backlog : réunion en 2 partie
 
product owner montre ce qu'ils doivent faire, l'equipe pose question sur les questionnement sur ces feature

2eme partie : découpe besoin en tache et elle doivent durée entre 0.5 min et 2 jours max. Cette réunion doit comprendre l'équipe en complet (pour que la résponsabilité soit partagé avec tout le monde).

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/xu9zwUDHCyzQ2oiE-image-1665570627159.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/xu9zwUDHCyzQ2oiE-image-1665570627159.png)

#### Réunion quotidienne

Réunion rapide, avec 2 minutes par personnes. On se concentre sur l'essentiel. Tous les participants sont débout et tournés vers le tableau qui contient les besoins du projet.

Les participant doivent répondre à 3 questions, de manière précise :

1. Qu'as tu fais hier ? (dernière journée de travail, dire quelle tache réalisé précisément)
1. Que fait-tu aujourd'hui ? (quelle tache)
1. Quels sont les problèmes qui t'empêchent de progresser ? On défini un moment après pour résoudre ce problème si ça prend trop de temps.

Objectif de cette réunion quotidienne :

- communication au sein de l'équipe : savoir qui fait quoi.
- synchronisation du travail entre les membres de l'équipe.
- découvrir la problèmatique à traiter depuis la question numéro 3.
- Permet d'améliorer la motivation car on forme une equipe et on se motive chacun.

### Le tableau blanc

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/3zDkmw4oRJGj8eIh-image-1665570734427.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/3zDkmw4oRJGj8eIh-image-1665570734427.png)

Les colonnes représentes :

1. Tache en attente
2. Tache en cours
3. Tache terminé : testé et validé sur l'outil de versionning (dans la bonne branche)
4. Graphique Burndown chart : gauche : nombre de tache à réaliser depuis le début, bas : temps du sprint ; droite diagonal : courbe idéale de charge : courbe : représente les taches rééle réaliser par rapport au temps.
5. (UNPLANNED ITEMS) taches rajouté après coup, mais à réaliser
6. (NEXT) taches en cas où tout est réalisé

Product owner a également un graphique du projet global qui est similaire à celui du sprint, mais pour tout le projet.

#### Burndown chart

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/fQV61ENIOpC8ydXh-image-1665571120095.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/fQV61ENIOpC8ydXh-image-1665571120095.png)

On représente sur l'axe des ordonnées le nombre de taches que l'on devra réaliser sur le sprint

Sur l'axe des absice les dates jusqu'à la fin du sprint.

### Fin de sprint

On réalise une réunion de 4h maximum.

L'équipe, le product owner et toute personnes ayant un intéret au projet ou qui souhaitent participer.

On présente la version du logiciel produit.

Les bénécies de cette réunion :

- l'équipe est valorisé d'un travail accompli
- communication entre equipe et product owner, avec des avis direct
- Communication vers le reste de l'entreprise : tout le monde peut savoir ce qui se passe pendant la journée
- permet de movité l'équie à terminer réellement les taches entamées.

### Réunion post mortem du sprint

4 heure max

Il n'y a que les membres de l'équipe, et il permet de faire un point sur le sprint.
Le scrummaster peut participer juste pour vérifier que les régles de la réunion sont respécté.

On tient cette réunion après la revu de sptring :

- Qu'est ce qui c'est bien passé (ce qu'on peut répéter pour le prochain sprint) ?
- Qu'est ce qu'on aurait pu modifier dans ce sprint pour l'améliorer (et donc changer pour les prochains) ?
- Qu'est ce qu'on peut améliorer pour le prochain sprint ? Quelles idées pour améliorer ?

La descision sur l'ensemble de ces point est décidé collectivement.

### Définition des releases

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/sMKNq2u5mYTyTfMl-image-1665571974505.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/sMKNq2u5mYTyTfMl-image-1665571974505.png)

Le product owner décidera par rapport à l'importance qui souhaite à quelle moment il veut une version de son application.

On regarde a quelle moment cette fonctionnalité sera implémenté et on délivra une release à la fin du sprints.

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/NOtF9uFvOQwoteXO-image-1665577374186.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/NOtF9uFvOQwoteXO-image-1665577374186.png)

#### Déterminer la capacité de travail

Le temps correspond au temps de travail appliqué au projet.

Formule générique :

```
Temps une période * Nombre de période * Nombre de personnes * Taux de concentration = Temps idéal
```

Formule appliqué au nombre de jours :

```
Nombre de jour sur une semaine * Nombre de semaine * Nombre de personne * Taux de concentration = Nombre de jour idéal
```

Le taux de concentration ne sera jamais de `1.0`. En générale il est de `0.7`, mais le définira en fonction du niveau des membres de l'équipe, de ...

Exemple :

> L'exemple suivant tient compte d'une équipe de 4 personnes, de sprints de 3 semaines et d'un facteur de concentration de 0,7. En 3 semaines, l'équipe peut donc réaliser :  
**5 jours x 3 semaines x 4 personnes x 0,7 concentrations = 42 jours idéaux.**

Pour le scrummaster, plus le temps d'un sprint est court, plus c'est difficile de le calculer.

### Elements important

#### Définition de "fini"

A quand on défini clairement qu'une fonctionnalité est défini : test, controle à travers git ?

#### Velocité

On compare ce qu'on été sensé réaliser (vélocité estimé) avec ce qu'on a réaliser (vélocité réelle).

On calcul la différence entre le nombre de taches par sprint à effectuer et le nombre de taches réellements effectué.

Ce calcul nous donnera un taux de concentration (correspond à la productivité du développeur).

```
Vélocité estimé / Vélocité réelle = Taux de concentration
```

> Par exemple, pour un développeur, sur une vélocité estimé de 26 et une vélocité réelle de 13, son taux de concentration sera de 0.5 car : 26 / 13 = 0.5 

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/FnA5RAuleQ0PAanU-image-1665577583347.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/FnA5RAuleQ0PAanU-image-1665577583347.png)

#### Si il y a beaucoup de développeurs

On va créer plusieurs groupes avec chacun des scrummaster, et on définira un scrummaster des scrummaster

# Outils

## Zenhub (Github)

<https://github.com/marketplace/zenhub>

## Taiga

<https://tree.taiga.io/>

# Liste

devoir donner idée temps et budge

- Réunion client
- base backlog générale
- deuxième réunion -> confirmation backlog + priorité

Budget défini par rapport aux user story + homme par jour 

- oranise réunion début :
- réalise backlog avec sprint : répartie user story sur l'ensemble des sprints
- sprint :
    - réunion préliminaire :
    	1. Avec client : établire quoi faire & max question equipe au client
        2. uniquement equipe :
    - réaliseation du sprint
    	- hebdomanaire réunion matin rapide : scrummaster vérifie que c'est bien fait
    	- constament scummaster : vérifie que l'equipe peut travailler + mise à jour states + vérifie que scrum est correct
        - equipe : développe sans contacte avec client
    - réunion fin sprint:
    	1. Avec client : demo, presentation, retour client, envoie release si existant
        1. Uniquement equipe : fait le point et ...
- fonctionnalités
	- user stori : 2-3j max
    - tache : 0.5 à 2 heures
    
### Formalisation User story

#### Régle pour trouver des user stories

> En tant que { X }, je veux { Y } afin de { Z }

- Y est une **fonctionnalité**
- Z est le **bénéfice** de la fonctionnalité
- X et **la personne (ou rôle)** qui va en bénéficier

Permet d'identifier ainsi la valeur ajouté par 

Exemple :

> En tant que **client (X)**, je souhaite **accéder au suivi de ma commande (Y)** afin de **m’assurer d’être présent lors de la livraison à domicile (Z)**.

- Bénéficiaire : client
- Fonctionnalité : accéder au suivi de ma commande
- Bénéfice : m’assurer d’être présent lors de la livraison à domicile

#### Trois aspect

Pour trouver un User story, il faut se poser les 3 questions :

- Utilisateur type : *quelles sont les caractéristiques de l’utilisateur final ?*
- Besoin : *quel est le besoin de l’utilisateur final ?*
- Objectif : *quel est l’objectif de la fonctionnalité logicielle pour l’expérience de l’utilisateur final ?*

##### Identifier l'utilisateur type

Identifiez le profil de l’utilisateur final en cernant votre public cible. Posez-vous la question suivante : qui sera concerné par cette fonctionnalité logicielle ?

Question à se poser :

- Pour qui créons-nous cette fonctionnalité logicielle ?
- Quel type de fonctionnalité l’utilisateur final veut-il ?
- Quel sont les profils démographique et psychographique de l’utilisateur final ?

Un User Story peut contenir plusieurs utilisateurs types.

Exemple :

> Exemple de profil type d’utilisateur : Katie, chef de projet à la tête d’une équipe de 10 personnes.

##### Décrire le besoin

Décrire comment l'utilisateur utilisera la fonctionnalités, et pour quelle raison. Il faut que l'équipe comprenne la demande.

Question à se poser :

- Que cherche à accomplir l’utilisateur final ?
- Comment votre fonctionnalité aidera-t-elle l’utilisateur final à accomplir ses objectifs ?

Il faut plutot se focaliser sur l'attente de l'utilisateur plutot que sur la fonctionnalités, et pour quelle raison votre application l'aidera.

> Exemple de besoin : aider les membres d’équipe à comprendre comment les tâches individuelles contribuent aux objectifs commerciaux globaux

##### Définir l'objectif

Définir l'objectif de la fonctionnalités.

Questions à ce poser :

- Quels sont les avantages de la fonctionnalités ?
- Quels problème la fonctionnalité vient-elle résoudre ?
- Comment cette fonctionnalité s'intétre-t-elle aux objectifs généraux ?

> exemple d’objectif : gagner en efficacité en créant un parcours clair

##### Exemple d'User Story

Développement de produits :

> En tant que chef de produit, je souhaite que les membres d’équipe puissent comprendre en quoi leurs tâches individuelles contribuent aux objectifs commerciaux globaux afin de booster leur motivation.

Expérience client :

> En tant que client récurrent, je souhaite que mes informations soient sauvegardées afin que mon expérience de paiement soit plus fluide.

Application mobile :

> En tant qu’utilisateur régulier de l’application, je souhaite consulter les informations pertinentes le plus vite possible.


#### Vérifier la qualité de la User Story

Il faut se servir de la grille **INVEST** pour vérifier de la qualité du User Story :

- **I**dépendante : elle n'a **aucune indépendance** vis-à-vis d'une autre story du backlog.
- **N**égociable : elle doit pouvoir être **modifier** et affinée pendant le projet.
- **V**alorisable : elle doit apporter une **valeur ajoutée** à l'utilisateur pour avoir une raison d'exister.
- **E**stimable : l'equipe de développement doit pouvoir en déduire **une estimation de temps** de réalisation à sa simple lecture. 
- **S**mall : il doit pouvoir être **réalisable en un sprint** et sinon découpable en plus petites user stories. Plus il sera court, plus elle sera rapide et simple à développer.
- **T**estable : on doit pouvoir la **tester** selon les critères d'accaptation pour pouvoir la validé.

#### Estimation du temps

Raisons pour estimer des user story :

- repérer si elle est réalisable en un sprint.
- inciter l'equipe à se projeter sur une manière concrete de la réaliser.
- aider à la gestion de la planification du sprint.
- donner une visibité de ce que l'équipe réalisera pendant le sprint.

Il existe différentes methodes pour trouver une estimation de temps.

##### Planning poker
On utilisera des cartes comprenant :

- les nombres de la suite de Fibonacci.
- une carte point d'intérrogation ❓ dans le cas d'un US (User Story) non précis.
- une carte signe infini ∞ s'il faut la redécoupée.
- une carte pause café ☕ si l'équipe à besoin d'une pause.

##### Le Bucket System

Il est similaire au Planning Poker, on utilise l'image de seaux dans lesquelles les User Stories seront triées en fonction de leur compléxité.

A voir.

##### La taille de t-shirt

Utiliser les tailles de T-Shirt XS, S, M, L ou XL pour estimer la complexité plus grossièrement que le planning poker.

#### Critére d'acceptance

On les défini avec l"équipe de développement pendant le **backlog grooming** (ou backlog refinement).

***Les testes d'acceptance*** ou d'acceptation permet de vérifier que l'implémentation de la User Story répond au besoin.

Ils doivent être :

- réalisable.
- estimable.
- compris et accéptés par tous.
- rédigés en équipe, idéalement.

On peut les rédiger en scénario avec le langage Gherkin en utilisant la description de la User Story.

##### Régle pour rédiger test Gherkin

- **Given - Etant donné que** : décrit le contexte initial
- **When - Lorsque, quand** : décrit l'action faite par l'utilisateur à partir du contexte initial
- **Then - Alors** : décrit le comportement attendu suite à l'action faite par l'utilisateur.
- **And - Et** : ajoute une condition au *Given, When* ou *Then*.
- **But - Mais** : exclut une condition au *Given, When* ou *Then*.

Exemple :

> Scénario : le client souhaite consulter l’état de sa commande.

**Étant donné que** j’ai réalisé une commande, je me rends dans mon espace client pour suivre son avancement.  
**Lorsque** je clique sur le numéro de ma commande  
**Alors** je peux voir l’état du traitement de ma commande, ainsi qu’une date de livraison estimée.

> Scénario : le client souhaite consulter l’état de sa commande depuis l’email de confirmation

**Étant donné que** j’ai réalisé une commande, je souhaite suivre son avancement  
**Lorsque** je clique sur le lien dans mon email de confirmation  
**Alors** je peux voir directement l’état du traitement de ma commande, ainsi qu’une date de livraison estimée.

##### Exemple avec et sans Gherkin

Sans :

> On souhaite réduire notre stock le tome 1 de harry Potter. Pour toute commande contenant le tome 1 de Harry Potter et un autre livre de la collection Harry Potter, on fait 25% de réduction sur le prix de ces 2 livres.

Les test développeur doivent donc être très complet et complexe :

```
if (order.contains.HarryPotterV1 AND order.contains.HarryPotterV2)
	order.finalAmount = Math.Roundd(order.HarryPotterTotal * 75 / 100);
```

Le test d'un autre métier comme l'assurance qualité, sera complétement différent :

```
Se connecter au site  
Indiquer "Tome 1 Harry Potter" dans la barre de recherche
...
```

Avec :

> **Etant donné que** l'utilisateur a ajouté au panier le tome 1 d'Harry Potter  
**Quand** l'utilisateur ajouter un autre livre de la collection Harry Potter au panier  
**Alors** le prix des 2 livres Harry Potter est réduit de 25%

##### Template user story

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/eEd6bAB1qe0BwJLT-image-1666096799224.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/eEd6bAB1qe0BwJLT-image-1666096799224.png)

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/TfvlLoN8IzWmzLEW-image-1666097188284.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/TfvlLoN8IzWmzLEW-image-1666097188284.png)

# Récape

## Créer les users story

## Définir le temps des users storys

point histoire : prendre le plus petit user story et on étalone dessus.

## 1 Calcule temps

Prix prévisionnel du projet :  
Nb d'heure total des users story * (350€ (par jour) / 7(h par jour))

Prévisions des cout

Prévision quand livraison :  
combient de temps un sprint ? ex: 2 jours.  
Quelle capacité de travail pour 2 jours ? 
2(nb jours sprint) * 3(nb de personnes) * (capacité moyenne de travail de l'ensemble des employé par jour) -> nombre d'heure idéal de travail dans un sprint.

On multiplie le tout par le taux de concentration pour avoir l'heure réélle (jour réelle) de travail par sprint.

3) livraison du sprint

| 300h pour le projet | 13 sprint pour le projet | 24.7j pour le projet
|---|---|---
| 24.22 | 1 | 2j

## Définir les importances avec le client

## Préparer le backlog de sprint

Mettre les users story dans le backlog

## Burndown charn

haut gauche: charge de travail : temps 0 à 300h charge de travail

<div drawio-diagram="165" style="background-color: white; padding: 20px;"><img src="https://wiki.akipe.fr///uploads/images/drawio/2022-10/LYaUCM17gUzQMrl1-drawing-5-1666617194.png"></div>

## Exemple

- On défini une estimation du nombre d'heure pour l'ensemble des users story d'un projet à 300 heure idéal au total.

- On fait une estimation du cout du projet, on souhaite arbitrairement être payé 350€ par jour, et donc 350/7 = 50€ par jour : `300 h (temps total projet) x 50€ (cout par heure) = 15000 €` le projet coutera 150000 €

- On décide qu'un sprint dure 2 jours. il y a 3 employés. on calcule la capacité moyenne de travail par jour :

```
2 (jour par sprint) x 3 (employés) x (
		(35-2.5-5/5)+			# heures de travail par jour employé 1
		(35-2.5-5/4)+			# heures de travail par jour employé 2
		(35-2.5-5/2)			# heures de travail par jour employé 3
    /3							# ça fait 5.8H de travail par jour en moyenne
) = 34.6 heures de travail dans 1 sprint
```

| 300h pour le projet | 13 sprint pour le projet | 24.7j pour le projet
|---|---|---
| 24.22 | 1 | 2j

## Réunion daily scrum

- rappeler les régles, ne pas être comme un supérieur

Réunion de 15 minutes, où le scrum master doit poser 3 questions à chacun des développeurs (quelques minutes pour l'ensemble) :   

- Qu'est ce que tu as fait hier ?
- Qu'est ce que tu vas faire aujourd'hui ?
- Est-ce que tu rencontre des problèmes ?

## Réunion post-mortem

Elle se déroule avec l'équipe entière du projet avec le scrum master qui va annimer la réunion :

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/ahq9vg9eD02QwZPi-image-1666792979556.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/ahq9vg9eD02QwZPi-image-1666792979556.png)

- Question sur le positif du déroulé du projet :
	- Qu'est ce qui a fait avancer le sprint ?
    - Qu'est ce qui a été apprécié durant le sprint ?
    	- Bonne chose qui se son bien passé et qu'on fera pareil ? 
- Question sur le négatif du déroulé du projet :
	- Quels on été les freins du sprint ?
    	- Quels choses qu'on voudrait changer pour le prochain sprint ? et comment ?
- Question sur l'avenir du déroulé du projet :
	- quels sont les risques à venir ?
    
## Nomenclature

### Sprint

### User Story

Les Users Stories sont l'ensemble des taches à réaliser pour un projet. Ils sont défini par le Scrum Master et le Product Owner.

Ces taches peuvent être lié à la technique ou à un autre domaine : gérer la publicité, gérer la formation des futures utilisateurs...

#### Grille INVEST

### Planning Poker

### Point d'histoire

### Scrum master

### Backlog

#### Product Backlog

#### Sprint Backlog

### Notation de Gherkin

### Taux de concentration

### Capacité de travail / Vélocité

### Jours idéaux et réelles

### Tableau blanc

### Brundown Chart

### Réunion Daily Scrum

### Réunion Post-Mortem

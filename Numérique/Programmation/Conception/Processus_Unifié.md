---
title: Processus Unifié
description: 
published: true
date: 2024-05-21T15:26:47.571Z
tags: 
editor: markdown
dateCreated: 2024-05-21T15:26:47.571Z
---

# Processus Unifié

Le Processus Unifié (ou *Unified Process* en anglais) est une méthodologie de conception d'application informatique.

Il utilise entre autre la notation UML.

Chaque étape peut corriger les étapes précédentes. Il ne faut donc pas hesiter à revenir en arriére lorsqu'on découvre une erreur ou des oublies.

Bien sûr, pour des projets concrets, on pourra modifer la méthodologie Processus Unifié pour l'adapter en fonction de la taille de l'application ou du temps impartie. On peut se limiter à certaines parties ou en simplifier.

Il n'est pas obligatoire de réaliser tous les cas d'utilisations avant d'avancer. Il faut selectionner les plus importants, ou les plus problèmatiques ou non compréhensibles.

## Résumé des étapes

1. Spécifications initiales
    1. [Cahier des charges](#bkmrk-cahier-des-charges)
    1. [Specifications](#bkmrk-sp%C3%A9cification)
1. [Analyse](#bkmrk-analyse)
	1. [Identifier les acteurs](#bkmrk-identifier-les-acteu)
        - Description verbale des acteurs
    1. Definir les intéractions avec le système.
    	- [Diagramme de contexte](https://wiki.akipe.fr///books/formation-cda/page/diagramme-de-contexte)
    1. [Maquettage](#bkmrk-maquettage)
    	- Maquette visuelle des écrans
    1. Définir les relations entre les écrans
        - [Diagramme de navigabilité](https://wiki.akipe.fr///books/formation-cda/page/diagramme-de-navigabilite)
    1. [Identifier les cas d'utilisations](#bkmrk-identifier-les-cas-d)
    	- [Diagramme de cas d'utilisation (use case)](https://wiki.akipe.fr///books/formation-cda/page/diagramme-de-cas-dutilisation)
        - Description verbale
    1. [Analyse de chaque cas d'utilisations](#bkmrk-travail-sur-les-cas-)
        1. Décrire textuellement le cas d'utilisation
            - Définir l'acteur principal
        1. Décrire les scénarios du cas d'utilisation
            1. Définir la précondition
            1. Définir la postcondition
            1. Définir le scénario nominal
            1. Définir les scénarios alternatif
            1. Définir les scénarios exceptionnels
        1. Représenter graphiquement les scénarios
            - [Diagramme d'activité](https://wiki.akipe.fr///books/formation-cda/page/diagramme-dactivite)
        1. Représenter graphiquement les intéractions dans le temps du cas d'utilisation
            - [Diagramme de séquence système fermé](https://wiki.akipe.fr///books/formation-cda/page/diagramme-de-sequence-en-systeme-ferme)
1. [Conception](#bkmrk-conception)
	1. [Diagramme d'objet **métier** global](#bkmrk-diagramme-d%27objet-m%C3%A9)
    1. Analyse linguistique (optionnel)
    1. [Définir l'architecture de l'application (optionnel)](#bkmrk-d%C3%A9finir-l%27architectu)
    	- [Diagramme de paquetages](https://wiki.akipe.fr///books/formation-cda/page/diagramme-de-paquetages)
    1. [Conception de chaque cas d'utilisations](#bkmrk-pour-chaque-cas-d%27ut)
    	1. Analyse des messages échangés entre les objets
            - [Diagramme de communication / collaboration](https://wiki.akipe.fr///books/formation-cda/page/diagramme-de-communication-collaboration)
        1. Analyse des messages échangé chronologiquement entre les objets
            - [Diagramme d'intéraction /de séquence systéme ouvert](https://wiki.akipe.fr///books/formation-cda/page/diagramme-de-sequence-en-systeme-ouvert-interaction)
        1. Représentation partiel des entités (optionnel)
            - Diagramme de classe et d'objet du cas d'utilisation
    1. [Finalisation des représentations de nos entités et autre classes](#bkmrk-diagramme-de-classe--0)
        - Diagramme d'objet finalisé
        - Diagramme de classe finalisé
        - Diagrammes de nos différentes couches finalisés
1. [Implémentation](#bkmrk-implementation)
1. [Test](#)

Résumé graphique des différentes étapes :  

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/qo5G1NSV2hEt2rnx-image-1665833401855.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/qo5G1NSV2hEt2rnx-image-1665833401855.png)

(2) Résumé graphique des différentes étapes :  

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/lj0QJglCOHPigBmT-image-1665127904019.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/lj0QJglCOHPigBmT-image-1665127904019.png)

Autre parties à réaliser :  

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/IYwZzq2MxSpjKuot-image-1665129352803.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/IYwZzq2MxSpjKuot-image-1665129352803.png)

## Les étapes du Processus Unifié

### Besoins client

Il consiste à récupérer l'ensemble des demandes du client.

#### Cahier des charges

- todo : <https://aynils.ca/fr/information/guide-cahier-des-charges-refonte-site-internet/>

Le cahier des charges permet de se forger une idée globale du système à développer.

Il est généralement rédigé par le client, ou le maitre d'ouvrage (employé de l'entreprise client). Il peut également être exprimé oralement.

Le client exprime son besoin pour l'application à développer. Il peut donc contenir des informations en trop, ou en manquer, et ne pas correspondre à l'ensemble des données nécéssaire à la réalisation du projet.

Il faudra donc pour arriver à l'étape suivante entammer un échange avec le client pour clarifier ces manques d'informations.

Questions à se poser :

- A qui l'application est-elle destinée ?
- Quel problèmes l'application résoudra-t-elle ?
- Quelles sont les conditions d'utilisations de l'application ? (Application accessible à l'exterieur, sur quel materiel ?)
- Pour quand l'application est-elle attendue ?
- Pourquoi l'application est-elle attendue ?
- Comment l'application fonctionnera-t-elle ? (Il faut voir avec les utilisateurs du logiciel comment eux ils utilisent et vont utiliser le logiciel, et ne pas imaginer à leur place leur utilisation, ne pas inventer par nous même) (faire attention aux habitudes des utilisateurs).

Il y a 4 parties :

1. Expliquer pourquoi le projet existe, objectifs et qui pilote, procédure validation, rôles respectifs MOA & MOE.
1. Définir les besoins fonctionnels, techniques et organisationnels, avec en plus les contraintes et les exigences. (qui sera là pour répondre aux questions, besoins techniques de BDD ou autre, temps de réponse)
1. La liste des prestations et des livrables attendus. (prestation : maintenance, cours sur le logiciel, gestion de bugs et ticketing)
1. Definir le cadre de la réponse : planning de l'appel d'offres, documents attendus, régles de selection...


#### Spécification

La spécification permet de s'accorder sur ce qui doit être fait dans le système.

Ce document permet de définir les fonctionnalités obligatoire. Il est rédigé par le maitre d'oeuvre (de l'entreprise développant le logiciel) et est créé à partir du cahier des charges (si présent).

La spécification ne doivent pas étres trop technique : il doit être compréhensible par le client, et donc par tout le monde du métier (notamment des non techniciens).

Il faut également définir les demandes de manière claires et compéhensible pour éviter tout incompréhension du client.

Il est important de versionner ce document (v1, v1.1, v2, etc).

Ce document est très important, car il pourra servir de base légale (valeur d'un contrat) lors de conflits avec le client. Il perment également de clarifier les échanges avec le client en cas de contradictions sur les fonctionnalités de l'application.

### Analyse

On réalise une analyse **fonctionnel**, c'est à dire qu'on va devoir trouver l'ensemble des fonctionnalités de notre future application, et connaitre avec quels acteurs et autres systèmes il va intérargir.

Il n'est pas rare de reprendre les diagramme jusqu'à 7 fois.

On analyse notre système comme s'il était une boite fermé : on cherche qui utilise quoi, et comment le système s'articule.

On ne s'attarde pas encore à chercher à définir le fonctionnement interne du système.

Cette partie peut être réaliser par une personne en particulier, qui est un "analyste fonctionnelle".

#### Identifier les acteurs

Avec une description verbale de l'ensemble des acteurs.

Analyse système fermé :
- on défini les différents acteurs (role joué par entité externe, humain, materiel, autre systeme)

#### Définir les intéractions avec le système

Il permet de représenter l'ensemble des acteurs du système.

[Diagramme de contexte](https://wiki.akipe.fr///books/formation-cda/page/diagramme-de-contexte) :  

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/8EHVDI49lwv2bZXP-image-1665845052222.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/8EHVDI49lwv2bZXP-image-1665845052222.png)

#### Maquettage

Avec des maquettes visuels des différents écran et un diagramme de navigabilité.

On peut le réaliser sous plusieurs formes :

- juste une interface simple avec bouton
- ou avec un design avancé avec un début d'implémentation visuel.

On peut utiliser un certains nombre de logiciels pour nous aider à réaliser le maquettages.

Peut être réaliser en parallèle avec Identifier les acteurs & Identifier les cas d'utilisation.

#### Définir les relations entre les écrans

On va pouvoir définir comment naviguer entre les différents écrans/fenêtres/pages de notre application.

[Diagramme de navigabilité](https://wiki.akipe.fr///books/formation-cda/page/diagramme-de-navigabilite) :  

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/cPP1BsKveeW9bVaa-image-1665845130063.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/cPP1BsKveeW9bVaa-image-1665845130063.png)

#### Identifier les cas d'utilisation

On va identifier l'ensemble des cas d'utilisations (ou use case) de notre application, avec une description courte et verbale.

Permet de se mettre d'accord avec le client sur les besoins du logiciel.

Identifier les cas d'utilisations :

- on défini les les cas les plus important
- définir les cas de valeurs ajouté (le plus du système par rapport à avant)
- pas trop de détaille, et essayer de prendre en compte le plus de specs en ayant le moins de cas d'utilisation

Un nom de cas d'utilisation commencer toujours par un verbe à l'infinitif.

On va ensuite les insérer dans le diagramme de cas d'utilisation (ou diagramme use case).

[Diagramme de cas d'utilisation](https://wiki.akipe.fr///books/formation-cda/page/diagramme-de-cas-dutilisation) :  

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/FNTdRD1OtGBLVQm7-image-1665844371923.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/FNTdRD1OtGBLVQm7-image-1665844371923.png)

#### Analyse de chaque cas d'utilisations

##### Decrire textuellement le cas d'utilisation

Pour chaque cas d'utilisation : on décrit textuellement le cas d'utilisation :

*Effectuer une commande: Le client doit pouvoir accéder au formulaire du bon de commande, dans lequel il peut saisir ses coordonnées et les informations nécessaires au paiement et à la livraison.*

###### Définir l'acteur principal

Il faut donner une description courte mais explicite de ce que fait cet acteur dans ce cas d'utilisation.

##### Decrire mes scénarios du cas d'utilisation

Ensuite in décrit un scenario (on image une scene comme dans un film).

###### Définir la précondition

La précondition est la condition de départ pour laquel le scénario nominal peut débuter.

###### Définir la postcondition

La postcondition est l'état final des différents éléments ayant eu une relation avec ce cas d'utilisation - c'est le résultat du cas d'utilisation.

###### Définir le scénario nominal

Le scénario nominal est le cas "normal" du cas d'utilisation : c'est un peu "l'histoire" qui résume au mieux comment on réalise ce cas d'utilisation.

Dans cette "histoire", on en se préocupe ni des risque d'erreur, ou de choix alternatif : on cherche le recit le plus "optimal" que ce cas d'utilisation peut réaliser.

Dans la rédaction de ce cas d'utilisation, chaque ligne correspond à une action, ou une étape. Cette ligne doit commencer par qui ou quoi va faire cette étape (l'acteur principal, notre système, ou autre).

Il faut réaliser une sorte de "ping pong" : les différents acteurs et le système s'échange des "choses" à chacune des étapes et donc ils doivent également "répondre".

###### Définir les scénarios alternatifs

Comme pour le scénario nominal, il faut faire un "ping pong" : les phrases doivent commencer par l'acteur principal, ou bien le système.

###### Définir les scénarios exceptionnels

Comme pour le scénario nominal, il faut faire un "ping pong" : les phrases doivent commencer par l'acteur principal, ou bien le système.

###### Exemple

```
- Acteur principal : le client
- Préconditions *(départ, avant action)* : le panier du client n'est pas vide et il est identifié.
- Postconditions *(destination, une fois action terminé)* :
	- une commande a été enregistrée et transmise au service Commandes.
    - unr transaction chiffré a été réalisée avec le système externe de paiement et sauvegardée. (un peu technique)
- Scenario nominal *(chemin idéal sans problème pour arrivé à la postcondition, commence toujours pas le nom de l'acteur ! 1 seul scenario nominal)*:
	1. Le Client saisit l’ensemble des informations nécessaires à la livraison, à savoir :
    	- les coordonnées de l’adresse de facturation (nom, prénom, adresse postale complète, téléphone)
        - les coordonnées de l’adresse de livraison si elle est différente de l’adresse de facturation (nom, prénom, adresse postale complète, téléphone).
    2. Le Système affiche un récapitulatif des adresses indiquées et du panier à commander.
    3. Le Client sélectionne le paiement par carte bancaire et valide sa commande. Il doit pour cela fournir un numéro de carte de crédit avec son type, sa date de validité et son numéro de contrôle.
    4. Le Système envoie les informations cryptées au système externe de Paiement sécurisé.
    5. Le Paiement sécurisé autorise la transaction.
    6. Le Système confirme la prise de commande au Client.
    7. Le Système envoie la commande validée au Service clients.
    8. Le Système enregistre la commande.
- Scenario alternatifs *(d'autres chemin qui améne au même résultat que le scénario nominal)*
	- on pourrait faire un scenario alternatif (3b A1) pour utiliser un système alternatif de payement, jusqu'à l'étape 6 (reprise du scenario nominal à l'étape 6)
- Scenario exceptionnel *()*:
	- 1 à 3 E1 *(Exception 1)* *(veut dire que ce scenario peut se déclencher de 1. à 3.)* Le Client annule sa commande
    1. Le Système revient sur l’affichage du panier et le cas d’utilisation se termine en échec.
```

##### Représenter graphiquement le cas d'utilisation

On utilisera le diagramme d'activité qui représentent tous les scénarios.

Il permet d'avoir une vision graphique de comment les actions s'enchaines sur le système, comme avec un organigramme. Il ne sera pas utilisé pour générer du code.

*Sur Enterprise Architect, il faut selectionner le "use case"*

[Diagramme d'activité](https://wiki.akipe.fr///books/formation-cda/page/diagramme-dactivite) :  

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/T4tTKYhoSUgkCmsG-image-1665844064480.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/T4tTKYhoSUgkCmsG-image-1665844064480.png)

##### Représenter graphiquement les intéractions dans le temps du cas d'utilisation

On utilisera le diagramme de séquence système fermé.

On le réalise à partir du scénario nominal. Mais on peut le réaliser également pour les autres scénario pour des cas spécifique, pour notamment mieux comprendre les enchaines et résoudre des incompréhensions.

Il faut se focaliser sur le diagramme d'activité ***nominal***, mais il faudrait dans des cas spécifique faire un diagramme de sequence fermé pour le cas nominal, alternatifs et exceptionnelles.

[Diagramme de séquence en système fermé](https://wiki.akipe.fr///books/formation-cda/page/diagramme-de-sequence-en-systeme-ferme):  
[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/SY6zTnCPjPjL9xjd-image-1665845292263.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/SY6zTnCPjPjL9xjd-image-1665845292263.png)

### Conception

A cette étape, on va devoir s'accorder sur la manière dont le système va fonctionner. Il va donc falloir comprendre comment il fonctionnera pour pouvoir le construir.

On va donc concevoir l'ensemble des entités (classes, avec leurs opérations, attributs, et leur relations) que disposera notre application.

On peut réaliser cette partie avec un architecte logiciel & système.

#### Diagramme d'objet métier global

Pour l'instant on ne représente que les objets métier, que l'on aura analyser dans les phases précédantes.

On peut ajouter lorsqu'on les connait le nom des "roles" (c'est à dire le nom des futures attribut) à coté des entités d'objets pour rajouter de la précision.

Au final, dans notre code, les relations entre les acteurs et le système ne sont pas importantes car on n'implémentera que les relations entre les entité du système.  
C'est à dire on n'implémentera que le système, pas comment les acteurs utilisent le système).

[Diagramme d'objet](https://wiki.akipe.fr///books/formation-cda/page/diagramme-dobjet):  
[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/OKcAfsFChZL53Vgs-image-1665845176386.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/OKcAfsFChZL53Vgs-image-1665845176386.png)

#### Analyse linguistique

On peut utiliser l'analyse linguistique pour nous aider à identifier nos entité (qui représente nos futures objets). On va lire chacune des phrases et trouver des entités.

Voici un ensemble de régles pour nous aider :

| Type de mots | Signification | exception
|--|--|--
| Nom & groupes nominaux	| Objet entités |
| Ce/cette/ces | Références aux sujet de la phrase précédente |
| Son/sa/ses  | Association si le possesseur et la possession sont des conceptes
| ∼  | Attribut si la possession est une simple caractèristique du possesseur
| Ou/ou exclusif  | Généralisation ou spécialisation si les conceptes spécialisé ont des attrivuts & comportements différents
| ∼  | Enumération
| Verbe  | Association
| ∼  | Il peut parfoit cacher une entité (un nom) qui représente un contrat entre deux entité, il représente donc des classes d'association.
| Abjectif | Attribut d'une entité
| ∼ | Relation de généralisation
| Participe présent | Association entre deux entités
| ∼ | Représente des échanges de messages entre instance (dépendance)

Informations complémentaires :

- **Les synonymes** peuvent représenter la même entité.
- Le diagramme doit représenter une vue statique valable à tout moment : **les associations doivent être les plus neutres possible**.

Exemple :  

> Le processus de formation est initialisé lorsque **le responsable formation** ***reçoit*** une **demande de formation** de la part d’**un employé**.

- le responsable de formation : acteur
- demande de formation : use case, sera surement une entité
- reçoit : un verbe, surement une relation
- un employé : acteur

On va ensuite représenter les entités trouvé dans un diagramme d'objet.

#### Définir l'architecture de l'application

On doit à la fois définir les futures courches de notre système, qui correspondra à l'architecture de notre système.

Il faut également représenter les communications entre nos différents paquets.

On peut réaliser un [diagramme de paquetages (ou diagramme de package)](https://wiki.akipe.fr///books/formation-cda/page/diagramme-de-paquetages) pour représenter les communications entre nos différentes couches :  

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/teLhAHwTmPuc3rl6-image-1664960353614.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/teLhAHwTmPuc3rl6-image-1664960353614.png)

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/8vhgZ3VbggUBdRrn-image-1664960400386.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/8vhgZ3VbggUBdRrn-image-1664960400386.png)

#### Conception de chaque cas d'utilisations

##### Analyse des messages échangés entre les objets

En utilisant [un diagramme de communication](https://wiki.akipe.fr///books/formation-cda/page/diagramme-de-communication-collaboration), également appelé diagramme de collaboration.

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/qLsy6rc1OKYqD1my-image-1665844951741.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/qLsy6rc1OKYqD1my-image-1665844951741.png)

##### Analyse des messages échangé chronologiquement entre les objets

En utilisant [un diagramme d'intéraction](https://wiki.akipe.fr///books/formation-cda/page/diagramme-de-sequence-en-systeme-ouvert-interaction), également appelé diagramme de séquence systéme ouvert.

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/vHov0M8TIR7QTW1z-image-1665845247792.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/vHov0M8TIR7QTW1z-image-1665845247792.png)

##### Représentation partiel des entités

Il est optionnel. Diagramme de classe et d'objet du cas d'utilisation.

#### Finalisation des représentations de nos entités et autre classes

On finalise les diagrammes suivants :

- Diagramme d'objet global
- Diagramme de classe global
- Les différents diagrammes de nos couches

Il contiendra l'ensemble des classes de la couche métier, et des différentes couches.

Le principal est de réaliser les classes métier : les classes des autres couches pourront différer en fonction des langages, technologies et framework utilisés.

On réalise également un diagramme de classe par couche, pour une meilleure visibilité.

Avec Enterprise Architect, on réalise les diagrammes de classes au tout début du Processus Unifié, pour pouvoir générer les objets et les réutiliser dans l'ensemble du Processus Unifié.

### Implementation

C'est ici que l'on va coder le résultat de la conception sur notre système, et donc les différentes classes & algorythmes avec les langages et les technologies défini précédament.

On se servira de l'ensemble des diagrammes pour mieux comprendre ce qui doit étre coder.

### Test

On réalise l'ensemble des test (unitaire, fonctionnel, etc) pour vérifier si notre implémentation est conforme aux spécifications.
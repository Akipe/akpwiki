---
title: Tests
description: 
published: true
date: 2024-05-21T17:00:17.886Z
tags: 
editor: markdown
dateCreated: 2024-05-21T17:00:17.886Z
---

# Tests

## Les types de tests

Pendant longtemps, il n'y avait pas de norme sur les tests : donc pas de norme sur les noms des testes.

Voici quelques normes :

- Norme internationale : [International Software Testing Qualifications Board - **ISTBQ**](https://www.istqb.org/)
- Norme française  : [Comité Français des Tests Logiciels - **CFTL**](https://www.cftl.fr/)

Il existe d'autres normes et processus :

- Test Process Improvement - **TPI** (créer par Sogeti)
- Capability Maturity Model Integration - **CMMI**
- Test Maturity Model integration - **TTMi**

Dans un projet, on prévoit en général théoriquement 30% du temps à l'analyse, conception et à l'implémentation des tests.

**La suite de ce document utilisera la norme ISTBQ**.

Lors d'un projet, il peut y avoir **énormement** de tests : il n'est pas possible de tout tester (pour des raisons de temps et de couts), il faudra donc choisir intélligament ce que l'on souhaite tester.

### Méthodes de test

- Méthode en V : les tests à réaliser à chaque étapes, on attends pas la fin du projet pour les réaliser.
- Methodes en cascade : les tests sont réalisé à la fin.
- Methode itérative : comme la méthode en V, mais on les réalises par petites parties du projets

### Un Mock

Un Mock (ou **bouchon** en français) permet de forcer des valeurs pour des variables pour  définir des états prévisibles et ainsi réaliser des tests dont on connaitra le résultat.

> Exemple : pour tester une application de météo, on va définir un *mock* pour définir qu'il va pleuvoir pour pouvoir tester si notre application affiche correctement les logique lié à la pluie.

### Liste des tests

1. Tests d'acceptation
1. Tests système
1. Tests d'intégration
1. Tests de composant

<div drawio-diagram="171" style="background-color:white; padding: 20px"><img src="https://wiki.akipe.fr///uploads/images/drawio/2022-10/AoDP3I7Ft65e4qjl-drawing-5-1666861335.png"></div>

A chaque étape du projet, par exemple dans la gestion de projet Processus Unifié, on rédige les tests à chaque étape.

<div drawio-diagram="174" style="background-color:white; padding: 20px"><img src="https://wiki.akipe.fr///uploads/images/drawio/2022-10/zV59HMV7nHgKjqq0-drawing-5-1666940571.png"></div>

> Exemple : Lorsqu'on défini *les besoins clients*, on rédige ensuite les tests d'acceptation avant de passer à l'étape *Analyse*

#### Tests composants   

Exemple : un bouton "se connecter" peut être considérer comme un composant.

Les tests de composants doivent être théoriquement automatisé, notamment dans de l'intégration continue.

Ils sont réalisé par l'équipe de test ou les développeurs.

Il test si le composant fonctionne, on regarde le composant comme une boite noire et on le tests (vérifier si le résultat attendu est vien là). Il peut être réaliser par quelqu'un de non technique. Il veut tester qu'une donnée en entrée donne bien une certaine donnée en sortie, sans faire attention au contenu du composant.

ça doit être sur une petites partie du composant.

> Exemple : sur Word, je veux tester lorsque je selectionne du texte et que je selectionne l'option "mettre en rouge" que le texte est bien changé en rouge.

#### Tests Unitaire

composant : une "chose" contenu dans notre logiciel, comme un bouton, un menu, etc...

Il est appliqué à un morceau de code qu'on test.

Il test une fonction du code, un morceau de code, on doit savoir comment le code fonctionne pour créer le test.

Il doivent être également automatisé.

Ils sont réalisé par l'équipe de test ou les développeurs.

> Exemple : sur Word, je veux tester la fonction qui change la couleur :  
`void ChangerCouleurTexte(Color c, int caractereDebut, int caractereFin)`  
On vérifie par exemple si une couleur `c` existe ou pas, ce qui se passe quand `caractereDebut` est supérieur à `caractereFin`, ou si on défini une taille trop grande...

#### Tests d'intégration

composant : une bibliothèque ou un logiciel, dans tout les cas un groupe de code qui partagent un même "sens".

On peut faire des tests d'intégrations entre différents composants d'un même système ou des composants de différents systèmes.

> Exemple : un composant d'envoie de sms arrive t'il à intéragir avec le composant de paiement de carte bancaire ? On peut définir un mock (*bouchon*) qui va tout le temps renvoyer dans le composant de paiement de carte bancaire *commande validé* et observer si le composant sms arrive bien à envoyer un sms.

##### Liste des strategie

- Stratégie **Big-Bang**  
	On teste si tout les composants fonctionnent d'un coup. Mais c'est une mauvaise technique parce qu'on ne saura pas quel composant logiciel ne fonctionnera pas.
- Stratégie **Top-Down**  
	On va tester en premier les composants qui dépendent le moins des autres.
- Stratégie **Bottom-Up**  
	On va tester les composants qui ont le plus de dépendances, pour cyblé là où il y a le plus de problèmes.

Exemple de composants (Comptabilité dépends de Gestion des formations qui dépend de formations) :

<div drawio-diagram="172" style="background-color:white; padding: 20px"><img src="https://wiki.akipe.fr///uploads/images/drawio/2022-10/U1MuHfUWLSsu1VFW-drawing-5-1666863881.png"></div>

#### Tests système

Ces tests sont souvent réalisé manuellement par un humain.

Avant, ce test se nommait *test fonctionnel*, mais c'est un abus de langage.

On regarde comment le système fonctionne : on peut utiliser le scénario d'un cas d'utilisation du [Processus unifié](https://wiki.akipe.fr///books/formation-cda/page/processus-unifie) pour tester le système.

On va vérifier si le système réponds aux exigences définies dans les spécifications.

Certains tests système peuvent être également considérés comme des test d'acceptance.

#### Test d'acceptation

Ce test se nomme également *tests de recettage*.

On peut utiliser les **User Story** de la méthodologie Scrum pour faire des tests d'acceptation.

Ce sont les tests considérés comme utile **par le client** car il est important, essentiel pour lui.

Ce n'est pas parce qu'on a respecté les specifications ou que l'application fonctionne qu'elle sera acceptée par le client.

Ce tests permettent au client de débloquer les fonds pour payer le projet.

Différents tests d'acceptation :

- Tests d'acceptation usine : Ce test peut être réalisé en usine (dans l'entreprise du développeur).
- Tests d'acceptation sur site : Ce test peut être réalisé sur site (chez le client).
- Tests d'acceptation opérationnelles : On test avec des données du client, mais simulé.

ou on appeler avant :

- Test alpha
- Test beta 

Ces différents tests sont réalises en fonction de la criticité du logiciel.

### Tests fonctionnelles et non fonctionnelles

A chaque niveau 

D'après la norme **ISO 9126** qui précise les attributs de qualités à tester :

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/iMooWXZeDvOat7Cq-image-1666864838746.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/iMooWXZeDvOat7Cq-image-1666864838746.png)

Les test fonctionnelles correspondent au tableau *functionality*. Les autres tests sont concidéré comme des tests non fonctionnelles.

- Tests fonctionnelles
	- le type de test qui garantit le bon fonctionnement du logiciel
- Tests non fonctionnelles
	- le type de test qui vérifie les aspects non fonctionnels tels que les performances, la convivialité, la fiabilité, etc. du logiciel.


### Test de régrétion

On va vérifier, après modification du code, que le reste du code non modifié fonctionne toujours correctement.

## La démarche de tests

Les tests logiciels sont un métier à part entière. Ce n'est pas le développeurs.

ON défini qui est responsable d'écrire les tests et ceux qui les executes.

Pour écrire les tests, il faut une gestion de projets qui permet de définir les besoins du logiciel. Ces besoins pourront être testé par ces tests.

A chaque phase du projet, on va réfléchir au différents tests à concevoir en même temps que le reste du projet.

Les tests peuvent être **statiques** :

- revue de code.
- relecture des specifications du projet.

Il faut également une traçabilité sur :

1. L'exigence
1. Tests
1. Résultats
1. Anomalie (du test)

Il faut pouvoir mettre en lien l'ensemble des étapes précédantes (l'exicence X est testé par le test Y qui à donnée le resutat Z et une anomalie A).

Il faut également trouver les plus gros risque du logiciel pour natemment prioriser les tests pour ces risques.

### Pour la méthode ISTQB

De toute manière, on ne peut pas tout tester. Il faut définir une stratégie de test :

- quelle fonctionnalités ?
- cas d'utilisation métier
- environments d'execution
- jeu de données
- instruction dans le code

Plus au mets en place des tests, moins on trouvera d'erreurs. Et plus on mets de test, plus ça va couter chère : il faut définir une limite au nombre de test.

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/eou0mpu5fZiuCz4b-image-1666941987142.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/eou0mpu5fZiuCz4b-image-1666941987142.png)

Il faut tester tôt pour découvrir et tester les défaut tôt :

1. Des défauts sont introduits tôt dans le programme.
1. Les résoudres permettra d'éviter de propager les erreurs et les multiplier.
1. Le coût de la correction sera moindre que d'attendre au dernier moment.

#### Paradoxe du pesticide

Si on utilise toujours les mêmes jeux de donnée pour les tests, on ne vérifira que les mêmes données à chaque fois. On risque de ne pas capturer tous les bugs.

> Exemple : si on applique toujours un même type de pesticide sur une plante, d'années en années, les insectes seront de moins en moins sernsible au produit.

#### Tests adapté au contexte

On doit étudier les environnements pour determiner quels tests seront adaptés.

- Contexte d'utilisation métier du logiciel :
	- Quel est le domaine du logiciel ?
    - Quel est la criticité du logiciel ?
- Contexte d'execution du logiciel :
	- Dans quel environnement doit-il fonctionner ?
    - Sur quelles plates-formes matérielles et logicielles ?
- Contexte du projet :
	- Quelles sont les contraintes de temps ?
    - Quelles sont les contraintes du budget ?
    - Quel est le mode de développement du projet (méthode Agile) ?

#### Processus de test

> "Si vous ne pouvez pas décrire vos activités dans un processus, vous ne savez pas que vous faites." - *W Edward Deming*

A gauche on voit les différents environnements de tests :

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/uL2YW0d2GDk9luWJ-image-1666943262582.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/uL2YW0d2GDk9luWJ-image-1666943262582.png)

- Les différents tests n'ont pas à attendre la fin du test de l'étape précédante
- Activités : c'est la planification des temps pour réaliser les tests
- Rapport de test : c'est une liste de l'ensemble des tests ainsi que du résultat de ces tests, avec des informations en plus (description, contexte...)

#### Plan de test

##### Plan de test "maitre"

Il pilote les plan de test de chaque niveau (test de système, d'acceptance...).

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/a1x9LoCHnJBBtL4c-image-1666943783547.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/a1x9LoCHnJBBtL4c-image-1666943783547.png)

##### Plan de test

Il y en a un par niveau de test :

- Tests d'acceptation
- Tests système
- Tests d'intégration
- Tests de composant

Voir un exemple de document (la suite des image sera basé sur cet exemple) :

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/vn84pmg305Q9YQR6-image-1666947034237.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/vn84pmg305Q9YQR6-image-1666947034237.png)

###### Méthode RACI

Pour définir le rôle de chaque personnes qui participe au plan de test :

- R : Réalisation
- A : Approbation
- C : Consultation
- I : Information

###### Jalons

- Etude d’opportunité (T-1)
- Analyse détaillée (T0) -> *métier de concepteur*
- Développement (T1) -> *métier de dévelopeur*
- Déploiement (T2)
- Lancement sur le marché (T3)
- Clôture du projet (T4) -> *le logiciel est installé chez le client, on régle quelques soucis si besoin*

Il faut définir avec le client la maintenance :

- combien de temps après la mise en place du logicel

Et définir un contrat de maintenance si besoin :

- définir les bug "critiques"

Exemple de type de support : <https://www.proxmox.com/en/proxmox-ve/pricing>

###### Element à tester

On liste les différents éléments qui l'on souhaite tester. On défini également ce qu'on souhaite ne pas tester (test non fonctionnel et tests fonctionnel)

###### Stratégie de test

- Quel partie du logiciel à tester.
- Quels sont les partis critiques à tester (partie financier d'un site par rapport à la partie des "avis utilisateurs"). Il faut donc comprendre ce qui est important et ce qui ne l'ai pas pour le client.
- Type de test (Bottom-Up, etc.).

Exemple de calcul et utilisation de l'effort de test :  

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-10/scaled-1680-/WaJWku4CkHsccQU8-image-1666948022097.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-10/WaJWku4CkHsccQU8-image-1666948022097.png)

Test :

- statiques : lecture et relecture (spécification, test d'acceptance par exemple)
- dynamique : lorsqu'on execute quelque chose pour tester

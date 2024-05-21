---
title: GrumPHP
description: 
published: true
date: 2024-05-21T14:09:19.298Z
tags: 
editor: markdown
dateCreated: 2024-05-21T14:09:19.298Z
---

# GrumPHP

**GrumPHP** est un outil de test de **qualité de code** qui permet d'exécuter un ensemble de tâches (phpstan, phpmd, twigcs, yamllint, ...)
via des hooks git. L'avantage est qu'il va centraliser le déclenchement de ces tâches (One tool to rule them all !).

Techniquement c'est un ``plugin composer`` qui va ajouter des **hooks de commit** dans votre projet.
A chaque commit, GrumPHP va se déclencher et lancer des tests sur le code modifié. Si les tests échouent, vous ne pourrez pas commit vos changements.
Cet outil permet d'améliorer la qualité du code mais également d'apprendre à mieux développer en suivant les bonnes pratiques.

GrumPHP possède un ensemble de tâches préconfigurées ce qui permet de l'utiliser simplement avec un minimum de paramétrage.

Le projet et la documentation sont hébergé sur <https://github.com/phpro/grumphp>

## Installation

Pour utiliser GrumPHP, vous aurez besoin de ``php``, ``composer`` et ``git`` en **ligne de commande**.

.. warning::
    GrumPHP peut rencontrer des problème avec Xdebug. Si c'est le cas, vous devrez commenter la partie xdebug dans votre php.ini pour le désactiver.

GrumPHP est un plugin composer qui doit être installé en tant que dépendance de développement de votre projet en utilisant composer via la commande

``composer require --dev phpro/grumphp``

Une fois installé, il va ajouter des hooks git à votre projet. Vous devez voir apparaître le message **Watch out! GrumPHP is sniffing your commits!** dans la console.
Si ce n'est pas le cas, installez les hooks avec la commande

``php ./vendor/bin/grumphp git:init``

.. warning::
    GrumPHP écrase les hooks de votre projet lors de son installation.
    Si vous ne voulez pas que ce soit le cas, vous devez exécuter ``composer install`` avec l'option ``--no-plugins`` ou ``--no-scripts``

## Configuration

La configuration de GrumPHP se fait dans un fichier ``grumphp.yml`` à la racine de votre projet.
Dans ce fichier vous allez pouvoir utiliser un ensemble de paramètres permettant de modifier le comportement de GrumPHP en choisissant
par exemple le répertoire dans lequel se trouvera les hooks, la manière de gérer la parallélisation ou encore s'il doit corriger automatiquement les erreurs.
Tous les paramètres son listés sur <https://github.com/phpro/grumphp/blob/master/doc/parameters.md>

C'est également dans ce fichier que vous allez devoir définir et configurer les tâches que GrumPHP devra lancer.
Une tâche est un outil externe à GrumPHP qui permet d'analyser et valider le code.
Il en existe des dizaines comme par exemple : phpcsfixer, phpmd, phpstan, psalm...
La liste complète se trouve sur <https://github.com/phpro/grumphp/blob/master/doc/tasks.md>

Chaque tâche possède différents paramètres qui vont permettre de configurer le comportement de l'outil associé.
Pensez à consulter la documentation pour adapter le paramétrage à vos besoins.

.. note::
    Lorsque vous ajoutez une tâche, pensez à installer la dépendance associée.
    Par exemple pour **phpcsfixer**, ``composer require --dev friendsofphp/php-cs-fixer``
    Vous trouverez les informations dans la documentation associée à chaque tâche.
    Par exemple pour **phpcsfixer** <https://github.com/phpro/grumphp/blob/master/doc/tasks/phpcsfixer.md>

Une fois votre configuration faite, vous pouvez exécuter toutes vos tâches grâce à la commande ``vendor/bin/grumphp run``

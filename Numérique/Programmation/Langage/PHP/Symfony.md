---
title: Symfony
description: 
published: true
date: 2024-05-21T18:27:05.195Z
tags: 
editor: markdown
dateCreated: 2024-05-21T18:27:05.195Z
---

# Symfony

Symfony est un framework pour le langage PHP.

## Informations

### Arborescence

```
├── bin/
├── composer.json
├── composer.lock
├── config/
├── public/
├── src/
├── symfony.lock
├── var/
└── vendor/
```

#### Ressources publiques

Tout ce qui est dans le dossier `public`.

## Code

### Evenements

#### Liste

```bash
php bin/console debug:event-dispatcher
php bin/console debug:event-dispatcher kernel.exception
php bin/console debug:event-dispatcher kernel // matches "kernel.exception", "kernel.response" etc.
```

#### Créer un événement

```bash
symfony console make:subscriber TwigEventSubscriber
```

#### Exemple

```bash
<?php

namespace App\EventSubscriber;

use Twig\Environment;
use App\Repository\ConferenceRepository;
use Symfony\Component\HttpKernel\Event\ControllerEvent;
use Symfony\Component\EventDispatcher\EventSubscriberInterface;

class TwigEventSubscriber implements EventSubscriberInterface
{
    private Environment $twig;
    private ConferenceRepository $conferenceRepository;

    public function __construct(Environment $twig, ConferenceRepository $conferenceRepository)
    {
        $this->twig = $twig;
        $this->conferenceRepository = $conferenceRepository;
    }
    public function onControllerEvent(ControllerEvent $event): void
    {
        $this->twig->addGlobal('conferences', $this->conferenceRepository->findAll());
    }

    public static function getSubscribedEvents(): array
    {
        return [
            ControllerEvent::class => 'onControllerEvent',
        ];
    }
}

```

#### Liste d'événements

| Classe | Description 
|--|--
| Symfony\Component\HttpKernel\Event\ControllerEvent | Avant l'appelle d'un controleur


### Débugage

- `dump($uneVariable)` : permet d'afficher le contenu dans la toolbar de débug

## Configuration

### Fichiers d'environement

- `.env` : ajouté au dépot git
- `.env.local` : non commité

## Modules

### Doctrine ORM

#### Configuration de la BDD

```
DATABASE_URL="postgresql://username:password@127.0.0.1:5432/db?serverVersion=13&charset=utf8"
```

Dans les fichiers `.env`

#### Entités

##### Générer ou modifier une entité

```bash
symfony console make:entity NomEntite
```

Si l'on souhaite ajouter des attributs, il suffit de définir le même nom d'entité.

#### Migrations

Une migration permet de modifier les tables de la base de données d'un instant N à un instant N+1 suite à la modification des schémas.

Créer la migration :  

```bash
symfony console make:migration
```

Verifier le fichier généré dans `migrations/`.

Mettre à jour la base de données :

```bash
symfony console doctrine:migrations:migrate
```

##### Modification d'attribut non `null`

Dans le cas d'ajout d'attribut non null, il faut préciser comment ajouter des valeurs aux données existantes dans la base de donnée.

Il faut modifier la migration.

Par exemple :  

```bash
public function up(Schema $schema): void
{
	// this up() migration is auto-generated, please modify it to your needs
    
    // Ancienne ligne, posant problème
	//$this->addSql('ALTER TABLE conference ADD slug VARCHAR(255) NOT NULL');
	
    // Modification pour la migration de données non null
    $this->addSql('ALTER TABLE conference ADD slug VARCHAR(255)');
	$this->addSql("UPDATE conference SET slug=CONCAT(LOWER(city), '-', year)");
	$this->addSql('ALTER TABLE conference ALTER COLUMN slug SET NOT NULL');
}
```

#### Les types

```
Main types
  * string
  * text
  * boolean
  * integer (or smallint, bigint)
  * float

Relationships / Associations
  * relation (a wizard will help you build the relation)
  * ManyToOne
  * OneToMany
  * ManyToMany
  * OneToOne

Array/Object Types
  * array (or simple_array)
  * json
  * object
  * binary
  * blob

Date/Time Types
  * datetime (or datetime_immutable)
  * datetimetz (or datetimetz_immutable)
  * date (or date_immutable)
  * time (or time_immutable)
  * dateinterval

Other Types
  * decimal
  * guid
  * json_array
```

#### Cycle de vie

Exemple :  

```php
<?php

namespace App\Entity;

use App\Repository\CommentRepository;
use Doctrine\DBAL\Types\Types;
use Doctrine\ORM\Mapping as ORM;

#[ORM\Entity(repositoryClass: CommentRepository::class)]
#[ORM\HasLifecycleCallbacks]
class Comment
{
    #[ORM\Id]
    #[ORM\GeneratedValue]
    #[ORM\Column(type: 'integer')]

    #[ORM\Column]
    private ?\DateTimeImmutable $createdAt = null;

    public function getId(): ?int
    {
        return $this->id;
    }

    public function getCreatedAt(): ?\DateTimeImmutable
    {
        return $this->createdAt;
    }

    public function setCreatedAt(\DateTimeImmutable $createdAt): self
    {
        $this->createdAt = $createdAt;

        return $this;
    }

  	// Cette méthode est executé lorsqu'on sauvegarde pour la première fois
  	// l'objet dans la base de donnée
    #[ORM\PrePersist]
    public function setCreatedAtValue()
    {
        $this->createdAt = new \DateTimeImmutable();
    }
}

```

##### Liste des événements

| Nom | Description
|---|---
| `ORM\PrePersist` |  Lors de la sauvegarde de l'objet pour la première fois

## Commandes

### Lister les commandes

Avec `php bin/console` :

| Commande | Fonction |
|--|--|
| `php bin/console about` | Afficher les informations de Symfony
| `php bin/console debug:router ` | Afficher la liste des routes existantes
| `php bin/console about ` | Informations du projet
| `php bin/console cache:clear ` | Supprimer le cache en environment dev
| `symfony console list make` | Liste de taches d'automatisation de création
| `symfony console make:controller` | Créer un controlleur

Avec `symfony` :

| Commande | Fonction |
|--|--|
| `symfony server:start -d` | Lancer un serveur local web
| `symfony server:stop` | Arreter le serveur local web
| `symfony open:local` | Ouvrir le navigateur avec l'url du serveur local web
| `symfony server:log` | Afficher en temps réel les logs du serveur local
| `symfony console list make` | Afficher la liste de code générable
| `symfony run pg_dump --data-only > dump.sql` | Sauvegarder une BDD postgre
| `symfony run psql < dump.sql` | Restaurer une BDD postgre
| `symfony var:export` | Afficher les variables d'environment

### Initialisation d'un projet

- <https://symfony.com/download>

#### Initialisation avec symfony-cli

Télécharger et installer `symfony-cli`.

Example :

```
symfony new guestbook --version=5.4 --php=8.1 --webapp --docker --cloud
```

Pour créer la base d'un projet (pour installer une lts, rajouter `--version=lts`:

- application minimal, pour créer des applications de type **microservice, console ou API**.

```bash
symfony new NOM_PROJET
```

- application web, ajout du **webapp pack**.

```bash
symfony new --webapp NOM_PROJET
```

- Pour apprendre : clonage de "Symfony: The Fast Track book project" pour de l'apprentissage.

```bash
symfony new --book NOM_PROJET
```

Avec des options optionnels :

| Option | Signification |
|--|--|
|`--docker`| Ajout du support de docker
|`--debug`| Affiche les sorties des commandes
|`--dir`| Pour spécifier le dossier où installer symfony 
|`--version=value`| Pour définir la version à installer (valeur possible: `lts`, `6.1.*` ou `next` pour la version en dev)

#### Initialisation avec Composer

Pour installer la version minimal pour console, API et microservice :

```bash
composer create-project symfony/skeleton:"6.1.*" NOM_PROJET
```

Si l'ont veut créer un projet web complet (similaire à `symfony new --webapp`):

```bash
composer create-project symfony/skeleton:"6.1.*" NOM_PROJET
cd NOM_PROJET
composer require webapp
```

### Génération de code

Avec le paquet `symfony/maker-bundle`

`symfony console list make` : lister les diffférents code générable

#### Controlleur

```bash
symfony console make:controller ConferenceController
```

##### Entité

```bash
symfony console make:entity Conference
```

#### Conventions

- <https://symfony.com/doc/current/contributing/code/standards.html>

## Outils

### symfony-cli

#### Configurer la version de PHP

On peut choisir quel executable PHP à utilisé s'il en existe plusieurs accessible depuis le PATH.

Il faut définir la version de PHP dans le fichier `.php-version` :

```txt
8.1
```

### Composer

## Ressources

### Documentation

- <https://symfony.com/doc/current/index.html>  
Ne pas oublier de selectionner la version de Symfony pour adapter la documentation.

### Todo

```
compact('form');
```

### Ressources

#### Tutoriels

- [Développer une API REST avec Symfony et api-platform](https://www.kaherecode.com/tutorial/developper-une-api-rest-avec-symfony-et-api-platform)

### todo

#### BDD

- https://www.wanadev.fr/283-le-bdd-behavior-driven-development-avec-behat-et-symfony/

#### autre

- composer recipes

```
php bin/console config:dump-reference framework workflows
```

- event :
```
php bin/console debug:event-dispatcher
```

- twig :
  - app.user
  -  is_granted('ROLE_ADMIN')
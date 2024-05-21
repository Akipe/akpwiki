---
title: Make et Makefile
description: 
published: true
date: 2024-05-21T17:25:54.952Z
tags: 
editor: markdown
dateCreated: 2024-03-04T12:23:56.287Z
---

# Make et Makefile

`make` permet de gérer la compilation de programmes depuis des langages comme le C, mais peut également être utilisé pour automatiser et regrouper des commandes.


## Configuration & syntaxe

### Principe de base

Il faut créer un fichier nommé `Makefile`.

**Attention!** Les commandes doivent être **précédée d'une tabulation**, et non d'espaces.

```makefile
cible: prerequis1 prerequis2
    command1
    command2
```

Exemple de configuration :

```makefile
main.o : main.c defs.h
    cc -c main.c
```

Pour créer le fichier `main.o`, on indique à *make* qu'il dépend des fichiers `main.c` et `defs.h`.  
Donc si le fichier `main.o` est plus ancien que l'une des dépendances, *make* executera la commande `cc -c main.c`

### Commentaires

On peut ajouter des commentaires pour les cibles avec `##`.

```makefile
cible: ## Ceci est un commentaire
  echo "Hello World!"
```

On doit utiliser `@` pour indiquer à *make* de ne pas afficher la commande.

```makefile
target:
    @echo "Building!"
```

### `.PHONY`

  Permet d'utiliser *make* pour appeler les *cibles* comme des alias dans le shell.

```makefile
.PHONY: mon_alias

hello_world:
    echo "Hello World!"

mon_alias: hello_world
```

```shell
make mon_alias # va afficher "Hello World!"
```

### Cible `help`

On peut utiliser plusieurs example :

```makefile
help: 
    @grep -E '(^[a-zA-Z_-]+:.*?##.*$$)|(^##)' $(MAKEFILE_LIST) | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[32m%-10s\033[0m %s\n", $$1, $$2}' | sed -e 's/\[32m##/[33m/'
```

### Variables

On peut par exemple définir quel version de PHP utiliser pour les commandes :

```makefile
PHP=php

test: install ## Lance les tests unitaire
    $(PHP) ./vendor/bin/phpunit --stop-on-failure
```

Les variables peuvent être dynamiques :

```makefile
CURRENT_DIR=$(shell pwd)

echo_dir:
  echo $(CURRENT_DIR)
```

Elles peuvent être également surchargé à l'execution de la commande `make` :

```makefile
PHP=php
CURRENT_DIR=$(shell pwd)
ifdef VERSION
    PHP=docker run -it --rm --name phpcli -v $(CURRENT_DIR):/usr/src/myapp -w /usr/src/myapp php:$(VERSION)-cli php
endif

test: install ## Lance les tests unitaire
    $(PHP) ./vendor/bin/phpunit --stop-on-failure
```

```shell
make test
make test VERSION=7.0
make test VERSION=7.1
make test VERSION=7.2-rc
```

Plus d'informations : <https://www.gnu.org/software/make/manual/html_node/#toc-How-to-Use-Variables>

#### Définir une variable si non défini à l'execution

Avec `VARIABLE?=VALEUR` :

```makefile
one = hello
one ?= will not be set
two ?= will be set

all: 
	echo $(one)
	echo $(two)
```

### Pattern Rule

On peut définir des motifs de règles avec `%` :

```makefile
images/optimized/%.jpg: images/raw/%.jpg
    mkdir -p images/optimized
    guetzli --quality 85 --verbose $< $@
```

### Conditions

```makefile
ifdef VERSION
    PHP=docker run -it --rm --name phpcli -v $(CURRENT_DIR):/usr/src/myapp -w /usr/src/myapp php:$(VERSION)-cli php
endif
```

### Fonctions

<https://www.gnu.org/software/make/manual/make.html#toc-Functions-for-Transforming-Text>

#### `subst`

#### `wildcard`

### Couleurs

```makefile
COM_COLOR   = \033[0;34m
OBJ_COLOR   = \033[0;36m
OK_COLOR    = \033[0;32m
ERROR_COLOR = \033[0;31m
WARN_COLOR  = \033[0;33m
NO_COLOR    = \033[m

server: install
    echo -e "Lancement du serveur sur $(OK_COLOR)http://127.0.0.1:8080$(NO_COLOR)"
    ENV=dev php -S 127.0.0.1:80 -t public/ -d display_errors=1
```

## Commandes

Il faut commencer avec la commande `make`.

### Paralléliser les taches

Avec la commande `-j` :

```shell
make -j8
```

## Exemple de configuration

- <https://github.com/Grafikart/Grafikart.fr/blob/master/Makefile>

### Configuration web & PHP

```makefile
PHP=php
PORT_PHP?=8000
PORT_SYNC?=3000
HOST?=127.0.0.1
COM_COLOR   = \033[0;34m
OBJ_COLOR   = \033[0;36m
OK_COLOR    = \033[0;32m
ERROR_COLOR = \033[0;31m
WARN_COLOR  = \033[0;33m
NO_COLOR    = \033[m

.PHONY: test server watch cache-clear install update help

composer.lock: composer.json ## si "composer.json" est plus récent que "composer.lock", on mets à jour la liste des dépendances composer
    composer update

vendor: composer.lock app/config/parameters.yml.dist ## si "composer.lock" est plus récent que le contenu du dossier "vendor", alors on installe les dépendances composer
    composer install

install: vendor ## on autorise l'execution manuel de la commande "make install" avec la config ".PHONY: install"

update: ## Mettre à jour vers la derniers version les dépendances Composer
  composer update

help: 
    @grep -E '(^[a-zA-Z_-]+:.*?##.*$$)|(^##)' $(MAKEFILE_LIST) | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[32m%-10s\033[0m %s\n", $$1, $$2}' | sed -e 's/\[32m##/[33m/'

test: install ## Lance les tests unitaire
    php ./vendor/bin/phpunit --stop-on-failure

cache-clear: ## Nettoie le cache
    rm -rf ./tmp

server: install ## Lance le serveur interne de PHP
    echo -e "Lancement du serveur sur $(OK_COLOR)http://$(HOST):$(PORT_PHP)$(NO_COLOR)"
    ENV=dev $(PHP) -S $(HOST):$(PORT_PHP) -t public/ -d display_errors=1

browsersync:
    npx browser-sync start --port $(PORT_SYNC) --proxy $(HOST):$(PORT_PHP) --files 'src/**/*.php' --files 'src/**/*.twig'

watch: server browsersync ## Nécessite "make watch -j2" pour executer les 2 taches en parallèles
```

## Ressources

- <https://www.gnu.org/software/make/manual/html_node/>
- <https://makefiletutorial.com/>


---


Filename : `Makefile`
Use TAB, no space !!!

## For compilation

```
cible: prerequis1 prerequis2
    command1
    command2
    <-- tab !!!!
```

Example :

```
main.o : main.c defs.h
    cc -c main.c
```
To get `main.o`, we need `main.c` & `defs.h`. If `main.o` is more recent than `main.c` & `defs.h`, we don't execute the command.

## For command helper

```
.PHONY: install update

composer.lock: composer.json
    composer update
    
vendor: composer.lock
    composer install

install: vendor
```

->
- If `composer.json` more recent than `composer.lock`, so we update dependencies with `composer update`
- If the file `composer.lock` is more recent than the directory `vendor`, so we install dependencies
- We create .PHONY who permit to execute `make install/install`

An other example :

```
.PHONY: test server cache-clear install help
.DEFAULT_GOAL= help

composer.lock: composer.json
    composer update

vendor: composer.lock
    composer install

install: vendor

help: 
    @grep -E '(^[a-zA-Z_-]+:.*?##.*$$)|(^##)' $(MAKEFILE_LIST) | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[32m%-10s\033[0m %s\n", $$1, $$2}' | sed -e 's/\[32m##/[33m/'

test: install ## Lance les tests unitaire
    php ./vendor/bin/phpunit --stop-on-failure

cache-clear: ## Nettoie le cache
    rm -rf ./tmp

server: install ## Lance le serveur interne de PHP
    ENV=dev php -S localhost:8000 -t public/ -d display_errors=1
```

### Variables

```
PHP=php
CURRENT_DIR=$(shell pwd)
ifdef VERSION
    PHP=docker run -it --rm --name phpcli -v $(CURRENT_DIR):/usr/src/myapp -w /usr/src/myapp php:$(VERSION)-cli php
endif

test: install ## Lance les tests unitaire
    $(PHP) ./vendor/bin/phpunit --stop-on-failure
```

Puis les commandes à éxécuter :

```
make test
make test VERSION=7.0
make test VERSION=7.1
make test VERSION=7.2-rc
```

### Pattern Rule

```
RAW_IMAGES=$(subst images/raw/,images/optimized/,$(wildcard images/raw/*.jpg))

images/optimized/%.jpg: images/raw/%.jpg
    mkdir -p images/optimized
    guetzli --quality 85 --verbose $< $@

images: $(SRC)
```

Si on tape `make images` le système va automatiquement optimiser les nouvelles images et les placer dans le dossier optimized. Il est aussi possible, gràce au drapeau -j de paralléliser les tâches.


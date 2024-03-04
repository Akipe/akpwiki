---
title: Makefile
description: 
published: true
date: 2024-03-04T12:23:56.287Z
tags: 
editor: markdown
dateCreated: 2024-03-04T12:23:56.287Z
---

# Makefil

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


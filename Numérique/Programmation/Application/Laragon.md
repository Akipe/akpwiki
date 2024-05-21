---
title: Laragon
description: 
published: true
date: 2024-05-21T16:39:20.309Z
tags: 
editor: markdown
dateCreated: 2024-05-21T16:39:20.309Z
---

# Laragon

Depuis le site officiel ou depuis le repo officiel sur Github :
- <https://laragon.org/download/>
- <https://github.com/leokhoa/laragon/releases>

Prendre la version **portable** si vous avez un compte non administrateur.

## Définir le dossier du serveur web

Dans la zone des notifications, accédez aux paramètres de Laragon :  
***www > Switch document root > Select another*** et selectionnez le dossier voulu.

[![laragon_select_directory.png](https://wiki.akipe.fr///uploads/images/gallery/2022-08/scaled-1680-/rbcAmoRHkSWh60ck-laragon-select-directory.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-08/rbcAmoRHkSWh60ck-laragon-select-directory.png)

## Ajouter une version de PHP

Télécharger la version de PHP voulu sur :

- <https://windows.php.net/download>

Prendre la version ***Thread Safe x64***.

A la racine du repertoire de Laragon, décompresser l'archive contenant PHP dans le repertoire, avec un dossier comportant la référence de la version de PHP téléchargé : `REPERTOIRE_LARAGON\bin\php`.

Par exemple pour PHP 8.1.8, vous aurez un dossier `REPERTOIRE_LARAGON\bin\php\php-8.1.8-Win32-vs16-x64` contenant l'ensemble des fichiers de l'archive.

Ensuite, dans la zone des notifications, accédez aux paramètres de Laragon :  
***PHP > Version*** et selectionnez la nouvelle version.

[![laragon_select_custom_php_version.png](https://wiki.akipe.fr///uploads/images/gallery/2022-08/scaled-1680-/jK92gDJ6DxGmP4eI-laragon-select-custom-php-version.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-08/jK92gDJ6DxGmP4eI-laragon-select-custom-php-version.png)

## Ajout de Xdebug

Télécharger Xdebug, prendre la dernière version en mode **x64 & TS** (Thread Safe) (exemple : *PHP 8.1 VS16 TS (64 bit)*) :  
<https://xdebug.org/download/historical>

Déplacer le fichier dans le dossier `REPERTOIRE_LARAGON\bin\php\php_VERSION_UTILISE\ext` (remplacer ***php_VERSION*** par la version de PHP utilisé, comme par exemple ***php-8.1.8-Win32-vs16-x64***).

Ensuite, renomez le fichier en `php_xdebug.dll`, **faites bien attentions à l'extension du fichier!**

Vous devriez avoir par exemple ce resultat : `REPERTOIRE_LARAGON\bin\php\php-8.1.8-nts-Win32-vs16-x64\ext\php_xdebug.dll`

Ensuite, ajouter **à la fin** du fichier `php.ini` dans le dossier de votre version PHP (``REPERTOIRE_LARAGON\bin\php\php_VERSION_UTILISE\php.ini``):

```ini
# ...

[xdebug]
zend_extension=php_xdebug
xdebug.mode=debug
xdebug.client_host=127.0.0.1
xdebug.client_port=9003
```

Redémarrer Laragon pour activer l'utilisation d'Xdebug.

## A Modifier : vs code

```
Dans settings.json
"php.debug.executablePath": "C:\\Users\\CRM\\Applications\\laragon-portable\\bin\\php\\php-8.1.9-Win32-vs16-x64\\php.exe"
```

## Ajout PostgreSQL

Récupérer le lien de PostgreSQL : <https://www.enterprisedb.com/download-postgresql-binaries>

Clique droit sur la toolbar de Laragon > tools > Quick add > Configuration...

Modifier la ligne de PostgreSQL :

```
# postgresql-11=https://get.enterprisedb.com/postgresql/postgresql-11.2-1-windows-x64-binaries.zip
# postgresql-10=https://get.enterprisedb.com/postgresql/postgresql-10.7-1-windows-x64-binaries.zip
postgresql-13=https://get.enterprisedb.com/postgresql/postgresql-13.2-2-windows-x64-binaries.zip
```

Sauvegarder et fermer le fichier.

Clique droit sur la toolbar de Laragon > tools > Quick add > postgresql-14.5...

## Configurer Symfony

### Nginx

```
server {
    listen 80 default_server;
    server_name localhost ;
    root "C:/Users/CRM/Developpement/symfony_guest_book_training/public/"; # A définir 
    index index.html index.htm index.php;
    # Access Restrictions
    allow       127.0.0.1;
    deny        all;
    include "C:/Users/CRM/Applications/Laragon/etc/nginx/alias/*.conf";
    location / {
        #try_files $uri $uri/ =404;
        #autoindex on;
        try_files $uri /index.php$is_args$args;
    }
    location ~ ^/index\.php(/|$) {
        include snippets/fastcgi-php.conf;
        fastcgi_pass php_upstream;
        fastcgi_split_path_info ^(.+\.php)(/.*)$;
        #fastcgi_pass unix:/run/php/php7.0-fpm.sock;
        fastcgi_param SCRIPT_FILENAME $realpath_root$fastcgi_script_name;
        fastcgi_param DOCUMENT_ROOT $realpath_root;
        internal;
    }
    location ~ \.php$ {
        return 404;
    }
    charset utf-8;
    location = /favicon.ico { access_log off; log_not_found off; }
    location = /robots.txt  { access_log off; log_not_found off; }
    location ~ /\.ht {
        deny all;
    }
}
```
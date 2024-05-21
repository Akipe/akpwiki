---
title: Twig
description: 
published: true
date: 2024-05-21T15:04:06.435Z
tags: 
editor: markdown
dateCreated: 2024-05-21T15:04:06.435Z
---

# Twig

C'est un langage de templating conçu pour le PHP : c'est à dire que c'est un langage qui permet de simplifié la création de vues en évitant d'utiliser du PHP.

## Standard

### Nomage

Il est recommandé de nommé le fichier représentant la base de nos vue en `layout.twig` (le nommé en `base.twig` est déprécié).

## Type de notations

### Commentaires

```twig
{% Ceci est un commentaire %}
```

### Afficher une variable

```twig
Tu es agé de {{ age_utilisateur }}.
```

### Tagues

#### Structures de controle

##### Conditions

```twig
{% if age >= 18 %}
	Vous êtes majeur.
{% elseif age < 3 %}
	Vous êtes un bébé.
{% else %}
	Vous êtes mineur.
{% endif %}
```

###### Tester si une valeur est vide

```twig
{% if foo is empty %}
    ...
{% endif %}
```

###### Tester si une varialbe est initialisé

```twig
{% if foo is defined %}
    ...
{% endif %}
```

##### Boucles

```twig
{% for user in users %}
	<li>{{ user.username|e }}</li>
{% endfor %}
```

#### Gestion de block

##### Inclusions

```twig
{{ include('sidebar.html') }}
```

##### Template parent

```twig
<!DOCTYPE html>
<html>
    <head>
        {% block head %}
            <link rel="stylesheet" href="style.css"/>
            <title>{% block title %}{% endblock %} - My Webpage</title>
        {% endblock %}
    </head>
    <body>
        <div id="content">{% block content %}{% endblock %}</div>
        <div id="footer">
            {% block footer %}
                &copy; Copyright 2011 by <a href="http://domain.invalid/">you</a>.
            {% endblock %}
        </div>
    </body>
</html>
```

#### Macro (ou fonctions personnalisés)

<https://twig.symfony.com/doc/3.x/tags/macro.html>

## Exemple

```twig
{# templates/base.html.twig #}
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>{% block title %}Welcome!{% endblock %}</title>
        {% block stylesheets %}{% endblock %}
    </head>
    <body>
        {% block body %}{% endblock %}
        {% block javascripts %}{% endblock %}
    </body>
    {% if block("footer") is defined %}
    	Il y a un footer.
	{% endif %}
</html>
```

### Filtres

#### Mettre en majuscule

- `upper` :

```twig
{{ 'welcome'|upper }}
{# outputs 'WELCOME' #}
```

#### Trimmer

- `trim` :

```twig
{{ '  I like Twig.  '|trim }}
{# outputs 'I like Twig.' #}

{{ '  I like Twig.'|trim('.') }}
{# outputs '  I like Twig' #}

{{ '  I like Twig.  '|trim(side='left') }}
{# outputs 'I like Twig.  ' #}

{{ '  I like Twig.  '|trim(' ', 'right') }}
{# outputs '  I like Twig.' #}
```

#### Mettre une majuscule à chaque mots

- `title` :

```twig
{{ 'my first car'|title }}
{# outputs 'My First Car' #}
```

#### Convertir une chaine de caractère en une liste

- `split` :

```twig
{% set listWords = "one,two,three"|split(',') %}
{# listWords contains ['one', 'two', 'three'] #}
```

#### Gestion de chaine de caractère (UTF-8)

- `u` : il va permettre de gérer une chaine de caractère comme un objet Unicode (une instance de UnicodeString de Symfony). On va pouvoir effectuer des manipulations.

```twig
{{ 'Symfony String + Twig = <3'|u.wordwrap(5) }}
Symfony
String
+
Twig
= <3
```

```twig
{{ 'Lorem ipsum'|u.truncate(8) }}
Lorem ip
```

##### Convertir la case en snake, camelCase...

```
{{ 'SymfonyStringWithTwig'|u.snake }}
symfony_string_with_twig

{{ 'symfony_string with twig'|u.camel.title }}
SymfonyStringWithTwig
```

#### Encoder des caractère pour générer des URL

- `url_encode ` :

```twig
{{ "path seg*ment"|url_encode }}
{# outputs "path%20seg%2Ament" #}
```

#### Trier un tableau

- `sort ` :

```twig
{% for user in users|sort %}
    ...
{% endfor %}
```

Il est possible d'utiliser une fonction flécher pour gérer le tri :

```twig
{% set fruits = [
    { name: 'Apples', quantity: 5 },
    { name: 'Oranges', quantity: 2 },
    { name: 'Grapes', quantity: 4 },
] %}

{% for fruit in fruits|sort((a, b) => a.quantity <=> b.quantity)|column('name') %}
    {{ fruit }}
{% endfor %}

{# output in this order: Oranges, Grapes, Apples #}
```

#### Convertir une chaine de caractère en caractère ASCII (slug)

- `slug ` :

```twig
{{ 'Wôrķšƥáçè ~~sèťtïñğš~~'|slug }}
Workspace-settings

{{ 'Wôrķšƥáçè ~~sèťtïñğš~~'|slug('/') }}
Workspace/settings
```

#### Inverser un tableau ou une chaine de caractère

- `reverse ` :

```twig
{% for user in users|reverse %}
    ...
{% endfor %}

{{ '1234'|reverse }}

{# outputs 4321 #}
```

#### Gérer le format des nombres

- `number_format ` :

<https://twig.symfony.com/doc/3.x/filters/number_format.html>

#### Fusionner des tableau

- `merge ` :

```twig
{% set values = [1, 2] %}
{% set values = values|merge(['apple', 'orange']) %}

{# values now contains [1, 2, 'apple', 'orange'] #}
```

#### Convertir du Markdown en HTML

- `markdown_to_html ` :

```twig
{% apply markdown_to_html %}
Title
======

Hello!
{% endapply %}
```

On peut également l'appliqué à un fichier ou une variable :

```
{{ include('some_template.markdown.twig')|markdown_to_html }}

{{ changelog|markdown_to_html }}
```

#### Appliquer des actions en chaine à un tableau (map)

- `map` :

```twig
{% set people = [
    {first: "Bob", last: "Smith"},
    {first: "Alice", last: "Dupond"},
] %}

{{ people|map(p => "#{p.first} #{p.last}")|join(', ') }}
{# outputs Bob Smith, Alice Dupond #}
```

<https://twig.symfony.com/doc/3.x/filters/map.html>

#### Mettre une chaine de caractère en minuscule

- `lower` :

```twig
{{ 'WELCOME'|lower }}
{# outputs 'welcome' #}
```

#### Récupérer la taille d'un élément

- `length`  :

```twig
{% if users|length > 10 %}
    ...
{% endif %}
```

#### Récupérer le dernier élément

- `last` :

```twig
{{ [1, 2, 3, 4]|last }}
{# outputs 4 #}
```

#### Récupérer la clée d'un élément

- `keys` :

```twig
{% for key in array|keys %}
    ...
{% endfor %}
```

#### Encoder un contenu en JSON

- `json_encode` :

```twig
{{ data|json_encode() }}
```

#### Joindre et concaténer des éléments entre eux

- `join ` :

```twig
{{ [1, 2, 3]|join }}
{# returns "123" #}

{{ [1, 2, 3]|join('|') }}
{# outputs "1|2|3" #}

{{ [1, 2, 3]|join(', ', ' and ') }}
{# outputs "1, 2 and 3" #}
```

#### Convertir du HTML en Markdown

- `html_to_markdown` :

```twig
{% apply html_to_markdown %}
    <html>
        <h1>Hello!</h1>
    </html>
{% endapply %}
```

```twig
> {{ include('some_template.html.twig')|html_to_markdown }}
```

#### Valeur absolu d'un nombre

- `abs` :

```twig
{{ -5|abs }}
{# outputs 5 #}
```

#### Format du temps

##### Date et heure

- `lower ` :

```twig
{{ 'WELCOME'|lower }}
{# outputs 'welcome' #}
```

##### Heure seul

- `format_time` :

Similaire à `format_datetime`.

##### Date seul

- `format_date` :

Similaire à `format_datetime`.

#### Gérer les dates

- `date` :

```twig
{{ "now"|date("m/d/Y") }} {# Date d'aujourd'hui #}
{{ post.published_at|date("m/d/Y") }}
{{ post.published_at|date("m/d/Y", "Europe/Paris") }}
```

#### Modifier une date

- `date_modify` :

```twig
{{ post.published_at|date_modify("+1 day")|date("m/d/Y") }}
```

#### Définir une valeur par défaut si variable vide ou non défini

- `default()` :

```twig
{{ var|default('var is not defined') }}
{{ var.foo|default('foo item on var is not defined') }}
{{ var['foo']|default('foo item on var is not defined') }}
{{ ''|default('passed var is empty')  }}
```

**Attention avec la gestion des booléens !** : <https://twig.symfony.com/doc/3.x/filters/default.html>

#### Récupérer la première valeur d'un colonne d'un tableau

- `column` :

```twig
{% set items = [{ 'fruit' : 'apple'}, {'fruit' : 'orange' }] %}
{% set fruits = items|column('fruit') %}
{# fruits now contains ['apple', 'orange'] #}
```

#### Conversion de table de code de caractère

- `convert_encoding(expected, inputCharset)` :

```twig
{{ data|convert_encoding('UTF-8', 'iso-2022-jp') }}
```

#### Générer une URML en respectant la RFC 2397

- `data_uri` :

<https://twig.symfony.com/doc/3.x/filters/data_uri.html>

#### Echaper des caractères

- `escape` ou `e`:

Par défaut, on échape les caractères HTML (pour éviter des problèmes de sécurité).

On peut utiliser :
- html
- js
- css
- url
- html_attr

```twig
{{ user.username|escape }}
{{ user.username|e }}
{{ user.username|e('html') }}
{{ user.username|escape('js') }}
{{ user.username|e('js') }}
```

## Options

Une liste d'options est disponible à cette adresse : <https://twig.symfony.com/doc/3.x/api.html#environment-options>

### Être stricte sur la gestion des variables

- `strict_variables`

## Todo

- https://twig.symfony.com/doc/3.x/filters/filter.html
- https://twig.symfony.com/doc/3.x/filters/first.html
- https://twig.symfony.com/doc/3.x/filters/format.html
- https://twig.symfony.com/doc/3.x/filters/format_number.html
- https://twig.symfony.com/doc/3.x/filters/format_datetime.html
- https://twig.symfony.com/doc/3.x/filters/format_date.html
- https://twig.symfony.com/doc/3.x/tags/deprecated.html

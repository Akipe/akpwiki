---
title: HTML
description: 
published: true
date: 2024-05-21T14:28:30.162Z
tags: 
editor: markdown
dateCreated: 2024-05-21T14:19:46.430Z
---

# HTML

**HTML** est l'abréviation de ***Hypertext Markup Language***.

## Historique

Deux languages : XHTML et HTML, le HTML5 est hérité des deux mouvements.

HTML descendant du SGML (Standard Generalized Markup Language).

Fichier HTML similaire à la forme XML respectant la convention.

## Exemple d'une page

```html
<!-- On défini le type et la version, ici HTML 5 -->
<!DOCTYPE html>

<!-- Code language de la page, 2 caractères ou sur 2-2 caractères -->
<!-- "fr" ou "fr-be" -->
<html lang="fr">

    <!-- Entête de la page-->
    <head>
        <!-- Le type encodage -->
        <meta charset="utf-8">

        <!-- Le "viewport" correspond à la zone d'affichage -->
        <meta name="viewport" content="width=device-width, initial-scale=1.0">

        <!-- "width=device-width": pour définir la taille du viewport, en JS -->
        <!-- On défini la largeur du périphérique est égale à la largeur de la page -->
        <!--     pour faire du responsive-->
        <!-- "initial-scale=1": pour définir le niveau de zoom de base -->

        <!-- Titre de la page -->
        <title>Webchat</title>

        <!-- Inclusion de fichier CSS -->
        <link rel="stylesheet" href="assets/style.css">

        <!-- Inclusion de fichier JS -->
        <script src="assets/main.js" defer></script>
        <!-- "defer" permet d'attendre que le DOM soit construit avant de charger le fichier JS-->
    </head>

    <!-- Contenu de la page -->
    <body>
    
        <!-- titre du site, logo, différents elements de la page -->
        <header> <!-- Peut être dans balise "section" et "article" -->
            <!-- Pas de titre dans le header, sauf si utile au contenu de la page! -->

            <a href="#">WeChat</a>

            <!-- Menu de navigation du site grace à "navigation" -->
            <!-- Si pas lié au menu du site, on retire role="navigation" -->
            <nav role="navigation">

                <!-- Liste de données, non ordonnée -->
                <ul> <!-- "Unordered List"-->
                    <li> <!-- "List Item" -->
                        <a href="#">Accueil</a> <!-- Liens-->
                        <a href="#">Utilisateurs</a>
                        <ul> <!-- Sous liste d'une liste -->
                            <li><a href="">Sous menu</a></li>
                        </ul>
                    </li> 
                </ul>
            </nav>
        </header>

        <!-- Navigation, file d'ariane (grace à "breadcrumb") -->
        <!-- tant que role breadcrumb, peut être placé un peu n'importe où -->
        <nav role="breadcrumb">
            <!-- Vu qu'on est dans un file d'ariane, on utilise des listes ordonnées -->
            <ol> <!-- "Ordened list" -->
                <li><a href="/">Accueil</a></li>
                <li>Page actuelle</li>
            </ol>
        </nav>

        <!-- contenu principal -->
        <!-- ne peut avoir qu'une seul balise main dans la page (du moins affiché) -->
        <main>

            <!-- Titre principal de la page -->
            <h1>Connexion</h1>
        </main>

        <!-- Contient condition utilisation, crédit, navigation -->
        <footer> <!-- Peut être dans balise "section" et "article" -->

        </footer>
    </body>
</html>

```

Fichier HTML obligatoirement balise entête et contenu.

Attention : vérifier que le code caractère (charset) soit identique entre celui de l'editeur et de la page soit le même.

Lorsque chargement de la page : création du DOM (Document Object Model, représentation objet de l'arbre HTML de la page. Tant que le DOM n'est pas construit : pas possible au JS d'y accéder.

**Attention !** Pour chaque page, on ne défini qu'un seul titre `<h1>` qui correspond au titre de la page, pas au titre du site. Ce titre doit correspondre au contenu principal de la page.

Pour les balises `h1` : on ne peut définir qu'une seul balise **par niveau**.
Mais par convention et pour la compatibilité, on préférera garder qu'une seul balise `<h1>` par document. h2 et h3 sont préférable pour les sections et les articles.

Les balises `<header>` et `<footer>` peuvent être également contenu dans une section et un article en plus du body.

On aura généralement au minimum 2 balises nav obligatoires par site :

- navigation sur le site
- file d'ariane

Comment choisir les balises de type "block" :
[![h5d-sectioning-flowchart.png](https://wiki.akipe.fr///uploads/images/gallery/2022-03/scaled-1680-/UerdeSZrbon60fD7-h5d-sectioning-flowchart.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-03/UerdeSZrbon60fD7-h5d-sectioning-flowchart.png)

### Tableaux

```html
<table>
  <thead> <!-- Table Head -->
    <tr> <!-- Table Row -->
      <th></th> <!-- Table Teader, ici représente la cellule -->
    </tr>
  </thead>
  <tbody>
    <tr> <!-- Table Row -->
      <th></th> <!-- Table body, ici représente la cellule -->
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <th></th>
    </tr>
  </tfoot>
</table> 
```

## Images avec `figure`

```html
<figure>
  <img src="/source.png" alt="Une desciption">
  <figcaption>Une phrase de description de l'image</figcaption>
</figure>
```

## Formulaires

```html
<form action="http://localhost/chemin" method="post"> <!-- method="get" -->

	<input 
		type="hidden"
		name="id" value="42"
	>
  
  <fieldset>
    <legend>
    	<label for="lastname">Nom: </label>
    </legend>
    <input 
           type="text"
           id="lastname" // Fait le lien avec le label (attribut for)
           name="lastname" // nom de la variable lors de l envoie
           placeholder="Last Name" // Valeur par défaut mais non copiable et remplaçable facilement
           value="Valeur par defaut" // Valeur par défaut comme placeholder, mais selectionnable
           pattern="[a-zA-Z]{2,16}" // Doit respecter la regle regex
           title="Message lorsque l'utilisateur a rentré une mauvaise donnée"
           required // Doit contenir une donnée
           disabled // Non modifiable
     >
  </fieldset>
  
  <fieldset>
    <legend>
      <label for="toto">Un exemple toto</label>
    </legend>
    <input
           type="radio" // type en mode choix unique
           id="toto" // Valeur de ce choix
           name="bouton-radio" // nom du groupe qui rassemble l ensemble des choix
           >
  </fieldset>
  <fieldset>
    <legend>
    	<label for="tata">Un exemple tata</label>
    </legend>
    <input type="radio" id="tata" name="bouton-radio">
  </fieldset>
  <fieldset>
    <legend>
    	<label for="titi">Un exemple titi</label>
    </legend>
    <input type="radio" id="titi" name="bouton-radio">
  </fieldset>

  <div>
    <button
            type="submit"
    >
      	Enregistrer le nouveau candidat
    </button>
  </div>
</form>
```

### Attribut

- **autocomplete**
- **autofocus**
- **disabled**
- **readonly** 
- **required**
- **value**

### Type

- **hidden**
- **button**
- **submit**
- **search**

- **password**

- **checkbox** : case à cocher
- **radio**

- **color**

- **date** : jour, mois, année
- **datetime-local** : remplace **datetime**
- **month**
- **time**
- **week**

- **text**
- **number**
- **range**

- **email**
- **tel**
- **url**
- **file**
- **image**

- **reset**

## Référencement

Quelques balises intéressantes pour le référencement naturelle :

```html
<meta name="author" content="John Doe">
<meta name="description" content="Un exemple de description de notre page">
<meta name="keywords" content="html,demo,balise"
```

Il faut également utiliser les bonnes balises pour définir le sens sémantique de notre page.

## Balises non courantes

- `<time>`

```html
<p>The Cure will be celebrating their 40th anniversary on <time datetime="2018-07-07">July 7</time> in London's Hyde Park.</p>

<p>The concert starts at <time datetime="20:00">20:00</time> and you'll be able to enjoy the band for at least <time datetime="PT2H30M">2h 30m</time>.</p>
```

- `<abbr>`
- `<address>`
- `<area>`
- `<audio>`
- `<blockquote>`
- `<canvas>`
- `<cite>`
- `<code>`
- `<data>`
- `<colgroup>`
- `<dd>`
- `<del>`
- `<details>`
- `<dfn>`
- `<dialog>`
- `<embed>`
- `<hgroup>`
- `<ins>`
- `<kbd>`
- `<keygen>`
- `<map>`
- `<mark>`
- `<menu>`
- `<menuitem>`
- `<noscript>`
- `<object>`
- `<optgroup>`
- `<param>`
- `<pre>`
- `<progress>`
- `<meter>`
- `<q>`
- `<summary>`

## Ressources

- Une liste de l'ensemble des balises HTML avec une description détaillée : <https://htmlreference.io/>
- [http://html5doctor.com/](http://html5doctor.com/)
- <https://eastmanreference.com/complete-list-of-html-tags>

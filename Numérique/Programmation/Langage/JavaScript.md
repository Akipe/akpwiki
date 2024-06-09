---
title: JavaScript
description: 
published: true
date: 2024-06-09T23:11:00.198Z
tags: 
editor: markdown
dateCreated: 2024-03-04T12:26:06.796Z
---

# JavaScript

## Historique

Commandé par IBM, créer en 10 jours, ressemblant au Java.

**Attention !** ce n'est pas du Java.

Le language s'appelle à présent **JS**.

Au début : s'executer sur Netspace. Permet de m'anipuler les pages web.

## Langage

Lors de la modification du JS, tout le DOM JS est réécrit en entier.

Langague sensible à la case et peut utiliser les caractères Unicode.

```js
// Commentaire sur une ligne
/* Commentaire
	Multi
    Ligne */
```

### Variable

```js
let var_local; // Prtée uniquement dans son bloque de déclaration, recommandé.
var var_fonction; // Portée dans toute la fonction là où déclaré
// var permet de "remonter" sa portée (hoisting)
const CONSTANTE = ""; // Constante, portée dans toute la fonction, comme "var"

// Non recommandé :
var_global = ""; // Portée global, accessible dans tout le JS
// accessible également par "window.var_global"
```

Les **constantes** de types objets et de type tableau autorise la modification de leurs propriétés et de le contenue.

Si une variable n'a pas de valeur défini vaudra `undefined`. Elle vaut `false` dans les conditions.  
Si on tente d'accéder à une variable non existante, celà génére une exception `ReferenceError`.  
Si on tente des calcules sur des variables qui ne peuvent être convertie en nombre, on les converties en `NaN`.  

Types primitifs :
- true / false
- null
- undifined
- type nombre entier ou decimaux
- BigInt
- type chaine de caractère
- type pour les symboles
- type object

```js
// parseInt(string_a_convertir, base) // base = 10 : base de 10, etc
parseInt("101", 2) 

parseFloat()
```

Variables **littéraux** sont des valeurs fixes utilisé pour représenter des valeurs.

```js
// Echapper un caractère
let chemin = "c:\\temp"; // = c:\temp

// Chaine de caractère multiligne
let poeme =
    "Les roses sont rouges,\n\
Les violettes sont bleues.\n\
Le miel est sucré,\n\
Et moi je suis."

let poème =
`Les roses sont rouges,
Les violettes sont bleues,
Le miel est sucré,
Et moi je suis.`
```

---

Déclaration :

```js
var maVariable = 1;
let maSecondeVariable = 2;
```

Array :

```js
let monArray = ['lol', 10, uneFonction()]
monArray[0]
```

String :

```js
let maPhrase = 'Voici ma phrase';
console.log(`Contenu de la phrase : ${maPhrase}, c'est cool nan ? :)`);
```

Float :
Langage de précision flotant ! > `0.1 + 0.2 = 0.300000004`

Concaténation : `console.log('Ma phrase est ' + 'super cool !');`

Variable "complexe" : objet
```js
var eleve = {
    nom: 'Jean,
    moyenne: 15
}
eleve.nom
eleve.moyenne
```

Variable par défaut ou indéfini : ```erreurVar == undefined```

Chaque variables disposent de méthodes, comme des objets

```js
let phraseEnMajuscule = "Une super phrase".toUpperCase();
```

### Chaines de caractère

Caractères spéciaux de chaine de caractère :

| Caractère | Sens
|---|---
| `\0` | Octet null
| `\b` | Retour arrière
| `\f` | Saut de page
| `\n` | Nouvelle ligne
| `\r` | Retour chariot
| `\t` | Tabulation
| `\v` | Tabulation verticale
| `\'` | Apostrophe ou guillemet droit simple
| `\"` | Guillemet droit double
| `\\` | Barre oblique inversée
| `\XXX` | Le caractère dont l'encodage Latin-1 est spécifié grâce à, au plus, 3 chiffres octaux XXX entre 0 et 377. \251, par exemple représente le caractère copyright.
| `\xXX` | Le caractère dont l'encodage Latin-1 est spécifié par deux chiffres hexadécimaux entre 00 et FF. Ainsi, \xA9 correspond à la séquence hexadécimale pour le caractère copyright.
| `\uXXXX` | Le caractère Unicode spécifié par quatre chiffres hexadécimaux XXXX. Ainsi, \u00A9 correspondra à la séquence Unicode du symbole copyright. Voir Les caractères d'échappement Unicode.
| `\u{XXXXX}` | Échappement de codes Unicode. Par exemple, \u{2F804} est équivalent à la combinaison d'échappements « simples » \uD87E\uDC04.

### Portés

> `var`
```
for (var i = 0; i w 3; i++) {
    var d = 'Je sais pas quoi';
}

console.log(d); // Affiche Je sais pas quoi, PAS de scop dans un block
```
- Accessible en dehors du block.

### Les erreurs

```js
// Génére une exception
throw "Une erreure";
throw {toString: function() { return "Je suis un objet!"; }};

try {
  // insctructions à executer
} catch (error) {
  gestionErreurLog(error);
} finally { // Optionnel, si on veut réaliser une action, erreur ou non
  fermerFichier();
}

// https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Error#error_types
new Error([message[, fileName[, lineNumber]]])
const err = new Error("J'ai été créée avec new");
```

Type d'erreur :

| Nom | Sens
|---|---
| `EvalError` | Crée une instance représentant une erreur se produisant en relation avec la fonction globale eval().
| `RangeError` | Crée une instance représentant une erreur se produisant quand une variable numérique ou un paramètre est en dehors de sa plage de validité.
| `ReferenceError` | Crée une instance représentant une erreur se produisant lors du déréférencement d'une référence invalide.
| `SyntaxError` | Crée une instance représentant une erreur de syntaxe se produisant lors d'une analyse de code dans eval().
| `TypeError` | Crée une instance représentant une erreur se produisant quand une variable ou un paramètre n'est pas d'un type valide.
| `URIError` | Crée une instance représentant une erreur se produisant quand des paramètres invalides sont passés à encodeURI() ou à decodeURI().
| `AggregateError` | Crée une instance représentant différentes erreurs agrégées en une seule lorsque plusieurs erreurs sont rapportées par une opération, par exemple avec Promise.any().
| `InternalError` | Crée une instance représentant une erreur se produisant quand une erreur interne dans le moteur JavaScript est déclenchée. Par ex., "too much recursion".

Plus d'informations sur les erreurs : https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Error

### Logique

#### Condition

```js
if (condition1) {
  // ...
} else if (condition2) {
  // ...
} else {
  // ...
}

switch (expression) {
  case premiere_valeur:
    // ...
    [break;]
  case deuxieme_valeur:
    // ...
   	[break;]
  // ...
  default:
    // insctruction par défaut ...
    [break;]
```

### Boucles

```js
for (let pas = 0; pas < 5; pas++) {
  console.log("J'ai fais le pas" + pas);
}

let n = 0;
while (n < 5) {
  n++;
  console.log(n);
}

let n = 0;
do {
  n += 1;
  console.log(n);
} while (n < 5);
```

Les boucles pour parcourir des tableaux :
```js
let arr = ['utilisateurA', 'utilisateurB', 'utilisateurC', toto: "coucou"];

// Afficher les contenus d'un tableau
for (let data of arr) {
  console.log(data); // Affiche 'utilisateurA', 'utilisateurB', 'utilisateurC', "coucou"
}

// Afficher les clés d'un tableau
for (let cle in arr) {
  console.log(cle); // Affiche 0, 1, 2, "toto"
}

// Ou
arr.forEach(data => console.log(data));
arr.forEach(data, cle => console.log(cle + ": " + data));
```

Les boucles `for ... of` sont un peu plus rapides que les boubles `foreach` car ils sont un peu plus bas niveau.

### Les tableaux (array)

```js
let arr = new Array(1, 2, 3);
let arr = Array(1, 2, 3);
let arr = [1, 2, 3];

// Tableau vide avec une longueur
let arr = new Array(longueur);
let arr = Array(longueur);
let arr = [];
arr.length = longueur;

let emp = [];
emp[0] = "Casey Jones";
emp[1] = "Phil Lesh";
emp[2] = "August West";
let monTableau = ["Air", "Eau", "Feu"];
```

Quelques méthodes intéressantes :

| nom | utilité
|---|---
| `concat()` | permet de fusionner deux ou plusieurs tableaux et de renvoyer le résultat dans un nouveau tableau
| `join(délimiteur = ',')` | permet de fusionner les éléments du tableau en une chaîne de caractères
| `push()` | permet d'ajouter un ou plusieurs éléments à la fin d'un tableau et renvoie la longueur du tableau
| `pop()` | permet de retirer le dernier élément (le plus à droite) du tableau et renvoie cet élément
| `shift()` | retire le premier élément d'un tableau (le plus à gauche) et renvoie cet élément
| `unshift()` | ajoute un ou plusieurs éléments au début du tableau et renvoie la longueur du tableau ainsi modifié
| `slice(indice_début, indice_fin)` | extrait une portion d'un tableau et renvoie un nouveau tableau avec ce fragment
| `splice(indice, nbASupprimer, ajouterElement1, ajouterElement2, ...)` | retire des éléments du tableau et (éventuellement) les remplace
| `reverse()` | transpose les éléments du tableau à même ce tableau : le premier élément devient le dernier, le dernier devient le premier et ainsi de suite :
| `sort()` | trie les éléments d'un tableau à même ce tableau
| `indexOf(élémentRecherché[, indiceDépart])` |  recherche la valeur élémentRecherché dans le tableau et renvoie l'indice du premier élément qui correspond
| `lastIndexOf(élémentRecherché[, fromIndex])` | 
| `forEach(callback[, objetThis])` | exécute la fonction callback sur chaque élément du tableau.
| `map(callback[, objetThis])` | renvoie un nouveau tableau dont les éléments sont les images des éléments du tableau courant par la fonction callback
| `filter(callback[, objetThis])` |  renvoie un nouveau tableau qui contient les éléments du tableau courant pour lesquels callback a renvoyé true.
| `every(callback[, objetThis])` |  renvoie true si callback renvoie true pour chaque élément du tableau.
| `some(callback[, objetThis]) ` | renvoie true si callback renvoie true pour au moins un élément du tableau.
| `reduce(callback[, valeurInitiale])` | applique callback(premièreValeur, secondeValeur) au fur et à mesure sur le tableau pour le réduire en une seule valeur, c'est cette valeur qui est renvoyée par la fonction
| `reduceRight(callback[, valeurInitiale])` | fonctionne comme reduce(), mais débute avec le dernier élément (parcourt le tableau de droite à gauche). reduce() et reduceRight() sont à utiliser lorsqu'on souhaite n'obtenir qu'une seule valeur, récursivement, à partir des différents éléments du tableau.


## Fonctions

```js
// Déclarer une fonction
function carre(nombre) {
  return nombre * nombre;
}

var x = carre(4);

// Expression de fonction, qui peuvent être anonymes
car carre = function (nombre) {
  return nombre * nombre;
};

var x = carre(4);
```

Les expressions de fonction permettent :
- de pouvoir être envoyé en paramètre d'une autre fonction.

Pour parcourir des arguments d'une fonction, on peut utiliser l'objet `arguments` :
```js
// arguments[i] : récupére l'argument numéro i
// arguments.length : récupére le nombre d'arguments
function monConcat(séparateur) {
   var result = ""; // on initialise la liste
   var i;
   // on parcourt les arguments
   for (i = 1; i < arguments.length; i++) {
      result += arguments[i] + séparateur;
   }
   return result;
}

// renverra "rouge, orange, bleu, "
monConcat(", ", "red", "orange", "blue");

// Les aparmètres du reste
function multiplier(facteur, ...lesArgs) {
  return lesArgs.map(x => facteur * x);
}
let arr = multiplier(2, 1, 2, 3);
console.log(arr); // [2, 4, 6]
```

Valeurs pas défaut pour les fonctions :
```js
// Navigateurs récents
function multiplier(a, b = 1) {
  return a*b;
}
// Avant ECMAScript 2015 :
function multiplier(a, b) {
  b = typeof b !== 'undefined' ? b : 1; // Argument par défaut de b : 1
  return a*b;
}
```

Les fonctions fléchées : elle permettent une syntaxe plus concise.  
Elle ne possède pas de valeur propre pour :
- `this`
- `arguments`
- `super`
- `new.target`

```js
var a = [
  "Hydrogen",
  "Helium",
  "Lithium",
  "Beryllium"
];
// Fonction classique
var a2 = a.map(function(s){ return s.length }); // = [8, 6, 7, 9]
// Fonction fléchée
var a3 = a.map( s => s.length ); // = [8, 6, 7, 9]
```

Exemple de problèmes avec les `this` dans les fonctions classique :

```js
// Fonction classique avec le problème de "this" multiple
function Personne() {
  // Le constructeur Personne() utilise 'this' comme lui-même
  this.age = 0;
  
  setInterval(function grandir() {
    // En mode non-strict, la fonction grandir() définit `this`
    // avec l'objet global, qui est donc différent du `this`
    // défini par le constructeur Person().
    this.age++; // "this.age" ne référence pas Personne.age
  }, 1000);
}

// Fonction classique avec in fix pour le "this" multiple
function Personn() {
  var self = this; // Certain utilise "that" ou "selg"
  self.age = 0;
  
  setInterval(function grandir() {
    self.age++; // Référence Personne.age
  }, 1000);
}

// Fonction anonyme
personne = function() {
  var self = this; // Certain utilise "that" ou "selg"
  self.age = 0;
  
  setInterval(function grandir() {
    self.age++; // Référence Personne.age
  }, 1000);
}

// Fonction fléché
function Personne() {
  this.age = 0;
  
  setInterval(() => {
    this.age++; // Référence à Personne.age
}
```

### Classique

```js
function (argument) {
    ...
    return 0;
}
```

### Fonction anonyme

```js
var fonctionAnonyme = function (a, b) {
    ...
}

fonctionAnonyme(10, 20)
```

https://www.pierre-giraud.com/javascript-apprendre-coder-cours/fonction-anonyme-auto-invoquee-recursive/

- Premières versions de JS :

```js
// Affectation d'une fonction anonyme à la variable maVariable
const maVariable = function(param1, param2, ...) {
  // Instructions pouvant utiliser param1, param2, ...
}

// Appel de la fonction anonyme
// param1 reçoit la valeur de arg1, param2 la valeur de arg2, ...
maVariable(arg1, arg2, ...);
```

- Dernières versions JS :

```js
// Affectation d'une fonction anonyme à la variable maVariable
const maVariable = (param1, param2, ...) => {
  // Instructions pouvant utiliser param1, param2, ...
}

// Appel de la fonction anonyme
// param1 reçoit la valeur de arg1, param2 la valeur de arg2, ...
maVariable(arg1, arg2, ...);
```

### Les objets

Respecter le principe **SOLID** :
- Single responsabilité
Une seul résponsabilité par classe (par exemple pas de traitement et d'affichage)
- Open Close
Fermé à la modification mais ouvert à l'extensions, si on veut ajouter une fonctionnalité on utilise l'heritage pour modifier une classe.
- Liskov substition principe
- Interface segragation principe
Quand paramètre de méthode, pas de mettre de classe concraite mais utiliser des interface ou classes abstraite, pour pouvoir changer de classe sans réécrire.
- Dependency inversion principle

Les classes n'existe pas de base en JS, ce sera transpiller en prototypes.  
Un prototype, similaire à une classe, est déjà une classe : lors de la création d'un objet, on copie l'objet de notre classe.  
On peut également modifier la classe à tout moment, notamment pendant l'execution.

Plusieurs choses importantes à se rappeler du JS par rapport à d'autres langages :
1. Tout est objet, notamment le prototype ou une classe
2. Tous les prototypes et les sucres de classe peuvent être modifié à tout moment
3. Bonus: tout est publique en JS, du moins pour l'instant.

```js
// Création d'objets manuellement
let monObjet = {
  nom: "toto",
  age: 2,
  estVrai: false
};

console.log(monObjet.nom);

let objetVide = {};
```

```js
class User 
{
  #namePrivate; // Attribut privé, pas encore implémenté par tous les navigateurs

    constructor() { // Constructeur
        this.#namePrivate = "toto"; // Utilisation d'attribut privé
        this.name = "toto" // On créer et initialise l'attribut publique
    }

    getName() { // Methode
        return this.name;
    }
}

const User2 = function()
{
    this.name = "toto";

    this.getName = () => { // Duplication de cet methode pour chaque objet
        return this.name;
    }// Pour ce faire, il faut le déclarer dans le prototype pour éviter de répéter
}

User2.prototype.getName = () => {
    return this.name;
}

const User3 = function()
{
    this.name = "toto";
}

let u1 = new User();
let u2 = new User2();
let u3 = new User3();

console.log(u1.getName());
console.log(u2.getName());

// On peut modifier un prototype à tout moment
User2.prototype.getName = null

console.log(u1, u2, u3);

let a = [];
a.push("toto");
console.log(a);

// On peut également supprimer des methodes du langage JS.
// Il faut faire attention à la porté de nos modifications
// autorisé par le système de prototype du langage.
Array.prototype.push = function(item) {
    console.log("NON " + item);
};

a.push("titi");
console.log(a);

```

```js
let maVoiture = new Object();
maVoiture.fabricant = "Ford"; // ou maVoiture["fabricant"]
maVoiture.modele = "Mustang";
maVoiture.annee = 1969;
// ou
let maVoiture = {
  make: 'Ford',
  model: 'Mustang',
  year: 1969
};

// Constructeur
function Voiture(fabricant, modele, annee) {
  this.fabricant = fabricant;
  this.modele = modele;
  this.annee = annee;
};
let maVoiture = new Voiture("Ford", "Mustang", 1969);
```

#### Duplication
```js
let source = {
  name: "toto"
}
let destination = {}

Object.asign(destination, source)
```
### Desctructuration d'objets

```js
let object = {
  firstName: "Axel",
  lastName: "Toto",
  age: 46,
  favorite_food: "Tacos"
};

let destructure = {};

({
	age: destructure.info1,
	firstName: destructure.info2,
	favorite_food: destructure.info3
} = object);

console.log(destructure);
/**
destructure : {
	destructure.info1 = 46,		// age
	destructure.info2 = "Axel", // firstName
	destructure.info3 = "Tacos" // favorite_food
}
*/

let destructure2 = {};
({
	firstName: destructure2.name,
	... destructure2.all_other_informations
} = object);

console.log(destructure2);
/**
destructure2 : {
	destructure.name = "Axel", // firstName
	destructure.all_other_informations = [
    	lastName: "Toto",
        age: 46,
        favorite_food: "Tacos"
    ]
}
*/
```

Le spread : `...`
Permet de préciser que nous prenoms tous les prochains paramètres d'une fonction ou d'une destructuration.
```js
function addition(numberA, ...allOtherNumbers)
{
	let result = numberA;
    allOtherNumbers.forEach((number) => {
    	result += number;
    });
    return result;
}
```

### Les promesses (déprécié, voir fonction asynchrone)

Fonction qui s'exécute qui promet de renvoyer une réponse. Cette réponse peut être validée ou erronnée. L'avantage des promesses, c'est qu'elle sont asynchronne, c'est à dire qu'elle est executer en parallèle du reste du code, ne bloquant pas ce code.

Les promesses représente la bonne réalisation ou l'échec d'une opération asynchrone.  
On attache des actions, dites ***callbacks***, à la suite, une fois une promesses terminée.

```js
// On créer notre promesse
// Notre promesse
let isMajor = (age) =>
{
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (age >= 18) {
                resolve();
            } else {
                reject();
            }
        }, 5000);
    });
}
// Fonction exécuté si la promesse est fonctionnelle
let resolvedPromise = () => {
    console.log("Vous êtes majeur !");
}

// Fonction exécuté si la promesse renvoie une erreur
let rejectedPromise = () => {
    console.error("Vous êtes mineur !");
}

isMajor(24)
// Si la promesse est valide
.then((resolve) => {
    resolvedPromise();
})
// Sinon si la promesse a une erreur
.catch((reject) => {
    rejectedPromise();
})

isMajor(16)
// Si la promesse est valide
.then((resolve) => {
    resolvedPromise();
})
// Sinon si la promesse a une erreur
.catch((reject) => {
    rejectedPromise();
})

console.log("Ce texte s'affichera avant les promesses.");
```

```js
FaireQuelqueChose() {
  return new Promise((successCalback, failureCallback) => {
    console.log("C'est fait");
    // réussir une fois sur deux
    if (Math.random() > .5) {
      successCallback("Réussite");
    } else {
      failureCallback("Échec");
    }
  })
}

FaireQuelqueChoise().then(result => {
  return faireAutreChose(result);
})
.then(newResult => {
  return faireEncoreAutreChose(newResult);
})
.then(finalResult => {
  return console.log('Résultat final : ' + finalResult);
})
.catch(failureCallback);
// ==
FaireQuelqueChoise()
  .then(result => faireAutreChose(result))
  .then(newResult => faireEncoreAutreChose(newResult) )
  .then(finalResult => {
  	console.log('Résultat final : ' + finalResult);
  })
  .catch(failureCallback);
```

### Fonction asynchrone

```js
// Fonction asynchrone
// let isMajor2 = async function(age) ...
async function isMajor2(age)
{
    // On est obliger d'utiliser "await" dans une fonction asynchrone
    let result = await new Promise((resolve, reject) => {
        setTimeout(() => {
            if (age >= 18) {
                resolve();
            } else {
                reject();
            }
        }, 5000);
    });

    return result;
}
// Fonction exécuté si la promesse est fonctionnelle
let resolvedPromise = () => {
    console.log("Vous êtes majeur !");
}

// Fonction exécuté si la promesse renvoie une erreur
let rejectedPromise = () => {
    console.error("Vous êtes mineur !");
}

isMajor2(24)
// Si la promesse est valide
.then((resolve) => {
    resolvedPromise();
})
// Sinon si la promesse a une erreur
.catch((reject) => {
    rejectedPromise();
})

isMajor2(16)
// Si la promesse est valide
.then((resolve) => {
    resolvedPromise();
})
// Sinon si la promesse a une erreur
.catch((reject) => {
    rejectedPromise();
})
console.log("Ce texte s'affichera avant les promesses.");
```

### Gestion des taches

Le Javascript s'execute sur un seul tread du processeur. Pour mettre en place les taches asynchrones, il existe donc 2 files d'attentes :

1. **La micro-tache**, qui est prioritaire.
2. **La macro-tache**, qui est secondaire.

L'ensemble des instructions sont executé soit dans la premiére, soit dans la deuxième file d'attente.
Lorsqu'il y a des taches dans la micro-tache, JS execute toutes les taches avant d'éxecuter les macro-taches.

Par exemple dans la file d'attente micro-tache, on a :

- process.nextTick()
- Promise
- Async
- queueMicrotask

Par exemple dans les macro-taches :

- setTimeout()
- setInterval()
- setImmediate()

### Modules

1. Ajouter l'attribut type="module" au fichier JS qui va utiliser les modules

```html
<!-- les modules ont automatiquement l'attribut "defer" -->
<script src="assets/app.js" type="module"></script>
```

2. On défini les éléments JS qui seront exportés dans les futures fichiers importés.

```js
export class Employee {
  //...
};

// ou
class maClass {}
let maVariable
function maFonction() {}

export { maClass, maVariable, maFonction }
```

3. On défini les imports des différents modules, à la première ligne du fichier.  

Le chemin est relatif au fichier qui importe le module.

```js
import { EmployeeApi } from "./modules/EmployeeApi.js";
```

### Choses utiles

```js
setTimeout(maFonction, 5000); // Attendre 5 secondes avant d'executer la fonction
```

### Prototypes

<https://www.youtube.com/watch?v=ECuaZxM82fw> (35:00)

## DOM

Lorsque page charge la page, il créait le DOM de la page. JS permet de manipuler le DOM (modifier, ajouter et supprimer les élament de la page).

### Inserer script JS dans HTML

Ajouter un fichier JS :

```html
<html lang="fr">
    <head>
        <!-- Inclusion du fichier JS -->
        <script src="assets/main.js" defer></script>
        <!-- "defer" permet d'attendre que le DOM soit construit avant de charger le fichier JS-->
    </head>
</head>
```

### Selection d'éléments

On choisi les constantes pour sélectionner les éléments du DOM.

Accéder aux éléments du DOM :

```js
// Accés directe
const elementHTML = document.documentRoute; // <html>
// Selecteurs individuels
const elementID = document.getElementById('logo'); // Balise avec le paramètre "id=logo"
const selectionnerElementCSS = document.querySelector('#logo'); // Même selecteurs qu'en CSS
// Selecteurs multiples
const selectionnerPlusieursElementsCSS = document.querySelectorAll('#logo'); // Plusieurs éléments avec régle CSS
// Non recommandé, utiliser plutôt le querySelectorAll()
const selectionnerBalises = document.getElementsByTagName('a'); // Selectionne les éléments par leur balises
const selectionnerClass = document.getElementsByClassName('a'); // Selectionne les éléments par leur balises
elementHTML.remove(); // Supprime l'élément lui même
linkPara.parentNode.removeChild(linkPara); // Même resultat que ligne du dessus
```

Afficher des données dans la console :

```js
console.log("Hello World!");
console.error('IL y a une erreure');
```

```js
const element = document.getElementById('identifiant');

// Modifier la couleur d'un element
// Il vaut mieux utiliser le CSS pour appliquer du théme car accéleration par GPU
// Donc meilleures performances
element.style.color = 'red';
element.style.fontSize = '200px';
```

### Variables du DOM

| Nom de la variable | Représente
|---|---
| `Window` | Fenêtre du navigateur, avec notamment la taille de la fenêtre.
| `Navigator` | Le navigateur, avec notamment le materiel de la machine (GPS, flux vidéo...).
| `document` | La page, notamment le DOM.

### Balises DOM utiles

```js
element.textContent = "Texte"; // Interargir avec le contenu de la balise
element.innerText = "Texte"; // Interargir avec le contenu de la balise, déprécié
element.innerHTML = "Texte"; // Interargir avec le contenu en HTML de la balise, déprécié
elementLink.href = "https://test.com"; // Changer l'URL d'un lien
document.createTextNode("Texte à ajouter"); // Créer un node pour du texte à ajouter.
element.setAttribute('attribut', 'valeur');
element.setAttribute('class', 'hightlight');
window.innerWidth; // largeur de la fenêtre
window.innerHeight; // Hauteur de la fenêtre
element.dataset.monAttributSpe = "valeur";
```

### Placer des élements

```js
let element = document.createElement("p"); // On créer une balise <p>
element.appendChild(secondElements); // Ajouter "secondElements" en tant qu'enfant de "element"
element.removeChild(secondElements); // Supprime "secondElements" du parent "element"
element.remove(); // Supprime "element"
secondElements = node.cloneNode(element); // Clone "element" dans "secondElements"
```

### Evenements

```js
const btn = document.querySelector('button');
// On ajouter un évenement lors du click qui exécutera la fonciton nomFonctionAExecuter
btn.addEventListener('click', nomFonctionAExecuter);
// On retire l'évenement
btn.removeEventListener('click', nomFonctionAExecuter);
```

Récupérer l'objet événement à travers `event`, `evt` ou `e` :

```js
function nomFonctionAExecuter(event) {
  console.log("Hello World!");
  e.target.style.backgroundColor = black; // On change la couleur de l'élément éxécutant cet fonction
}
```

Supprimer l'événement par défaut :

```js
const formulaire = document.getElementById('superForm');

formulaire.addEventListener('submit', (event) => {
  e.preventDefault();
});
```

Liste des événements disponibles : [MDN Event reference](https://developer.mozilla.org/en-US/docs/Web/Events)

### Fetch

Fonction asynchrone. Pour les requetes distantes, il faut obligatoirement que le site soit chiffré (en HTTPs). 

```js
// Pour le fetch, on peut définir un accés local ou distant
fetch("https://api.devoldere.net/dataset/users.json")
// Le role du prochain then sera de formater la requete, en JSON, binaire, etc
.then(response => {
    console.log(response);
    return response.json();
})
// On récupére le JSON dans le paramètre "json"
.then(json => {
    console.log(json);
})
// On affiche l'erreur en cas d'échec
.catch(error => {
    console.error(error);
})
```

### Mode strict

Le mode strict permet de n'activer qu'une version plus récente de Javascript.  
Il n'est compatible qu'avec les navigateurs récents, et doit être activer manuellement.  
Il permet entre autre :

- Il transforme certaines erreurs silencieuses en erreurs explicites.
- Le code est plus rapide grace à l'activation de certaines optimisations.
- Il interdit des mot-clés susceptibles d'être utilisé pour les prochaines versions de ECMAScript.

On peut l'activer soit pour le script en entier ou pour des fonctions spécifiques.

```js
// A mettre avant toutes lignes de JS
"use strict";

function strict() {
  "use strict";
  console.log("Fonction en mode strict");
}
```

L'activation permets plus précisement :

- d'interdir la création de variables globales
- l'affectation d'une variable à "NaN" générera une erreur
- également une erreur pour toute affectation qui échoue
- génére également une erreur lors de la suppression de propriété non supprimable
- les nom des arguments doivent être tous différents
- pas de syntaxe pour les nombres de type octale
- interdiction du mot clé "with"
- "eval" ne créer pas de variable dépassant la porté de l'"eval"

Plus d'informations sur [MDM Strict mode](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Strict_mode)

## Conventions

- <https://standardjs.com/>

## Astuces

### Drapeaux Emoji à partir du code ISO du pays (2 lettres du pays)

```js
function isoToEmoji (code) {
  return code
    .split('') // Convertir code en tableau de lettre
    .map(letter => letter.charCodeAt(0) % 32 + 0x1F1E5) // Position de chaque lettre dans UTF8; % 32 pour avoir la lettre A (min ou maj) = 1, B = 2, etc; 0x1F1E5 pour avoir la position de la lettre en version Unicode
    .map(n => String.fromCodePoint(n) // Conversion de la position unicode en carctère unicode, qui génére un emoji de la lettre
    .join('') // On ajoute les lettres unicode pour obtenir le pays en emoji
}

console.log(
  isoToEmoji('fr'),
  isoToEmoji('be'),
  isoToEmoji('ca'),
  isoToEmoji('us'),
)
```

## Ressources

- [MDN Guide JavaScript](https://developer.mozilla.org/fr/docs/Web/JavaScript/Guide)
- [MDN Manipuler des documents](https://developer.mozilla.org/fr/docs/Learn/JavaScript/Client-side_web_APIs/Manipulating_documents)
- [MDN Principaux blocs en JS](https://developer.mozilla.org/fr/docs/Learn/JavaScript/Building_blocks)
- [MDN Chaines de caractère](https://developer.mozilla.org/fr/docs/Web/JavaScript/Guide/Text_formatting#les_litt.c3.a9raux_de_cha.c3.aenes_de_caract.c3.a8res)
- [MDM Le modèle objet](https://developer.mozilla.org/fr/docs/Web/JavaScript/Guide/Details_of_the_Object_Model#la_cr.c3.a9ation_de_la_hi.c3.a9rarchie)
- [MDM Utiliser mes promesses](https://developer.mozilla.org/fr/docs/Web/JavaScript/Guide/Using_promises)
- [MDM Itérateurs et générateurs](https://developer.mozilla.org/fr/docs/Web/JavaScript/Guide/Iterators_and_Generators)
- [Comment utiliser l'API Fetch de JavaScript pour récupérer des données](https://www.digitalocean.com/community/tutorials/how-to-use-the-javascript-fetch-api-to-get-data-fr)

### Documentation

- <https://developer.mozilla.org/fr/docs/Web>
- <https://devdocs.io/javascript/>

### Cours vidéos

- <https://www.grafikart.fr/formations/debuter-javascript>

### Exercices

- [Générateur d'histoires absurdes](https://developer.mozilla.org/fr/docs/Learn/JavaScript/First_steps/Silly_story_generator)  
Leçon associée : [Premiers pas en JavaScript](https://developer.mozilla.org/fr/docs/Learn/JavaScript/First_steps)

- [Test your skills: Events](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Test_your_skills:_Events)  
Leçon associée : [Introduction to events](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events#test_your_skills!)
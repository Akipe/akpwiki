---
title: JavaScript
description: 
published: true
date: 2024-03-04T12:26:06.796Z
tags: 
editor: markdown
dateCreated: 2024-03-04T12:26:06.796Z
---

# JavaScript

## Ressources
> Documentation :
- https://developer.mozilla.org/fr/docs/Web
- https://devdocs.io/javascript/

> Cours vidéos
- https://www.grafikart.fr/formations/debuter-javascript

## Variable

> Déclaration
```
var maVariable = 1;
let maSecondeVariable = 2;
```

> Array
```
let monArray = ['lol', 10, uneFonction()]
monArray[0]
```

> String
```
let maPhrase = 'Voici ma phrase';
console.log(`Contenu de la phrase : ${maPhrase}, c'est cool nan ? :)`);
```

> Float
Langage de précision flotant ! > `0.1 + 0.2 = 0.300000004`

> Concaténation : `console.log('Ma phrase est ' + 'super cool !');`

> Variable "complexe" : objet
```
var eleve = {
    nom: 'Jean,
    moyenne: 15
}
eleve.nom
eleve.moyenne
```

> Variable par défaut ou indéfini : ```erreurVar == undefined```

> Chaque variables disposent de méthodes, comme des objets
```
let phraseEnMajuscule = "Une super phrase".toUpperCase();
```

## Portés

> `var`
```
for (var i = 0; i w 3; i++) {
    var d = 'Je sais pas quoi';
}

console.log(d); // Affiche Je sais pas quoi, PAS de scop dans un block
```
- Accessible en dehors du block.


## Logique

### Condition
```
if (condition) {
    ...
} else if (condition) {
    ...
} else {
    ...
}
```

### Boucles
```
while (condition) {
    ...
}
```
```
do {
    ...
} while (condition);
```
```
for (initialise; condition; exec à chaque boucle) {
    ...
}
for (iterator = 0; iterator < tableau.length; iterator++) {
    ...
}
```

## Fonctions

### Classique
```
function (argument) {
    ...
    return 0;
}
```

### Fonction anonyme
```
var fonctionAnonyme = function (a, b) {
    ...
}

fonctionAnonyme(10, 20)
```

https://www.pierre-giraud.com/javascript-apprendre-coder-cours/fonction-anonyme-auto-invoquee-recursive/
- Premières versions de JS :
```
// Affectation d'une fonction anonyme à la variable maVariable
const maVariable = function(param1, param2, ...) {
  // Instructions pouvant utiliser param1, param2, ...
}

// Appel de la fonction anonyme
// param1 reçoit la valeur de arg1, param2 la valeur de arg2, ...
maVariable(arg1, arg2, ...);
```
- Dernières versions JS :
```
// Affectation d'une fonction anonyme à la variable maVariable
const maVariable = (param1, param2, ...) => {
  // Instructions pouvant utiliser param1, param2, ...
}

// Appel de la fonction anonyme
// param1 reçoit la valeur de arg1, param2 la valeur de arg2, ...
maVariable(arg1, arg2, ...);
```

### Prototypes


https://www.youtube.com/watch?v=ECuaZxM82fw        35:00
---
title: Vue.js
description: 
published: true
date: 2024-05-21T14:54:56.913Z
tags: 
editor: markdown
dateCreated: 2024-05-21T14:54:56.913Z
---

# Vue.js

## Informations

Vue.js est un framework frontend, que l'ont peu utiliser pour développer une partie de notre application ou pour son entiereté.

Version de Vue.js présenté sur cette page est la version 3.

- SPA : Single Page Application
- SFC : Single-File Components, tout le code est contenue dans un seul fichier (recommandé avec l'I de composition)

### Choix du style de l'API

On peut utiliser Vue.js de deux manières :
1. Avec l'API d'options (la manière la plus accessible)
2. Avec l'API de composition (la manière la plus "intéréssante" pour Vue.js)

#### Option API

```js
<script>
export default {
  data() {
    return {
      count: 0
    }
  },
  methods: {
    increment() {
      this.count++
    }
  },
  mounted() {
    console.log(`The initial count is ${this.count}.`)
  }
}
</script>

<template>
  <button @click="increment">Count is: {{ count }}</button>
</template>
```

#### Composition API

```js
<script setup>
import { ref, onMounted } from 'vue'

const count = ref(0)

function increment() {
  count.value++
}

onMounted(() => {
  console.log(`The initial count is ${count.value}.`)
})
</script>

<template>
  <button @click="increment">Count is: {{ count }}</button>
</template>
```

## Environement de développement

### VSCode

Extensions :

- Vetur (Vue.js 2)
- Volar (Vue.js 3)

settings.json :

```json
emmet.includeLanguages: {
    'vue' : 'html',
    'vue-html': 'html'
}
```

## Charger Vue.js

### Simplement

```html
<!-- index.html -->
<html>
    <head>
        <title>Ma page Vue.js</title>
      	<script src="https://unpkg.com/vue@3" defer></script>
    	<script src="./mon_appli_vue.js" defer></script>
    </head>
</html>
```

### Simplement avec support des modules ES6

```html
<html>
<head>
    <title>Ma page Vue.js</title>
  	<!-- Si besoin -->
    <script src="https://unpkg.com/es-module-shims@1/dist/es-module-shims.js" defer></script>
    <!-- importer directement vue -->
    <script type="importmap" defer>
        {
          "imports": {
            "vue": "https://unpkg.com/vue@3/dist/vue.esm-browser.js"
          }
        }
      </script>
    <script src="./mon_appli_vue.js" type="module" defer></script>
</head>
</html>
```

### Bonus : fichiers à charger lors de la mise en production

- remplacer `https://unpkg.com/vue@3` par `https://unpkg.com/browse/vue@3/dist/vue.global.prod.js`
- remplacer `https://unpkg.com/vue@3/dist/vue.esm-browser.js` par `https://unpkg.com/vue@3/dist/vue.esm-browser.prod.js`

## Utilisation de Vue.js

### Initialiser notre code

On doit dans un premier temps définir notre application et ensuite définir un point de montage où s'executera notre application.

On peut monter notre application Vue.js dans la balise `<body>` depuis la version 3.

```html
<!DOCTYPE html>
<html>
<head>
    <title>Demo Vue.js</title>
    <script src="https://unpkg.com/es-module-shims@1/dist/es-module-shims.js" defer></script>
    <script type="importmap" defer>
        {
          "imports": {
            "vue": "https://unpkg.com/vue@3/dist/vue.esm-browser.js"
          }
        }
      </script>
    <script src="./assets/app.js" type="module" defer></script>
</head>
<body>
    <div id="app"> <!-- c'est ici qu'on montera notre application -->
        {{ title }}
    </div>
</body>
</html>
```

```js
import { createApp } from 'vue'

const app = createApp({ // On créer notre application
  data() {
    return {
      title: "Hello World"
  }
})

app.mount('#app') // On le monte sur la balise ayant l'id "#app"
```

### Code logique (Option API)

#### Listes des options

```js
import { createApp } from 'vue'

const app = createApp({

  // Propriétés qui seront accessible dans `this` et seront "reactive state" :
  // c'est à dire que leur mises à jour sera pris en compte dans Vue.js
  data() {
    return {
      uneVariable: 0,
      autreVariable: "toto
  },
  
  // Fonctions avec un état mutable. Elle peuvent être déclenché par des événements
  methods: {
    uneMethode() {
      this.uneVariable++
    }
  },
  
  // Fonction mises à jour automatiquement lors de la mise à jour de notre application
  // Elles sont idéals pour définir des getter
  // Il faut éviter de modifier après coup les valeurs retourné par ces applications
  computed: {
    recupererDesDonneesFiltrer() {
      return autreVariable + " coucou" 
    }
  },
    
  // Fonctions mises à jour lorsque l'un des arguments de la fonction est mise à jour
  // Elles sont idéals comme mutateur / setter
  watch: {
    title(newTitle, oldTitle) {
        console.log(`Le titre ${oldTitle} a changé pour ${newTitle}`)
    }
  }
    
  // Fonctions déclanché lors d'un certain etat de notre application
  // dans ce cas, lorsque l'application est chargé
  mounted() {
    console.log("L'application est chargé")
  }
})
  
app.mount('#app')
```

##### Option `methods`

Permet une meilleurs organisation du code. On peut les executer quand on veut.

```js
import { createApp } from 'vue'

const app = createApp({
    data() {
        return {
            name: "Mike Taylor", // On défini une variable
        }
    },
    methods: { // On défini nos méthodes
        resetName(newName, e) {
        	this.name = newName
        	console.log(e.target.textContent)
    	}
    }
}).mount('#app')
```

```html
<input v-model="name" type="text" /> 
<button @click="resetName('John', $event)" type="text">Effacer</button>
```

##### Option `computed`

Elle sont mises à jour dès qu'il y a un changement dans notre application.

```js
import { createApp } from 'vue'

const app = createApp({
    data() {
        return {
            compteur: 0,
        }
    },
    methods: {
        increment() {
        	this.compteur++
    	}
    },
    computed: {
        getCompteurPairImpaire() {
        	if (compteur % 2 == 0) {
              return "pair"
            } else {
              return "impair"
            }
    	}
    }
}).mount('#app')
```

```html
<button @click="increment">Incrémenté le compeur</button>
<p>Le compteur est un nombre {{ this.getCompteurPairImpaire() }}</p>
```

##### Option `watch`

Méthodes qui s'exécutera à chaque changement d'une variable.

```js
watch: {
    title(newTitle, oldTitle) {
        console.log(`Le titre ${oldTitle} a changé pour ${newTitle}`)
    }
}
```

##### Option déclenché à un certain état de notre application

Ils permettent d'exécuter des actions en fonction de différentes étapes lors de la création de la page par Vue.

Voici une liste de certaines de ces étapdes :
- `beforeCreate`
- `created`
- `beforeMount`
- `mounted`
- `beforeUpdate`
- `updated`
- `beforeDestroy`
- `destroyed`

### Template (HTML)

On ne peut écrire qu'une seul expression par méthode !

#### Ecrire du contenu

- `{{ }}`

Permet d'écrire le contenu d'une variable ou du JS.
```html
<p>Bonjour {{ name }}</p>
<p>Votre nom en majuscule : {{ name.toUpperCase() }}</p>
<p>{{ isValueIsOk ? 'YES' : 'NO' }}</p>
<p>{{ message.split('').reverse().join('') }}</p>
```

- `v-html`

Permet d'écrire le contenu d'une variable en interprétant correctement les balises html.
```html
<p>AFfichage du contenu de la variable : <template v-html="variableAvecBalise"></template></p>
```

Pour définir des attribut :

Si on ne veut pas de mise à jour de variable : `v-once`

```html
<div v-once>
   {{ title }}
</div>
```

On peut définir directives Vue sans utilise de balises HTML avec la balise `<template></template>` :
<p>
  La quantité doit être supérieure à <template v-show="quantity === 0">zéro</template>
</p>

#### Ecrire du javascript dans les attributs

```html
<!-- Ecrire du javascript dans les attributs avec `` -->
<div :id="`list-${id}`"></div>
```

#### Définir des attribut variables

Il faudra définir l'attribut entre deux crochet comme `[attributName]` :
```html
<a v-bind:[attributeName]="url">...</a>
<a :[attributeName]="url">...</a>
```

#### Utiliser les variables dans les attributs

On ne peut pas utiliser l'operateur "moustache" dans les attributs HTML, il faut utiliser les `v-bind:ATTRIBUT` (similaire à `:ATTRIBUT` :

```html
<img v-bind:src="image_url" /> <!-- Va remplacer l'expession "image_url" par sa valeur -->
<!-- ou la forme raccourcie -->
<img :src="image_url" />

<!-- il est possible d'executer des fonctions -->
<img :src="getImageUrl()" />
```

Il est souvent utilisé avec l'attribut `:disabled`

#### Gérer les logiques

##### Conditions

Avec les directives : `v-if`, `v-else-if` et `v-else`

Rend l'élément visible ou invisible selon le retour de l'expression.  
Si l'élément n'est pas visible, il n'est pas rendu dans le HTML.

```html
<div v-if="montant > 100">
    Livraison gratuite!
<div>
<div v-else-if="montant > 50">
    Livraison 9.95$
</div>
<div v-else>
    Livraison 19.95$
</div>
```

##### Boucles

Avec les directives `v-for` et `:key`, `:key` permet de définir l'identifiant qui différencie l'ensemble des éléments.

```html
<ul>
    <li v-for="item in items" :key="item.id">
        {{ item.name }}
    </li>
</ul>
```

#### Les événements

On peut définir directement des événements dans les balises avec les directives `v-on:NOM_EVENEMENT` ou `@NOM_EVENEMENT`.  
Liste des autres événements du DOM : <https://vuejs.org/guide/essentials/event-handling.html>

```html
<button v-on:click="console.log(`Hello`)">Cliquez moi</button>
<!-- Ou en version raccourcie : -->
<button @click="console.log(`Hello`)">Cliquez moi</button>
```

On peut également envoyer l'objet `event` lors de l'execution de notre événement avec `$event` :

```html
<button @click="resetName('John', $event)" type="text">Effacer</button>
```

Quelques événements souvent utilisés :

- input
- click
- change
- keydown

On peut également utilisé l'option `.prevent` pour désactiver l'action par défaut de cet événement :

```html
<form v-on:submit.prevent="saveName()">
    <input v-model="name" type="text" /> 
    <button type="submit">Sauvegarde</button>
</form>
```

#### Les formulaires

On peut relier les valeurs d'un formulaire à des variables JS avec la directive `v-model`.  
La variable changera lorsque le formulaire changera, dans les deux sens.
```html
<input v-model="name" type="text" />
<div>
    Nom : {{ name }}
</div>
```

#### Récupérer une balise facilement

On peut récupérer une balise sans utilise un `getElementById()` ou d'autres methodes du DOM en utilisant la directive `ref="variableContenantNode"` & `this.$refs.variableContenantNode` :

```html
<!-- on défini un champ où l'utilisateur pourra rentrer une valeur -->
<input id="monChamp" type="text" ref="userName">
```
```js
// Ensuite dans notre code JS on pourra accéder au node de ce champ grace à la variable 'userName'
handleClick() {
  console.log(this.$refs.userName)
  // est égale à
  console.log(document.getElementById("monChamp"))
}
```

### Vue avec TypeScript

```bash
npm init vue@latest # choisir TypeScript
cd NOM_PROJET
npm install
npm run dev
```

Ensuite, ne garder que les fichiers à la racine, et les fichiers suivants :

/public
/src
	|-main.ts
    
Et également modifier :

```ts
// vite.config.ts
import { fileURLToPath, URL } from 'url'

import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [vue()],
  build: {
    sourcemap: true, // Pour le débug dans VSCode
  },
  resolve: {
    alias: {
      '@': fileURLToPath(new URL('./src', import.meta.url)),
      vue: 'vue/dist/vue.esm-bundler.js', // Pour autoriser l'utilisation de l'API d'options
    }
  }
})

```

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" href="/favicon.ico" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Vite App</title>
    <link rel="stylesheet" href="style.css"> <!-- on charge notre css -->
    <script type="module" src="/src/main.ts"></script><!-- pas besoin de le mettre à la fin de la page -->
  </head>
  <body>
    <div id="app">
      <h1>{{ message }}</h1>
    </div>
  </body>
</html>

```

```css
/* public/style.css */
body {
  background-color: black;
  color: white;
}
```

```ts
// src/main.ts
import { createApp } from 'vue'
import App from './app'

createApp(App).mount('#app')
```

```ts
// src/app.ts
import { defineComponent } from 'vue'

export default defineComponent({
  data() {
      return  {
          message: "test"
      }
  },
  mounted() {
      console.log("test")
  }
})

```

### Divers

## Les composants

Vue.js utilise le paradigme de **composants**, c'est à dire chacune des parties de l'application doit être répartie en composants et sous composants, qui pourrait être rappelé ou même utilisé dans d'autres applications.  
Par exemple une barre de navigation pourrait être un sous composant d'un composant NavBar, qui pourra être réutilisé sur plusieurs pages.

```js
import { createApp } from 'vue';

const app = createApp({
    data() {
        return {
            message: 'Un message'
        }
    },
    methods: {
        deleteUser(userID) {
            console.log(`User ${userID} deleted`)
        }
    }
})

app.component('nav-bar', {
    template: `
        <div>
            {{ title }}
            ...navigation bar code...
        </div>
    `,
    props: {
        title: {
            type: String,
            required: true,
            default: 'Mon application'
        }
    },
    methods: {
        sendDelete() {
            const userId = 10;
            this.$emit('delete', userId);
        }
    }
})

app.mount('#app');

```
```html
<div id="app">
  <div>
    <nav-bar title="Mon application" v-on:delete="deleteUser($event)" />
  </div>
</div>
```

## Commandes

### Lint
npm run lint

### Démarrer en mode développement
npm run dev

## Ressources

- [https://dev.to/ericlecodeur/apprendre-vue-js-3-jour-1-concepts-de-base-2jfn](https://dev.to/ericlecodeur/apprendre-vue-js-3-jour-1-concepts-de-base-2jfn)
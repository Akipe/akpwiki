---
title: Android
description: 
published: true
date: 2024-05-21T16:44:08.618Z
tags: 
editor: markdown
dateCreated: 2024-05-21T16:44:08.618Z
---

# Android

On utilisera un langage natif d'Android.

Il faut se poser la question de quel seront les utilisateurs qui utiliseront l'application.

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-11/scaled-1680-/i3JsPldOZF4SENvJ-image-1667819559333.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-11/i3JsPldOZF4SENvJ-image-1667819559333.png)

En fonction des API, on est pas sûr que l'application sera compatible avec les versions d'API précédante et suivante.

## Ressources apprentissage

### Kotlin

- Créer votre première application Android : <https://developer.android.com/training/basics/firstapp?hl=fr>
- Atelier de programmation : <https://developer.android.com/training/basics/firstapp?hl=fr>
- Cours sur les principes de base d'Android : <https://developer.android.com/courses/android-basics-compose/course?hl=fr>

### Java

- Principes de base du développement Android : <https://developer.android.com/courses/fundamentals-training/overview-v2?hl=fr>
- Tuto Permière application android en Java : 
<https://developer.android.com/codelabs/build-your-first-android-app#0>
- Tuto Open Classroom en Java (20h) :
<https://openclassrooms.com/fr/courses/4517166-developpez-votre-premiere-application-android>
- <https://profgra.org/lycee/activite_Android_activities.html>

## SDK

- machine virtuelle + tous les outils pour compiler

## Machine virtuelle

Pour tester l'application.

## Connaitre les différentes versions des API

<https://apilevels.com/>

## Arboréscence d'un projet

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-11/scaled-1680-/dQUNHP4Oe0U7pWKl-image-1667895710440.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-11/dQUNHP4Oe0U7pWKl-image-1667895710440.png)

Principaux répertoires :

- manifests
- java
- res
- AndroidManifest.xml : fichier description, notamment API 
- classes.dex  : conteint bytecode
- META-INF
- ressource.ap_ contient ressources compilées

### Répertoire `manifests`

Il ne contient généralement que `AndroidManifests.xml`, qu'on peut comparer à la carte d'identité.

Exemple de fichier :

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.TopQuiz"
        tools:targetApi="31">
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>

            <meta-data
                android:name="android.app.lib_name"
                android:value="" />
        </activity>
    </application>

</manifest>
```

```xml
android:label="@string/app_name" <!-- Texte défini dans res -->
```

**Manifest** contient :

- package : nom du package ou se trouve l'activité principale
- versionCode : cersion du code de l'appli non visible pour l'utilisateur
- versionName : donne la version de l'application visible sur Google Play

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-11/scaled-1680-/HyXugMVA56CcIBnY-image-1667822076332.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-11/HyXugMVA56CcIBnY-image-1667822076332.png)

### Répertoire `java`

Il contient le code source Java (ou kotlin) du projet.

### Répertoire `res`

Contient toutes les ressources de l'application, avec 4 sous dossiers :

- `drawable`: contient les images et contenus à afficher *(image de bouton, icones, logo...).
- `layout`: contient les fichiers de mises en page.
- `mipmap`: principalement l'icone de lancement de l'application.
- `values`: contient les paramètres et valeurs *(code couleur de variables, traduction de texte, style graphique à utiliser...)*

- drawable-xxx : image, en fonction résolution (*xxx*). Dossier `drawable` est le pardéfaut.
- ic_launcher.png : icone de l'application
- layout-xxx : Inteface graphique en XML. `layout` par défaut, `layout-land` format paysage, `layout-land-large`, `layout-port`  format portrait, `layout-small` (petit écran)
- activity_main.xml : fichier principal de votre interface
- values : contient l'ensemble des fichiers comprenant les valeurs : string.xml, dimens.xml...
	- strings.xml : contient l'ensemble des chaines de caractères pour la traduction
    - dimens.xml : contient les dimensions utilisé par l'appli
    - styles.xml : contient le design de l'appli

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-11/scaled-1680-/eU1S5LOtf42Aiumx-image-1667821339116.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-11/eU1S5LOtf42Aiumx-image-1667821339116.png)

### Ressources  **Assets**

Pas traité par les outils package d'Android

Copié sans transformation.

Non répertorier par la classe R

La lecture se fait à parfir de l'objet **AssetManager** : getAssets()

## Interface graphique

### Activité

Appelé **Activity**, c'est une classe Java ou Kotlin qui à pour role d'interagir avec l'utilisateur. Elle hérite de la classe **Android Activity** ou **AppCompatActivity**.

Une activité contient :

- une classe Java ou Kotlin (controlleur)
- un layout en xml (vue)

> AppComptatActivity permet de fixer le problème d'heritage de fonctionnalités récentes sur des ancien systèmes Android.

En générale, vous aurez une activité par écran dans votre application.

Les activité doivent être suffixé par *Activity* et écrit en __CamelCase__.

> *Exemple : Un écran de connexion et un écran de tutoriel donnera une activité **LoginActivity** et **TutorialActivity**.

### Elements graphiques

Les *éléments graphiques* (widgets ou éléments de controle) permettent d'intéragir avec l'utilisateur.

Il peuvent être:

- des boutons
- des zones de saisie
- menus déroulants
- ...

On écrit ces éléments dans les fichiers ***layout***.

### Fragment

Comme les User Control un Winform.

### Layout

Les layouts sont défini dans un fichier `layout`, dans le répertoire `res/layout` et sont écrit en format **xml**.

Par convention, on les suffixes par ***Activity*** s'ils sont lié à une activité, et on utilise la nomation __snake_case__.

> *Par exemple le layout associé à `MainActivity` se nomme `acitivity_main.xml` et le layout de `LoginActivity` se nomme `activity_login.xml`. 

*Exemple de Layout* :

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- Element suivent est un conteneur -->
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity"> <!-- fin conteneur -->

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

#### Conteneurs

Il est nécessaire d'utiliser un conteneur pour afficher les éléments à l'écran.

Dans l'exemple précédent, le conteneur s'appelle `<androidx.constraintlayout.widget.ConstraintLayout`

Dans ce cas, c'est un conteneur de type `ConstraintLayout`.

Voici une liste de type de conteneurs :

- **FrameLayout** : élément les uns au dessus des autres.
- **LinearLayout** : éléments les un à la suite des autres, verticalement ou horizontalement.
- **RelativeLayout** : éléments positioné les uns par rapport aux autres.
- **ConstraintLayout** : comme le **RelativeLayout**, mais avec des règles de positionnement plus puissantes.

#### Attributs

- `android:layout_width`
- `android:layout_height`

Valeurs :

- `match_parent` : élément doit s'étendre le plus possible (remplace `fill_parent`).
- `wrap_content` : élément doit s'étendre le moins possible (n'occupe que la place nécessaire).
- `0dp` : taille de l'élément est défini par ses contraintes.
- `layout_gravity` : positionnement de l'élément.
- `gravity` : positionnement du contenu dans l'élément.

Valeurs:

- `left` ou `start`
- `right` ou `end`
- `center`
- `center_vertical`
- `center_horizontal`
- `android:text` : Contenu en texte
- `android:layout_margin` : marge 
- `android:layout_marginTop` : marge haut
- `android:layout_marginBottom` : marge bas
- `android:layout_marginStart` : marge gauche
- `android:layout_marginEnd` : marge droite
- `android:layout_padding` : padding (ou rembourrage en français) pour ajouter du contenu entre le contenu de l'élément et les bords de l'élément.
- `android:padding`

#### Mesures

- `dp`: density-independant pixels, permet de s'affranchir des différentes résolutions des appareils.
	- il est conseillé d'utiliser des multiples de 4 (4dp, 8dp, 16dp...)

#### Elements de controles

##### Zone de saisie

Balise : `EditText`

```xml
<EditText
   android:layout_width="match_parent"
   android:layout_height="wrap_content"
   android:layout_marginStart="16dp"
   android:layout_marginEnd="16dp"
   android:hint="Please type your name" />
```

Attribut :

- `android:hint`: Texte descriptif du champ.

##### Bouton

Balise `Button`.

```xml
<Button
   android:layout_width="wrap_content"
   android:layout_height="wrap_content"
   android:layout_gravity="center_horizontal"
   android:layout_margin="16dp"
   android:text="Let's play" />
```

##### Afficher du texte

Balise `TextView`.

```xml
<TextView
   android:layout_width="wrap_content"
   android:layout_height="wrap_content"
   android:layout_margin="16dp"
   android:padding="8dp"
   android:text="Welcome! What's your name?" />
```

## String

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-11/scaled-1680-/jW3HMSYvpUMNjBhK-image-1667991930141.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-11/jW3HMSYvpUMNjBhK-image-1667991930141.png)

## Code Java

### R.java

Ressence toutes les ressources. Il est auto généré.

### Activité

Chaque activité à sa vie indépendante, le téléphone passe son temps à écouter les demandes d'intentions sur le téléphone.

- trouver le layout : `R.layout.new_magazine` & `setContentView(R.layout.new_magazine)`
- trouver les composants visuels : `R.id.magazine_name` et `findViewById(R.id.magazine_name)`
- charger du texte en fonction de la langue : `R.string.commentRemove` & `remover.setText(R.string.commentRemov)e`
- charger de l'image : `R.drawable.kandinsky` & `image.setImageResource(R.drawable.kandinsky)`

```xml
<!-- dans AndroidManifest.xml -->
<manifest>
    <application>
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter> <!-- chaque activité à sa vie indépendante, le téléphone passe son temps à écouter les demandes d'intentions sur le téléphone -->
                <!-- toutes les activités sont à l'écoute, mais je doit définir sous quels conditions j'éxécute cette activité -->
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>

            <meta-data
                android:name="android.app.lib_name"
                android:value="" />
        </activity>
    </application>
</manifest>
```

```java
package com.akipe.topquiz;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState /* ce bundle contient toutes les sauvegardes des instances */) { // Appelé lors de la création de la vue
        super.onCreate(savedInstanceState); // ???
        setContentView(R.layout.activity_main); // On choisi l'activitée à chargé
    }
}
```

#### Intent (intentions)

Toutes les activités sont à l'écoute, mais je doit définir sous quels conditions j'éxécute cette activité

#### Intentions implicite

Le système d'exploitation va demander à toutes les applications qui on les **intent** de la réaliser.

A ce moment une fenêtre s'ouvre et l'utilisateur choisi l'application.

> *Exemple : lorsque j'ouvre une image, un **intent** d'ouverture d'image est demandé à l'ensemble des applications, et l'utilisateur peut choisir quel application prendre.*

#### Intentions explicites

#### Définir des options

On peut définir des régles de sécurité et autres pour chaque activités.

#### Composantes

- activités : est un algorythme qui est lié à une vue (layout)
- les services (algorythme sans apparences). Ils peuvent être lancé à différents moment (démarrage appareil, à un événement, au laucement de l'application...)
- les broadcast (envoyer des intentions à beaucoup d'autres applications)
- les intent receivers (des applications qui attente des intent)
- les content providers (des applications qui propose du contenu, comme des contactes, les sms, photos, etc...)

Les communications entre les applications utilisent les intent.

> Exemple : application qui liste les images :
> - une vue pour afficher les images
> - une activité pour géer le remplissage et l'affichage de la liste
> - activités pour ajouter, supprimer des images

#### Cycle de vie d'une activité

![Cycle de vie](https://profgra.org/lycee/img/formation_android_pfr/life_cycle.png)

On peut surcharger chacune des étapes.

1. onCreate
	- Cette méthode est appelée à la création de votre activité  (Activity). 
	- Elle sert à initialiser votre activité ainsi que toutes les données nécessaires à cette dernière. 
	- Quand la méthode onCreate est appelée, on lui passe un Bundle en argument. Ce Bundle contient l’état de sauvegarde enregistré lors de la dernière exécution de votre activité.
	- Elle charge l’IHM et retrouve les widgets pour les interactions futures
1. onStart
	- Cette méthode signifie le début d’exécution de votre activité (début du passage au premier plan). Si votre activité ne peut pas aller en avant plan quelque soit la raison, l’activité sera transférée à onStop.
	- La vue va devenir visible
1. onResume
	- Cette méthode est appelée après onStart (au moment où votre application passe ou repasse en avant plan). A la fin de l’appel à la méthode onResume, votre application se trouve au premier plan et reçoit les interactions utilisateurs.
1. onPause
	- Si une autre activité passe au premier plan, la méthode onPause est appelée sur votre activité. Afin que vous sauvegardiez l’état de l’activité et les différents traitements effectués par l’utilisateur. Ex: une nouvelle activity pas en full size ou une activité transparente. A ce stade, votre activité n’a plus accès à l’écran, vous devez arrêter de faire toute action en rapport avec l’interaction utilisateur (désabonner les listeners). Vous pouvez par contre continuer à exécuter des algorithmes nécessaires mais qui ne consomment pas trop de CPU.
1. onStop
	- Appelée quand votre activité n’est plus du tout visible quelque soit la raison. Dans cette méthode vous devez arrêter tous les traitements et services exécutés par votre application.
	- L’application pourrait être stoppée. On arrête tout ce qui consomme de l’énergie ou de la mémoire
1. onRestart
	- l’application revient à la vie on peut réactiver des éléments
1. onDestroy
	- Appelée quand votre application est totalement fermée (Processus terminé). Toutes les données non sauvegardées sont perdues
	- Il faut libérer et fermer toutes les ressources (fichiers, bases, réseaux, etc…)
    
#### Gérer la sauvegarde de l'activité

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-11/scaled-1680-/kXHOP7HgaWHlCvoS-image-1667993614551.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-11/kXHOP7HgaWHlCvoS-image-1667993614551.png)

On surcharge les méthodes (comme `onSaveInstanceState()`) pour définir quoi sauvegarder.

De base Android peut sauvegarder les activités, mais définir cette méthode permet d'être sûr qu'on ne perdra pas de données.

```java
public class ExempleActivity extends Activity {
// …
    @Override
    protected void onSaveInstanceState(Bundle outState /* tout ce qui est déjà sauvegardé */) {
      	// Toast : c'est les messages de notifications en bas de l'écran
		Toast.makeText(this, "Save", Toast.LENGTH_LONG().show();
        EditText s = (EditText) findViewById(R.id.autosaved);
        outState.putString("text", s.getText().toString());
        super.onSaveInstanceState(outState);
    }
    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.state_save);
        if (savedInstanceState == null) {
            Toast.makeText(this, "Create", Toast.LENGTH_LONG).show();
        } else {
             String text = savedInstanceState.getString("text");
            Toast.makeText(this, "Restore with "+text, Toast.LENGTH_LONG).show();
        }
    }
	@Override
    protected void onDestroy() {
        super.onDestroy();
        Toast.makeText(this, "Destroy", Toast.LENGTH_LONG).show();
    }
}

```

Peu d'espace dispo, donc si besoin de plus : onRetainNonConfigurationInstance() &  getLastNonConfigurationInstance()

### Taches (threads)

Utile si une activité est trop gourmande. On peut exterioliser ce code.

#### AsyncTask

Il faut étendre `AsyncTask<T, U, V>()`

- T : paramètre fournis à la tache (Integer... de doInBackground())
- U : donnée transmises durant la progression du traitement (Integer... de onProgress())
- V : résultat de la tache (void de retour de doInBackground())

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-11/scaled-1680-/v7FiZEa9z2ll5qWd-image-1668002822340.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-11/v7FiZEa9z2ll5qWd-image-1668002822340.png)

#### Lier des actions entre Java et le layout

##### Avec `onClick`

```java
public class MainActivity extends AppCompatActivity {

    private Integer number;
    private EditText numberBtn;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        this.number = 10;
        this.numberBtn = findViewById(R.id.numberField);

        this.numberBtn.setText(this.number.toString());
    }

    // Le listener doit avoir cette signature
    public void manageNumber(View view)
    {
        if (view.getId() == R.id.increment_number_btn) {
            this.number++;
        } else {
            this.number--;
        }

        this.numberBtn.setText(this.number.toString());
    }
}
```

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.appcompat.widget.LinearLayoutCompat xmlns:android="http://schemas.android.com/apk/res/android">

    <androidx.appcompat.widget.LinearLayoutCompat
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal">

      	<!-- On ajoute "android:onClick" avec le nom de la méthode -->
        <Button
            android:id="@+id/increment_number_btn"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="0"
            android:text="@string/increment_btn"
            android:onClick="manageNumber" />

        <EditText
            android:id="@+id/numberField"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="@string/default_number_value"
            android:layout_weight="1"
            app:layout_constraintBottom_toBottomOf="parent"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toTopOf="parent" />

        <Button
            android:id="@+id/decrement_number_btn"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="0"
            android:text="@string/decrement_btn"
            android:onClick="manageNumber"/>
    </androidx.appcompat.widget.LinearLayoutCompat>

</androidx.appcompat.widget.LinearLayoutCompat>
```

##### Avec `setOnClickListener`

```java
public class MainActivity extends AppCompatActivity {

    private Integer number;
    private EditText numberBtn;
    private Button incrementBtn;
    private Button decrementBtn;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        this.number = 10;
        this.numberBtn = findViewById(R.id.numberField);

        this.numberBtn.setText(this.number.toString());

        decrementBtn = findViewById(R.id.decrement_number_btn);
        incrementBtn = findViewById(R.id.increment_number_btn);

        decrementBtn.setOnClickListener(
            this::manageNumber
        );
        incrementBtn.setOnClickListener(
            this::manageNumber
        );
    }

    // Le listener doit avoir cette signature
    public void manageNumber(View view)
    {
        if (view.getId() == R.id.increment_number_btn) {
            this.number++;
        } else {
            this.number--;
        }

        this.numberBtn.setText(this.number.toString());
    }
}
```

##### Avec design pattern

#### Communications entre activités

```java
public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        /* Gérer les activités internes ou précises */
        // this: packageContexte, là où on est,
        // com.akipe.listviewdemo.MainActivity.class: classe java qui correspond à l'activité
        Intent intent = new Intent(this, com.akipe.listviewdemo.MainActivity.class);

        // on démarre l'activité
        startActivity(intent);

        /* Gérer les activités standart Android ou de d'autres appli */
        Intent generalIntent = new Intent(Intent.ACTION_DIAL, Uri.parse("tel://0101010101"));
        startActivity(generalIntent);
    }
}
```

##### Transfére de données

```java
void startActivityForResult(Intent intent, int requestCode /* index de l'intention */);
void setResult(int resultCode); // resultCode prend des coonstantes, comme RESULT_CANCELED, RESULT_OK
void setResult(int resultCode, Intent dataCourent); // dataCourent contient les données à retourner.
  
finish(); // fermer la fenêtre
getIntent(); // Récupérer l'intention, depuis la fenêtre d'origine

// Ajouter des données dans l'intention
intent.putExtra(String nameData, boolean value): Intent;
intent.putExtra(String nameData, boolean[] value): Intent;
intent.putExtra(String nameData, byte value): Intent;
intent.putExtra(String nameData, byte[] value): Intent;
...;

// Pour des données plus complexes
intent.putExtra(String nameData, Parcelable value): Intent;
intent.getSerializableExtra(String nameData): Serializable;
intent.putExtra(String nameData, Parcelable[] value): Intent;
intent.getShortArrayExtra(String nameData): short[];
intent.putExtra(String nameData, Serializable value): Intent;
intent.getShortExtra(String nameData): short;


void onActivityResult(int requestCode, int resultCode, Intent data);

```

```java
/* Gérer les activités internes ou précises */
// this: packageContexte, là où on est,
// com.akipe.listviewdemo.MainActivity.class: classe java qui correspond à l'activité
Intent intent = new Intent(this, com.akipe.listviewdemo.MainActivity.class);

// on démarre l'activité
startActivity(intent);

/* Gérer les activités standart Android ou de d'autres appli */
Intent generalIntent = new Intent(Intent.ACTION_DIAL, Uri.parse("tel://0101010101"));
startActivity(generalIntent);
```


Exemple :
```java
// MainActivity.java
public class MainActivity extends AppCompatActivity {

    private TextView firstnameTw;
    private TextView lastnameTw;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        this.firstnameTw = findViewById(R.id.person_firstname);
        this.lastnameTw = findViewById(R.id.person_lastname);

        Button definePersonBtn = findViewById(R.id.add_person_btn);
        definePersonBtn.setOnClickListener(
                this::AskDefinePersonActivity
        );
    }

    @Override
    protected void onActivityResult(int requestCode, int resultCode, Intent data) {

        super.onActivityResult(requestCode, resultCode, data);

        this.firstnameTw.setText(data.getStringExtra("firstname"));
        this.lastnameTw.setText(data.getStringExtra("lastname"));
    }

    private void AskDefinePersonActivity(View view)
    {
        Intent definePersonIntent = new Intent(this, com.akipe.listviewdemo.DefinePersonActivity.class);

        definePersonIntent.putExtra("firstname", this.firstnameTw.getText().toString());
        definePersonIntent.putExtra("lastname", this.lastnameTw.getText().toString());

        startActivityForResult(definePersonIntent, 1);
    }
}
```

```java
public class DefinePersonActivity extends AppCompatActivity {

    private Intent currentIntent;
    EditText firstnameEt;
    EditText lastnameEt;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_define_person);

        this.currentIntent = getIntent();

        this.firstnameEt = findViewById(R.id.firstname_et);
        this.lastnameEt = findViewById(R.id.lastname_et);

        this.firstnameEt.setHint(this.currentIntent.getStringExtra("firstname"));
        this.lastnameEt.setHint(this.currentIntent.getStringExtra("lastname"));

        Button definePersonBtn = findViewById(R.id.define_person_btn);
        definePersonBtn.setOnClickListener(this::DefinePerson);
    }

    private void DefinePerson(View view)
    {
        this.currentIntent.putExtra("firstname", firstnameEt.getText().toString());
        this.currentIntent.putExtra("lastname", lastnameEt.getText().toString());

        setResult(RESULT_OK, this.currentIntent);
        finish();
    }
}
```

```java
// Activité qui va appeler une autre activité
void startActivity(Intent intent);
void startActivityForResult(Intent intent, int requestCode);

// Activité appelé
intent.putExtra("dataName", firstname.toString());
setResult(RESULT_OK, intent);
finish();

// Activité qui reçoit les données
@Override
protected void onActivityResult(int requestCode, int resultCode, Intent intent)
{
  super.onActivityResult(requestCode, resultCode, data);
  
  if (requestCode == 1 && resultCode == RESULT_OK) {
    String dataName = intent.getStringExtra("dataName");
  }
}
```

Type de donnés pour résultats :

- RESULT_CANCELED
- RESULT_OK
- RESULT_FIRST_USER

### ListView

#### Simple

```xml
<ListView
        android:id="@+id/list_data_listview"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        />
```

```java
ArrayList<String> listData = new ArrayList<String>();

ArrayAdapter arrayAdapterListData = new ArrayAdapter(
  Activity activityContexte, // L'activité qui gére l'arrayAdapter
  int android.R.layout.simple_list_item_1, // Le layout a utiliser
  this.listData // Le tableau à définir
);

findViewById(R.id.list_data_listview)
  .setAdapter(arrayAdapterListData);
```

### Classes utiles

```java
// NumberManagerOnClickLister.java
public class NumberManagerOnClickListener implements View.OnClickListener {
    private EditText _numberInput;
    private int _number;

    public NumberManagerOnClickListener(EditText numberInput)
    {
        this._numberInput = numberInput;
    }

    @Override
    public void onClick(View view) {
        if (view.getId() == R.id.increment_number_btn) {
            this._number++;
        } else {
            this._number--;
        }

        this._numberInput.setText(String.format("%d", this._number));
    }
}
```

```java
// NumberManagerOnClickLister.java
public class MainActivity extends AppCompatActivity {

    private Integer number;
    private EditText numberBtn;
    private Button incrementBtn;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        this.number = 10;
        this.numberBtn = findViewById(R.id.numberField);

        this.numberBtn.setText(this.number.toString());

        decrementBtn = findViewById(R.id.decrement_number_btn);
        incrementBtn = findViewById(R.id.increment_number_btn);
        exitBtn = findViewById(R.id.exit_btn);

        incrementBtn.setOnClickListener(
                new NumberManagerOnClickListener(this.numberBtn)
        );
    }
}
```

#### Toast

Gére les messages de notifications en bas de l'écran.

## Android Studio

### Astuce

#### Ouvrir l'emulateur dans une autre fenêtre

<https://stackoverflow.com/questions/70986530/android-studio-emulator-in-a-separate-window>

## Conventions

- Java : <https://source.android.com/docs/setup/contribute/code-style#follow-field-naming-conventions>

- jetpack : <https://developer.android.com/jetpack>
---
title: C
description: 
published: true
date: 2024-03-04T12:31:23.380Z
tags: 
editor: markdown
dateCreated: 2024-03-04T12:31:23.380Z
---

# C

# IDE / Editeur de code

## Visual studio code
HowTo: https://code.visualstudio.com/docs/languages/cpp

Extensions :
- C/C++ : https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools

# Bases

## Compilation
```
   Préprocesseur      Compilateur       Linker
inclusion fichiers | transforme .c   |
  .h dans .c       |   en binaire    |
fichier.h ---- fichier.c ------- fichier.o ----\
fichier.h ---- fichier.c ------- fichier.o -------> executable.exe
fichier.h ---- fichier.c ------- fichier.o ----/
```

## Code minimal
```
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char *argv[])
{
    printf("Hello world!\n");
    return 0
}
```

## Portée variables/fonctions

### Variables
```
#include <stdio.h>
#include <stdlib.h>

int var_global = 0 // Accessible dans tout le projet
static var_global_fichier = 0 // Variable accessible dans tout le fichier

int une_fonction()
{
    // Accessible uniquement une seule instance de fonction
    int var_local_fonction = 0;
    // Accessible dans toutes les instances de cette fonction
    static int var_local_toutes_fonction = 0;
}
```

### Fonctions
```
// Fonction accessible dans tout le projet
int fonction_global()
{
}

// Fonction accessible uniquement dans le fichier
statis int fonction_dans_fichier()
{
}
```


## Infos

##### Commentaires
`// Un commentaire d'une ligne`
`/* commentaires multiligne */`

##### Variables
> Nommage
- commence par une lettre
- minuscule
- majuscule
- chiffres

> Types | Recommendation : `int` (entier) & `double` (flotant)
- signed char: `[-127;127]`
- unsigned char:  `[0; 255]`
- int `[-32 767; 32 767]`
- unsigned int : `[0; 65 535]`
- long : ` [-2 147 483 647; 2 147 483 647]`
- unsigned long : `[0; 4 294 967 295]`
- float : `[-1 x1037; 1 x1037]`
- double : `[-1 x1037; 1 x1037]`

> Nombre flotant
- écriture : 1.2

> Déclaration
```
type nomVariable = value, deuxiemeVariable = value;
int ageUtilisateur = 0, estValide = 1;

int ageUtilisateur    = 0,
    estValide         = 0;
```

> Constante
```
const int NOMBRE_MAX = 30;
```

> Boolean
- depuis C 99 :
```
#include <stdbool.h>
bool isExist  = true,
    isTheBest = false;

if (isExist) {
    isTheBest = true;
}
```

> Calculs
- `+` addition
- `-` soustraction
- `*` multiplication
- `/` division
- `%` modulo
- `variable++` itération
- `variable--` décrementation
```
variableNombre = variableNombre + 2;
// est équivalent à
variableNombre += 2;
```
- `#<math.h>` Pour avoir d'autre fonctions de math

> Conditions
- test de valeur
    - `==` est égale à
    - `>`   supérieur à
    - `>=` supérieur ou égale à
    - `<`   inférieur à
    - `<=` inférieur ou égale à
    - `!=` est différent de
- assemblage de conditions
    - `&&` ET
    - `||` OU
    - `!`  NON (inverse)
- Sauvegarde de condition dans variable
```
majeur     = ageUtilisateur >= 18; // majeur = 1 si oui, sinon = 0
adulteHome = majeur && estGarcon;
```
- `if, else if, else`
```
if (/* condition */) {
    // ...
} else if ( /* condition */ ) {
    // ...
} else {
    // ...
}
```
-`switch`
```
switch (ageUtilisateur) {
    case 2:
        printf("Salut ! Ça va bébé ? :)");
        break;
    case 5:
        printf("Bienvenu à l'école :)");
        break;
    case 16:
        printf("L'adolescence ;)");
        break;
    case 18:
        printf("Enfin adulte !");
        break;
    default:
        printf("Vous avez %d ans.", ageUtilisateur);
        break;
}
```
- conditions ternaires
```
if (majeur) {
    age = 18;
} else {
    age = 17;
}
// Est similaire à
age = (majeur) ? 18 : 17;


if (age >= 18) {
    autorisation = 1 // autorisation = true
} else {
    autorisation = 0 // autorisation = false
}
// Est similaire à
autorisation = (age >= 18) 1 : 0;
autorisation = (age >= 18) true : false;
```

> Boucles

- `while`    tant que
```
while (/* condition */) {
    // ...
}
```
- `do ... while`
```
do {
    // ...
} while (/* condition */);
```
- `for`
```
int compteurBoucle = 0;

for (compteurBoucle = 0; compteurBoucle < 10; compteurBoucle++) {
    // ...
}
```

## Fonctions

> Base des fonctions
```
type_de_retour    nomFonction(type parametre1, type parametre2) {
    // ...
    // "return" si retour
}

int tripleNombre(int nombre) {
    return nombre * 3;
}
resultat = tripleNombre(15);

int addition(int premierNombre, int deuxiemeNombre) {
    return premierNombre + deuxiemeNombre;
}
resultat = addition(5, 10);

void afficherNombre(double nombre) {
    printf("Le nombre est %f", nombre);
}
afficherNombre(2.5);
```

`void*` comme type de retour dans une fonction pour un pointeur de n'importe quel type == pointeur universel.

> `printf()`    afficher du texte
```
printf(
    "Message avec des variable, un int %d, un long %ld et un float %f",
    varInt,
    varLong,
    varFloatEtDouble
);
```
- type de variables
    - `%d`    : int
    - `%ld`  : long
    - `%f`    : float & double
- carractères spéciaux
    - `\n` : retour à la ligne
    - `\t` : tabulation
- chaines de caractères
    - `%c`    : char

> `sprintf`    écrire dans une chaine.
```sprintf(chaine, 'Tu as %d ans!', age)```

> `scanf()`    stocker une variable demandé à l'utilisateur
```
int ageUtilisateur = 0;
scanf("%d", &ageUtilisateur); // enregistre le resultat à l'adresse de la var
```
- type de variables
    - `%d`    : int
    - `%ld`  : long
    - `%f`    : float
    - `%lf`  : double (Différent de printf() !!!)
    - `%c`    : char



> `size_t strlen(const char* chaine)`
Retourne le nombre de caractères de la chaine.

> `char* strcpy(char* copieDeLaChaine, const char* chaineACopier)`
Copie une chaine dans une autre, retourne un pointeur vers copieDeLaChaine.

> `char* strcat(char* chaine1, const char* chaine2)`
Concataine 2 chaines de caractères. Ajoute chaine2 à la suite de chaine1, retourne pointeur de chaine1.

> `int strcmp(const char* chaine1, const char* chaine2)`
Compare 2 chaine de caractères si identique. Retourn e 0 si identique, si chaine1 > chaine2 alors int positif, si chaine1 < chaine2 alors int negatif.

> `char* strchr(const char* chaine, int caractereARecherche)`
Recherche caractére dans chaine. renvoie l'adresse du premier caractère trouvé ou NULL si non trouvé.

> `char* strrchr(const char* chaine, int caractereARecherche)`
Recherche caractére dans chaine. renvoie l'adresse du dernier caractère trouvé ou NULL si non trouvé.

> `char* strpbrk(const char* chaine, const char* lettreARerchercher)`
Recherche caractére dans chaine. renvoie l'adresse du dernier caractère trouvé ou NULL si non trouvé.

> `exit(int valeurFinApp)`
Arréte le programme avec comme valeur de retour `valeurFinApp`.

## Programmation modulaire

### Types de fichiers
- `fichier.c` > fichier source
- `fichier.h` > fichier headers (contient prototypes)
Les deux types de fichiers ci-dessus vont de pair.

```
/
|- Sources/
|    |- editeur.c
|    |- fichier.c
|    |- jeu.c
|    |- main.c
|- Headers/
     |- constantes.h
     |- editeur.h
     |- fichier.h
     |- jeu.h
```


### Headers
Contient l'ensemble des protopypes du fichier.c correspondant.

```
// Dans le fichier source.c
#include "header.h"
```

```
#ifndef DEF_NOMDUFICHIER

#define DEF_NOMDUFICHIER

#define CONSANTE 10

struct NomDuneStructure
{
    int autreVariables;
    double nombreDecimal;
};

double airRectangle(double largeur, double longueur);

#endif
```

### Prototypes
Permet de pouvoir utiliser les fonctions dans n'importe quel ordre d'initialisation.

```
#include <stdio.h>
#include <stdlib.h>

// Prototype
double airRectangle(double largeur, double longueur);

// Fonction du prototype
double airRectangle(double largeur, double longueur)
{
    return largeur * longueur;
}
```
### Directive préprocesseur
Ils commencent par le caractère `#`.
Avant la compilation un programme est exécuté pour executé les directives préprocesseures.

#### include
Permet d'inclure le contenu du fichier.
```
#include <stdio.h> // Inclusion de bibliothèques de l'editeur/global
#include "jeux.h" // Inclusion de fichiers dans le projet
```

 #### define
Permet de définir une constante de préprocesseur. À la différence d'une constante, elle n'est pas stocké dans la mémoire vive mais remplace directement dans les fichiers sources du code la valeur de la constante.
Elles sont souvent défini dans le `header`.

```
#define UNE_CONTANTE 3

#define LARGEUR_FENETRE    800
#define HAUTEUR_FENETRE    600
#define NOMBRE_PIXELS      (LARGEUR_FENETRE * HAUTEUR_FENETRE)

// Constantes prédéfinies (double "_")
__LINE__ // numéro ligne actuelle
__FILE__ // nom fichier actuel
__DATE__ // date de compilation
__TIME__ // heure de compilation

printf("Erreur à la ligne %d du fichier %s\n", __LINE__, __FILE__);
printf("Fichier compilé le %s a %s\n", __DATA__, __TIME__);
```

##### Macro
```
#define COUCOU() printf("Coucou");
                 printf("Ça va ?");

int main(int argc; char *argv[])
{
    COUCOU()
    
    return 0;
}

#define MAJEUR(age) if (age >= 18) \
                    printf("Vous êtes majeur\n");

int main(int argc; char *argv[])
{
    MAJEUR(22)
    
    return 0;
}
```

 #### Conditions

```
#if condition
    // ...
#elif
    // ...
#endif
```

```
#define WINDOWS

#ifdef WINDOWS
    // ...
#endif

#ifdef LINUX
    // ...
#endif

#ifndef LINUX
    // ...
#endif
```


## Pointeur

### Base
```
int age = 18;
int *pointeur = NULL; // = int* pointeur = NULL;

age; // = contenu variable (18)
&age; // = adresse variable (0023FF74, hexadecimal)
pointeur; // = valeur de pointeur c.a.d. une adresse memoire en hexa
*pointeur; // = valeur de la variable à l'adresse contenu dans pointeur

// Sauvegarde adresse age dans pointeurSurAge
int *pointeurSurAge = &age;
// ==
int *pointeurSurAge = NULL;
pointeurSurAge = &age;

printf("L'adresse de la variable age est : %p", &age)
// ==
printf("L'adresse de la variable age est : %d", pointeurSurAge)

printf("La valeur de la variable age est : %d", age)
// ==
printf("La valeur de la variable age est : %d", *pointeurSurAge)
```

### Pointeurs avec fonction
```
int main(int argc, char *argv[])
{
    int nombre = 5;
    
    triplePointeur(&nombre)
    printf("%d", nombre) // = "15"
    
    return 0;
}

void triplePointeur(int *pointeurSurNombre)
{
    *pointeurSurNombre *= 3; // Multiplie par 3 le nombre
}
```

```
int main(int argc, char *argv[])
{
    int nombre = 5;
    int *pointeurNombre = &nombre;
    
    triplePointeur(pointeurNombre);
    printf("%d", *pointeurNombre);
    
    return 0;
}

void triplePointeur(int *pointeursurNombre)
{
    *pointeurSurNombre *= 3;
}
```

## Tableau
Les adresses mémoires des différentes "cases" sont discontinues & de même types.

### Initialisation
```
int tableau[4] = {0}; // "tableau" est un pointeur de "tableau[0]"
// ==
int tableau[4] = {0, 0, 0, 0};
int tableau[4] = {0};
int tableau[4] = {42, 30} // == tableau[4] = {42, 30, 0, 0}

int tailleTableau = 5;
int tableau[tailleTableau]; // Depuis C99
```

### Parcourir un tableau
```
int tableau[4],
    iterateur = 0;

tableau[0] = 10;
tableau[0] = 4;
tableau[0] = 120;
tableau[0] = 42;

for (iterateur = 0; iterateur < 4; iterateur++) {
    printf("%d\n", tableau[iterateur]);
}
```

### Dans fonction
```
int tableau[4] = {10, 33, 42, 120};

void fonction(int tableau[], int tailleTableau) { // tableau[] == *tableau
// ...
}
```

### Allocation dynamique


## Chaines de caractères
Le type `char` permet de stocker un nombre entre `-128 et 127`. Il permet de stocker une lettre (ASCII).

### Lettres
```
char lettre = 'A';
scanf("%c", &lettre);
printf("%c", lettre);
```

### Mots/phrases
```
char mot[] = 'Salut'; // caractère d'échapement '\0'
char phrase[100] = {0};
scanf("%s", mot);
printf("%s", mot);
```

## Variables personnalisées

### Structures
Assemblages de variables qui peuvent avoir différents types. Elles sont généralements défini dans le header. Par convention le nom d'une structure commence par une majuscule.

```
typedef struct NomDeVotreStructure NomDeVotreStructure
struct NomDeVotreStructure
{
    int variable1;
    int variable2;
    int autreVariables;
    double nombreDecimal;
    char phrase[100];
};

NomDeVotreStructure variableStruct = {0, 0, 0, 0.0, ""};

variableStruct.variable1 = 0;
variableStruct.nombreDecimal = 1.2;


```

```
typedef struct Coordonnees Coordonnees;
// ...
Coordonnes point; // Plus besoin de "struct"
```

```
void initialiserCoordonnes(Coordonnees* point)
{    
    (point*).x = 0; // == point->x = 0;
    (point*).y = 0; // == point->y = 0;
}
```

### Énumerations
Créer une liste de valeurs possibles pour une variables.

Dans l'exemple ci-dessous, le compilateur attribut automatiquement une valeur numérique à chaques valeurs : FAIBLE = 0, MOYEN = 1, FORT = 2.
```
typedef enum Volume Volume;
enum Volume
{
    FAIBLE, MOYEN, FORT
};

Volume musique = MOYEN;
```

Pour définir ses propres valeurs :
```
typedef enum Volume Volume;
enume Volume
{
    FAIBLE = 10, MOYEN = 50, FORT = 100
};
```

## Fichiers
Nécessaire les bibliothèques standart
```
#include <stdlib.h>
#include <stdio.h>
```

> `FILE* fopen(const char* nomDuFichier, const char* modeOuverture);` ouvrir un fichier
- modeOuverture
    - `r` lecture seul (le fichier doit existé)
    - `w` écriture seul
    - `a` mode ajout
    - `r+` lecture & écriture
    - `w+` lecture & écriture avec suppression du contenu au préalable
    - `a+` ajout en lecture & écriture à la fin
    - `...b` ajout de 'b' pour le mode binaire

> `fclose(fichier)` supprimer le pointeur du fichier

> `int fputc(int caractere, FILE* pointeurSurFichier)`
Écrire un caractère à la fois. Retourne un code d'erreur, si `EOF` alors il y a eu une erreur.

> `char* fputs(const char* chaine, FILE* pointeurSurFichier)`
Écrire une chaine de caractère dans un fichier. Renvoie `EOF` si erreur.

> `fprintf(FILE* pointeurSurFichier, char* chaine, void* variables[])`
Écrire dans un fichier, similaire à printf().

> `int fgetc(FILE* pointeurSurFichier)`
Lit un caractère du fichier. Retourne le caractère lu, ou `EOF` si erreur.

> `char* fgets(char* chaine, int nombreDeCaracteresALire, FILE* pointeurSurFichier)`
Lit une ligne dans un fichier. Renvoie `NULL` si n'est n'a pas fini de lire le fichier en entier.

> `fscanf(FILE* pointeurSurFichier, char* exressionVariable, void* variable[])`
`fscanf(fichier, "%d %d %d", &score[0], &score[1], &score[2])`
Permet de lire dans un fichier qui a été écrit de manière précise.

> `long ftell(*FILE pointeurSurFichier)`
Indique la position actuelle dans le fichier. Renvoie la position du curseur dans le fichier.

> `int fseek(*FILE pointeurSurFichier, long deplacement, int origine)`
Positionne le curseur à un endroit précis. "deplacement" indique le nombre de caractère à se déplacer par rapport à "origine". "déplacement" peut être positif (se déplacé à l'avent), nul, ou négatif (déplacer en arriére).
"origine" peut prendre plusieurs valeurs :
- `SEEK_SET` début du fichier
- `SEEK_CUR` position actuelle
- `SEEK_END` fin du fichier
Si le curseur est à la fin : écrira à la suite du fichier, mais si le curseur est au début, il remplacera le contenu du fichier.

> `void rewind(FILE* pointeurSurFichier)`
Remet le curseur au début du fichier.

> `int rename(const char* ancienNom, const char* nouveauNom)`
Renommer un fichier. Renvoie 0 si réussi.

> `int remove(const char* fichierASupprimer)`
Supprimer un fichier.

## Allocation dynamique
Pour une déclaration manuel des variables.

> `sizeof(char/int/...)`
Permet d'avoir la taille en octet d'un type de variable

Besoin des bibliotèques suivantes : `stdlib.h` pour les fonctions suivantes :

> `void* malloc(size_t nombreOctetsNecessaires)`
Demande au systéme de la mémoire. Renvoie `NULL` si il y eu une erreur.
Example :
```
int* memoireAllouee = NULL;
memoireAllouee = malloc(sizeof(int));
```

> `void free(void* pointeur);`
Libére la mémoire demandé précédament.

### Allocation de mémoire dynamique pour un tableau

```
// Tableau dynamique de int
int nombreCaseTableau = 0;
int *tableauDynamique = NULL;
scanf("%d", &nombreCaseTableau);

tableauDynamique = malloc(nombreCaseTableau * sizeof(int));

if (tableauDynamique == NULL) {
    exit(0);
}

// ...

free(tableauDynamique);
```

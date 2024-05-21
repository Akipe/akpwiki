---
title: C# (C Sharp)
description: 
published: true
date: 2024-05-21T14:04:11.400Z
tags: 
editor: markdown
dateCreated: 2024-05-21T14:02:31.719Z
---

# C# (C Sharp)

## Langages

C'est un langage managé, c'est à dire un langage où l'on a pas besoin de gérer la mémoire. Il a un "garbage colector", qui est un petit processus en arriére plan qui vérifie si une variable sera réutiliser dans une variable, si ce n'est pas le cas il la supprime automatiquement.

### Variables

#### Constantes

```c#
private const string FREQUENCY_MONTHLY = "Mensuelle";
```

#### Typage simple

| Type | Description | Taille | Valeurs | Autre
|---|---|---|---|---
| sbyte | Nombres entiers | Entier 8 bits signé | -128 à 127
| byte | Nombres entiers | Entier 8 bits non signé | 0 à 255
| short | Nombres entiers | Entier 16 bits signé | -32 768 à 32 767
| ushort | Nombres entiers | Entier 16 bits non signé | 0 à 65 535
| int | Nombres entiers | Entier 32 bits signé | -2 147 483 648 à 2 147 483 647
| uint | Nombres entiers | Entier 32 bits non signé | de 0 à 4 294 967 295
| long | Nombres entiers | Entier 64 bits signé | -9 223 372 036 854 775 808 à 9 223 372 036 854 775 807
| ulong | Nombres entiers | Entier 64 bits non signé | de 0 à 18 446 744 073 709 551 615
|---|---|---|---|---
| float | Nombre à virgule flottante | 4 octets | ±1,5 x 10−45 à ±3,4 x 1038 | ~6-9 chiffres
| double | Nombre à virgule flottante | 8 octets | De ±5,0 × 10−324 à ±1,7 × 10308 | ~15-17 chiffres
| decimal | Nombre à virgule flottante | 16 octets | ±1,0 x 10-28 to ±7,9228 x 1028 | 28 à 29 chiffres
|---|---|---|---|---
| bool | Valeur booléenne |  | true / false
| string | Représente une séquence de caractères Unicode. |  |
| char | Caractère Unicode UTF-16 | 16 bits | U+0000 à U+FFFF
| object | Tous kes types héritent de System.Object |  |

(https://docs.microsoft.com/fr-fr/dotnet/csharp/language-reference/builtin-types/built-in-types)[Lien vers les types C#]

##### String

```c#
String.IsNullOrEmpty(maChaineDeCaractère); // Test si la variable ne contient pas de texte
String.Empty; // Quand on veut définir à null
System.Environment.NewLine; // Nouvelle ligne

// Ecrire des chaines de caractères
string chaineCaractere = "hello " + name;
string output = String.Format("Hello {0}", name);
string chaineCaractere = $"Hello {name}";

// '' pour les caractères et "" pour les chaines de caractères
char caractere = 'a';
string chaineCaractere = "aaa";

// Utilisation des format comme dans certains langages (C)
string chaine = String.Format("Demandeur n°{0} ajouté en {1},", jobSeeker.Id, jobSeeker.RegistrationYear);

// Formater les nombres
monNombre.ToString("##.###"); // 2 chiffres à partir des unités et 3 après la virgule

// Tester une égalité de chaine
String.Equals("une chaine", "une chaine");

// Tester une chaine vide
String.IsNullOrEmpty(LastDiplomaName);

// Différents traitements sur une chaine
"une chaine".ToLower();
"une chaine".ToUpper();
"  ne chaine ".Trim();
```

##### Double

Formatage en string :

```c#
double monNombre1 = 150.78942;
double monNombre2 = 150.7;
monNombre1.ToString("0.##"); // 150.78
monNombre1.ToString("0.00"); // 150.78
monNombre2.ToString("0.##"); // 150.7
monNombre2.ToString("0.00"); // 150.70
// Ou alors 
monNombre2.ToString("F4"); // 150.7000
monNombre2.ToString("0.00"); // 150.70
monNombre2.ToString("0.00"); // 150.70
```

Voir les exemples [Microsoft](https://docs.microsoft.com/en-us/dotnet/api/system.double.tostring?view=net-6.0#system-double-tostring(system-string)).

```c#
// The example displays the following output to the console:
//       Formatting of 1054.32179:
//          C:                     $1,054.32
//          C0:                    $1,054
//          C1:                    $1,054.3
//          C2:                    $1,054.32
//          C3:                    $1,054.322
//
//          E:                     1.054322E+003
//          E0:                    1E+003
//          E1:                    1.1E+003
//          E2:                    1.05E+003
//          E3:                    1.054E+003
//
//          e:                     1.054322e+003
//          e0:                    1e+003
//          e1:                    1.1e+003
//          e2:                    1.05e+003
//          e3:                    1.054e+003
//
//          F:                     1054.32
//          F0:                    1054
//          F1:                    1054.3
//          F2:                    1054.32
//          F3:                    1054.322
//
//          G:                     1054.32179
//          G0:                    1054.32179
//          G1:                    1E+03
//          G2:                    1.1E+03
//          G3:                    1.05E+03
//
//          N:                     1,054.32
//          N0:                    1,054
//          N1:                    1,054.3
//          N2:                    1,054.32
//          N3:                    1,054.322
//
//          P:                     105,432.18 %
//          P0:                    105,432 %
//          P1:                    105,432.2 %
//          P2:                    105,432.18 %
//          P3:                    105,432.179 %
//
//          R:                     1054.32179
//          #,000.000:             1,054.322
//          0.###E-000:            1.054E003
//          000,000,000,000.00###: 000,000,001,054.32179
//
//       Formatting of -195489100.8377:
//          C:                     ($195,489,100.84)
//          C0:                    ($195,489,101)
//          C1:                    ($195,489,100.8)
//          C2:                    ($195,489,100.84)
//          C3:                    ($195,489,100.838)
//
//          E:                     -1.954891E+008
//          E0:                    -2E+008
//          E1:                    -2.0E+008
//          E2:                    -1.95E+008
//          E3:                    -1.955E+008
//
//          e:                     -1.954891e+008
//          e0:                    -2e+008
//          e1:                    -2.0e+008
//          e2:                    -1.95e+008
//          e3:                    -1.955e+008
//
//          F:                     -195489100.84
//          F0:                    -195489101
//          F1:                    -195489100.8
//          F2:                    -195489100.84
//          F3:                    -195489100.838
//
//          G:                     -195489100.8377
//          G0:                    -195489100.8377
//          G1:                    -2E+08
//          G2:                    -2E+08
//          G3:                    -1.95E+08
//
//          N:                     -195,489,100.84
//          N0:                    -195,489,101
//          N1:                    -195,489,100.8
//          N2:                    -195,489,100.84
//          N3:                    -195,489,100.838
//
//          P:                     -19,548,910,083.77 %
//          P0:                    -19,548,910,084 %
//          P1:                    -19,548,910,083.8 %
//          P2:                    -19,548,910,083.77 %
//          P3:                    -19,548,910,083.770 %
//
//          R:                     -195489100.8377
//          #,000.000:             -195,489,100.838
//          0.###E-000:            -1.955E008
//          000,000,000,000.00###: -000,195,489,100.8377
//
//       Formatting of 1.0437E+21:
//          C:                     $1,043,700,000,000,000,000,000.00
//          C0:                    $1,043,700,000,000,000,000,000
//          C1:                    $1,043,700,000,000,000,000,000.0
//          C2:                    $1,043,700,000,000,000,000,000.00
//          C3:                    $1,043,700,000,000,000,000,000.000
//
//          E:                     1.043700E+021
//          E0:                    1E+021
//          E1:                    1.0E+021
//          E2:                    1.04E+021
//          E3:                    1.044E+021
//
//          e:                     1.043700e+021
//          e0:                    1e+021
//          e1:                    1.0e+021
//          e2:                    1.04e+021
//          e3:                    1.044e+021
//
//          F:                     1043700000000000000000.00
//          F0:                    1043700000000000000000
//          F1:                    1043700000000000000000.0
//          F2:                    1043700000000000000000.00
//          F3:                    1043700000000000000000.000
//
//          G:                     1.0437E+21
//          G0:                    1.0437E+21
//          G1:                    1E+21
//          G2:                    1E+21
//          G3:                    1.04E+21
//
//          N:                     1,043,700,000,000,000,000,000.00
//          N0:                    1,043,700,000,000,000,000,000
//          N1:                    1,043,700,000,000,000,000,000.0
//          N2:                    1,043,700,000,000,000,000,000.00
//          N3:                    1,043,700,000,000,000,000,000.000
//
//          P:                     104,370,000,000,000,000,000,000.00 %
//          P0:                    104,370,000,000,000,000,000,000 %
//          P1:                    104,370,000,000,000,000,000,000.0 %
//          P2:                    104,370,000,000,000,000,000,000.00 %
//          P3:                    104,370,000,000,000,000,000,000.000 %
//
//          R:                     1.0437E+21
//          #,000.000:             1,043,700,000,000,000,000,000.000
//          0.###E-000:            1.044E021
//          000,000,000,000.00###: 1,043,700,000,000,000,000,000.00
//
//       Formatting of -1.0573E-05:
//          C:                     $0.00
//          C0:                    $0
//          C1:                    $0.0
//          C2:                    $0.00
//          C3:                    $0.000
//
//          E:                     -1.057300E-005
//          E0:                    -1E-005
//          E1:                    -1.1E-005
//          E2:                    -1.06E-005
//          E3:                    -1.057E-005
//
//          e:                     -1.057300e-005
//          e0:                    -1e-005
//          e1:                    -1.1e-005
//          e2:                    -1.06e-005
//          e3:                    -1.057e-005
//
//          F:                     0.00
//          F0:                    0
//          F1:                    0.0
//          F2:                    0.00
//          F3:                    0.000
//
//          G:                     -1.0573E-05
//          G0:                    -1.0573E-05
//          G1:                    -1E-05
//          G2:                    -1.1E-05
//          G3:                    -1.06E-05
//
//          N:                     0.00
//          N0:                    0
//          N1:                    0.0
//          N2:                    0.00
//          N3:                    0.000
//
//          P:                     0.00 %
//          P0:                    0 %
//          P1:                    0.0 %
//          P2:                    0.00 %
//          P3:                    -0.001 %
//
//          R:                     -1.0573E-05
//          #,000.000:             000.000
//          0.###E-000:            -1.057E-005
//          000,000,000,000.00###: -000,000,000,000.00001
```

##### Tableaux statiques

```c#
int[] = new int[4] {
  15,
  9,
  150,
  1
}
```

#### Typage complexe

##### Tableaux dynamiques

```c#
List<int> = new List<string>();
List<int> = new List<string>() { "France", "Belgique"};

list.Add(element);
list.RemoveAt(indexElement);
```

```c#
List<Form> result = list.FindAll(f => f is NomClass);
```

###### Parcourir

```c#
for (int index = 0; index < tableau.Lenght; index++)
{
  Console.WriteLine(tableau[index]);
}

foreach(int item in items)
{
  Console.WriteLine($"Un des items : {item}");
}

// Lorsqu'on veut supprimer les éléments d'un tableau, on parcours à l'envers
int listCount = Source.Count;

for (int index = listCount - 1; i >= 0; i--)
{
  Target.Add(Source[index]);
  Source.RemoveAt(index);
}

// Ou
while(Source.Count > 0)
{
  Target.Add(Source[index]);
  Source.RemoveAt(index);
}
```

###### Vérifier si le contenu existe

```c#
using System.Linq;

variables.Contains(content);
```

##### Dictionnaires (tuple)

```c#
Dictionary<string, int> jsonData = new Dictionary<string, int>();
jsonData.Add("data", 10);
```

#### Typage génériques

```c#
// "where T:Form" T doit déscendre de Form
// "new()" Le type doit avoir comme constructeur par défaut
public class AppBuilder<T> where T:Form, new()// T remplace le type qui sera envoyé à la construction de l'object
{

}

AppBuilder<ChildForm> monForm = new AppBuilder<ChildForm>();
```

#### Cast

Forcer des nombres dans un certain format :

```c#
1000f; // en float
1000d; // en double
```

Parcer des variables de nombre :

```c#
double nbDouble = (double)nbInt;
int nbInt = (int)nbDouble;

bool resultParse = Int32.TryParse(varToParse, out newVarParsed);
```

```c#
// si sender n'est pas un bouton, alors le programme plante
Button btn = (Button)sender; 
// si sender n'est pas de type Bouton, alors on lui attribut la valeur null
btn = sender as Button;
// On enregistre directement le cast la procédure renvoie si le cast à été réalisé
sender is Button btn

// Dans le premier cas
try {
  Button btn = (Button)sender; 
}
catch() {
  // ...
}

// Dans le deuxième cas
btn = sender as Button;
if (btn != null)
{
  // ...
}
else
{
  // ...
}

// Dans le troisième cas
if (sender is Button btn)
{
  // ...
}
else
{
  // ...
}
```

##### Methodes avec cast

```c#
public static void Download(Uri uri)
{
  
}

public static void Download(object? uri)
{
  Download((Uri)uri);
}

// Ancienne version du C#, non fonctionnelle à présen
public static void Download(object? uri) : this((Uri)uri)
{
  
}
```

#### Enumerations

```c#
public enum TimeFrequency
{
    Monthly = 1,
    BiMonthly = 2,
    Quarterly = 3,
    SemiAnnual = 6,
    Annual = 12
}

TimeFrequency repaymentFrequency = TimeFrequency.Monthly;
```

##### Une énumération depuis une chaine de caractère

```c#
// Levels est une énumération
// On récupére la chaine de caractère depuis une énumération
cbxLevel.DataSource = Enum.GetNames<Levels>();
```

```c#
// On obtient une énumération depuis la chaine de caractère
Level = (Levels)Enum.Parse<Levels>(cbxLevel.SelectedItem.ToString())
```

##### Enumeration avec des chaines de caractère

```c#
public enum Levels
{
    [Description("InfBac")]
    InfBac = 30,
    [Description("Bac")]
    Bac = 40,
    [Description("Bac+1")]
    BacPlus1 = 50,
    [Description("Bac+2")]
    BacPlus2 = 60,
    [Description("Bac+3")]
    BacPlus3 = 70,
    [Description("Bac+4")]
    BacPlus4 = 80,
    [Description("Bac+5")]
    BacPlus5 = 90,
    [Description("SupBac+5")]
    SupBacPlus5 = 100
}
```

```c#
using System.Reflection;

public static class EnumExtensions
{
  public static string GetDescription(this Enum enumValue)
  {
    Type enumType = enumValue.GetType();

    MemberInfo[] enumValueInfo = enumType.GetMember(enumValue.ToString());

    // If we don't find any enumeration value,
    // we return a generic name
    if ((enumValueInfo.Length < 1))
    {
      return enumValue.ToString();
    }

    object[] descriptionAttribute = enumValueInfo[0]
      .GetCustomAttributes(typeof(DescriptionAttribute), false);

    // If there is no description attribute,
    // we return a generic name
    if (!descriptionAttribute.Any())
    {
      return enumValue.ToString();
    }

    // Return the description value as string
    return ((DescriptionAttribute)descriptionAttribute.ElementAt(0)).Description;
  }
}
```

```c#
// Affichage de l'ensemble des descriptions d'une énumération
List<string> listNameEnum = new List<string>();

foreach (Levels levels in Enum.GetValues(typeof(Levels)))
{
  listNameEnum.Add(EnumExtensions.GetDescription(levels));
}
```

### Syntaxe de base

#### Boucles

#### Conditions

```c#
if (a = 10)
{
  // ...
}
else if ()
{
  // ...
}
else
{
  // ...
}
```

```c#
string value = isOk() ? 10 : String.Empty; 
```

```c#
// Si error vaut null, alors elle prend la valeur "Valeur par défaut"
error = error ?? "Valeur par défaut";
```

### Orienté objets

#### Classes

Le visibilité `internal` permet d'accéder à la classe uniquement dans le namespace.

```c#
manager = new ListManager()
{ // Les attributs publiques sont accessibles lors de l'instanciation de la classe
  Source = "toto",
  Target = "tata
  };
```

##### Constructeur

```c#
public class Production
{
  public Production(TypeCaisse type, int quantiteVoulu)
  {
    // ...
  }
}
```

Surcharge de constructeur :

```c#
public class Production
{
  public Production(TypeCaisse type, int quantiteVoulu)
  {
    // ...
  }

  public Production(TypeCaisse type) : this(type, 10000)
  {
  }
}
```

Constructeur par copie, utile lors du clonage d'un objet :

```c#

public class Production
{
  public Production()
  {
    Name = "Test";
  }
  
  public Production(Production other)
  {
    Name = other.Name;
  }
}
```

##### Attributs

###### Initialiser dans le constructeur `readonly`

Possibilité de modifier la variable uniquement dans le constructeur.

```c#
public class Production
{
  private readonly TypeCaisse _type; // Modifiable uniquement dans le constructeur
  private double _tauxDefautGlobal;

  public Production(TypeCaisse type)
  {
    _type = type;
    _tauxDefautGlobal = 0;
  }
}
```

Ou en passant par les accesseurs :

```c#
public class Production
{
  private TypeCaisse Type { get; init; } // Modifiable uniquement dans le constructeur
  private double _tauxDefautGlobal;

  public Production(TypeCaisse type)
  {
    Type = type;
    _tauxDefautGlobal = 0;
  }
}
```

##### Getters / Setters
Automatique : clique droit sur l'attribut, Quick action and refactoring, Encapsulate field.

```c#
public partial class Form1 : Form
{
	private string _attribut2;
    
	private int Attribut1 { get; set; }
    private string Attribut2
    {
        get => _attribut2;
        private set => _attribut2 = value;
    }
	public int Attribut3 { get; private set; } // visibilité interne doit être moins forte
	private int Attribut4 { get; init; } // On ne peut le modifier uniquement dans le constructeur
}
```

#### Statique

On utilise les méthodes statiques dans 2 cas :

1. lorsqu'on n'accéde à aucune données à l'instance de la classe
2. On souhaite définir un attribut commun à l'ensemble des instances de la classe.

#### Classes abstraites

```c#
public abstract class IFormBuilder
{
  public void virtual MethodModifiableParEnfant() { wait 0; }
  public void MethodNonModifiable() { wait 0; }
  public abstract void MethodAModifier();
}
```

override permet d'appeler la methode du parent.
new : on remplace la methode du parent

#### Interface

```c#
public interface IFormBuilder
{
  void CreateInstance();
}
```

### Exceptions

On gére les exceptions des methodes utilisé par rapport à ce qu'il peut générer.

On les mets dans le même ordre que ce qui est affiché.

On rajoute à la fin la gestion des erreurs génériques.

### Délégués

Permet de découper les objets : éviter les liens entre plusieurs classes / objets.

Lors de la création d'un délégué, c'est comme créer un classe : on pourra instancier le délégué.

Ils peuvent également être utilisé dans le cadre d'utilisation de plusieurs threads.

Plus d'informations sur :

- <https://www.geeksforgeeks.org/c-sharp-delegates/?ref=lbp>

```c#
// Fichier avec notre classe utilisant le délégué
// et avec la définition du délégué

namespace CoursDelegues
{
  // Il est recommandé de définir le délégué dans le même namespace
  public delegate void DisplayNumber(int num); // création du délégué

  public class SquareCalculator
  {
    private int number;
    // On enregistre de délégué ici
    public DisplayNumber callback;

    // On sauvegardera le callback depuis le constructeur avec le typage du délégué
    public SquareCalculator(int _number, DisplayNumber callback)
    {
      number = _number;
    }

    public SquareIt()
    {
      number *= number;

      // Utilisation du délégué stocké dans callback
      if (callback != null)
      {
        callback(number);
      }
    }
  }
}
```

```c#
// Fichier utilisant le délégué

IWriter writer = new ResultTextWriter();

// WriteResult() à la même signature que le délégé "DisplayNumber"
DisplayNumber callback = new DisplayNumber(writer.WriteResult); // On transfére une référence de la méthode

// On pourra également utilisé "callback2"
IToto toto = new TotoDisplay();
DisplayNumber callback2 = new DisplayNumber(toto.Display);

SquareCalculator calc = new SquareCalculator(2, callback);

// Se serat "callback" qui sera executé
calc.SquareIt();

// On change la référence du délégué
calc.callback = callback2;

// Se serat "callback2" qui sera executé
calc.SquareIt();
```

Pour l'utilisation en multi-thread :

```c#
// Fichier avec notre classe utilisant le délégué
// et avec la définition du délégué

namespace CoursDelegues
{
  public delegate void DisplayNumber(int num);

  public class SquareCalculator
  {
    private int number;
    public DisplayNumber callback;

    public SquareCalculator(int _number, DisplayNumber callback)
    {
      number = _number;
    }

    public SquareIt()
    {
      number *= number;

      if (callback != null)
      {
        // IL FAUDRA NE PAS OUBLIER DE RAJOUTER LE "Invoke()"
        callback.Invoke(number);
      }
    }
  }
}
```

```c#
// Fichier utilisant le délégué

IWriter writer = new ResultTextWriter();

DisplayNumber callback = new DisplayNumber(writer.WriteResult);

IToto toto = new TotoDisplay();
DisplayNumber callback2 = new DisplayNumber(toto.Display);

calc.SquareIt();

// "threadStart()" est un délégué
// Parameterized.. est un délégué
Thread th1 = new Thread(new threadStart());

Thread th = new Thread(() =>
{
  // Erreur : 
  SquareCalculator calc = new SquareCalculator(2, callback);
  calc.SquareIt();
  
  Thread.Sleep(2000);
  
  calc.callback = callback2;
  calc.SquareIt();
}
                       
th.Start();

Console.WriteLine("Ecrit avant le contenu de l'autres thread");
```

### Evenements

#### Création

```c#
/* Program.cs */
using EventHandler;

Console.WriteLine("Hello, World!");

// On créer notre personne
Person toto = new Person("Toto");

// Méthode qui va s'abonner à l'événement
public void ListenPerson(object sender, PropertyChangedEventArgs e)
{
  if (sender is Person person)
  {
    Console.WriteLine("Mon nom a changé : je m'appelle à présent " + person.Name);
  }
}

public void SayToto(object sender, PropertyChangedEventArgs e)
{
  Console.WriteLine("toto");
}

toto.OnNameChangedEvent += ListenPerson;
toto.OnNameChangedEvent += SayToto;

// Chaque changement de nom execute
// les événements abonnés à
// toto.OnNameChangedEvent
toto.Name = "Charle";
toto.Name = "Xoxo";
toto.Name = "Xoxoxo";

Console.ReadLine();
```

```c#
/* Person.cs */
using System;
using System.Collections.Generic;
using System.ComponentModel; // pour PropertyChangedEventHandler
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace EventHandler
{
    internal class Person
    {
        // Attribut stockant une collection d'événements
        public event PropertyChangedEventHandler OnNameChangedEvent;
        private string _name;

        public string Name
        {
            get
            {
                return _name;
            }
            set
            {
                _name = value;
                // On execute toutes les methodes abonnées
                // à l'événement "OnNameChangedEvent"
                ExecuteOnNameChangedEvent();
            }
        }

        public Person(string name)
        {
            Name = name;
        }

        // La methode qui va executer tous les événements abonnées
        private void ExecuteOnNameChangedEvent()
        {
            if (OnNameChangedEvent != null)
            {
                // L'execution des événements
                OnNameChangedEvent( // Ensuite on spécifie les données à transmettre aux appellants :
                  this, // va représenté le "object sender"
                  new PropertyChangedEventArgs(nameof(Name)) // va représenté le "PropertyChangedEventArgs e"
                );
            }
        }
    }
}
```

### Taches parallèles

<https://devstory.net/10553/csharp-multithreading>

- pour opération lourde comme serialisation
- quand on veut plusieurs taches en parallèles (plusieurs processus en parallèle)

![Example de ligne de vie de deux processus](/numerique/programmation/7600154.png)

#### Fonction asynchrone `async`

permet de bloqué le contexte du "await" en le mettant de coté et en executant le reste du code.

Si une méthode renvois `Tasks<NomClass>` alors c'est que la methode est asynchrone et il faut utiliser le mot clé `await`.


#### Les processus (thread)

```c#
// Envoie en tant que délégué
// On ne peut envoyer qu'un seul parametre à la methodes de type objet
Thread t = new Thread(p.Executer);

// Envoie en tant que fonction lambda
Thread t = new Thread(() => {
	p.Executer();
}); 

```

#### Les taches (Tasks)

```c#
public void Start()
{
  Task.Run(() => BackgroundAction());
}
```

#### CancelationToken

```c#
internal class MyDutyTask
{
  private CancellationTokenSource cancelToken;

  public MyDutyTask()
  {
    cancelToken = new CancellationTokenSource();
  }

  public void Start()
  {
    Task.Run(
      () => BackgroundAction(),
      cancelToken.Token
    );
  }

  public void BackgroundAction()
  {
    try
    {
      do
      {
        // On remplace le sleep par une méthode qui gére le CancellationToken
        // Thread.Sleep(1000);
        cancelToken.Token.WaitHandle.WaitOne(1000);
        
        cancelToken.Token.ThrowIfCancellationRequested();
      } while (true);
    }
    catch(OperationCanceledException)
    {
      cancelToken.Dispose();
    }
  }

  public void Stop()
  {
    cancelToken.Cancel();
  }
}
```

## Projets

Recommandations dans le nommage des différents projets : il est intéréssant d'ajouter un point pour avoir le même namespace partagé.

- `NomProjet.App` : Winform

- `NomProjet.Lib` : Library

- `NomProjet.Test` : Test WinTest

### Générer des UMLs

1. Ajouter un nouveau "item" dans votre projet
1. Chercher et selectionner "Class Diagram"

Vous pouvez ensuite ajouter vos classes existantes avec un glissé déposé, ou créer vos classes dans le diagramme, qui seront également créer dans votre projet.

### Ajout d'une bibliothèque / DLL

Il faut ajouter un nouveau projet, selectionner "Bibliothèque de classe" ou "Class Library".  
Il faut également selectionner la même version du framework .Net.

Il faut ensuite ajouter une référence dans le projet d'origine.

### Test unitaires

Les tests unitaire permettent de tester une méthode, une classe, etc...

Ajout d'un projet : MSTest test project

On doti ajouter une référence aux librairies à tester (dépendance) : clique droit sur notre projet, add, Project Reference puis le projet.

Pour executer le test : view > Test explorer  
Puis on fait un clique droit sur le test > run

```c#
namespace TestValidation
{
    [TestClass]
    public class UnitTest1
    {

        [TestMethod] // Permet d'inclure les resultats dans le test
        public void TestValidationName()
        {
            // On réalise le test
            NameValidation nameValidation = new NameValidation();
            string nameValid = "toto";
            bool testValid = nameValidation.IsValid(nameValid);

            // On vérifie si le resultat est bien celui qu'on attend
            Assert.IsTrue(testValid);
            Assert.IsFalse(testValid);
            // ou, similaire à au dessus
            Assert.AreEqual(testValid, true);
          
          Assert.ThrowsException<ArgumentException>(new Action(PlayerInstanciationWithErrors));
        }
      
        private void PlayerInstanciationWithErrors()
        {
            Player p = new Player("Jusss", DateTime.Now, -50, 1, 0);
        }
    }
}
```

**Attention !** Lors d'un test unitaire pour des methodes liées à l'API WinForm, il faut modifier le fichier de configuration du projet de test unitaire (fichier ".csproj").

On remplace la ligne suivante :
```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net6.0</TargetFramework> <!-- ici -->
  </PropertyGroup>
</Project>
```
Par :
```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net6.0-windows</TargetFramework> <!-- ici -->
  </PropertyGroup>
</Project>
```

### Les assets

#### Ressources

On peut gérer n'importe quel ressources comme des images, des fichiers HTML CSS JS, des messages...

On se gére des ressources pour les stocker.

Pour ce faire : clique droit sur le projet > propriété > Ressources > Create or open assembly ressources

On créer ensuites nos différentes ressources.

Pour les utiliser dans notre code :

```c#
// On défini un paramètre "NOM_DE_MA_RESSOURCE"
// puis on peut y accéder :
Properties.Resources.NOM_DE_MA_RESSOURCE

// Ou
using NOM_NAMESPACE.Properties;
Resources.NOM_DE_MA_RESSOURCE
```

#### Paramètres (settings)

Gérer des paramètres stocké dans divers types de variables.

On initialise les settings : clique droit sur le projet > propriété > Settings > Create or open application settings

On créer ensuite nos différents paramètres.

Pour les utiliser dans notre code :

```c#
// On défini un paramètre "NOM_DE_MA_SETTINGS"
// puis on peut y accéder :
Properties.Settings.Default.NOM_DE_MA_SETTINGS;

// Ou
using NOM_NAMESPACE.Properties;
Settings.Default.NOM_DE_MA_SETTINGS;
```

scope : si utilisateur, chaque session a accés à ses paramètres.
Application : tous les utilisateurs partages les mêmes paramètres, si l'un modifier, l'autre le modifier.

#### ViewModel

Example :

```c#
public class JobSeeker // Modèle
{
  private static int lastId = 0;
  public int Id { get; set; }
  public string FirstName { get; set; }
  public string LastName { get; set; }
  public Levels Level { get; set; }
  public int RegistrationYear { get; set; }
  public string? LastDiplomaName { get; set; }
  public int? LastDiplomaYear { get; set; }
  public string Employability { get { return Level + "%"; } }

  public JobSeeker()
  {
    Id = ++lastId;
  }

  public JobSeeker(JobSeeker other)
  {
    FirstName = other.FirstName;
    LastName = other.LastName;
    RegistrationYear = other.RegistrationYear;
    Level = other.Level;
    LastDiplomaName = other.LastDiplomaName;
    LastDiplomaYear = other.LastDiplomaYear;
    Id = other.Id;
  }
}
```

```c#
public class JobSeekerViewModel: JobSeeker
{ 
    private readonly Regex regexNames = new Regex(@"^[a-zA-Z]+(?:\s[a-zA-Z]+)*$");
    private readonly Regex regexDiploma = new Regex(@"^[a-zA-Z]+(?:\s[a-zA-Z]+)*$");

    public bool IsValid()
    {
        if (!regexNames.IsMatch(LastName) || !regexNames.IsMatch(FirstName))
        {
            return false;
        }

        if (LastDiplomaName is not null && !regexDiploma.IsMatch(LastDiplomaName))
        {
            return false;
        }

        RegistrationYear = DateTime.Now.Year;

        if (
            LastDiplomaYear < RegistrationYear - 60
            || LastDiplomaYear > RegistrationYear + 2
        )
        {
            return false;
        }

        return true;
    }
}
```

```c#
viewModel = new JobSeekerViewModel()
{
  FirstName = tbFirstName.Text,
  LastName = tbLastName.Text,
  Level = (Levels)cbxLevel.SelectedItem,
  LastDiplomaName = tbDiplomaName.Text,
  LastDiplomaYear = Convert.ToInt32(tbDiplomaYear.Text),
  RegistrationYear = DateTime.Now.Year
  };

if (viewModel.IsValid())
{
  jobSeeker = new JobSeeker(viewModel);
}
```

## Interfaces utiles

### IDisposable (jettable)

Lors de l'implémentation du IDisposable, on peut libérer les ressources non managés (methode `Dispose()`).

C'est souvent le cas pour le code tournant en arriére plan, ou l'accés à des fichiers et documents.

Lors d'une utilisation d'un object implémentant un IDisposable, on peut utilisé le mot clé `using` pour automatiquement libérer les ressources :

```c#
// HttpListener implémente "IDisposable"
using (server = new HttpListener())
{
	// On utilise notre object "server"
}
// On n'a plus besoin de "server" après le "using"
// C# invoque automatiquement Dispose()
```

```c#
partial class Form1
{
  /// <summary>
  ///  Required designer variable.
  /// </summary>
  private System.ComponentModel.IContainer components = null;

  /// <summary>
  ///  Clean up any resources being used.
  /// </summary>
  /// <param name="disposing">true if managed resources should be disposed; otherwise, false.</param>
  protected override void Dispose(bool disposing)
  {
    if (disposing && (components != null))
    {
      components.Dispose();
    }
    base.Dispose(disposing);
  }
}
```

## Classes utiles

### Regex

```c#
using System.Text.RegularExpressions;

Regex regexControl = new Regex("");
```

On peut mettre un `@` pour éviter de devoir echapper les caractères speciaux.

```c#
new Regex(@"^[\w]{2,30}$");
regexRule.IsMatch("Une chaine à tester");
```

### Le constructeur de chaine de caractère (StringBuilder)

```c#
using System.Text;

builder = new StringBuilder();
builder.Clear();
builder.Append("une chaine");
builder.Insert(indexInt, "une chaine ");
builder.AppendLine("une nouvelle ligne");
builder.ToString();
```

### Minuteur de temps (Stopwatch)

```c#
stopwatch = new Stopwatch();

// On démarre
stopwatch.Start();

// On arréte
stopwatch.Stop();

// On récupére le temps en secondes
(stopwatch.ElapsedMilliseconds / 1000.0).ToString("##.###");
```

### Les dates (DateTime)

#### Cast en chaine de caractère

```c#
DateTime.Now.ToString("MM/dd/yyyy") 	// 05/29/2015
DateTime.Now.ToString("dddd, dd MMMM yyyy") 	// Friday, 29 May 2015
DateTime.Now.ToString("dddd, dd MMMM yyyy") 	// Friday, 29 May 2015 05:50
DateTime.Now.ToString("dddd, dd MMMM yyyy") 	// Friday, 29 May 2015 05:50 AM
DateTime.Now.ToString("dddd, dd MMMM yyyy") 	// Friday, 29 May 2015 5:50
DateTime.Now.ToString("dddd, dd MMMM yyyy") 	// Friday, 29 May 2015 5:50 AM
DateTime.Now.ToString("dddd, dd MMMM yyyy HH:mm:ss") 	// Friday, 29 May 2015 05:50:06
DateTime.Now.ToString("MM/dd/yyyy HH:mm") 	// 05/29/2015 05:50
DateTime.Now.ToString("MM/dd/yyyy hh:mm tt") 	// 05/29/2015 05:50 AM
DateTime.Now.ToString("MM/dd/yyyy H:mm") 	// 05/29/2015 5:50
DateTime.Now.ToString("MM/dd/yyyy h:mm tt") 	// 05/29/2015 5:50 AM
DateTime.Now.ToString("MM/dd/yyyy HH:mm:ss") 	// 05/29/2015 05:50:06
DateTime.Now.ToString("MMMM dd") 	// May 29
DateTime.Now.ToString("yyyy’-‘MM’-‘dd’T’HH’:’mm’:’ss.fffffffK") 	// 2015-05-16T05:50:06.7199222-04:00
DateTime.Now.ToString("ddd, dd MMM yyy HH’:’mm’:’ss ‘GMT’") 	// Fri, 16 May 2015 05:50:06 GMT
DateTime.Now.ToString("yyyy’-‘MM’-‘dd’T’HH’:’mm’:’ss") 	// 2015-05-16T05:50:06
DateTime.Now.ToString("HH:mm") 	// 05:50
DateTime.Now.ToString("hh:mm tt") 	// 05:50 AM
DateTime.Now.ToString("H:mm") 	// 5:50
DateTime.Now.ToString("h:mm tt") 	// 5:50 AM
DateTime.Now.ToString("HH:mm:ss") 	// 05:50:06
DateTime.Now.ToString("yyyy MMMM") 	// 2015 May
```

#### Cast de chaine de caractère en DateTime

```c#
DateTime dateValue;
string dateString = "2/16/2008 12:15:12 PM";
try {
  dateValue = DateTime.Parse(dateString);
  Console.WriteLine("'{0}' converted to {1}.", dateString, dateValue);
}
catch (FormatException) {
  Console.WriteLine("Unable to convert '{0}'.", dateString);
}
// '2/16/2008 12:15:12 PM' converted to 2/16/2008 12:15:12 PM.

// Parse string with date but no time component.
dateString = "2/16/2008";
try {
  dateValue = DateTime.Parse(dateString);
  Console.WriteLine("'{0}' converted to {1}.", dateString, dateValue);
}
catch (FormatException) {
  Console.WriteLine("Unable to convert '{0}'.", dateString);
}
// '2/16/2008' converted to 2/16/2008 12:00:00 AM.
```

Parse avec les informations culturelles :

```c#
CultureInfo culture = CultureInfo.CreateSpecificCulture("fr-FR");

string[] dateStrings = {"01/10/2009 7:34 PM",
						"10.01.2009 19:34",
                        "10-1-2009 19:34" };

foreach (string dateString in dateStrings)
{
  try {
    dateValue = DateTime.Parse(dateString, culture);
    Console.WriteLine("   Converted '{0}' to {1}.",
                      dateString, dateValue.ToString("f", culture));
  }
  catch (FormatException) {
    Console.WriteLine("   Unable to convert '{0}' for culture {1}.",
                      dateString, culture.Name);
  }
}
/*
Converted '01/10/2009 7:34 PM' to jeudi 1 octobre 2009 19:34.
Converted '10.01.2009 19:34' to samedi 10 janvier 2009 19:34.
Converted '10-1-2009 19:34' to samedi 10 janvier 2009 19:34.
*/
```

```c#
string dateFormat = "dd/MM/yyyy";
Console.Write($"Veuillez entrer une date au format : {dateFormat}");
string userInputDate = Console.ReadLine();
              
try {
  DateTime dt = DateTime.ParseExact(
  	userInputDate,
    dateFormat,
    CultureInfo.InvariantCulture
  );
}
catch(ArgumentNullExcetion e)
{
  Console.WriteLine("Veuillez entrer une date");
}
catch (FormatException e)
{
  Console.WriteLine(e.Message);
}
```

### Arreter une application

```c#
Application.Exit(); // Arréter l'application

Environment.Exit(0); // Fermer l'ensemble des applications du même environement
// Sauf si nécéssaire, à éviter
```

### Serialization JSON

```c#
List<Car> cars = Car.getCars();

string json = JsonSerializer.Serialize(cars); // serialiser un objet

List<Car> newCars = JsonSerializer.Deserialize<List<Car>>(json); // transformer un json serialiser en objet

byte[] rep = Encoding.UTF8.GetBytes(json.ToCharArray()); // récupérer une chaine de caractère de json sérialiser
// pour pour le transférer
```

### Gestion de fichier

#### Les chemins

Choisir un dossier avec les droits en lecture/écriture :

```bash
$HOME\AppData\{Local(compte locaux),LocalRow (commun,Roaming(fonctionne compte itinérant, données stocké sur le serveur car partagé avec un AD sur un reseau}

# $HOME correspond au dossier de l'utilisateur
```

- Local : compte local (`Environment.SpecialFolder.LocalApplicationData`)
- LocalRow : ?
- Roaming : données partagé si l'utilisateur est un compte itinérant, les données sont stocké sur le Windows AD et synchronisés.
- Bureau : `Environment.SpecialFolder.Desktop`
- Dossier utilisateur : `Environment.SpecialFolder.UserProfile`

```c#
Environment.SpecialFolder // Classe contenant un ensemble de chemin courant utilisé dans Windows

// Là où l'on va sauvegarder les données de l'application :
string localAppPath = Environment.GetFolderPath(Environment.SpecialFolder.LocalApplicationData);

// On génére un chemin avec l'ajout d'un fichier
string jsonPath = Path.Combine(localAppPath, $"fileName-{Id.ToString()}.json");
```

#### Ecrire le fichier

```c#
File.WriteAllText(jsonPath, jsonContent, Encoding.UTF8);
```

#### Lire un fichier
```c#
jsonContent = File.ReadAllText(jsonPath, Encoding.UTF8);
```

### Serveur web

```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Net;
using System.Text;
using System.Threading.Tasks;

namespace HttpServerExample
{
    public class WebServer
    {
        Boolean running; // Gére si on arréte le serveur
        HttpListener server;

        public async void Start()
        {
            // Dans le bloc "using", on utilise notre serveur
            // HttpListener implémentant IDisposable,
            // il sera libéré à la fin du bloc de using
            using (server = new HttpListener())
            {
                // On initialise notre serveur
                server.Prefixes.Add("http://localhost:8000/");
                server.Start();
                running = true;

                // Ici on attent des requetes t'utilisateurs
                while(running)
                {
                    var context = await server.GetContextAsync();

                    // On créer notre processus
                    Thread t = new Thread(OnRequest);
                  	Thread t = new Thread(new ParameterizedThreadStart(OnRequest));

                    // On envoie le contexte au processus
                    t.Start(context);
                }
            }
        }

        // Pour stoper notre serveur
        public void Stop()
        {
            running = false;
        }

        // Methode executé dans un processus pour chacune des requetes
        public void OnRequest(object? request)
        {
            if (request is HttpListenerContext ctx)
            {
                // Message affiché à chaque requéte
                MessageBox.Show("Nouvelle requete !");

                string page = "<html>Bonjour !</html>";

                // On convertie les caractères en octet UTF-8 (binaire)
                byte[] response = Encoding.UTF8.GetBytes(
                    // On convertie notre chaine de caractère en tableau de caractère
                    page.ToCharArray()
                );

                // On envoie la réponse au client (HTTP)
                ctx.Response.Close(response, true);
            }

        }
    }
}
```

### Gérer les ressources externes (URI)

```c#
uri = new Uri(txtUrl.Text);
```

### Fichiers

#### Fichier existe

```c#
string path;

if (!Directory.Exists(path))
{
  // ...
}
```

```c#
EnumerationOptions options = new EnumerationOptions()
{
  IgnoreInaccessible = true, // RecurseSubdirectories = true
};
string[] directories = Directory.GetDirectories(path, "*", options);
string[] files 
```

## Organisation avancé

```
- Formulaire (interface graphique)
  |
  |
  |
- Unité de travail (Work unit)
  |
  |
  |
- ViewModel
  |
  |
  |
- Model
  |
  |
  |
- Liaison de donnée avec la BDD (Factory)
```

## API

### Winform
[Winform C#](https://wiki.akipe.fr///books/formation-cda/page/winform-c)

## Outils

### Visual Studio

#### Raccourcis clavier

- Reformater le code
<kbd>CTRL</kbd> + <kbd>K</kbd> & <kbd>CTRL</kbd> + <kbd>D</kbd>
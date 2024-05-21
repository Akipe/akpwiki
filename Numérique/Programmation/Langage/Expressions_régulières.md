---
title: Expressions régulières
description: 
published: true
date: 2024-05-21T17:06:31.463Z
tags: 
editor: markdown
dateCreated: 2024-05-21T14:14:49.262Z
---

# Expressions régulières

Également appelè ***Regex***.

- <https://www.youtube.com/watch?v=XPrnB_v4NX8&t=226>
- regex isn't hard <https://timkellogg.me/blog/2023/07/11/regex>

Présentation d'une regex classique :

`(?x)([Rr]egexp?)\?` :

- `(?x)` : meta composant
- `([Rr]egexp?)` : groupe
- `[Rr]` : classe de caractères
- `?` : quantifiers and other special tokens in blue
- `\?` : escaped characters

Il existe plusieurs formats différentes :

- PCRE2
- ECMAScript 5

## Langage

### Ancres

Les différents modes :

- *normal* : les ancres sont défini entre le début et la fin de l'ensemble de la chaine de caractère.
- *multi ligne* : les ancres sont défini aux débuts et aux fin de chaques lignes.

| | |
|:-:|-|
| `^` | Début de la ligne ou de la chaine de caractère
| `$` | Fin de la ligne ou de la chaine de caractère
| `^ (...) $` | Doit être la chaine de caractère

| | | |
|:-:|:-:|-|
| `\` | `[\\]` | pour échaper des caractères : selectionner le caractère `\` |
| `[]` | `[ab]` | Tout ce qui est dans le bloc : les lettres `a` & `b` |
| `[^]` | `[^ab]` | Tout ce qui n'est pas lettre `a` et `b`  |

| | |
|:-:|-|
| `\A` | Début de la chaine de caractère |
| `\Z` | Fin de la chaine de caractère |
| `\b` | Limite de mot, entre les caractères reconnu en `\w` |
| `\B` | Not word boundary |
| `\<` | Début d'un mot |
| `\>` | Fin d'un mot |

### Caractères

| | |
|:-:|-|
| `\s` | Espace blanc (ainsi que les tabs et les retours à la ligne) |
| `\S` | Pas d'espace blanc |
| `\d` | Chiffres |
| `\D` | Pas de chiffres |
| `\w` | Les mots alphabetique + underscore |
| `\W` | Pas de mots alphabetique + underscore |
| `\x` | Chiffres hexadecimal |
| `\xhh` | Chiffres hexadecimal (hh) |
| `\Oxxx` | Chiffre octet (xxx) |

Les retours à ligne différes des OS :

- Windows : `\r\n`
- Linux : `\n`

| | |
|:-:|-|
| `.` | Tous les caractères sauf nouvelle ligne `\n` |
| `\` | Echapper un caractère spéciaux |
| `\n` | Caractère nouvelle ligne |
| `\r` | Caractère chariot |
| `\t` | Caractère tab |
| `\v` | Caractère tab vertical |
| `\f` | Form feed |
| `\a` | Alarm |
| `[\b]` | Backspace |
| `\e` | Escape |
| `\N{name}` | Named Character |
| `\uFFFF` | Caractère unicode |
| `\x{FFFF}` | Caractère unicode |

- `\u20AC` ou `\x{20AC}` pour selectionner le caractère `€`

### Assertions

| | |
|:-:|-|
| `?!` | Negation |
| `?()` | Condition : si donc |
| `?()\|` | Condition : si donc alors |
| `?#` | Commentaires |
| `?!` | Negation |
| `?!` | Negation |
| `?!` | Negation |

### Alternation

Représente un **ou** logique :

- `cat|dog` : `About cats and dogs`

### Quantifieurs

| | |
|:-:|-|
| `?` | 0 ou 1 fois |
| `*` | 0 ou plusieurs fois |
| `+` | 1 ou plusieurs fois |

| | | |
|:-:|:-:|-|
| `{X}` |`{3}` | Exactement X fois |
| `{X,}` |`{3,}` | X fois ou plus |
| `{,X}` |`{,3}` | X fois ou moins |
| `{X,Y}` |`{3,5}` | Entre X et Y |

### Groupe

Les intervals sont inclusifs.

| | | |
|:-:|:-:|-|
| `(...)` | `(voiture)` | Une selection précise: `voiture` |
| `(...)?` | `(voiture)` | Qui n'est pas une selection précise: `voiture` |
| `[...]` | `[abc]` | Un interval : `a` ou `b` ou `c` |
| `[^...]` | `[^abc]` | Tout sauf l'interval : ni `a` ou `b` ou `c` |
| `-` | `[a-q]` | Les caractères entre `a` et `q` |
| `-` | `[A-Q]` | Les caractères en majuscules entre `A` et `Q` |
| `-` | `[0-5]` | les chiffres entre `0` et `5` |
| `(...\|...)` | `(voiture\|bateau)` | Selectionner "voiture" ou "bateau" |
| `(...\|...)?` | `(voiture\|bateau)?` | Ne pas selectionner "voiture" et "bateau" |

### Echappement de caractères spéciaux

### Caractères alphabétiques

La selection des caractères correspond à la suites de caractères des différents charsets (ASCII, UTF-8...).

| | |
|:-:|-|
| `[a-zA-Z]` | caractères simples |
| `[a-zA-ZÀ-ÿ]` | caractères simples et accentués |
| `[\w]` | caractères simples et accentués |

### Chiffres

| | |
|:-:|-|
| `[0-9]` | Chiffres |
| `\d` | Chiffres |

### Les modifieurs de patterns

| | |
|:-:|-|
| `g` | Selection global |
| `i` | Non sensible à la case |
| `m` | Multiligne |
| `s` | Traiter une chaine de caractère comme une ligne |
| `x` | Autoriser les commentaires et les espaces dans les patternes |

### Caractères spéciaux à échaper (metacharacters)

Par exemple, si l'on cherche "1+1=2", le patterne sera : `1\+1=2`

| |
|:-:|
|`^`|
|`[`|
|`.`|
|`$`|
|`{`|
|`*`|
|`(`|
|`\`|
|`+`|
|`)`|
|`\|`|
|`?`|
|`<`|
|`>`|

## Exemples de régles

- des lettres, chiffres et traits d'unions  
`([A-Za-z0-9-]+)`

- Alpahnumérique sans accent  
`^[0-9A-Za-z\s]+`

- Lettres sans accent  
`^[A-Za-z\s]+$`

- Lettres avec accents  
`^[A-Za-zàâÂäÄéÉèÈêÊëËîÎïÏôÔöÖ\s]+$`

- Lettres sans accent + tiret  
`^[A-Za-z\s\-]+$`

- Lettres avec accents + tiret  
`^[A-Za-zàâÂäÄéÉèÈêÊëËîÎïÏôÔöÖ\s\-]+$`

- Des dates : 21/3/2006  
`(\d{1,2}\/\d{1,2}\/\d{4})`

Ou plus précis : `^(([1-9]|[0-2][0-9]|3[0-1])\/([1-9]|1[0-2])\/\d{4})$`

- Date Française  
`^(([1-2]\d|0[1-9]|[3][0-1])\/([0][1-9]|[1][0-2])\/[2][0-9]\d{2})$`

- Code postal Français  
`^\d{5}$`

- Des extensions jpg, gif ou png  
`([^\s]+(?=\.(jpg|gif|png))\.\2)`

- couleurs hexadecimal  
`(#?([A-Fa-f0-9]){3}(([A-Fa-f0-9]){3})?)`

- adresse mail  
`(\w+@[a-zA-Z_]+?\.[a-zA-Z]{2,6})`

- un nombre entre 100 & 9999  
`\b[1-9][0-9]{2,4}\b`

- un nombre sans ou avec des décimal (jusqu'à 4)  
`^[\d]{1,}([,.]{1}[\d]{1,4})?$`  
(en C# : `$"^[\\d]{{1,}}([,.]{{1}}[\\d]{{1,{numberOfDecimal}}})?$"`)

- adresse IPv4 
`^([0-9])+\.([0-9])+\.([0-9])+\.([0-9])+`

## Ressources

### Outils de vérification

- <https://regex101.com/>

### Cheatsheet

- Guide pour débuter en Regex : <https://www.regular-expressions.info/quickstart.html>
- CheatSheet Microsoft Doc : <https://docs.microsoft.com/en-us/previous-versions/troubleshoot/winautomation/process-development-tips/text-manipulation/regular-expressions-cheat-sheet>
- [https://www.lucaswillems.com/fr/articles/25/tutoriel-pour-maitriser-les-expressions-regulieres](https://www.lucaswillems.com/fr/articles/25/tutoriel-pour-maitriser-les-expressions-regulieres)
- Liste de liens, de documentations et d'outils utiles pour les Regex : <https://github.com/aloisdg/awesome-regex>

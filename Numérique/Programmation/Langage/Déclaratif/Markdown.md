---
title: Markdown
description: 
published: true
date: 2024-05-21T18:29:26.378Z
tags: 
editor: markdown
dateCreated: 2024-05-21T18:29:26.378Z
---

# Markdown

## Syntax de base

### Titre

Simple :

```markdown
# Heading level 1
## Heading level 2
### Heading level 3
#### Heading level 4
##### Heading level 5
###### Heading level 6
```

Alternatif :

```markdown
Heading level 1
===============

Heading level 2
---------------
```

### Retour à la ligne

Pour ajouter une retour à la ligne, ajouter 2 ou plus d'espace à la fin de la ligne, et ajouter un retour à la ligne.

### Gras

```markdown
I just love **bold text**.
I just love __bold text__.
```

I just love **bold text**.  
I just love __bold text__.

### Italique

```markdown
Italicized text is the *cat's meow*.
Italicized text is the _cat's meow_.
```

Italicized text is the *cat's meow*.  
Italicized text is the _cat's meow_.

### Mot barré

```markdown
~~Scratch this.~~
```

~~Scratch this.~~

### Citation

```markdown
> Dorothy followed her through many of the beautiful rooms in her castle.
```

> Dorothy followed her through many of the beautiful rooms in her castle.

Sur de multiples lignes :

```markdown
> Dorothy followed her through many of the beautiful rooms in her castle.
>
> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.
```

> Dorothy followed her through many of the beautiful rooms in her castle.
>
> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.

Avec des sous citations :

```markdown
> Dorothy followed her through many of the beautiful rooms in her castle.
>
>> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.
```

> Dorothy followed her through many of the beautiful rooms in her castle.
>
>> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.


### Les listes

```markdown
1. First ordered list item
2. Another item
    * Unordered sub-list. 
1. Actual numbers don't matter, just that it's a number
    1. Ordered sub-list
4. And another item.
```

1. First ordered list item
2. Another item
    * Unordered sub-list. 
1. Actual numbers don't matter, just that it's a number
    1. Ordered sub-list
4. And another item.

```markdown
* Unordered list can use asterisks
* Test
- Or minuses
- Test
+ Or pluses
+ Test
```

* Unordered list can use asterisks
* Test
- Or minuses
- Test
+ Or pluses
+ Test


### Les liens

```markdown
<https://duckduckgo.com/>
```

<https://duckduckgo.com/>

An hyperlink not clickable:

```markdown
`https://duckduckgo.com/`
```

`https://duckduckgo.com/`

```markdown
[I'm an inline-style link](https://www.google.com)
```

[I'm an inline-style link](https://www.google.com)

```markdown
[I'm an inline-style link with title](https://www.google.com "Google's Homepage")
```

[I'm an inline-style link with title](https://www.google.com "Google's Homepage")

```markdown
[I'm a reference-style link][Arbitrary case-insensitive reference text]
```

[I'm a reference-style link][Arbitrary case-insensitive reference text]

```markdown
[I'm a relative reference to a repository file](../blob/master/LICENSE)
```

[I'm a relative reference to a repository file](../blob/master/LICENSE)

```markdown
[You can use numbers for reference-style link definitions][1]
```

[You can use numbers for reference-style link definitions][1]

```markdown
Or leave it empty and use the [link text itself].
```

Or leave it empty and use the [link text itself].

```
URLs and URLs in angle brackets will automatically get turned into links. 
http://www.example.com or <http://www.example.com> and sometimes 
example.com (but not on Github, for example).
```

Some text to show that the reference links can follow later.

```
[arbitrary case-insensitive reference text]: https://www.mozilla.org
[1]: http://slashdot.org
[link text itself]: http://www.reddit.com
```

[arbitrary case-insensitive reference text]: https://www.mozilla.org
[1]: http://slashdot.org
[link text itself]: http://www.reddit.com


### Images

Inline-style:

```markdown
![alt text](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 1")
```

![alt text](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 1")

Reference-style:

```markdown
![alt text][logo]
```

![alt text][logo]

```
[logo]: https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 2"
```

### Code

````markdown
```javascript
var s = "JavaScript syntax highlighting";
alert(s);
```
````

```javascript
var s = "JavaScript syntax highlighting";
alert(s);
```

````markdown
```python
s = "Python syntax highlighting"
print s
```
````

```python
s = "Python syntax highlighting"
print s
```

````markdown
```
No language indicated, so no syntax highlighting. 
But let's throw in a <b>tag</b>.
```
````

```
No language indicated, so no syntax highlighting. 
But let's throw in a <b>tag</b>.
```

### Note de bas de page

```markdown
Here is a simple footnote[^1].
```

Here is a simple footnote[^1].

```markdown
A footnote can also have multiple lines[^2].  
```

A footnote can also have multiple lines[^2].  

```markdown
You can also use words, to fit your writing style more closely[^note].
```

You can also use words, to fit your writing style more closely[^note].

```markdown
[^1]: My reference.
[^2]: Every new line should be prefixed with 2 spaces.  
  This allows you to have a footnote with multiple lines.
[^note]:
    Named footnotes will still render with numbers instead of the text but allow easier identification and linking.  
    This footnote also has been made with a different syntax using 4 spaces for new lines.
```

[^1]: My reference.  
[^2]: Every new line should be prefixed with 2 spaces.    
  This allows you to have a footnote with multiple lines.  
[^note]:  
    Named footnotes will still render with numbers instead of the text but allow easier identification and linking.  
    This footnote also has been made with a different syntax using 4 spaces for new lines.

### Tableau

Colons can be used to align columns:

```markdown
| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |
```

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

There must be at least 3 dashes separating each header cell.  
The outer pipes (|) are optional, and you don't need to make the 
raw Markdown line up prettily. You can also use inline Markdown.

```markdown
Markdown | Less | Pretty
--- | --- | ---
*Still* | `renders` | **nicely**
1 | 2 | 3
```

Markdown | Less | Pretty
--- | --- | ---
*Still* | `renders` | **nicely**
1 | 2 | 3

### Barre horizontal

Three or more...

Hyphens :

```markdown
---
```

---

Asterisks :

```markdown
***
```

***

Underscores :

```markdown
___
```

___

## HTML

```html
<dl>
  <dt>Definition list</dt>
  <dd>Is something people use sometimes.</dd>

  <dt>Markdown in HTML</dt>
  <dd>Does *not* work **very** well. Use HTML <em>tags</em>.</dd>
</dl>
```

<dl>
  <dt>Definition list</dt>
  <dd>Is something people use sometimes.</dd>

  <dt>Markdown in HTML</dt>
  <dd>Does *not* work **very** well. Use HTML <em>tags</em>.</dd>
</dl>


## Syntax étendue

### Rendu de touche de clavier

```markdown
<kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>Space</kbd>
```

<kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>Space</kbd>
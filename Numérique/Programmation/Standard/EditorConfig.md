---
title: EditorConfig
description: 
published: true
date: 2024-05-21T17:19:39.773Z
tags: 
editor: markdown
dateCreated: 2024-05-21T17:19:39.773Z
---

# EditorConfig

Permet de sauvegarder dans un fichier `.editorconfig` à la racine du projet une convention concernant un certain nombre de mise en page, comme le type de retrait (espace ou indentation), le nombre d'espace, le type de retours à la ligne... 

- <https://editorconfig.org/>

## Configuration

### Exemple depuis editorconfig.org

```ini
# .editorconfig

# top-most EditorConfig file
root = true

# Unix-style newlines with a newline ending every file
[*]
end_of_line = lf
insert_final_newline = true

# Matches multiple files with brace expansion notation
# Set default charset
[*.{js,py}]
charset = utf-8

# 4 space indentation
[*.py]
indent_style = space
indent_size = 4

# Tab indentation (no size specified)
[Makefile]
indent_style = tab

# Indentation override for all JS under lib directory
[lib/**.js]
indent_style = space
indent_size = 2

# Matches the exact files either package.json or .travis.yml
[{package.json,.travis.yml}]
indent_style = space
indent_size = 2
```

### Exemple perso

```ini
root = true

[*]
charset = utf-8
end_of_line = lf
indent_style = space
indent_size = 2
insert_final_newline = true
trim_trailing_whitespace = true
```

## Intégration

Voir <https://editorconfig.org/>.

### VSCode

<https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig>

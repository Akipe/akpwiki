---
title: Composer
description: 
published: true
date: 2024-05-21T14:10:12.442Z
tags: 
editor: markdown
dateCreated: 2024-05-21T14:10:12.442Z
---

# Composer

## Example

```json
{
  "name": "nom/projet",
  "description": "PHP client library for Network Ups Tools (NUT)",
  "type": "library",
  "keywords": ["nut", "network ups tools", "ups"],
  "license": "MIT",
  "authors": [
    {
      "name": "Nom prénom",
      "role": "Developer"
    }
  ],
  "require": {
    "php": ">=8.1"
  },
  "autoload": {
    "psr-4": {
      "Lepidoptaire\\": "src/"}
  }
}
```

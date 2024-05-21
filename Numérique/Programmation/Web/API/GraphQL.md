---
title: GraphQL
description: 
published: true
date: 2024-05-21T18:46:34.724Z
tags: 
editor: markdown
dateCreated: 2024-05-21T18:46:17.450Z
---

# GraphQL

- <https://dev.to/ryosuke/graphql-for-beginners-11m9>

```graphql
query test_julien {
  infrastructures(nom: "lt"){
    totalCount
    edges{ //noeux
      node {
      	nom
        libelle
      }
    }
  }
}
```
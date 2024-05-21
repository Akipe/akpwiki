---
title: PlantUML
description: 
published: true
date: 2024-05-21T18:34:01.352Z
tags: 
editor: markdown
dateCreated: 2024-05-21T18:34:01.352Z
---

# PlantUML

PlantUML permet de réaliser l'ensemble des diagrammes UML en textuelle : <https://plantuml.com/fr/>

Documentation :

- <https://plantuml.com/fr/commons>

## Exemple

### Diagramme de contexte

fichier ".puml" :

```puml
@startuml diagramme_contexte

left to right direction

package "Acteurs Principaux" as principaux {
  actor "humain 1" as csh << Humain >>
  actor "humain 2" as admin << Humain >>
}

package "Acteurs Secondaires" as secondaire {
  actor "humain 3" as rsp << Humain >>
  actor "systeme 1" as ldap << Système >>
  actor "systeme 2" as infra << Système >>
}

package "Système" as systeme {
  rectangle Application {
  }
}

principaux -- systeme
systeme -- secondaire

@enduml
```

## Compilateurs

### Visual Studio Code

Utiliser l'extension **PlantUML** de *jebbs* : <https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml>

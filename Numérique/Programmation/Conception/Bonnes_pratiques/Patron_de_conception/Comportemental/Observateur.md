---
title: Observateur
description: 
published: true
date: 2024-05-21T16:06:53.135Z
tags: 
editor: markdown
dateCreated: 2024-05-21T16:06:53.135Z
---

# Observateur

Qu'est ce ?

Patterne comportementale : s'occupe de relations entre objets

Permet de notifier le changement d'un objet vers un autre.

Permet d'éviter qu'un observateur ai à demander au sujet ses informations

Couplage faible

Observation dynamique

exemple : enchère en ligne

Enchère à observer.

```c#

```

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-09/scaled-1680-/zDk6dpepYLNSsvLh-image-1663235599333.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-09/zDk6dpepYLNSsvLh-image-1663235599333.png)

Avantage :
- classe faiblement couplé
- objet peuvent s'abonner ou se désabonné dynamiquement

Désavantage :
- Changement envoyé à tous les observateurs, même si le changement n'es pas intéréssant, donc + de traitement
- observateurs avertis dans l'ordre du tableau

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-09/scaled-1680-/PS8zY6G2xWcQPtyx-image-1663246083291.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-09/PS8zY6G2xWcQPtyx-image-1663246083291.png)

```c#
public void DevientNuageux()
{
  tempsActuel = temps.Nuageux;
  NotifierChangementTemps();
}

public void NotifierChangementTemps()
{
  foreach(IObservateurDeMeteo observateur in observateurs)
  {
    observateur.SeMettreAJour(this);
  }
}

public void SeMettreAJout(Meteo meteoObserve)
{
  if (meteoObserve.GetTemperature.Equals(Temps.Pluieux))
  {
   	// Je sort le parapluie 
  }
}
```

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-09/scaled-1680-/GnTbbwPumf9QhXJP-image-1663247049896.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-09/GnTbbwPumf9QhXJP-image-1663247049896.png)
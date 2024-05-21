---
title: État
description: 
published: true
date: 2024-05-21T16:06:06.601Z
tags: 
editor: markdown
dateCreated: 2024-05-21T16:06:06.601Z
---

# État

Surnom :

- *State* en anglais

## Exemples

### L'eau

Etats de l'eau :

- gazeux
  - si refroidi : liquide
  - si rechauffer : rien
- liquide
  - si refroidi : solide
  - si réchauffer : gazeux
- solide
  - si refroidi : rien
  - si rechauffer : liquide

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-09/scaled-1680-/e4twVyf2qZZurlfi-image-1662560176852.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-09/e4twVyf2qZZurlfi-image-1662560176852.png)

```c#
public class Eau
{
  	private IEtatEau etatEau;
  
  	public Eau()
    {
      	etatEau = new Liquide();
    }
  
  	public void Chauffer()
    {
      	etatEau.Chauffer();
    }
  
  	public void Refroidir()
    {
      	etatEau.Refroidir();
    }
}
```

```c#
public interface IEtatEau
{
	IEtatEau Chauffer();
    IEtatEau Refroidir();
}
```
```c#
public class Gazeux : IEtatEau
{
	public IEtatEau Chauffer()
    {
    	return this;
    }
    
    public IEtatEau Refroidir()
    {
    	return new Liquide();
    }
}
```
```c#
public class Liquide : IEtatEau
{
	public IEtatEau Chauffer()
    {
    	return new Gazeux();
    }
    
    public IEtatEau Refroidir()
    {
    	return new Solide();
    }
}
```
```c#
public class Solide : IEtatEau
{
	public IEtatEau Chauffer()
    {
    	return new Gazeux();
    }
    
    public IEtatEau Refroidir()
    {
    	return this;
    }
}
```

### Video

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-09/scaled-1680-/l4doRHG3DlSgGYoq-image-1662554979371.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-09/l4doRHG3DlSgGYoq-image-1662554979371.png)

```c#
// Exemple d'une classe ayant un etat
public class Video
{
	private IEtatVideo etatVideoCourant;
    
    public Video()
    {
    	etatVideoCourant = new VideoArretee();
    }
    
    public void MettreEnLecture()
    {
    	etatVideoCourant = etatVideoCourant.MettreEnLecture(this);
    }
    
    public void MettreEnPause()
    {
    	etatVideoCourant = etatVideoCourant.MettreEnPause(this);
    }
    
    public void MettreEnAlArret()
    {
    	etatVideoCourant = etatVideoCourant.MettreAlArret(this);
    }
  
  	private void VideoRun()
    {
      //...
    }
  
  	private void VideoPause()
    {
      //...
    }
  
  	private void VideoReset()
    {
      //...
    }
}
```

```c#
// Interface d'état
public interface : IEtatVideo
{
	IEtatVideo MettreEnLecture(Video contexte);
    IEtatVideo MettreEnPause(Video contexte);
    IEtatVideo MettreAlArret(Video contexte);
}
```

```c#
// Exemple d'une implémentation d'un état
public class Arreter : IEtatVideo
{
	public IEtatVideo MettreEnLecture(Video contexte)
    {
    	contexte.VideoRun();
    	return new VideoEnLecture();
    }
    
    public IEtatVideo MettreEnPause(Video contexte)
    {
    	// Vu que la video est à l'arret, aucune logique que de la mettre en pause 
    	return this;
    }
    
    public IEtatVideo MettreAlArret(Video contexte)
    {
    	// La video est déjà à l'arret
    	return this;
    }
}
```

```c#
// Client
Video video = new Video();

video.MettreEnLecture();
video.MettreEnPause();
video.MettreAlArret();
```

### Exemple lepidoptere

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-09/scaled-1680-/cAOZxZWevrcOqnyW-image-1662706029889.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-09/cAOZxZWevrcOqnyW-image-1662706029889.png)

[![](https://wiki.akipe.fr///uploads/images/gallery/2022-09/scaled-1680-/mL3L2SsPw7wCf1xP-image-1662706020792.png)](https://wiki.akipe.fr///uploads/images/gallery/2022-09/mL3L2SsPw7wCf1xP-image-1662706020792.png)

## Notes

patron comportement, changer lorsque son état change

Proche de l'automate fini :

Chaque changement d'un état à un autre est une transition, et tous les etats ne peuvent être accéder directement.

Exemple : sur un blog, un article peut :

1. Être un brouillion tant que l'auteur le modifie
1. Ensuite être en état de modération une fois que l'auteur à terminé
1. Puis être publié si le modérateur l'a validé

Utilisé pour changer l'état d'un objet sans toucher à son instanciation.

Combiné avec d'autres patrons de conceptions.

Exemple sur une interface de lecteur vidéo :

- vidéo éteinds
- si on lance la vidéo, le bouton de lecture change en bouton de stope

1. Vidéo arrété
2. Une fois lecture, etat vidéo en lecture
2. Si on appuye sur Pause, on passe en vidéo en pause

Aucun intéré de passer l'état de la vidéo de arrété à pause : etat non accessible.

A l'utiliser si beaucoup de changement d'état sur beaucoup d'objet : va permettre de retirer des gros bloques de conditions.

Avantages:

- Principe responsabilité unique
- principe d'ouverture et de fermeture
- simplifier le code (élimination de bloques conditionnelles)

Désavantage :

- complexifie le code, pas nécessaire pour peu d'état
---
title: Urbanisation des systèmes d'information
description: 
published: true
date: 2024-09-12T08:45:20.145Z
tags: 
editor: markdown
dateCreated: 2024-09-10T06:30:08.954Z
---

# Urbanisation des systèmes d'information

## Système d'information

- Qu'est ce ?
	- Système informatique
	- Tous les logiciels
	- Toutes les données
	- Toutes les informations manuscrites et "dans la tête" des employés (qui doit être standardisé)
- Ingénieur
	- Savoir piloter SI
		- où va entreprise
		- Savoir comprendre statégie entreprise et savoir la concrétisé techniquement
		- communiquer sur cette évolution avec tout le monde (notamment non informaticien)

## Numérisation

- Pourquoi ?
	- Pouvoir le flexibilisé car en changement continue
		- Nouveaux outils techniques
		- Changement philosophie entreprise
	- Pouvoir enregistrer données lié à l'entreprise (changement RH)
- Qu'est urbanisation
	- comparable à l'urbanisation d'une ville
	- moyen de faire évoluer le système d'information
	- Etape (sur une durée maximal 5 ans)
		- qu'est ce que j'ai aujourd'hui
		- où dois-je aller ?
- Etapes ubranisation
	- Répertorier materiel et logiciel (inventaire)
		- GLPI et Fusion Inventory
	- Connaitre entrées et sortie materiel / logiciel
	- Réduction budgetaire & retour sur investissement
		- prouver les investissement
			- mise en place de métriques
	- gestion des risques
- Role ingénieur SI
	- écoute tous les acteurs et mets en place l'urbanisation SI
- **Framework alternative**
	- Framework de Zachman https://www.zachman.com
	- TOGAF: The Open Group Architecture Framework https://www.opengroup.org/togaf/
	- Praxeme https://www.praxeme.org

### Principe

4 Niveau :

1. Métier
2. Fonctionnel : fonction du métier, similaire aux fonction en code
3. Applicatif : logiciel
4. Technologie : Couche materiel

*Exemple : urbanisation des cités (politique urbaine).*

Comparaison :

Info | La cité | Le système d'information
--|--|--
- | Le PLU (Plan d'urbanisme) | Le POS (Plan d'occupation des sols
Echelle | Commune | Entreprise / administration
Objectif 1 | Définir droits par parcelle | définir service / responsabilité dans sous ensemble
Objectif 2 | Organiser urbanisation définissant destination | Organisation globale SI : mission des applicatifs
Objectif 3 |  | Regroupement d'applicatifs en sous ensemble | Regroupement d'applicatif en sous ensemble

#### Définir des zone

Il faut délémiter les "zone" :

1. Zone
2. Quartier
3. Ilots

### Régles

##### Urbanisme

- Accés au bloc uniquement par sa "prise" (API)
- Une donnée est la responsabilité d'un seul bloc (accès, mise à jour, etc)
- Un bloc est dans un seul quartier, qui est dans une seul zone.
- Un bloc est autonome, et représente des fonctionnalités cohérentes et ne doit avoir qu'un couplage faible avec les autres bloc
- Bloc émet des résultat normalisé

p11 doc

### Démarche d'urbanisation

```
-                                     |-----------------------------------------------------------------------\
-                                     |  Urbanisme                                                             \
-                                     |                         | définition cible SI                           \
-         stratégie -----------------> métier ----------------->| définition existant -------> -Architecture -------> Système d'information
- (Détermination des objectif      (Détermination des nouveau   | intégration                   (conception)
- stratégique)                     processus métiers)                                           (developpement)
-                                                                                               (intégration)
```

1. Vision Métier : déscription des étapes du métier
2. Vision fonctionnel : déscription de la façon de faire (numérisé ou pas)
3. Vision informatique : description de l'ensemble des ressources numérique (application, materiel et autre)

On utilisera BPMM pour décrire les processus.

Quand on arrive dans une entreprise, et qu'on a pas , on analyse l'existant et on part de la couche la plus basse :

1. Analyse de l'architecture technique (serveur, pc, etc)

2. Analyse architecture applicatif

Comment les blocs applicatifs communiquent entre elle.

3. Architecture logiciel

Comment se décompose en couche chaque application, en prenant en compte les patrons de conception, les framework, etc.

4. analyse architecture fonctionnelle

5. Analyse architecture métier

On va essayer de voir les responsables des différents services plutôt que les employés directe parce que le responsable aura moins "l'effet tunnel" sur son métier.

### Méta-modèle

p17

Ubraniste défini comment les bloque communique, et les architectes définissent comment les bloque fonctionnent à l'intérieur.

Etapes de processus d'urbanisation :

1. Planifier l'étude
2. Revue des axes stratégiques
3. Analyse de l'existant
4. Définir la stratégie
5. Plan de convergence
6. Publication de la statégie
7. Mise à jour stratégique







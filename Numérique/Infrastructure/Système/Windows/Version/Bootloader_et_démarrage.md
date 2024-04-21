---
title: Bootloader et démarrage
description: 
published: true
date: 2024-04-21T16:04:17.810Z
tags: 
editor: markdown
dateCreated: 2024-04-21T16:04:17.810Z
---

# Bootloader et démarrage

`bcdedit` (*Boot Configuration Data*) est une commande qui permet d'effectuer des opérations lié au démarrage de Windows.

**Attention !** Certaines commandes ne fonctionnent pas correctement avec le shell *Powershell*.  
Vour pouvez executer ces commandes depuis le shell de base :

```cmd
cmd
```

## Principe

On modifie des *identifiants* qui correspondent à des types de démarrage.

```cmd
bcdedit /set [{ID}] typeDeDonnées Valeur
```

### Commandes

Il existe plusieurs commandes :

- `set` : modifier une valeur
- `copy` : copier une entrée
- `deletevalue` : supprimer une valeur
- `delete` : supprimer une entrée du chargeur de démarrage

### Identifiants

Identifiants standards :

- `{bootmgr}` : Le gestionnaire de démarrage de Windows (Windows Boot Manager)
- `{current}` : L’OS sélectionné au démarrage de Windows
- `{default}` : L’OS sélectionné par défaut au démarrage de Windows
- `{ntldr}` : Un système d’exploitation en ntldr (Windows Legacy OS Loader) par exemple windows xp

## Commandes

### Lister les entrées

```cmd
bcdedit /enum
# ou
bcdedit /v
```

### Ajouter une options

```cmd
bcdedit /set {XXXX-XXXX-XXXX-XXXX} numproc 2
```

### Supprimé une options

```cmd
bcdedit /deletevalue {XXXX-XXXX-XXXX-XXXX} numproc
```

### Changer le menu de démarrage lorsque vous avez plusieurs entrées

```cmd
bcdedit /set {current} description "Mon Windows Boot entrée modifiée"
```

### Changer l’ordre d’une entrée et la placer en premier

```cmd
bcdedit /displayorder {XXXX-XXXX-XXXX-XXXX} /addfirst
```

### Définir une entrée comme étant par défaut

```cmd
bcdedit /default {XXXX-XXXX-XXXX-XXXX}
```

## Configuration

### Mode sans échec activable avec la touche F8

Activer :

```cmd
bcdedit /set {default} bootmenupolicy legacy
```

Désactiver :

```cmd
bcdedit /deletevalue {default} bootmenupolicy
```

### Boot Log

Activer :

```cmd
bcdedit /set {XXXX-XXXX-XXXX-XXXX} bootlog yes
```

Désactiver :

```cmd
bcdedit /set {XXXX-XXXX-XXXX-XXXX} bootlog no
```

### Signature numérique des pilotes

Activer :

```cmd
```

Désactiver :

```cmd
bcdedit /set nointegritychecks OFF
bcdedit /set testsigning off
```

### Contrôle de la stratégie d’état de démarrage

La stratégie d’état de démarrage peut être l’une des suivantes:

- `DisplayAllFailures` : Affiche toutes les erreurs en cas d’échec du démarrage, de l’arrêt ou du point de contrôle. L’ordinateur basculera vers l’environnement de récupération Windows au redémarrage.
- `IgnoreAllFailures` : Ignore les erreurs en cas d’échec du démarrage, de l’arrêt ou du point de contrôle. L’ordinateur essaiera de démarrer normalement après une erreur.
- `IgnoreShutdownFailures` : Ignorer les erreurs uniquement en cas d’échec de l’arrêt. En cas d’échec de l’arrêt, l’ordinateur ne bascule pas sur l’environnement de récupération Windows au redémarrage. C’est le paramètre par défaut pour Windows 8.
- `IgnoreBootFailures` : Ignorer les erreurs uniquement en cas d’échec du démarrage. En cas d’échec du démarrage, l’ordinateur ne bascule pas sur l’environnement de récupération Windows au redémarrage.
- `IgnoreCheckpointFailures` : Ignorer les erreurs uniquement si un point de contrôle a échoué. En cas d’échec d’un point de contrôle, l’ordinateur ne bascule pas sur l’environnement de récupération Windows au redémarrage.
- `DisplayShutdownFailures` : Affiche les erreurs en cas d’échec de l’arrêt. En cas d’échec de l’arrêt, l’ordinateur basculera dans l’environnement de récupération Windows au redémarrage. Ignore les échecs de démarrage et les points de contrôle ayant échoué.
- `DisplayBootFailures` : Affiche les erreurs en cas d’échec du démarrage. En cas d’échec du démarrage, l’ordinateur basculera dans l’environnement de récupération Windows au redémarrage. Ignore les échecs d’arrêt et les points de contrôle ayant échoué.
- `DisplayCheckpointFailures` : Affiche les erreurs en cas d’échec d’un point de contrôle. En cas d’échec d’un point de contrôle, l’ordinateur basculera vers l’environnement de récupération Windows au redémarrage. Ignore les échecs de démarrage et d’arrêt.

Example :

```cmd
bcdedit /set {default} bootstatuspolicy DisplayAllFailures
```

### Ajout du bootloader *systemd-boot*

```cmd
bcdedit /copy {bootmgr} /d "Linux Boot Manager"
```

Replace guid with the id returned by the first command :

```cmd
bcdedit /set {guid} path \EFI\systemd\systemd-bootx64.efi
```

You can also set it as the default :

```cmd
bcdedit /default {guid}
```

### Changer le timeout de choix du démarrage

```cmd
bcdedit /timeout <timeout>
```

### Affichage du menu

Activer :

```cmd
bcdedit /set {bootmgr} displaybootmenu yes
```

Désactiver :

```cmd
bcdedit /set {bootmgr} displaybootmenu no
```

### Ajouter une lettre à une partition EFI

```cmd
diskpart
list disk
select disk 0
list partition
select partition 1
assign letter=b
exit
```

## Outils

### Visual BCD

<https://www.boyans.net/DownloadVisualBCD.html>
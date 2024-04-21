---
title: Gestionnaires d'Applications Windows
description: 
published: true
date: 2024-04-21T16:02:39.402Z
tags: 
editor: markdown
dateCreated: 2024-04-21T16:02:39.402Z
---

# Gestionnaires d'Applications Windows

## Winget

- <https://www.youtube.com/watch?v=qrS7lQDOg9M>

### Installation

Recommandé (Windows Store) :

- <https://apps.microsoft.com/store/detail/programme-dinstallation-dapplication/9NBLGGH4NNS1>

Manuellement :

- <https://github.com/microsoft/winget-cli/releases>

### Informations

#### Liste des paquets

- <https://winget.run/>

#### Chemin des applications portables

```
%LOCALAPPDATA%/Microsoft/WinGet/Packages/
```

### Commandes

#### Liste applications installées

```powershell
(winget list) -match ' winget$'
```

## Scoop

### Installation

```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser # Optional: Needed to run a remote script the first time
```

```powershell
irm get.scoop.sh | iex
```

### Configuration

#### Dépots

Liste de dépots : <https://rasa.github.io/scoop-directory/by-apps>

- extra :

```cmd
scoop bucket add extras
```

- nonportable (non-portable applications) :

```cmd
scoop bucket add nonportable
```
- nirsoft-bucket (containing almost all of the 280+ programs available at nirsoft.net) :

```cmd
scoop bucket add nirsoft-alternative https://github.com/ScoopInstaller/Nirsoft.git
```

- java (for Oracle Java, OpenJDK, Eclipse Temurin, IBM Semeru, Zulu, ojdkbuild, Amazon Corretto, BellSoft Liberica, SapMachine and Microsoft JDK.) :

```cmd
scoop bucket add java
```

- versions (For alpha, beta, nightly, dev, canary, insiders, release candidates, and frozen/older versions of app manifests.) :

```cmd
scoop bucket add versions
```

### Informations

#### Liste des paquets

- <https://scoop.sh/>
- <https://bjansen.github.io/scoop-apps/>
- <https://rasa.github.io/scoop-directory/>
- <https://sedlar.me/scoop-frontend/>

### Commandes

```
alias      Manage scoop aliases
bucket     Manage Scoop buckets
cache      Show or clear the download cache
cat        Show content of specified manifest. If available, `bat` will be used to pretty-print the JSON.
checkup    Check for potential problems
cleanup    Cleanup apps by removing old versions
config     Get or set configuration values
create     Create a custom app manifest
depends    List dependencies for an app, in the order they'll be installed
download   Download apps in the cache folder and verify hashes
export     Exports installed apps, buckets (and optionally configs) in JSON format
help       Show help for a command
hold       Hold an app to disable updates
home       Opens the app homepage
import     Imports apps, buckets and configs from a Scoopfile in JSON format
info       Display information about an app
install    Install apps
list       List installed apps
prefix     Returns the path to the specified app
reset      Reset an app to resolve conflicts
search     Search available apps
shim       Manipulate Scoop shims
status     Show status and check for new app versions
unhold     Unhold an app to enable updates
uninstall  Uninstall an app
update     Update apps, or Scoop itself
virustotal Look for app's hash or url on virustotal.com
which      Locate a shim/executable (similar to 'which' on Linux)
```

#### Liste applications installées

```cmd
scoop list
```

## Communs

### Applications

#### WingetUI

- <https://github.com/marticliment/WingetUI>

Winget :

```cmd
winget install wingetui
```

Scoop :

```cmd
scoop bucket add extras
```

```cmd
scoop install extras/wingetui
```

## Astuces

### Ajout de raccourcies dans le menu démarré

Ajouter les raccourcies dans le dossier suivant :

```
C:\ProgramData\Microsoft\Windows\Start Menu\Programs
```

Par utilisateur :

```
%AppData%\Microsoft\Windows\Start Menu
```

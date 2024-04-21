---
title: Installations Recommandées
description: 
published: true
date: 2024-04-21T15:07:31.153Z
tags: 
editor: markdown
dateCreated: 2024-04-21T15:07:31.153Z
---

# Installations Recommandées

## Runtimes

### Bibliothèque .Net
<https://dotnet.microsoft.com/en-us/download>

```cmd
winget search Microsoft.DotNet
```

#### .Net Framework
- <https://dotnet.microsoft.com/en-us/download/dotnet-framework>
- <https://assiste.com/.NET_Framework.html>

##### .Net Framework 4.x

```cmd
winget install -e --id Microsoft.DotNet.Framework.DeveloperPack_4
winget install -e --id Microsoft.DotNet.Framework.DeveloperPack.4.5
```

##### .Net Framework 2.x et 3.xx

<https://assiste.com/Logitheque/.Net_3.5_Tous_les_telechargements.html>

##### .Net Framework 1.x

<https://assiste.com/Logitheque/.Net_1.1_Tous_les_telechargements.html>

#### .Net
Également appelé DotNet.

<https://dotnet.microsoft.com/en-us/download/dotnet>

##### .Net 3.1

**Plus supporté.**

- Desktop :

```cmd
winget install Microsoft.DotNet.DesktopRuntime.3_1
```

- Core :

```cmd
winget install Microsoft.DotNet.Runtime.3_1
```

##### .Net 5.0

**Plus supporté.**

- Desktop :

```cmd
winget install Microsoft.DotNet.DesktopRuntime.5
```

- Core :

```cmd
winget install Microsoft.DotNet.Runtime.5
```

##### .Net 6.0

- Desktop :
```cmd
winget install Microsoft.DotNet.DesktopRuntime.6
```

- Core :
```cmd
winget install Microsoft.DotNet.Runtime.6
```

##### .Net 7.0
<https://dotnet.microsoft.com/en-us/download/dotnet/7.0>

- Desktop :

```cmd
winget install Microsoft.DotNet.DesktopRuntime.7
```

- Core :

```cmd
winget install Microsoft.DotNet.Runtime.7
```

### Java

#### Java Officiel

#### Microsoft OpenJDK

```
winget search Microsoft.OpenJDK
```

```
winget install Microsoft.OpenJDK.17
```

#### Eclipse Adoptium
Basé sur OpenJDK Et AdoptOpenJDK.

<https://adoptium.net/>

#### AdoptOpenJDK

#### OpenJDK

<https://winget.run/pkg/ojdkbuild/openjdk.11.jre>

#### zulu-openjdk

#### Microsoft Build of OpenJDK

<https://learn.microsoft.com/fr-fr/java/openjdk/install>

### Microsoft Visual C++ Redistributable

```cmd
winget search Microsoft.VCRedist
```

#### Tous

#### Microsoft Visual C++ 2015-2022 Redistributable

- x64 :

```cmd
winget install -e --id Microsoft.VCRedist.2015+.x64
```

- x86 :

```cmd
winget install -e --id Microsoft.VCRedist.2015+.x86
```

#### Microsoft Visual C++ 2013 Redistributable

- x64 :

```cmd
winget install -e --id Microsoft.VCRedist.2013.x64
```

- x86 :

```cmd
winget install -e --id Microsoft.VCRedist.2013.x86
```

#### Microsoft Visual C++ 2012 Redistributable

- x64 :

```cmd
winget install -e --id Microsoft.VCRedist.2012.x64
```

- x86 :

```cmd
winget install -e --id Microsoft.VCRedist.2012.x86
```

#### Microsoft Visual C++ 2010 Redistributable

- x64 :

```cmd
winget install -e --id Microsoft.VCRedist.2010.x64
```

- x86 :

```cmd
winget install -e --id Microsoft.VCRedist.2010.x86
```

#### Microsoft Visual C++ 2005 Redistributable

- x64 :

```cmd
winget install -e --id Microsoft.VCRedist.2005.x64
```

- x86 :

```cmd
winget install -e --id Microsoft.VCRedist.2005.x86
```

### DirectX

```cmd
winget install -e --id Microsoft.DirectX
```

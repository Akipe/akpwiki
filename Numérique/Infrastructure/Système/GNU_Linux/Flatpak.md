---
title: Flatpak
description: 
published: true
date: 2024-06-06T16:29:49.718Z
tags: 
editor: markdown
dateCreated: 2024-06-06T16:29:49.718Z
---

# Flatpak

## Thème

- <https://docs.flatpak.org/en/latest/desktop-integration.html?highlight=theme#applying-themes>
- <https://docs.flatpak.org/en/latest/desktop-integration.html?highlight=theme#theming>

### Depuis système KDE

```bash
flatpak install flathub org.kde.KStyle.Adwaita
flatpak install org.gtk.Gtk3theme.Breeze-Dark
flatpak install org.gtk.Gtk3theme.Breeze

# Ou
flatpak remote-add kdeapps https://distribute.kde.org/kdeapps.flatpakrepo
flatpak install kdeapps org.kde.KStyle.Adwaita
```

### Follow system color (dark/white)

Configure :

```bash
flatpak override --filesystem=xdg-config/gtk-3.0
```

```bash
# Testing
flatpak run --env=GTK_THEME=Breeze-Dark APP

# Set
flatpak override --user --env=GTK_THEME=Breeze-Dark APP
```

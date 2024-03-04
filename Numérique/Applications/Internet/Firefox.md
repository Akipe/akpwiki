---
title: Firefox
description: 
published: true
date: 2024-03-04T14:33:35.664Z
tags: 
editor: markdown
dateCreated: 2024-03-04T14:21:51.732Z
---

# Firefox

## Configuration

### Changer le serveur de synchronisation

Configuration for browser users :

- <https://mozilla-services.readthedocs.io/en/latest/howtos/run-fxa.html>
- <https://github.com/michielbdejong/fxa-self-hosting>
- <https://kmj.at/en/Setup_Firefox_Sync_standalone_or_Firefox_FXA_Account_Server_and_Sync_Server_on_Debian_Bullseye_using_Docker/>

desktop `about:config` :
```
identity.sync.tokenserver.uri = https://MY_SERVER/1.0/sync/1.5
```

```
about:config 
identity.fxaccounts.autoconfig.uri = https://MY_SERVER
identity.sync.tokenserver.uri = https://MY_SERVER/1.0/sync/1.5

# Android
# Enable "Secret Menu"  See: https://github.com/mozilla-mobile/fenix/pull/8916
# "Custom Firefox Account server":"https://synccontent.YOURDOMAIN.com",
# "Custom Sync server": "https://MY_SERVER/1.0/sync/1.5",
  
# about:config android
# identity.fxaccounts.auth.uri = https://MY_SERVER/v1
# identity.fxaccounts.remote.webchannel.uri
# webchannel.allowObject.urlWhitelist
# identity.fxaccounts.remote.profile.uri
# identity.fxaccounts.remote.oauth.uri
```

### Définir différents état des extensions en fonctions des machines avec Firefox Sync

<https://wiki.mozilla.org/Services/Sync/Addon_Sync#Can_I_have_different_enabled_states_on_different_machines.3F>

```
services.sync.addons.ignoreUserEnabledChanges = true
```
---
title: Firefox
description: 
published: true
date: 2024-03-04T14:21:51.732Z
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

desktop :
```
about:config 
identity.fxaccounts.autoconfig.uri = https://sync.firefox.akpnet.fr
identity.sync.tokenserver.uri = https://sync.firefox.akpnet.fr/1.0/sync/1.5

# Android
# Enable "Secret Menu"  See: https://github.com/mozilla-mobile/fenix/pull/8916
# "Custom Firefox Account server":"https://synccontent.YOURDOMAIN.com",
# "Custom Sync server": "https://sync.firefox.akpnet.fr/1.0/sync/1.5",
  
# about:config android
# identity.fxaccounts.auth.uri = https://sync.firefox.akpnet.fr/v1
# identity.fxaccounts.remote.webchannel.uri
# webchannel.allowObject.urlWhitelist
# identity.fxaccounts.remote.profile.uri
# identity.fxaccounts.remote.oauth.uri
```
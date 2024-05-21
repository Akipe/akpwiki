---
title: Palword
description: 
published: true
date: 2024-05-21T19:41:50.655Z
tags: 
editor: markdown
dateCreated: 2024-05-21T19:41:50.655Z
---

# Palword

## Serveur

### Configuration

#### Configuration par défaut

```ini
; This configuration file is a sample of the default server settings.
; Changes to this file will NOT be reflected on the server.
; To change the server settings, modify Pal/Saved/Config/LinuxServer/PalWorldSettings.ini.
[/Script/Pal.PalGameWorldSettings]
OptionSettings=(Difficulty=None,DayTimeSpeedRate=1.000000,NightTimeSpeedRate=1.000000,ExpRate=1.000000,PalCaptureRate=1.000000,PalSpawnNumRate=1.000000,PalDamageRateAttack=1.000000,PalDamageRateDefense=1.000000,PlayerDamageRateAttack=1.000000,PlayerDamageRateDefense=1.000000,PlayerStomachDecreaceRate=1.000000,PlayerStaminaDecreaceRate=1.000000,PlayerAutoHPRegeneRate=1.000000,PlayerAutoHpRegeneRateInSleep=1.000000,PalStomachDecreaceRate=1.000000,PalStaminaDecreaceRate=1.000000,PalAutoHPRegeneRate=1.000000,PalAutoHpRegeneRateInSleep=1.000000,BuildObjectDamageRate=1.000000,BuildObjectDeteriorationDamageRate=1.000000,CollectionDropRate=1.000000,CollectionObjectHpRate=1.000000,CollectionObjectRespawnSpeedRate=1.000000,EnemyDropItemRate=1.000000,DeathPenalty=All,bEnablePlayerToPlayerDamage=False,bEnableFriendlyFire=False,bEnableInvaderEnemy=True,bActiveUNKO=False,bEnableAimAssistPad=True,bEnableAimAssistKeyboard=False,DropItemMaxNum=3000,DropItemMaxNum_UNKO=100,BaseCampMaxNum=128,BaseCampWorkerMaxNum=15,DropItemAliveMaxHours=1.000000,bAutoResetGuildNoOnlinePlayers=False,AutoResetGuildTimeNoOnlinePlayers=72.000000,GuildPlayerMaxNum=20,PalEggDefaultHatchingTime=72.000000,WorkSpeedRate=1.000000,bIsMultiplay=False,bIsPvP=False,bCanPickupOtherGuildDeathPenaltyDrop=False,bEnableNonLoginPenalty=True,bEnableFastTravel=True,bIsStartLocationSelectByMap=True,bExistPlayerAfterLogout=False,bEnableDefenseOtherGuildPlayer=False,CoopPlayerMaxNum=4,ServerPlayerMaxNum=32,ServerName="Default Palworld Server",ServerDescription="",AdminPassword="",ServerPassword="",PublicPort=8211,PublicIP="",RCONEnabled=False,RCONPort=25575,Region="",bUseAuth=True,BanListURL="https://api.palworldgame.com/api/banlist.txt")
```

#### Activer RCON

`RCONEnabled=False` à `RCONEnabled=True`

### Commandes Administrateurs

#### Connexion avec ARRCON

```shell
.\ARRCON.exe -H IP_SERVEUR -P PORT -p MOT_DE_PASSE
```


#### Commandes administrateurs

Depuis le jeu, il faut au prèalable s'authentifier avec la commande à écrire dans le chat :

```shell
/AdminPassword MOT_DE_PASSE
```

Lors de l'utilisation d'un client RCON, il faut retirer le caractère `\` en début de commande :

Commande | Description
---|---
`/Shutdown {Secondes} {TexteMessage}` | Éteint le serveur après le temps spécifié en secondes. De plus, votre message sera affiché.
`/DoExit` | Force l'arrêt immédiat du serveur.
`/Broadcast {TexteMessage}` | Envoie un message à tous les joueurs sur le serveur.
`/KickPlayer {SteamID}` | Expulse un joueur du serveur.
`/BanPlayer {SteamID}` | Bannit un joueur du serveur.
`/TeleportToPlayer {SteamID}` | Vous téléporte à la position actuelle d'un joueur.
`/TeleportToMe {SteamID}` | Téléporte le joueur à votre position actuelle.
`/ShowPlayers` | Affiche des informations sur tous les joueurs connectés.
`/Info` | Affiche les informations du serveur.
`/Save` | Sauvegarde les données du monde.
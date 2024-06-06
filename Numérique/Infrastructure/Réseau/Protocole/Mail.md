---
title: Mail
description: 
published: true
date: 2024-06-06T16:50:45.235Z
tags: 
editor: markdown
dateCreated: 2024-06-06T16:50:45.235Z
---

# Mail

<https://www.youtube.com/watch?v=CFx2K1rDfGU>

## Hebergement
- <https://net-security.fr/securite/postfix-secure/>
- Mail-in-a-box
- IRedMail
- HMail Server
- Modoboa
- MailcowMailcow
- https://poste.io/
- https://stalw.art/

### Personalisation

#### Sieve

Organisation automatique des emails à partir de règles.

<https://fr.m.wikipedia.org/wiki/Sieve>

### Sécuriser
- <https://www.tutos-informatique.com/mails-en-spam/>
- https://www.nextinpact.com/article/30341/109074-emails-avec-spf-dkim-dmarc-arcet-bimi-a-quoi-ca-sert-comment-en-profiter

#### SPF

#### DKIM

#### DMARC

### Blacklist

<https://www.tutos-informatique.com/comment-de-blacklister-son-serveur-pour-envoyer-des-mails/>

#### Vérifier si blacklisté

- <https://mxtoolbox.com/blacklists.aspx>
- https://mxtoolbox.com/
- https://www.mailgenius.com/
- https://multirbl.valli.org/

##### Par services

###### Outlook

- https://sendersupport.olc.protection.outlook.com/snds/index.aspx?wa=wsignin1.0
- https://sender.office.com/
- https://sendersupport.olc.protection.outlook.com/pm/services.aspx
- https://sendersupport.olc.protection.outlook.com/snds/
- https://www.knownhost.com/kb/how-to-remove-your-ip-from-the-hotmail-outlook-blacklist-in-3-easy-steps/

###### Google

- https://postmaster.google.com/

###### Yahoo
- Yahoo required a very complicated email to support where I had to go full Karen and ask for the manager and then they started helping.
- customercare@cc.yahoo.comcom

#### Vérifier le score du serveur mail

- <https://www.mail-tester.com/>

#### Test envoie reception

- https://www.bortzmeyer.org/repondeurs-courrier-test.html

- echo@nic.fr (Accessible en IPv6 et accepte TLS.)
- ping@stamper.itconsult.co.uk (analyse SPF et indique le résultat ; en revanche, il ne renvoie qu'une partie du message original ; par ailleurs, cette organisation héberge l'excellent service Stamper.)
- check-auth@verifier.port25.com
- test@doesnotwork.eu (IPv6 seulement, à n'utiliser que si vous pouvez envoyer et recevoir du courrier en IPv6, il teste réception et envoi, et vous envoie donc deux confirmations.)
- ping@tools.mxtoolbox.com (la réponse est en deux parties, texte et HTML et la partie texte est du n'importe quoi, il faut regarder la partie HTML, ou passer par le site Web ; sinon, tests SPF, DKIM et DMARC).
- Le réflecteur RFC 8255 permet de tester les messages multilingues du RFC 8255. Lisez son mode d'emploi pour en savoir plus.
- https://www.mail-tester.com/ qui n'est pas vraiment un répondeur : on regarde une page Web qui vous indique une adresse (à usage unique) à laquelle on écrit et qui vous affiche ensuite le résultat de l'analyse (y compris SPF et DKIM).
- À peu près la même chose avec https://www.mailgenius.com/.
- Un service analogue est MECSA, qui vous envoie un message auquel vous répondez et qui vous présentera alors divers diagnostics, notamment de sécurité. (À interpréter avec prudence, comme d'habitude.)

#### Autres verifications

- https://mxtoolbox.com/t/test/networktoolsdevt?command=ping

## Applications

- <https://mailcow.email/>
- https://github.com/mjl-/mox
- <https://gitlab.com/simple-nixos-mailserver/nixos-mailserver>
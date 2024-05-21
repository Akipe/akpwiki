---
title: Fail2ban
description: 
published: true
date: 2024-05-21T12:26:49.798Z
tags: 
editor: markdown
dateCreated: 2024-05-21T12:26:49.798Z
---

# Fail2ban

<https://wiki.salo.pe/fail2ban.html>

## Débanir adresse IP

```bash
iptables -L -n

fail2ban-client status
fail2ban-client status sshd
fail2ban-client set sshd unbanip IPADDRESS
```
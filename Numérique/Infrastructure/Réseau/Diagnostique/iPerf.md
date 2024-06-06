---
title: iPerf
description: 
published: true
date: 2024-06-06T16:43:55.137Z
tags: 
editor: markdown
dateCreated: 2024-06-06T16:43:55.137Z
---

# iPerf

iPerf est à installer sur la machine à tester et celle qui va tester.

Puis il faudra executer les commandes suivantes :

- Serveur :

```bash
iperf –s –i1 # test TCP
iperf –s –i1 -u # test UDP
```

- Client :

```bash
iperf –c 192.168.1.102 –i1 –t60 # test TCP
iperf –c 192.168.1.102 –i1 –t60 –u –b 1000M # test UDP
```

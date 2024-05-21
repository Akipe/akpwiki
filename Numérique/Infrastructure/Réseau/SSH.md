---
title: SSH
description: 
published: true
date: 2024-05-21T19:10:17.725Z
tags: 
editor: markdown
dateCreated: 2024-05-21T19:10:17.725Z
---

# SSH

## Configuration

### Authentification par clée

Générer la clé de la machine :

```shell
ssh-keygen -t ed25519 -a 100
```

```shell
ssh-keygen -t rsa -b 4096 -o -a 100
```

#### Machine à machine

##### Avec `ssh-copy-id`

```shell
ssh-copy-id username@remote_host
```

##### En une ligne de commande

```shell
cat ~/.ssh/id_rsa.pub | ssh username@remote_host "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys"
```

##### Manuellement

```shell
cat ~/.ssh/id_rsa.pub
```

```shell
ssh username@remote_host
```

```shell
mkdir -p ~/.ssh
```

```shell
echo public_key_string >> ~/.ssh/authorized_keys
```

```shell
chmod 700 ~/.ssh/
chmod 600 ~/.ssh/authorized_keys
```

## Sécurité

### Certificat racine
<https://redwatch.io/blog/2022/certificats_ssh_hosts/>

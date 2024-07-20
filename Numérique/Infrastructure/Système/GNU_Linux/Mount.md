---
title: Mount
description: 
published: true
date: 2024-07-20T13:47:30.269Z
tags: 
editor: markdown
dateCreated: 2024-07-20T13:39:56.167Z
---

# Mount

## CIFS

### fstab

```fstab
//SERVER/SHARENAME /mnt/MOUNTPOINT cifs _netdev,nofail,iocharset=utf8,username=myuser,password=mypass,x-systemd.automount,uid=root,gid=root 0 0
//SERVER/SHARENAME /mnt/MOUNTPOINT cifs _netdev,nofail,iocharset=utf8,credentials=/etc/samba/credentials/share,x-systemd.automount,uid=root,gid=root 0 0
```

```ini
# /etc/samba/credentials/share
username=myuser
password=mypass
```

````shell
chown root:root /etc/samba/credentials
chmod 700 /etc/samba/credentials
chmod 600 /etc/samba/credentials/share
```

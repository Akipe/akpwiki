---
title: Bookstack
description: 
published: true
date: 2024-06-06T17:29:19.327Z
tags: 
editor: markdown
dateCreated: 2024-06-06T17:29:05.036Z
---

# Bookstack

## Configuration

### User timeout

`.env`:

```php
SESSION_LIFETIME=120 # Minutes
```

```bash
sudo su

echo "SESSION_LIFETIME=20160" >> /var/www/bookstack/.env
```
---
title: Taiga
description: 
published: true
date: 2024-06-06T17:29:45.040Z
tags: 
editor: markdown
dateCreated: 2024-06-06T17:29:45.040Z
---

# Taiga

- <https://docs.taiga.io/setup-production.html>
- old :
  - <https://github.com/kaleidos-ventures/taiga-docker/>
  - <https://docs.taiga.io/setup-production.html#setup-prod-with-docker>

```bash
git clone https://github.com/kaleidos-ventures/taiga-docker.git

docker-compose -f docker-compose.yml up -d

docker-compose -f docker-compose.yml -f docker-compose-inits.yml run --rm taiga-manage migrate

docker-compose -f docker-compose.yml -f docker-compose-inits.yml run --rm taiga-manage createsuperuser
```

```bash
docker compose -f docker-compose.yml -f docker-compose-inits.yml run --rm taiga-manage createsuperuser
docker compose -f docker-compose.yml -f docker-compose-inits.yml run --rm taiga-manage loaddata initial_project_templates


sudo ./taiga-manage.sh migrate
(taiga-back) DJANGO_SETTINGS_MODULE=settings.config python manage.py migrate --noinput
# create an administrator with strong password
(taiga-back) CELERY_ENABLED=False DJANGO_SETTINGS_MODULE=settings.config python manage.py createsuperuser
(taiga-back) DJANGO_SETTINGS_MODULE=settings.config python manage.py loaddata initial_project_templates
(taiga-back) DJANGO_SETTINGS_MODULE=settings.config python manage.py compilemessages
(taiga-back) DJANGO_SETTINGS_MODULE=settings.config python manage.py collectstatic --noinput
```

## Utilisation

- <https://artisandeveloppeur.fr/chronologie-dune-mise-a-jour-majeure-de-notre-mode-de-fonctionnement/>
- <https://m.youtube.com/watch?v=JcpWqm23-qA>
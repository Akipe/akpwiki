---
title: ffmpeg
description: 
published: true
date: 2024-06-06T17:19:26.072Z
tags: 
editor: markdown
dateCreated: 2024-06-06T17:18:26.536Z
---

# ffmpeg

- <https://nixsanctuary.com/best-ffmpeg-advanced-commands-for-video-audio-and-images-encoding/>
- <https://nixsanctuary.com/ffmpeg-now-supports-jpeg-xl-and-avif-how-to-convert-images/>
- <https://lecrabeinfo.net/comment-utiliser-ffmpeg-fichiers-video-et-audio.html>

## Commandes

### Convertir en AVIF et en Opus et 720p max

```shell
# Une seul vidéo
ffmpeg -i "./input.mp4" -vf 'scale=if(gte(iw\,ih)\,min(1280\,iw)\,-2):if(lt(iw\,ih)\,min(1280\,ih)\,-2)' -c:a libopus -b:a 64k -c:v libsvtav1 -crf 45 "output.mkv"

# Toutes les vidéos en format mp4
for i in *.mp4; do ffmpeg -nostdin -i "$i" -vf 'scale=if(gte(iw\,ih)\,min(1280\,iw)\,-2):if(lt(iw\,ih)\,min(1280\,ih)\,-2)' -c:a libopus -b:a 64k -c:v libsvtav1 -crf 45 "${i%.*}.mkv"; done
```
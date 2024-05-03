---
title: Traitement
description: 
published: true
date: 2024-05-03T16:47:57.077Z
tags: 
editor: markdown
dateCreated: 2024-04-26T14:04:51.357Z
---

# Traitement

## Encodeur

- Shutter Encoder
- Internet Friendly Media Encoder
- FFQueue
- FFmpeg Batch AV Converter
- YOGA Image Optimizer

### FFMPEG

- <https://nixsanctuary.com/best-ffmpeg-advanced-commands-for-video-audio-and-images-encoding/>
- <https://nixsanctuary.com/ffmpeg-now-supports-jpeg-xl-and-avif-how-to-convert-images/>

#### Commandes

##### Convertir en AVIF et en Opus et 720p max

```shell
# Une seul vidéo
ffmpeg -i "./input.mp4" -vf 'scale=if(gte(iw\,ih)\,min(1280\,iw)\,-2):if(lt(iw\,ih)\,min(1280\,ih)\,-2)' -c:a libopus -b:a 64k -c:v libsvtav1 -crf 45 "output.mkv"

# Toutes les vidéos en format mp4
for i in *.mp4; do ffmpeg -nostdin -i "$i" -vf 'scale=if(gte(iw\,ih)\,min(1280\,iw)\,-2):if(lt(iw\,ih)\,min(1280\,ih)\,-2)' -c:a libopus -b:a 64k -c:v libsvtav1 -crf 45 "${i%.*}.mkv"; done
```
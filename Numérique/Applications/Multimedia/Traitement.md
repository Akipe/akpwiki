---
title: Traitement
description: 
published: true
date: 2024-05-30T09:03:32.685Z
tags: 
editor: markdown
dateCreated: 2024-04-26T14:04:51.357Z
---

# Traitement

## Ripper

### Audio

- dbpoweramp
- Exact Audio Copy
  - I use burst mode by default since it's the fastest. Only if CueTools / AccurateRip tells me the rip is inaccurate, I try again in secure mode.
  - https://m.youtube.com/watch?v=LkLCzfBa2gI
- cueripper
- fre:ac
- abcde - A Better CD Encoder
- cdparanoia
- whipper
  - 
  - https://wiki.musichoarders.xyz/guides/ripping-cds/ripping-on-linux/
- cdparanoia
- Asunder

- <https://flemmingss.com/perfect-cd-ripping-to-flac-with-exact-audio-copy/>

### Vidéo

#### DVD

- https://www.makemkv.com/

## Sous-titres

### Transcription

- <https://github.com/thewh1teagle/vibe>

## Encodeur

- Shutter Encoder : <https://www.shutterencoder.com/>
- Videomass : <https://jeanslack.github.io/Videomass/>
- Internet Friendly Media Encoder : <https://x265.github.io/>
- FFQueue : <https://ffqueue.bruchhaus.dk/>
- FFmpeg Batch AV Converter : <https://ffmpeg-batch.sourceforge.io/>
- YOGA Image Optimizer : <https://yoga.flozz.org/>
- Hybrid : <https://www.videohelp.com/software/Hybrid>
- XMedia Recode : <https://xmedia-recode.de/en/index.php>
- StaxRip : <https://github.com/staxrip/staxrip>

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
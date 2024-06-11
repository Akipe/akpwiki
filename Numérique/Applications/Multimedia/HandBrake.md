---
title: HandBrake
description: 
published: true
date: 2024-06-11T08:27:49.314Z
tags: 
editor: markdown
dateCreated: 2024-06-11T08:23:29.682Z
---

# HandBrake

HandBrake is a open-source tool, built by volunteers, for converting video from nearly any format to a selection of modern, widely supported codecs.

- <https://handbrake.fr/>

## Presets

### Encodage DVD vers H265 (MKV) de bonne qualité

```json
{
  "PresetList": [
    {
      "AlignAVStart": false,
      "AudioCopyMask": [
        "copy:aac",
        "copy:ac3",
        "copy:eac3",
        "copy:truehd",
        "copy:dts",
        "copy:dtshd",
        "copy:mp2",
        "copy:mp3",
        "copy:flac",
        "copy:opus"
      ],
      "AudioEncoderFallback": "opus",
      "AudioLanguageList": [
        "any"
      ],
      "AudioList": [
        {
          "AudioBitrate": 160,
          "AudioCompressionLevel": 0,
          "AudioEncoder": "copy",
          "AudioMixdown": "stereo",
          "AudioNormalizeMixLevel": false,
          "AudioSamplerate": "auto",
          "AudioTrackQualityEnable": false,
          "AudioTrackQuality": -1,
          "AudioTrackGainSlider": 0,
          "AudioTrackDRCSlider": 0
        }
      ],
      "AudioSecondaryEncoderMode": true,
      "AudioTrackSelectionBehavior": "all",
      "ChapterMarkers": true,
      "ChildrenArray": [],
      "Default": false,
      "FileFormat": "av_mkv",
      "Folder": false,
      "FolderOpen": false,
      "Optimize": false,
      "Mp4iPodCompatible": false,
      "PictureCropMode": 2,
      "PictureBottomCrop": 0,
      "PictureLeftCrop": 0,
      "PictureRightCrop": 0,
      "PictureTopCrop": 0,
      "PictureDARWidth": 0,
      "PictureDeblockPreset": "off",
      "PictureDeblockTune": "medium",
      "PictureDeblockCustom": "strength=strong:thresh=20:blocksize=8",
      "PictureDeinterlaceFilter": "decomb",
      "PictureCombDetectPreset": "default",
      "PictureCombDetectCustom": "",
      "PictureDeinterlacePreset": "default",
      "PictureDenoiseCustom": "",
      "PictureDenoiseFilter": "off",
      "PictureSharpenCustom": "",
      "PictureSharpenFilter": "off",
      "PictureSharpenPreset": "medium",
      "PictureSharpenTune": "none",
      "PictureDetelecine": "off",
      "PictureDetelecineCustom": "",
      "PictureColorspacePreset": "off",
      "PictureColorspaceCustom": "",
      "PictureChromaSmoothPreset": "off",
      "PictureChromaSmoothTune": "none",
      "PictureChromaSmoothCustom": "",
      "PictureItuPAR": false,
      "PictureKeepRatio": true,
      "PicturePAR": "auto",
      "PicturePARWidth": 0,
      "PicturePARHeight": 0,
      "PictureUseMaximumSize": true,
      "PictureAllowUpscaling": false,
      "PictureForceHeight": 0,
      "PictureForceWidth": 0,
      "PicturePadMode": "none",
      "PicturePadTop": 0,
      "PicturePadBottom": 0,
      "PicturePadLeft": 0,
      "PicturePadRight": 0,
      "PicturePadColor": "black",
      "PresetName": "DVD h265 software final 2",
      "Type": 1,
      "SubtitleAddCC": true,
      "SubtitleAddForeignAudioSearch": true,
      "SubtitleAddForeignAudioSubtitle": false,
      "SubtitleBurnBehavior": "none",
      "SubtitleBurnBDSub": false,
      "SubtitleBurnDVDSub": false,
      "SubtitleLanguageList": [
        "any"
      ],
      "SubtitleTrackSelectionBehavior": "all",
      "VideoAvgBitrate": 0,
      "VideoColorMatrixCode": 0,
      "VideoEncoder": "x265_10bit",
      "VideoFramerateMode": "vfr",
      "VideoGrayScale": false,
      "VideoScaler": "swscale",
      "VideoPreset": "slow",
      "VideoTune": "",
      "VideoProfile": "main10",
      "VideoLevel": "5.1",
      "VideoOptionExtra": "ctu=32:qg-size=16:tu-intra-depth=4:tu-inter-depth=4:subme=5:rc-lookahead=120:deblock=-1,-1:no-sao:me=sea:no-strong-intra-smoothing:aq-mode=3:rd=4:psy-rd=0.75:psy-rdoq=4.0:rdoq-level=1:rskip=2:strong-intra-smoothing=0:rect=0",
      "VideoQualityType": 2,
      "VideoQualitySlider": 22,
      "VideoMultiPass": false,
      "VideoTurboMultiPass": false,
      "x264UseAdvancedOptions": false,
      "PresetDisabled": false,
      "MetadataPassthrough": true
    }
  ],
  "VersionMajor": 56,
  "VersionMicro": 0,
  "VersionMinor": 0
}
```

### Encodage BluRay 1080p vers h265 (MKV) de bonne qualité

```json
{
  "PresetList": [
    {
      "AlignAVStart": false,
      "AudioCopyMask": [
        "copy:aac",
        "copy:ac3",
        "copy:eac3",
        "copy:truehd",
        "copy:dts",
        "copy:dtshd",
        "copy:mp2",
        "copy:mp3",
        "copy:flac",
        "copy:opus"
      ],
      "AudioEncoderFallback": "opus",
      "AudioLanguageList": [
        "any"
      ],
      "AudioList": [
        {
          "AudioBitrate": 160,
          "AudioCompressionLevel": 0,
          "AudioEncoder": "copy",
          "AudioMixdown": "stereo",
          "AudioNormalizeMixLevel": false,
          "AudioSamplerate": "auto",
          "AudioTrackQualityEnable": false,
          "AudioTrackQuality": -1,
          "AudioTrackGainSlider": 0,
          "AudioTrackDRCSlider": 0
        }
      ],
      "AudioSecondaryEncoderMode": true,
      "AudioTrackSelectionBehavior": "all",
      "ChapterMarkers": true,
      "ChildrenArray": [],
      "Default": false,
      "FileFormat": "av_mkv",
      "Folder": false,
      "FolderOpen": false,
      "Optimize": false,
      "Mp4iPodCompatible": false,
      "PictureCropMode": 2,
      "PictureBottomCrop": 0,
      "PictureLeftCrop": 0,
      "PictureRightCrop": 0,
      "PictureTopCrop": 0,
      "PictureDARWidth": 0,
      "PictureDeblockPreset": "off",
      "PictureDeblockTune": "medium",
      "PictureDeblockCustom": "strength=strong:thresh=20:blocksize=8",
      "PictureDeinterlaceFilter": "decomb",
      "PictureCombDetectPreset": "default",
      "PictureCombDetectCustom": "",
      "PictureDeinterlacePreset": "default",
      "PictureDenoiseCustom": "",
      "PictureDenoiseFilter": "off",
      "PictureSharpenCustom": "",
      "PictureSharpenFilter": "off",
      "PictureSharpenPreset": "medium",
      "PictureSharpenTune": "none",
      "PictureDetelecine": "off",
      "PictureDetelecineCustom": "",
      "PictureColorspacePreset": "off",
      "PictureColorspaceCustom": "",
      "PictureChromaSmoothPreset": "off",
      "PictureChromaSmoothTune": "none",
      "PictureChromaSmoothCustom": "",
      "PictureItuPAR": false,
      "PictureKeepRatio": true,
      "PicturePAR": "auto",
      "PicturePARWidth": 0,
      "PicturePARHeight": 0,
      "PictureUseMaximumSize": true,
      "PictureAllowUpscaling": false,
      "PictureForceHeight": 0,
      "PictureForceWidth": 0,
      "PicturePadMode": "none",
      "PicturePadTop": 0,
      "PicturePadBottom": 0,
      "PicturePadLeft": 0,
      "PicturePadRight": 0,
      "PresetName": "BluRay 1080p h265 software final 1",
      "Type": 1,
      "SubtitleAddCC": true,
      "SubtitleAddForeignAudioSearch": true,
      "SubtitleAddForeignAudioSubtitle": false,
      "SubtitleBurnBehavior": "none",
      "SubtitleBurnBDSub": false,
      "SubtitleBurnDVDSub": false,
      "SubtitleLanguageList": [
        "any"
      ],
      "SubtitleTrackSelectionBehavior": "all",
      "VideoAvgBitrate": 0,
      "VideoColorMatrixCode": 0,
      "VideoEncoder": "x265_10bit",
      "VideoFramerateMode": "cfr",
      "VideoGrayScale": false,
      "VideoScaler": "swscale",
      "VideoPreset": "slow",
      "VideoTune": "",
      "VideoProfile": "main10",
      "VideoLevel": "5.1",
      "VideoOptionExtra": "no-strong-intra-smoothing:strong-intra-smoothing=0:rect=0:aq-mode=3:rd=4:psy-rd=0.75:psy-rdoq=4.0:rdoq-level=1:rskip=2:deblock=-1,-1:no-sao",
      "VideoQualityType": 2,
      "VideoQualitySlider": 24,
      "VideoMultiPass": false,
      "VideoTurboMultiPass": false,
      "x264UseAdvancedOptions": false,
      "PresetDisabled": false,
      "MetadataPassthrough": true
    }
  ],
  "VersionMajor": 56,
  "VersionMicro": 0,
  "VersionMinor": 0
}
```

## Conseils d'encodage

### Audio

#### Opus

Maximum 255 kbps par channel.

- Channel 7.1 : 512kbps
- Channel 6.1 : 448kbps
- Channel 5.1 : 384kbps / 256kbps
- Channel stéréo : 192kbps / 160kbps
- Channel mono : 128kbps
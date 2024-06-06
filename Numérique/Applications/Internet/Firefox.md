---
title: Firefox
description: 
published: true
date: 2024-06-06T17:43:25.339Z
tags: 
editor: markdown
dateCreated: 2024-03-04T14:21:51.732Z
---

# Firefox

## Installation

### Réinitialiser la configuration

```shell
% mv ~/.mozilla ~/.mozilla.BACKUP
% rm -rf ~/.cache/mozilla/firefox
```

- <https://support.mozilla.org/en-US/kb/profiles-where-firefox-stores-user-data>

## Extensions

### Userscript

#### Userscript Manager

| Nom | Notes | Site | Code source
|---|---|---|---
| [Violentmonkey](https://addons.mozilla.org/fr/firefox/addon/violentmonkey/) |  | <https://violentmonkey.github.io/> | <https://github.com/violentmonkey/violentmonkey>
| [FireMonkey](https://addons.mozilla.org/en-US/firefox/addon/firemonkey/) |  | <https://github.com/erosman/support/issues> | Pas de code source

#### Trouver des scripts

- Greasy Fork : <https://greasyfork.org/>
- OpenUserJS : <https://openuserjs.org/>
- Userscript.Zone : <https://www.userscript.zone/>
- GitHub Gist : <https://gist.github.com/search?l=JavaScript&o=desc&q=%22%3D%3DUserScript%3D%3D%22&s=updated>

#### Scripts

| Nom | Fonction | Site | Code source
|---|---|---|---
| [FB - Clean my feeds](https://greasyfork.org/fr/scripts/431970-fb-clean-my-feeds) | Hide Sponsored and Suggested posts in FB's News Feed, Groups Feed, Watch Videos Feed and Marketplace Feed | <https://github.com/zbluebugz/facebook-clean-my-feeds> | <https://github.com/zbluebugz/facebook-clean-my-feeds>
| [Simple YouTube Age Restriction Bypass](https://github.com/zerodytrash/Simple-YouTube-Age-Restriction-Bypass/raw/main/dist/Simple-YouTube-Age-Restriction-Bypass.user.js) | This extension uses some API tricks to access age-restricted videos from YouTube anonymously. | <https://github.com/zerodytrash/Simple-YouTube-Age-Restriction-Bypass> | <https://github.com/zerodytrash/Simple-YouTube-Age-Restriction-Bypass>
| [AdsBypasser](https://adsbypasser.github.io/releases/adsbypasser.full.es7.user.js) | Skip countdown ads or continue pages and prevent ad pop-up windows. | <https://adsbypasser.github.io/> | <https://github.com/adsbypasser/adsbypasser>
| []() |  | <> | <>

### Vie privé

| Nom | Fonction | Site | Code source
|---|---|---|---
| [uBlock Origin](https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/) | Bloqueur de publicité |  | <https://github.com/gorhill/uBlock>
| [Privacy Badger](https://addons.mozilla.org/en-US/firefox/addon/privacy-badger17/) | Supprime différents trackers invisibles et visibles (comme les boutons "likes" de réseaux sociaux) |  | <https://github.com/EFForg/privacybadger>
| [LocalCDN](https://addons.mozilla.org/en-US/firefox/addon/localcdn-fork-of-decentraleyes/) | Remplacer les dépendances de ressources en ligne par des ressources en local |  | <https://codeberg.org/nobody/LocalCDN>
| [Decentraleyes](https://addons.mozilla.org/en-US/firefox/addon/decentraleyes/) | Remplacer les dépendances de ressources en ligne par des ressources en local |  | <https://git.synz.io/Synzvato/decentraleyes>
| [Privacy Possum](https://addons.mozilla.org/en-US/firefox/addon/privacy-possum/) |  |  | <https://github.com/cowlicks/privacypossum>
| [ClearURLs](https://addons.mozilla.org/en-US/firefox/addon/clearurls/) | Supprime des URLs les données de tracking non nécéssaire à la navigation |  | <https://gitlab.com/KevinRoebert/ClearUrls>
| [DuckDuckGo Privacy Essentials](https://addons.mozilla.org/en-US/firefox/addon/duckduckgo-for-firefox/) |  |  | <https://github.com/duckduckgo/duckduckgo-privacy-extension>
| [Cookie Quick Manager](https://addons.mozilla.org/en-US/firefox/addon/cookie-quick-manager/) |  |  | <https://github.com/ysard/cookie-quick-manager>
| [LibRedirect](https://addons.mozilla.org/fr/firefox/addon/libredirect/) | Remplacer automatiquement des dépendances de pages ou des services privateurs par des alternatives plus respectueuses | <https://libredirect.codeberg.page/> | <https://codeberg.org/LibRedirect/libredirect>
| [Terms of Service; Didn’t Read](https://addons.mozilla.org/en-US/firefox/addon/terms-of-service-didnt-read/) | Afficher de manière plus lisible les conditions d'utilisation de sites web |  | <https://github.com/tosdr/browser-extensions>
| [https://addons.mozilla.org/en-US/firefox/addon/privacyspy/](https://addons.mozilla.org/en-US/firefox/addon/privacyspy/) |  | <https://privacyspy.org/> | <https://github.com/Politiwatch/PrivacySpy-Extension>
| [Privacy Settings](https://addons.mozilla.org/en-US/firefox/addon/privacy-settings/) |  | <https://add0n.com/privacy-settings.html> | <https://github.com/schomery/privacy-settings>
| [AdNauseam](https://addons.mozilla.org/en-US/firefox/addon/adnauseam/) |  | <https://adnauseam.io/> | <https://github.com/dhowe/AdNauseam/>
| [History Cleaner](https://addons.mozilla.org/en-US/firefox/addon/history-cleaner/) | Deletes browsing history older than a specified number of days. | <https://github.com/Rayquaza01/HistoryCleaner> | <https://github.com/Rayquaza01/HistoryCleaner>
| []() |  | <> | <>

### Container

| Nom | Fonction | Site | Code source
|---|---|---|---
| [Firefox Multi-Account Containers](https://addons.mozilla.org/en-US/firefox/addon/multi-account-containers/) |  |  | <https://github.com/mozilla/multi-account-containers>
| [Amazon Container](https://addons.mozilla.org/en-US/firefox/addon/contain-amazon/) |  |  | <https://github.com/krober/contain-amazon>
| [Google Container](https://addons.mozilla.org/en-US/firefox/addon/google-container/) |  |  | <https://github.com/containers-everywhere/contain-google>
| [Facebook Container](https://addons.mozilla.org/en-US/firefox/addon/facebook-container/) |  |  | <https://github.com/mozilla/contain-facebook>
| []() |  | <> | <>

### Confort

| Nom | Fonction | Site | Code source
|---|---|---|---
| [Jiffy Reader](https://addons.mozilla.org/en-US/firefox/addon/jiffy-reader/) |  |  | <https://github.com/ansh/jiffyreader.com>
| [Dark Reader](https://addons.mozilla.org/en-US/firefox/addon/darkreader/) |  |  | <https://github.com/darkreader/darkreader>
| [I still don't care about cookies](https://addons.mozilla.org/en-US/firefox/addon/istilldontcareaboutcookies/) |  |  | <https://github.com/OhMyGuus/I-Dont-Care-About-Cookies>
| [I don't care about cookies](https://addons.mozilla.org/en-US/firefox/addon/i-dont-care-about-cookies/) |  |  | ???
| [Tree Style Tab](https://addons.mozilla.org/en-US/firefox/addon/tree-style-tab/) |  |  | <https://github.com/piroor/treestyletab>
| [Sidebery](https://addons.mozilla.org/fr/firefox/addon/sidebery/) |  |  | <https://github.com/mbnuqw/sidebery>
| [Vimium](https://addons.mozilla.org/en-GB/firefox/addon/vimium-ff/) |  | <https://vimium.github.io/> | <https://github.com/philc/vimium>
| [LeechBlock NG](https://addons.mozilla.org/en-US/firefox/addon/leechblock-ng/) |  | <https://www.proginosko.com/leechblock/> | <https://github.com/proginosko/LeechBlockNG>
| [Read Aloud](https://addons.mozilla.org/en-US/firefox/addon/read-aloud/) | A Text to Speech Voice Reader | <https://readaloud.app/> | <https://github.com/ken107/read-aloud>
| [EpubPress](https://addons.mozilla.org/en-US/firefox/addon/epub-read-the-web-offline/) | Read the web offline |  <https://epub.press/> | <https://github.com/haroldtreen/epub-press-clients>
| [Firefox Translations](https://addons.mozilla.org/en-US/firefox/addon/firefox-translations/) | Translate websites in your browser, privately - translation is done locally. |  | <https://github.com/mozilla/firefox-translations>
| [Unhook](https://addons.mozilla.org/en-US/firefox/addon/youtube-recommended-videos/) | Hide YouTube related videos, comments, video suggestions wall, homepage recommendations, trending tab, and other distractions. | <https://unhook.app/> | No source code
| [Buster](https://addons.mozilla.org/en-US/firefox/addon/buster-captcha-solver/) | Save time by asking Buster to solve captchas for you. | <https://github.com/dessant/buster> | <https://github.com/dessant/buster>
| [Dark Background and Light Text](https://addons.mozilla.org/en-US/firefox/addon/dark-background-light-text/) | Make every web page (or just the pages you want) display light text on dark backgrounds. | <https://github.com/m-khvoinitsky/dark-background-light-text-extension> | <https://github.com/m-khvoinitsky/dark-background-light-text-extension>
| [Hide Youtube-Shorts](https://addons.mozilla.org/en-US/firefox/addon/hide-youtube-shorts/) | Hides YouTube-shorts videos from home page, subscriptions, search results. | <https://github.com/Vulpelo/hide-youtube-shorts> | <https://github.com/Vulpelo/hide-youtube-shorts>
| [Refined GitHub](https://addons.mozilla.org/fr/firefox/addon/refined-github-/) | Simplifies the GitHub interface and adds many useful features. | <https://github.com/refined-github/refined-github> | <https://github.com/refined-github/refined-github>
| [Enhancer for YouTube](https://addons.mozilla.org/fr/firefox/addon/enhancer-for-youtube/) | the most trustworthy and featured extension you can get to improve your user experience on YouTube! | <https://www.mrfdev.com/enhancer-for-youtube> | <>
| []() |  | <> | <>

### Performance

| Nom | Fonction | Site | Code source
|---|---|---|---
| [Auto Tab Discard](https://addons.mozilla.org/en-US/firefox/addon/auto-tab-discard/) |  |  | <https://github.com/rNeomy/auto-tab-discard>
| []() |  | <> | <>

### Utilitaire

| Nom | Fonction | Site | Code source
|---|---|---|---
| [Offline QR Code Generator](https://addons.mozilla.org/en-US/firefox/addon/offline-qr-code-generator/) |  |  | <https://github.com/rugk/offline-qr-code>
| [Grammalecte](https://addons.mozilla.org/en-US/firefox/addon/grammalecte-fr/) |  |  | <http://code.grammalecte.net:8080/home>
| [Tab Reloader](https://addons.mozilla.org/en-US/firefox/addon/tab-reloader/) |  |  | <https://github.com/james-fray/tab-reloader>
| [Single File](https://addons.mozilla.org/firefox/addon/single-file) |  |  | <https://github.com/gildas-lormeau/SingleFile>
| [User-Agent Switcher and Manager](https://addons.mozilla.org/en-US/firefox/addon/user-agent-string-switcher/) |  | <https://add0n.com/useragent-switcher.html> | <https://github.com/ray-lothian/UserAgent-Switcher>
| [Search by Image](https://addons.mozilla.org/en-US/firefox/addon/search_by_image/) |  |  | <https://github.com/dessant/search-by-image#readme>
| [Tab Stash](https://addons.mozilla.org/en-US/firefox/addon/tab-stash/) |  | <https://josh-berry.github.io/tab-stash/> | <https://github.com/josh-berry/tab-stash>
| [Stylebot](https://addons.mozilla.org/en-US/firefox/addon/stylebot-web/) |  |  | <https://github.com/ankit/stylebot>
| [Bulk Media Downloader ](https://addons.mozilla.org/fr/firefox/addon/bulk-media-downloader/) | Grab and download media (image, audio, and video) resources by monitoring network. | <https://webextension.org/listing/bulk-media-downloader.html> | <<https://github.com/inbasic/bulk-media-downloader>>
| [Spoof Geolocation](https://addons.mozilla.org/fr/firefox/addon/spoof-geolocation/) | alters browser Geolocation latitude and longitude to user-defined values | <https://webextension.org/listing/spoof-geolocation.html> | <https://github.com/joue-quroi/spoof-geolocation>
| [Multithreaded Download Manager](https://addons.mozilla.org/en-US/firefox/addon/multithreaded-download-manager/) | Download manager with multithreading support. | <https://addons.mozilla.org/en-US/firefox/addon/multithreaded-download-manager/> | <https://github.com/jingyu9575/multithreaded-download-manager>
| [DownThemAll!](https://addons.mozilla.org/fr/firefox/addon/downthemall/) | Will help you select, queue, sort and run your downloads faster. | <https://www.downthemall.org/> | <https://github.com/downthemall/downthemall>
| [Regex Search](https://addons.mozilla.org/fr/firefox/addon/regexsearch/) | Search in HTML using Regular Expression (REGEX) | <https://github.com/Mohd-PH/RegexSearch/> | <https://github.com/Mohd-PH/RegexSearch/>
| [OCR Image Reader ](https://addons.mozilla.org/fr/firefox/addon/ocr-image-reader/) | Simple powerful OCR without server iteration | <https://webextension.org/listing/ocr.html> | <https://github.com/brian-girko/image-reader>
| [Simple Translate](https://addons.mozilla.org/en-US/firefox/addon/simple-translate/) | Quickly translate selected or typed text on web pages. Supports Google Translate and DeepL API. | <https://simple-translate.sienori.com/> | <https://github.com/sienori/simple-translate>
| [Emoji](https://addons.mozilla.org/en-US/firefox/addon/emoji-sav/) | It permits just with a single click to copy an emoji. | <https://www.emojiaddon.com/> | <https://github.com/Sav22999/emoji>
| [Video DownloadHelper](https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/) | The easy way to download and convert Web videos from hundreds of YouTube-like sites. | <https://www.downloadhelper.net/> | <>
| []() |  | <> | <>
| []() |  | <> | <>

### Sécurité

| Nom | Fonction | Site | Code source
|---|---|---|---
| [KeePassXC-Browser](https://addons.mozilla.org/en-US/firefox/addon/keepassxc-browser/) |  |  | <https://github.com/keepassxreboot/keepassxc-browser>
| [NoScript Security Suite](https://addons.mozilla.org/en-US/firefox/addon/noscript/) |  | <https://noscript.net/> | <https://github.com/hackademix/noscript/>
| [VT4Browsers](https://addons.mozilla.org/fr/firefox/addon/vt4browsers/) |  |  | 
| [CanvasBlocker](https://addons.mozilla.org/en-US/firefox/addon/canvasblocker/) | Alters some JS APIs to prevent fingerprinting. | <https://github.com/kkapsner/CanvasBlocker/> | <https://github.com/kkapsner/CanvasBlocker/>
| []() |  | <> | <>


    
### Developpement

| Nom | Fonction | Site | Code source
|---|---|---|---
| [Font Finder (revived)](https://addons.mozilla.org/en-US/firefox/addon/font-inspect/) |  | <https://add0n.com/font-finder.html> | <https://github.com/andy-portmen/font-finder>
| [Extended Color Management](https://addons.mozilla.org/fr/firefox/addon/extended-color-management/) |  |  | <https://github.com/mkaply/extended_color_management>
| [Augury](https://addons.mozilla.org/fr/firefox/addon/angular-augury/?utm_source=addons.mozilla.org&utm_medium=referral&utm_content=search) | Extends the Developer Tools, adding tools for debugging and profiling Angular applications. | <https://augury.rangle.io/> | <https://github.com/rangle/augury>
| [ColorZilla](https://addons.mozilla.org/fr/firefox/addon/colorzilla/) | Advanced Eyedropper, Color Picker, Gradient Generator and other colorful goodies... | <https://www.colorzilla.com/> | <>
| [Live Reload](https://addons.mozilla.org/fr/firefox/addon/live-reload/) | Monitors source files on a page. Reloads the host page or the changed source file when a change is detected. | <https://github.com/blaise-io/live-reload/> | <https://github.com/blaise-io/live-reload/>
| [Wappalyzer](https://addons.mozilla.org/en-US/firefox/addon/wappalyzer/?utm_source=addons.mozilla.org&utm_medium=referral&utm_content=search) | Find out the technology stack of any website. | <https://www.wappalyzer.com/> | <https://github.com/wappalyzer/wappalyzer>
| [Fake Filler](https://addons.mozilla.org/en-US/firefox/addon/fake-filler/) | A form filler that fills all form inputs (textboxes, textareas, radio buttons, dropdowns, etc.) with fake and randomly generated data. | <https://fakefiller.com/> | <https://github.com/FakeFiller/fake-filler-extension>
| [Fonts Ninja](https://addons.mozilla.org/en-US/firefox/addon/fonts-ninja/) | Identify fonts from any website | <https://www.fonts.ninja/> | <>
| []() |  | <> | <>

### Contenu

- Bypass Paywalls Firefox Clean

### Configurations avancés

#### Sidebery

- Configuration pour **Sidebery** : <https://github.com/mbnuqw/sidebery/wiki/Firefox-Styles-Snippets-(via-userChrome.css)>

#### Tree Style Tab*

```
about:addons -> Extensions -> Tree Style Tab -> Preferences :
- "Unlock Expert Options" selected
- Appearance -> Theme -> Photon
- Toolbar Icon Color -> for Dark Theme
- Tree Behavior -> "When a new tree appears, collapse others automatically" (unselected)
- Tree Behavior -> "When a tab gets focus, expand its tree and ..." (unselected)
```

#### Ublock Origin

##### Medium mode

<https://github.com/gorhill/uBlock/wiki/Blocking-mode:-medium-mode>

- *Settings* pane:
    - *I am an advanced user*: checked.
- *3rd-party filters* pane:
    - All of uBO's filter lists: checked
    - *EasyList*: checked
    - *Peter Lowe’s Ad server list*: checked
    - *EasyPrivacy*: checked
    - *Online Malicious URL Blocklist‎*: checked
- *My rules* pane:
    - Add `* * 3p-script block`
    - Add `* * 3p-frame block`

#### Vimium-FF

##### Raccourcies claviers

- Modifier keys are specified as `<c-x>`, `<m-x>`, and `<a-x>` for `ctrl`+`x`, `meta`+`x`, and `alt`+`x` respectively. See the next section for how to customize these bindings.

- Show help : `?.`

- Vimium supports command repetition so, for example, hitting `5t` will open 5 tabs in rapid succession. `<Esc>` (or `<c-[>`) will clear any partial commands in the queue and will also exit insert and find modes.

- Navigation page actuelle

Raccourcie | Action
---|---
`?` | show the help dialog for a list of all available keys
`h` | scroll left
`j` | scroll down
`k` | scroll up
`l` | scroll right
`gg` | scroll to top of the page
`G` | scroll to bottom of the page
`d` | scroll down half a page
`u` | scroll up half a page
`f` | open a link in the current tab
`F` | open a link in a new tab
`r` | reload
`gs` | view source
`i` | enter insert mode -- all commands will be ignored until you hit `Esc` to exit
`yy` | copy the current url to the clipboard
`yf` | copy a link url to the clipboard
`gf` | cycle forward to the next frame
`gF` | focus the main/top frame

- Navigation vers une autre page

Raccourcie | Action
---|--- 
`o` | Open URL, bookmark, or history entry
`O` | Open URL, bookmark, history entry in a new tab
`b` | Open bookmark
`B` | Open bookmark in a new tab

- Utilisation de l'outil de recherche (*For advanced usage, see regular expressions on the wiki.*)
  - <https://github.com/philc/vimium/wiki/Find-Mode>

Raccourcie | Action
---|---
`/` | enter find mode
`--` | type your search query and hit enter to search, or Esc to cancel
`n` | cycle forward to the next find match
`N` | cycle backward to the previous find match

- Navigation dans l'historique

Raccourcie | Action
---|---
`H` | go back in history
`L` | go forward in history

- Manipulation des onglets

Raccourcie | Action
---|---
`J, gT` | go one tab left
`K, gt` | go one tab right
`g0 go` | to the first tab
`g$ go` | to the last tab
`^` | visit the previously-visited tab
`t` | create tab
`yt` | duplicate current tab
`x` | close current tab
`X` | restore closed tab (i.e. unwind the 'x' command)
`T` | search through your open tabs
`<a-p>` | pin/unpin current tab

- Using marks

Raccourcie | Action
---|---
`ma, mA` | set local mark "a" (global mark "A")
`` `a, `A`` | jump to local mark "a" (global mark "A")
``` `` ``` | jump back to the position before the previous jump
`--` | that is, before the previous gg, G, n, N, / or `a

- Commandes avantés pour la navigation

Raccourcie | Action
---|---
`]], [[` | Follow the link labeled 'next' or '>' ('previous' or '<')
`-` | helpful for browsing paginated sites
`<a-f>` | open multiple links in a new tab
`gi` | focus the first (or n-th) text input box on the page
`gu` | go up one level in the URL hierarchy
`gU` | go up to root of the URL hierarchy
`ge` | edit the current URL
`gE` | edit the current URL and open in a new tab
`zH` | scroll all the way left
`zL` | scroll all the way right
`v` | enter visual mode; use p/P to paste-and-go, use y to yank
`V` | enter visual line mode

- Astuces
  - <https://github.com/philc/vimium/wiki/Tips-and-Tricks>

##### Ressources

- <https://github.com/philc/vimium/wiki>
- <https://github.com/philc/vimium/wiki/FAQ>


## Raccourcis

| Touches | Fonction |
|---|---
| Ctrl + Maj + S | Capture d'image de la page
`Alt` + *selection du texte* | Empécher le link dragging (Windows)
`Alt` + `Win` + *selection du texte* | Empécher le link dragging (Linux)

## Configuration

- https://vermaden.wordpress.com/2024/03/18/sensible-firefox-setup/

### Ublock origin

- <https://majkiit.github.io/polish-ads-filter/en/>

### Changer le serveur de synchronisation

Configuration for browser users :

- <https://mozilla-services.readthedocs.io/en/latest/howtos/run-fxa.html>
- <https://github.com/michielbdejong/fxa-self-hosting>
- <https://kmj.at/en/Setup_Firefox_Sync_standalone_or_Firefox_FXA_Account_Server_and_Sync_Server_on_Debian_Bullseye_using_Docker/>

desktop `about:config` :

```
identity.sync.tokenserver.uri = https://MY_SERVER/1.0/sync/1.5
```

```
about:config 
identity.fxaccounts.autoconfig.uri = https://MY_SERVER
identity.sync.tokenserver.uri = https://MY_SERVER/1.0/sync/1.5

# Android
# Enable "Secret Menu"  See: https://github.com/mozilla-mobile/fenix/pull/8916
# "Custom Firefox Account server":"https://synccontent.YOURDOMAIN.com",
# "Custom Sync server": "https://MY_SERVER/1.0/sync/1.5",
  
# about:config android
# identity.fxaccounts.auth.uri = https://MY_SERVER/v1
# identity.fxaccounts.remote.webchannel.uri
# webchannel.allowObject.urlWhitelist
# identity.fxaccounts.remote.profile.uri
# identity.fxaccounts.remote.oauth.uri
```

### Définir différents état des extensions en fonctions des machines avec Firefox Sync

<https://wiki.mozilla.org/Services/Sync/Addon_Sync#Can_I_have_different_enabled_states_on_different_machines.3F>

```
services.sync.addons.ignoreUserEnabledChanges = true
```

### Vie privé

<https://github.com/arkenfox/user.js>

## Thémes

- <https://addons.mozilla.org/de/firefox/addon/kristofferhagen-nord-theme/>

## Développement web

### Mesurer une portion de page

<https://firefox-source-docs.mozilla.org/devtools-user/measure_a_portion_of_the_page/index.html>

## Astuces

### Barre de recherche

<https://wiki.tilde.institute/w/firefox-address-bar-tips>

## Ressources

- <https://cheatsheets.stephane.plus/misc/firefox/>
- <https://addons.mozilla.org/blog/>
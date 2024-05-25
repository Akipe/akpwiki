---
title: DNS
description: 
published: true
date: 2024-05-25T18:37:11.807Z
tags: 
editor: markdown
dateCreated: 2024-03-24T22:04:01.108Z
---

# DNS

## Protocol

<https://wiki.salo.pe/dns/dns.html>

### Domaine de premier niveau pour réseau privé

`.home.arpa` : [rfc8375, Special-Use Domain 'home.arpa.'](https://datatracker.ietf.org/doc/html/rfc8375)

Ceux ci sont recommandé dans la [RFC6762, Appendix G., Private DNS Namespaces](<https://www.rfc-editor.org/rfc/rfc6762#appendix-G>) :

- .intranet.
- .internal.
- .private.
- .corp.
- .lan.

## Fournisseur DNS

### Classique

Serveur DNS associatif respectuant la vie privée.

| Structure | Domaine | IPv4 | IPv6
|---|---|---|---
| **[FDN](https://www.fdn.fr/actions/dns/)** | ns0.fdn.fr | `80.67.169.12` | `2001:910:800::12`
| x | ns1.fdn.fr | `80.67.169.40` | `2001:910:800::40`
| **[ARN](https://arn-fai.net/fr/internet-alternatif/dns)** | recursif.arn-fai.net | `89.234.141.66` | `2a00:5881:8100:1000::3`
| **[Aquilenet](https://www.aquilenet.fr/services/dns/)** | gaia-dns.aquilenet.fr  | `185.233.100.100` | `2a0c:e300::100`
| x | hades-dns.aquilenet.fr | `185.233.100.101` | `2a0c:e300::101`
| x | dns.aquilenet.fr | `45.67.81.23` | `2a0c:e300::1337`
| **[Wikimedia DNS](https://meta.wikimedia.org/wiki/Wikimedia_DNS)** et **[instructions](https://meta.wikimedia.org/wiki/Wikimedia_DNS/Instructions)** | x | `185.71.138.138` | `2001:67c:930::1`
| **[quad9](https://quad9.net/)** | x | `9.9.9.9` | `2620:fe::fe`
| x | x | `149.112.112.112` | `2620:fe::9`

### DNS over TLS (DoT)

| Structure | Domaine | IPv4 | IPv6 | Tor
|---|---|---|---
| **[FDN](https://www.fdn.fr/actions/dns/)** | `ns0.fdn.fr` | `80.67.169.12` | `2001:910:800::12`
|     | `ns1.fdn.fr` | `80.67.169.40` | `2001:910:800::40`
| **[Aquilenet](https://dns.aquilenet.fr/)** | `dns.aquilenet.fr` | `45.67.81.23` | `2a0c:e300::1337`
| **[Wikimedia DNS](https://meta.wikimedia.org/wiki/Wikimedia_DNS)** et **[instructions](https://meta.wikimedia.org/wiki/Wikimedia_DNS/Instructions)** | `wikimedia-dns.org` | `185.71.138.138` | `2001:67c:930::1`
| **[bortzmeyer](https://www.bortzmeyer.org/doh-bortzmeyer-fr-policy.html)** | `dot.bortzmeyer.fr` | `193.70.85.11` | ` 2001:41d0:302:2200::180` | `lani4a4fr33kqqjeiy3qubhfx2jewfd3aeaepuwzxrx6zywp2mo4cjad.onion`
| **[Mullvad](https://mullvad.net/en/help/dns-over-https-and-dns-over-tls)** | `dns.mullvad.net` | `194.242.2.2` | `2a07:e340::2`
| **[Shaft Inc.](https://www.shaftinc.fr/dns-shaftinc.html)** | `dns.shaftinc.fr` | | `2001:bc8:2c86:853::853`
| **[quad9](https://quad9.net/)** | `dns.quad9.net` | `9.9.9.9` | `2620:fe::fe`

Port par défaut : TCP sur `853`

### DNS over HTTPS (DoH)

| Structure | Domaine
|---|---
| **[FDN](https://www.fdn.fr/actions/dns/)** | `https://ns0.fdn.fr/dns-query`
|     | `https://ns1.fdn.fr/dns-query`
| **[Aquilenet](https://dns.aquilenet.fr/)** | `http://dns.aquilenet.fr`
| **[Wikimedia DNS](https://meta.wikimedia.org/wiki/Wikimedia_DNS)** et **[instructions](https://meta.wikimedia.org/wiki/Wikimedia_DNS/Instructions)** | `https://wikimedia-dns.org/dns-query`
| **[bortzmeyer](https://www.bortzmeyer.org/doh-bortzmeyer-fr-policy.html)** | `https://doh.bortzmeyer.fr`
| **[Mullvad](https://mullvad.net/en/help/dns-over-https-and-dns-over-tls)** | `https://dns.mullvad.net/dns-query`
| **[Shaft Inc.](https://www.shaftinc.fr/dns-shaftinc.html)** | `https://dns.shaftinc.fr`
| **[La Contre-Voie](https://lacontrevoie.fr/services/doh/) | `https://doh.lacontrevoie.fr/dns-query`
| **[quad9](https://quad9.net/)** | `https://dns11.quad9.net/dns-query`

- <https://github.com/curl/curl/wiki/DNS-over-HTTPS#publicly-available-servers>

## Commandes

### Réinitialiser les caches DNS

#### Windows

```cmd
ipconfig /flushdns
```

#### systemd (Unix)

```shell
systemd-resolve --flush-caches
```

## Sources

- FDN - French Data Network : <https://www.fdn.fr/actions/dns/>
- ARN - Alsace Reseau Neutre : <https://arn-fai.net/fr/internet-alternatif/dns>
- Aquilenet - Aquitaine : <https://www.aquilenet.fr/services/dns/>
- <https://cyrille.giquello.fr/glossaire/dns>
- <https://www.ffdn.org/wiki/doku.php?id=transmission:dns>
- <https://diyisp.org/dokuwiki/doku.php?id=technical:dnsresolver>
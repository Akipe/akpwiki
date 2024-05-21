---
title: OPNsense
description: 
published: true
date: 2024-05-21T19:55:19.016Z
tags: 
editor: markdown
dateCreated: 2024-03-25T13:49:44.252Z
---

# OPNsense

- <https://opnsense.org/>
- <https://docs.opnsense.org/>

## Informations

### Configuration matériel recommandé

- <https://docs.opnsense.org/manual/hardware.html>

## Configuration

### Ajouter une route personnalisé au clients DHCP

- <https://forum.opnsense.org/index.php?PHPSESSID=j9baqch44j4ga1skmh97u8nrpc&topic=1972.0>

```
Sending Classless Static Routes to DHCP Clients from OPNsense.

    In the OPNsense Web GUI, go to Services ==> DHCP ==> Server and select the tab for the apropriate interface.
    Scroll down to "Additional BOOTP/DHCP Options" and click the "Advanced" button.
    Click the little Plus button to add an additional option.
    In the Number field, enter the option number 121 for the Classless Static Route Option.
    Select String in the Type field, because this option sends is a string of octets to the DHCP client.
    Enter the apropriate string value field. This value is a number of octets, represented as a hexadecimal number and separated by colons.


Understanding the value string.
The string is made of the netmask and network of the destination (destination descriptor) and the address of the router that forwards traffic to the destination.
All octets are entered as their hexadecimal value.
So for example, if we want to route traffic to 192.168.10.0/24 via a router at 192.168.5.10, the string would be made as follows:

|-- Destination Descriptor --|
Netmask bits,  Network address, Forwarding router address
   24             192.168.10.0      192.168.5.10
    |             _|   |   |         |   |  |  |
    |            |   __|   |         |   |  |  |
    |            |  |   ___|         |   |  |  |
    |            |  |  |   __________|   |  |  |
    |            |  |  |  |   ___________|  |  |
    |            |  |  |  |  |   ___________|  |
    |_________   |  |  |  |  |  |   ___________|
              |  |  |  |  |  |  |  |
Hex string:  18:C0:A8:0A:C0:A8:05:0A


Note that in the example above, the last octet of the network address is omitted.
This is because, according to RFC 3442, the descriptor of the destination is in compact format.
This means that the destination descriptor starts with one octet that represents the subnet mask, followed by only the significant octets of the destination network address.
Significant octets are all octets where at least one of the corresponding netmask bits is 1.

So for example if I wanted to route the complete private class-B address range via 192.168.5.10, this would look like:

Netmask bits,  Network address, Destination router address
   12             172.16.0.0      192.168.5.10
    |             _|   |           |   |  |  |
    |            |   __|           |   |  |  |
    |            |  |   ___________|   |  |  |
    |            |  |  |   ____________|  |  |
    |            |  |  |  |   ____________|  |
    |_________   |  |  |  |  |   ____________|
              |  |  |  |  |  |  |
Hex string:  0C:AC:10:C0:A8:05:0A

Should we want to send multiple Classless Static Routing entries to the DHCP client, we can simply concatenate the two strings with a colon in between.
So for example for the above two routing entries, this would look like:

18:C0:A8:0A:C0:A8:05:0A:0C:AC:10:C0:A8:05:0A
```

### Receive-side scaling (RSS)

- <https://docs.opnsense.org/troubleshooting/performance.html#receive-side-scaling>

Check MSI-X support :
```shell
dmesg | grep vectors
```

Ajout des tunables :
```
net.isr.bindthreads = 1
net.isr.maxthreads = -1
net.inet.rss.enabled = 1

# for 4-core systems, use ‘2’
# for 8-core systems, use ‘3’
# for 16-core systems, use ‘4’
# Etc.
net.inet.rss.bits = X
```

Autre config (à vérifier) :

```
net.isr.defaultqlimit = 2048 # defaut : 256
net.isr.dispatch = deferred # defaut : direct
```

### Spectre & Meltdown

- <https://wiki.freebsd.org/SpeculativeExecutionVulnerabilities>
- <https://docs.opnsense.org/troubleshooting/hardening.html#spectre-and-meltdown>

Désactiver :
```
hw.ibrs_disable = 1
vm.pmap.pti = 0
```

### Intel carte réseau

#### Mbuf Exhaustion

- <https://docs.netgate.com/pfsense/en/latest/hardware/tune.html#id5>
- <https://docs.netgate.com/pfsense/en/latest/hardware/tune.html#intel-igb-4-and-em-4-cards>

```
kern.ipc.nmbclusters="1000000"
```

Vérifier avec :

```
netstat -m
```

### Autres optimisations

```
net.inet.ip.intr_queue_maxlen = 2048 # defaut : 1000
net.inet6.ip6.intr_queue_maxlen = 2048 # defaut : 1000
```

- <https://docs.netgate.com/pfsense/en/latest/hardware/tune.html#intel-igb-4-and-em-4-cards>
```
kern.ipc.nmbclusters="1000000" # defaut : 501190
kern.ipc.nmbjumbop="524288" # defaut: 250595
hw.intr_storm_threshold="10000"
```

### Éviter le bufferbloat

#### Tester

- <https://www.waveform.com/tools/bufferbloat>
- <https://www.dslreports.com/speedtest>
- <https://www.bufferbloat.net/fast.com> (“Show more info”)
- <https://speedtest.net/>

##### Manuellement

If you want to observe latency under load (“bufferbloat”) for yourself, try this:

1. Start a ping to google.com. You’ll see a series of lines, one per ping, typically with times in the 20-100 msec range.
2. Start a speed test from one of the speed test services below while the pings continue:
  - http://fast.com
  - http://speedtest.net
3. Watch the ping times while the speed test is running. If the times jump up when uploading or downloading, then your router is probably bloated.

#### Mise en place

- Firewall --> Shaper --> Pipes

Créer un "Pipe" pour le téléchargement, activer le mode avancé, puis :

- Bandwidth : vitesse de la connexion internet
- Queue : 2
- Scheduler type : FlowQueue-Codel
- (FQ-)CoDel ECN : enable
- FQ-CoDel quantum : *optimal rule seems to be 300 per 100 Mbps. so : 300 * X (by 100 Mbps)*
- Description : Download

Faire de même pour l'upload avec comme différence :

- Description : Upload

Aller dans le menu Queues, on ajoutera deux queues, une pour le téléchargement et l'autre pour l'upload :

Pour le téléchargement :

- Pipe : Download
- Weight : 100
- mask : Destination
- (FQ-)CoDel ECN : enable
- Description : Download Queue

Faire de même pour l'upload sauf :

- Pipe : Upload
- mask : source
- Description : Upload Queue

Aller dans le menu Rules, on va également créer deux régles :

Pour le téléchargement :

- Interface : l'interface WAN
- Direction : in
- Target : Download Queue
- Description : Download Rule

Pour l'upload :

- Interface : l'interface WAN
- Direction : out
- Target : Upload Queue
- Description : Upload Rule

réduisez environ 5 %

### HAProxy

- <https://forum.opnsense.org/index.php?topic=23339.0>

### Blocage d'adresses IP

Il faut créer un ALIAS de type `URL Table (IPs)` et ajouter l'URL de la liste.

Si nécessaire il faut augmenter le nombre d'entrées autorisés. Pour ce faire il faut aller dans `Firewall` > `Settings` > `Advanced` et définir dans `Firewall Maximum Table Entries` le nombre maximum d'éléments autorisés.

#### Sources

##### BE.CYBER Community

<https://github.com/duggytuxy/malicious_ip_addresses>

- `https://raw.githubusercontent.com/duggytuxy/malicious_ip_addresses/main/botnets_zombies_scanner_spam_ips.txt`
- `https://raw.githubusercontent.com/duggytuxy/malicious_ip_addresses/main/botnets_zombies_scanner_spam_ips_ipv6.txt`

### Liste de blocage IP

- <https://iplists.firehol.org/>
- <https://github.com/firehol/blocklist-ipsets>

## Commandes

### Afficher le menu root depuis un autre utilisateur

```shell
sudo /usr/local/sbin/opnsense-shell
```
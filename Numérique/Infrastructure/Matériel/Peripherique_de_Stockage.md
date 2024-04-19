---
title: Peripherique de Stockage
description: 
published: true
date: 2024-04-19T17:10:22.320Z
tags: 
editor: markdown
dateCreated: 2024-04-19T17:10:22.320Z
---

# Peripherique de Stockage

## Monitoring

### Self-Monitoring, Analysis, and Reporting Technology (S.M.A.R.T.)

Journal de bord de l'état du périphérique de donnée.

Il y a un ensemble d'attributs qui ont des valeurs qui ne doivent pas dépasser un seuil.

#### Attributs

<https://fr.m.wikipedia.org/wiki/Self-Monitoring,_Analysis_and_Reporting_Technology#Attributs_S.M.A.R.T._connus>

| ID	| Attributs S.M.A.R.T	| Description |	Comment le lire
|---|---|---|---
| 01 | 	Read Error Rate |	Donne des indications sur des erreurs de lecture sur la surface de disque. |	Cela peut indiquer des problèmes de disque sur la surface ou tête de lecture
| 05	| Reallocated Sectors Count |	indique le nombre de secteurs réalloués. Si des erreurs de lecture ou écriture/vérification d’un secteur sont détectées, les données sont déplacés vers un secteur “sain”.	|Trop de secteurs réalloués peut indiquer un problème matériel. D’autre part, cela peut ralentir la vitesse de lecteur/écriture
| 10	| Spin Retry Count |	Nombre total de tentative de rotation à la vitesse nominale du disque.	| Si ce nombre est trop élevé, cela peut indiquer un problème mécanique du disque dur. Une augmentation de cet attribut est signe de problèmes au niveau du sous-système mécanique du disque dur.
Cela ne concerne donc pas les SSD qui ne sont pas mécaniques.
| 196	| Reallocation Event Count	| Nombre de tentative de réallocation de secteurs	
| 197	| Current Pending Sector Count	| Nombre de secteurs potentiellement défectueux, si un secteur marqué comme défectueux a pu être réutilisé, le compteur est diminué	
| 187 |	Reported Uncorrectable Errors	| Le nombre d’erreurs qui n’ont pu être corrigées par le code correcteur.	
| 188	| Command Timeout	|Nombre total de d’opération interrompues avec un délai de réponse trop élevé (timeout)	
| 190	| Airflow Temperature (WDC)	| Température de l’air sur les disques Western Digital (la même que la température (C2), mais la valeur de l’attribut est inférieure de 50).	
| 196	| Reallocation Event Count	| Nombre d’opérations de réallocation (remap).	| La valeur brute de cet attribut est le nombre total de tentatives de transfert de données entre un secteur réalloué et un secteur de réserve. Les essais fructueux et les échecs sont tous comptés au même titre.
| 197	| Current Pending Sector Count	|Nombre de secteurs « instables » (en attente de réallocation).
Quand des secteurs instables sont lus avec succès, cette valeur est diminuée.	| Les données sont donc transférées un secteur sain. Toutefois un nombre élevés indique un problème sur la surface du disque (HDD) ou sur les unités de mémoires (SSD)
| 198	 | Uncorrectable Sector Count	|Nombre total d’erreurs incorrigibles à la lecture/écriture d’un secteur. | Une augmentation de cette valeur indique des défauts de la surface du disque et/ou des problèmes avec le sous-système mécanique

#### Lecture

##### CrystalDiskInfo

<https://crystalmark.info/en/download/>

###### Hard Disk Sentinel

<https://www.hdsentinel.com/>

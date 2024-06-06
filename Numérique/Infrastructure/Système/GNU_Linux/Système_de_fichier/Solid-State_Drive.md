---
title: Solid-State Drive
description: 
published: true
date: 2024-06-06T16:33:17.168Z
tags: 
editor: markdown
dateCreated: 2024-06-06T16:33:17.168Z
---

# Solid-State Drive

Egalement courament appelé **SSD**.

## TRIM

### TRIM all SSD

Make a secure erase TRIM of SSD.

**Carefull: it will delete all files !**

```bash
blkdiscard --secure /dev/device
```

> `--secure` option : "Perform a secure discard. A secure discard is the same as a regular discard except that all copies of the discarded blocks that were possibly created by garbage collection must also be erased. This requires support from the device".

If unsupported :

```bash
blkdiscard /dev/device
```

---
title: PDF
description: 
published: true
date: 2024-05-21T18:57:20.920Z
tags: 
editor: markdown
dateCreated: 2024-05-04T07:48:03.589Z
---

# PDF

- Libreoffice Draw
- PDFtk (ligne de commande)
- PDF Chain
- PDF Arranger

## Édition

### Ajouter un filigrane

Use pdftk (pdf tool kit) at : <https://www.pdflabs.com/tools/pdftk-the-pdf-toolkit/>

With command line :

```bash
pdftk document.pdf background watermark.pdf output document_watermarked.pdf
```

Or with graphical interface :

- choose the document to edit
- check watermark and set the watermark document path.
- select create pdf

### Supprimer un filigrane

Décompresser le fichier avec le filigranne :

```bash
pdftk DOC_FILIGRANE.pdf output uncompress.pdf uncompress 
```

Supprimer le filigranne (simple) :

```bash
sed -e 's/CONFIDENTIEL/ /' -e 's/EXEMPLAIRE/ /' uncompress.pdf > sansFiligrane.pdf
```

Supprimer le filigranne (composé de plusieurs mots) :

```bash
sed -e 's/CONFIDENTIEL/ /' -e 's/EXEMPLAIRE/ /' -e 's/John DOE/ /' uncompress.pdf > sansFiligrane.pdf
```

Recompresser le document :

```bash
pdftk sansFiligrane.pdf output output.pdf compress
```

### Retirer les protections

Afficher les permissions :

```bash
qpdf --show-encryption DOCUMENT.pdf
```

Retirer les protections :

```bash
qpdf --decrypt DOC_CHIFFRE.pdf DOC_DECHIFFRE.pdf
```

### Ressources

- <https://tutox.fr/2022/12/03/faire-sauter-les-protections-dun-pdf/>
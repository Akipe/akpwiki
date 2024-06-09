---
title: Puppeteer
description: 
published: true
date: 2024-06-09T23:06:15.257Z
tags: 
editor: markdown
dateCreated: 2024-06-09T23:06:15.257Z
---

# Puppeteer

- <https://pptr.dev/>

## Installation

```bash
npm i puppeteer
```

With typescript :

```bash
npm i --dev typescript
```

## Exemple

```js
import puppeteer from 'puppeteer';

(async () => {
  const browser = await puppeteer.launch();
  const page = await browser.newPage();

  await page.goto('https://developer.chrome.com/');

  // Set screen size
  await page.setViewport({width: 1080, height: 1024});

  // Type into search box
  await page.type('.search-box__input', 'automate beyond recorder');

  // Wait and click on first result
  const searchResultSelector = '.search-box__link';
  await page.waitForSelector(searchResultSelector);
  await page.click(searchResultSelector);

  // Locate the full title with a unique string
  const textSelector = await page.waitForSelector(
    'text/Customize and automate'
  );
  const fullTitle = await textSelector.evaluate(el => el.textContent);

  // Print the full title
  console.log('The title of this blog post is "%s".', fullTitle);

  await browser.close();
})();
```

## Aide

### Debugger

#### Afficher le contenu d'une page

```typescript
import puppeteer from "puppeteer";

const browser = await puppeteer.launch({
  headless: 'new',
})

const page = await browser.newPage()

await page.setViewport({
  width: 1080,
  height: 1024
})

const response = await page.goto("https://www.website.com")

console.log(await response?.text())

```

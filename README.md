# Word Garden — public product page

The marketing page for **Word Garden**, by
[StateLess Squad](https://github.com/StatelessSquad).

This repository contains **only the product page** — the game itself is not
published here. The page is a static site: no build step, no dependencies,
no tracking.

> **This repository is a build output.** The files are pushed by
> `scripts/sync-public.mjs` from the private source repository. Do not edit
> them by hand — the next sync overwrites the change.

## What is in here

```
index.html              the page
assets/style.css        the design system
assets/app.js           reveal, count-up and the lazy demo video
assets/demo.mp4         gameplay capture
assets/shots/*.webp     screenshots
assets/icon.png         the app icon
manifest.webmanifest    the installable-page manifest
```

## Local preview

```bash
python3 -m http.server 8000
# then open http://localhost:8000/
```

## Deployment

GitHub Pages, deployed from `main` by `.github/workflows/pages.yml`.

## Developed by StateLess Squad

<https://github.com/StatelessSquad>

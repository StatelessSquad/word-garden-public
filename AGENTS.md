# AGENTS.md — the public product page

> This repository is a **build output**. The files here are pushed by
> `scripts/sync-public.mjs` from the private source repository.
>
> **Do not edit anything in this repository by hand.** The next sync
> overwrites the change, and the change is lost.
>
> To change the page: edit `marketing/` in the private repository, then run
> `npm run marketing:sync` there.

## What lives where

| In the private repository | In this repository |
|--------------------------|--------------------|
| `marketing/index.html` | `index.html` |
| `marketing/assets/style.css` | `assets/style.css` |
| `marketing/assets/app.js` | `assets/app.js` |
| `marketing/manifest.webmanifest` | `manifest.webmanifest` |
| `marketing/assets/*` | `assets/*` |
| `marketing/.github/workflows/pages.yml` | `.github/workflows/pages.yml` |

Everything is rendered from `app.config.json` in the private repository: the
name, the tagline, the description, the colours, the rules and the features.

## The rules of the page

- **No build step, no dependencies, no tracking.** One HTML file, one
  stylesheet, one script.
- **The page must work from `file://`** as well as over HTTP — the preview
  is often just a double-click.
- **No `filter: blur()` on a big surface and no animated shadows.** The same
  lessons as the game apply here.
- **Motion only on the compositor** (transform / opacity).
- **Every image has an explicit size**, so the page does not shift while it
  loads.
- **The reveal animation only hides content when JavaScript can bring it
  back** (the `.js` class on `<html>`).
- **The demo video is optional.** If it is missing, the page falls back to
  the poster image.

## Changing the page

In the private repository:

```bash
# 1. Edit the template
$EDITOR marketing/index.html

# 2. Preview it locally (no push)
npm run marketing:render
# then: python3 -m http.server 8000 --directory marketing/dist

# 3. Push it
npm run marketing:sync
```

## The deployment

GitHub Pages, deployed from `main` by `.github/workflows/pages.yml`. The page
is live at the URL in `app.config.json` (`url`).

The workflow is part of the template — it is pushed by the sync too, so a
new app's public repository works the moment it exists.

## The images

```bash
npm run shots              # capture the app on every theme
npm run marketing:assets   # turn the captures into the page assets
```

The captures are reproducible (a fixed seed), so the same command always
produces the same board.

## Developed by StateLess Squad

<https://github.com/StatelessSquad>

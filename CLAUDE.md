# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Static wedding invitation site for Cata & Chano (24.10.2026, Buenos Aires). The site is a single `index.html` (inline CSS and JS) plus static assets: couple photos in `fotos/` (the hero postcard uses `fotos/surf-mar-faro.jpeg`) and the favicon PNGs. No build step, no dependencies, no framework, no tests. All content is in Spanish (Argentine voseo) — keep that tone in any copy changes. Guests will open this mostly on phones — design and verify mobile-first (occasionally desktop).

## Develop and deploy

- Preview locally with any static server, e.g. `python3 -m http.server 4173` (a `static-site` config exists in `.claude/launch.json`).
- Production: https://cataychano.vercel.app — Vercel project `cataychano` on Luciano's personal team, connected to GitHub `lucianoMintrone/cataychano`. Pushing to `main` deploys automatically (no build configured).

## Structure of index.html

One page, sections in order: hero (postcard photo + date) → countdown → agenda (`#agenda`, ceremony/party cards with Google Maps links) → RSVP (`#rsvp`) → gifts (`#regalos`) → photo grid (`#fotos`) → footer. Design tokens live as CSS variables in `:root` (paper/ink/sea/sand/accent palette); fonts are Cormorant Garamond (body) and Space Mono (labels/numbers, via the `.mono` pattern).

### RSVP flow (the only real logic)

One form per person — guests with a +1 are asked to have them submit their own form. On submit, the script picks a backend:

- `SHEET_URL` (top of the inline script) — if non-empty, POSTs JSON `{nombre, asistencia, dieta, mensaje}` to a Google Apps Script. Currently empty.
- Fallback: formsubmit.co, emailing luciano@amalgama.co.

## Known pending work (from README)

- Real alias/CBU in the gifts section (current `CATA.CHANO.BODA` is a placeholder)
- Set `SHEET_URL` once the Apps Script exists

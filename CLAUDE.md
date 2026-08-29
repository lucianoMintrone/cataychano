# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Static wedding invitation site for Cata & Chano (24.10.2026, Buenos Aires). The site is a single `index.html` (inline CSS and JS) plus static assets: couple photos in `fotos/` (the hero postcard uses `fotos/surf-mar-faro.jpeg`) and the favicon PNGs. No build step, no dependencies, no framework, no tests. All content is in Spanish (Argentine voseo) — keep that tone in any copy changes. Guests will open this mostly on phones — design and verify mobile-first (occasionally desktop).

## Develop and deploy

- Preview locally with any static server, e.g. `python3 -m http.server 4173` (a `static-site` config exists in `.claude/launch.json`).
- Production: https://cataychano.vercel.app — Vercel project `cataychano` on Luciano's personal team, connected to GitHub `lucianoMintrone/cataychano`. Pushing to `main` deploys automatically (no build configured).

## Structure of index.html

One page, sections in order: hero (postcard photo + date) → countdown → agenda (`#agenda`, ceremony/party cards with Google Maps links) → RSVP (`#rsvp`) → gifts (`#regalos`) → photo grid (`#fotos`) → music (`#musica`, Spotify embed + collaborator invite link) → footer. Design tokens live as CSS variables in `:root` (paper/ink/sea/sand/accent palette); fonts are Cormorant Garamond (body) and Space Mono (labels/numbers, via the `.mono` pattern).

### English version (`?lang=en`)

The page ships in Spanish. Opening it with `?lang=en` swaps every string to English; anything else (including no param) stays in Spanish. A discreet toggle in the footer links between the two.

**Dates are localised, not just copied.** Spanish shows day.month.year (`24.10.2026`); English shows month.day.year (`10.24.2026`). This applies everywhere the date is rendered — the hero `.bigdate`, the footer line, the RSVP thank-you and the `og:description`. Any new date needs the same treatment.

Translatable text is marked in the markup with `data-i18n` (textContent), `-html` (text containing markup), `-ph` (placeholder), `-alt`, `-aria`, `-title` and `-href`; the English strings live in the `I18N_EN` dictionary at the top of the inline script. Strings the script writes at runtime (countdown "¡Es hoy!", the RSVP button and its alerts) come from `TEXTOS[LANG]` instead. Adding copy means adding both the `data-i18n` attribute and its key.

A small script in `<head>` sets `LANG` and hides `main` (`html.pre-i18n`) so English readers never see a flash of Spanish; the body script unhides it, with a 1.5s timeout as a fallback. Note that `og:` tags are rewritten client-side only, so link previews of `?lang=en` still show the Spanish description.

### RSVP flow (the only real logic)

One form per person — guests with a +1 are asked to have them submit their own form. On submit, the script picks a backend:

- `SHEET_URL` (top of the inline script) — if non-empty, POSTs JSON `{nombre, asistencia, dieta, mensaje}` to a Google Apps Script. Currently empty.
- Fallback: formsubmit.co, emailing luciano@amalgama.co.

## Known pending work (from README)

- Set `SHEET_URL` once the Apps Script exists

The gifts section aliases (`CATA.CHANO.ARS` for pesos, `CATA.CHANO.USD` for dollars, account holder Catalina Rodriguez Kenny) are the real ones — don't treat them as placeholders.

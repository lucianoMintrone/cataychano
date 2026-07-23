# Cata & Chano — Invitación de casamiento

Web de invitación estática (un solo `index.html`).

- **Producción:** https://cataychano.vercel.app (proyecto Vercel `cataychano`, team personal de Luciano, conectado a GitHub `lucianoMintrone/cataychano`)
- **Fecha:** 24.10.2026 · 15:30hs Iglesia Michael Ham · 18hs Quinta El Tata

## Secciones
Cuenta regresiva · Agenda con mapas · RSVP (un form por persona) · Regalos (alias placeholder `CATA.CHANO.BODA`)

## RSVP
- Un form por persona (los +1 completan el suyo)
- Por defecto envía mail vía formsubmit.co a luciano@amalgama.co
- Para volcar a Google Sheets (una fila por confirmación): pegar la URL del Apps Script en la variable `SHEET_URL` del script en `index.html`

## Deploy
Vercel, sitio estático sin build. Push a `main` en GitHub deploya automáticamente.

## Pendientes
- [ ] Alias/CBU real en Regalos
- [ ] Conectar `SHEET_URL` (Apps Script)

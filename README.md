# Cata & Chano — Invitación de casamiento

Web de invitación estática (un solo `index.html`).

- **Producción:** https://cata-y-chano.vercel.app (proyecto Vercel `cata-y-chano`, team personal de Luciano)
- **Fecha:** 24.10.2026 · 15hs Iglesia Michael Ham · 18hs Quinta El Tata

## Secciones
Cuenta regresiva · Agenda con mapas · RSVP (múltiples nombres por confirmación) · Regalos (alias placeholder `CATA.CHANO.BODA`)

## RSVP
- Por defecto envía mail vía formsubmit.co a luciano@amalgama.co
- Para volcar a Google Sheets (una fila por nombre): pegar la URL del Apps Script en la variable `SHEET_URL` del script en `index.html`

## Deploy
Vercel, sitio estático sin build. `vercel --prod` o deploy desde git.

## Pendientes
- [ ] Reemplazar ilustración SVG por foto real
- [ ] Alias/CBU real en Regalos
- [ ] Conectar `SHEET_URL` (Apps Script)

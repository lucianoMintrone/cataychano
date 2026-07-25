# Cata & Chano — Invitación de casamiento

Web de invitación estática: un `index.html` (CSS y JS inline), las fotos en `fotos/` y `apps-script.gs`, que es la copia versionada del backend del RSVP que corre en Google Apps Script.

- **Producción:** https://cataychano.vercel.app (proyecto Vercel `cataychano`, team personal de Luciano, conectado a GitHub `lucianoMintrone/cataychano`)
- **Fecha:** 24.10.2026 · 15:30hs Iglesia Michael Ham · 18hs Quinta El Tata

## Secciones
Cuenta regresiva · Agenda con mapas · RSVP (un form por persona) · Regalos (dos alias, pesos y dólares, hoy placeholder, a nombre de Catalina Rodriguez Kenny) · Fotos · Música (playlist de Spotify colaborativa)

## RSVP
- Un form por persona (los +1 completan el suyo)
- Cada confirmación se escribe como una fila en la planilla de Google, vía el Apps Script publicado como web app. La URL está en `SHEET_URL`, arriba del script de `index.html`
- El código del Apps Script está en `apps-script.gs`, con los pasos de instalación y deploy en su comentario de cabecera. Ojo: al editarlo hay que crear una **nueva versión** de la implementación, si no la URL `/exec` sigue ejecutando el código viejo
- El envío por mail vía formsubmit.co quedó como fallback: sólo corre si `SHEET_URL` está vacía

## Música
La sección `#musica` embebe la playlist de Spotify y el botón "Agregá canciones" abre el link de invitación a colaborar. Para que la gente pueda sumar temas, la playlist tiene que estar en modo colaborativo en Spotify (playlist → menú → Invitar colaboradores).

## Deploy
Vercel, sitio estático sin build. Push a `main` en GitHub deploya automáticamente.

## Pendientes
- [ ] Alias/CBU real en Regalos (hoy `CATA.CHANO.ARS` y `CATA.CHANO.USD`)
- [ ] Confirmar que la playlist esté en modo colaborativo (probar el link desde otra cuenta)
- [ ] Opcional: renombrar la playlist, que hoy se muestra como "SWELL FOR LIFE"

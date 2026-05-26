# Demo 2 — Globo 3D con noticias legibles

Globo WebGL (Three.js) con marcadores clicables. Al hacer clic en un punto,
un **panel flotante de HTML real** muestra noticias de muestra de esa ciudad.
El panel se renderiza dentro del canvas vía `THREE.HTMLTexture` (que usa la API
**HTML-in-Canvas** por debajo), así que el texto es seleccionable, accesible e
indexable — no es una imagen.

## Stack
- Three.js r184 (`HTMLTexture` en el core, `InteractionManager` en addons) vía CDN.
- `three-html-render` polyfill: usa la API **nativa** si el navegador la trae
  (Origin Trial activo); si no, la **emula en JS** para que el demo igual renderice.

## Cómo verlo
- **Versión nativa (real):** despliega en Vercel + registra el Origin Trial
  (ver abajo). En Chrome 148+ funciona sin flags.
- **Versión polyfill (degradada):** funciona en cualquier Chrome moderno sin token,
  pero la fidelidad/accesibilidad es la del polyfill, no la nativa.
- **Local con flag:** Chrome Canary/Brave + `chrome://flags/#canvas-draw-element`.

## Origin Trial (para la versión nativa en tu dominio)
1. Deploy en Vercel, copia tu URL (`https://TU-DEMO.vercel.app`).
2. Registra ese origin en:
   https://developer.chrome.com/origintrials/#/view_trial/3478467762190286849
3. Pega el token en `index.html`, descomentando:
   ```html
   <meta http-equiv="origin-trial" content="TU_TOKEN" />
   ```
4. Redeploy. El badge inferior dirá "modo nativo".

> El token es por origin: este demo necesita el suyo (subdominio distinto al demo 1).

## Datos
Las noticias son **de muestra**, claramente etiquetadas. El demo ilustra la
mecánica de la API, no un feed real.

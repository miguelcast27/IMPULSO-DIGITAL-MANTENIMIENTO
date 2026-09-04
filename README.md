# Academia Impulso Digital — Página de mantenimiento

Landing estática de "en mantenimiento", 100% HTML/CSS/JS vanilla, sin dependencias de build.

## Estructura

```
index.html          → marcado + <img> del logo oficial
styles.css          → estilos, paleta de marca y animación de entrada del logo
script.js           → dispara la animación de entrada al cargar
logo-academia.png   → logo oficial de Academia Impulso Digital (ver nota abajo)
```

## Ver en local

Basta con abrir `index.html` en el navegador, o servirlo con cualquier servidor estático:

```bash
npx serve .
```

## Deploy

Es un sitio 100% estático (sin build step), así que cualquiera de estas opciones funciona directo:

### Vercel
```bash
npx vercel --prod
```
O bien: importar el repo en [vercel.com/new](https://vercel.com/new) — no requiere configurar build command ni output directory (déjalos vacíos / "Other").

### Netlify
Arrastrar la carpeta del proyecto a [app.netlify.com/drop](https://app.netlify.com/drop), o conectar el repo con:
- Build command: (vacío)
- Publish directory: `.`

### Cloudflare Pages
Conectar el repo con:
- Build command: (vacío)
- Build output directory: `/`

## Notas

- `logo-academia.png` es el ícono del búho recortado del logo oficial entregado por el cliente (sin el wordmark "Academia Impulso Digital", que se muestra aparte como texto vivo en `index.html` para que quede nítido en cualquier resolución y no se duplique). El CSS lo escala manteniendo su proporción (120px de ancho en mobile, 150px desde 640px).
- La fuente usada es **Montserrat** (Google Fonts, pesos 400/600/700), elegida por ser la que más se aproxima a la tipografía del banner de marca en LinkedIn ("Aprende con confianza. Impulsa tu futuro.") — confirmar con el cliente si existe una fuente de marca oficial distinta.
- La animación de entrada del logo (fade-in + leve desplazamiento hacia arriba) respeta `prefers-reduced-motion`.

Ver [SDD-mantenimiento-impulso-digital.md](../SDD-mantenimiento-impulso-digital.md) para el detalle completo del encargo.

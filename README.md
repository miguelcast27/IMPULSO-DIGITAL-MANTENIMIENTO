# Academia Impulso Digital — Página de mantenimiento

Landing estática de "en mantenimiento", 100% HTML/CSS/JS vanilla, sin dependencias de build.

## Estructura

```
index.html   → marcado y búho animado (SVG inline)
styles.css   → estilos, paleta de marca y animaciones
script.js    → dispara la animación de entrada al cargar
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

- El logo del búho está dibujado como SVG inline en `index.html` (no depende de un asset externo), siguiendo la paleta de marca definida en el SDD. Si la Academia entrega el logo oficial en SVG/PNG, puede reemplazarse fácilmente por ese asset.
- La fuente usada es **Poppins** (Google Fonts) como aproximación segura a la tipografía de marca — ver sección 5 del SDD para confirmar con el cliente si existe una fuente oficial distinta.
- Las animaciones respetan `prefers-reduced-motion`.

Ver [SDD-mantenimiento-impulso-digital.md](../SDD-mantenimiento-impulso-digital.md) para el detalle completo del encargo.

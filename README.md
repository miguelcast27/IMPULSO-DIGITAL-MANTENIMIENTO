# Academia Impulso Digital — Página de mantenimiento

Landing estática de "en mantenimiento", 100% HTML/CSS/JS vanilla, sin dependencias de build.

## Estructura

```
index.html               → marcado + <img> del ícono y del wordmark oficiales
styles.css               → estilos, paleta de marca y animación de entrada
script.js                → dispara la animación de entrada al cargar
logo-academia.png        → ícono (búho) del logo oficial
wordmark-academia.png    → wordmark "Academia Impulso Digital" en la tipografía real de marca
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

- `logo-academia.png` (ícono) y `wordmark-academia.png` (texto "Academia Impulso Digital") son ambos recortes del material oficial entregado por el cliente, con el fondo blanco eliminado (fondo transparente) para integrarse con el degradado de la página. El ícono lleva `alt=""` (decorativo) porque el wordmark ya aporta el nombre accesible de la marca. El CSS los escala manteniendo su proporción.
- La fuente **Montserrat** (Google Fonts, pesos 400/600/700) sigue usándose para el resto del texto de la página (título y subtítulo) — se eligió por ser la más parecida a la tipografía del wordmark oficial.
- La animación de entrada (fade-in + leve desplazamiento hacia arriba, ícono y luego wordmark) respeta `prefers-reduced-motion`.
- El fondo tiene un degradado sutil blanco → azul muy claro, más una capa decorativa en SVG inline (arcos concéntricos, patrón de circuito, puntos sueltos y cintas de flujo en las esquinas/bordes) a baja opacidad, puramente estática y detrás del contenido (`z-index` menor, `pointer-events: none`). En mobile (`max-width: 640px`) se ocultan los elementos secundarios (`.decor-mobile-hide`) para no saturar la pantalla.

Ver [SDD-mantenimiento-impulso-digital.md](../SDD-mantenimiento-impulso-digital.md) para el detalle completo del encargo.

# SDD — Página de Mantenimiento: Academia Impulso Digital

## 1. Contexto
Landing estática de "en mantenimiento" para la Academia Impulso Digital, usando como referencia estructural la página de NexoDev (nexodevss.tech). Debe verse profesional, minimalista, y usar la identidad visual real de la Academia (logo del búho, paleta de LinkedIn).

## 2. Objetivo
Una sola página (single page, sin rutas) que comunique que el sitio está en mantenimiento, con una animación sutil del logo (búho con casco de mantenimiento) que salude al cargar.

## 3. Stack sugerido
- HTML + CSS + JS vanilla (sin build tools), o Next.js/Vite si el amigo quiere algo desplegable en Vercel fácilmente.
- Sin dependencias de backend. 100% estático.
- Fuente vía Google Fonts (ver sección 5).

## 4. Estructura visual (de arriba hacia abajo, todo centrado)
1. **Logo del búho de Academia Impulso Digital** (asset SVG/PNG en alta resolución, fondo transparente).
2. **Nombre de marca**: "Academia Impulso Digital" (texto, debajo del logo, peso medium).
3. **Título principal (H1)**: "Estamos en mantenimiento"
4. **Subtítulo**: "Estamos realizando algunos ajustes y nuestro sitio web no está disponible temporalmente"

Sin emojis, sin iconografía decorativa adicional a lo especificado.

## 5. Identidad visual
- **Fondo**: blanco (`#FFFFFF`) — a diferencia de NexoDev (fondo oscuro), aquí el fondo es blanco por pedido explícito del cliente.
- **Paleta** (extraída del logo/LinkedIn de la Academia):
  - Azul marino oscuro: `#0B1F4D` (texto principal, contorno del búho)
  - Azul medio: `#1E5FBF` (acentos, ala/flecha del búho)
  - Naranja/ámbar: `#F5A623` (pico y ojo del búho, detalle de acento — también color del casco de mantenimiento)
  - Gris texto secundario: `#5B6472` (para el subtítulo)
- **Tipografía**: la página de LinkedIn usa la fuente por defecto de la plataforma, no la fuente real de marca — no se puede extraer con certeza desde el screenshot. Usar como aproximación segura una sans-serif geométrica/humanista similar a la que se ve en el banner: **Poppins** o **Montserrat** (pesos 400/600/700), vía Google Fonts. Confirmar con el cliente si tiene guía de marca con la fuente exacta.

## 6. Animación del búho (elemento diferenciador vs. NexoDev)
- El búho de Academia Impulso Digital reemplaza el ícono geométrico "N" de NexoDev.
- Al cargar la página:
  1. El búho aparece con un pequeño rebote/fade-in (300–500ms).
  2. Sobre su cabeza aparece (fade-in con leve delay) un **casco de mantenimiento amarillo/naranja** (ícono SVG simple, no emoji).
  3. El búho hace un gesto de "saludo": puede ser una de sus alas levantándose brevemente, o un guiño simple mediante CSS (parpadeo del ojo), en loop suave cada 4–6 segundos (no agresivo, sutil).
- Implementación sugerida: SVG inline con `<g>` separados para cuerpo, ala, casco → animar con CSS `@keyframes` (transform: translateY / rotate) o con una librería ligera tipo `anime.js` si se prefiere más control. Evitar Lottie/After Effects para no añadir peso innecesario.
- Fallback: si no se logra la animación a tiempo, el logo estático + casco fijo sobre la cabeza es aceptable como versión mínima viable.

## 7. Responsive
- Mobile-first. En mobile: logo más pequeño, título en 2 líneas si es necesario, subtítulo con `max-width` para legibilidad (similar al comportamiento de NexoDev).
- Breakpoint sugerido: 640px.

## 8. Accesibilidad y SEO básico
- `<title>Academia Impulso Digital — En mantenimiento</title>`
- `<meta name="description">` con el mismo texto del subtítulo.
- Contraste AA verificado entre texto y fondo blanco.
- `alt` descriptivo en el logo/búho.

## 9. Assets necesarios (entregar a Claude Code junto con este documento)
- Logo del búho en PNG/SVG de Academia Impulso Digital (adjunto).
- Si se quiere el casco como asset aparte, puede generarse como SVG simple directamente en el código (no requiere archivo extra).

## 10. Entregable esperado de Claude Code
- Carpeta del proyecto lista para deploy en Vercel/Netlify/Cloudflare Pages.
- Un solo archivo `index.html` (o página única si es framework) + `styles.css` + `script.js` (o equivalente en el framework elegido).
- README corto con instrucciones de deploy.

## 11. Fuera de alcance
- No se construye el sitio final de la Academia, solo el placeholder de mantenimiento.
- No hay formulario de contacto, ni newsletter, ni analytics en esta fase (se puede agregar después si el cliente lo pide).

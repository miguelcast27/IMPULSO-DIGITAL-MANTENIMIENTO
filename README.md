# Academia Impulso Digital — Página de mantenimiento

Landing estática de "en mantenimiento". 100% HTML/CSS/JS vanilla, sin build step ni dependencias — `index.html` en la raíz, todos los assets en rutas relativas (`./styles.css`, `./script.js`, `./logo-academia.png`, `./wordmark-academia.png`).

## Estructura

```
index.html               → marcado, SVG decorativo de fondo, <img> del ícono y wordmark
styles.css                → estilos, paleta de marca, animaciones y hover
script.js                 → dispara la animación de entrada al cargar
logo-academia.png         → ícono (búho) del logo oficial, fondo transparente
wordmark-academia.png     → wordmark "Academia Impulso Digital", tipografía real de marca
vercel.json                → config de deploy (build vacío, sitio estático)
```

## Ver en local

Abrir `index.html` directo en el navegador, o servirlo con cualquier servidor estático (`npx serve .`).

## Deploy en Vercel

**Desde CLI:**
```bash
npm i -g vercel   # si no la tienes instalada
vercel login
vercel            # primera vez: sigue el wizard y confirma el proyecto
vercel --prod     # despliega a producción
```

**Desde GitHub (recomendado para deploys automáticos):**
1. Sube este repo a tu cuenta de GitHub (`git push`).
2. En [vercel.com/new](https://vercel.com/new), importa el repo.
3. Vercel detecta `vercel.json` — no hace falta tocar build command ni output directory.
4. Cada push a la rama principal vuelve a desplegar automáticamente.

## Dominio personalizado

En el proyecto dentro de Vercel: **Settings → Domains → Add**, escribe tu dominio (`.io`, `.tech`, `.dev`, etc.) y sigue las instrucciones. Normalmente es uno de estos dos casos:
- **Dominio raíz** (`tudominio.tech`): Vercel te da un registro `A` → apúntalo a `76.76.21.21` en el DNS de tu proveedor.
- **Subdominio** (`www.tudominio.tech`): Vercel te da un registro `CNAME` → apúntalo a `cname.vercel-dns.com`.

La propagación DNS puede tardar desde minutos hasta un par de horas; Vercel emite el certificado SSL automáticamente en cuanto detecta el DNS correcto.

## Notas

- El ícono y el wordmark son recortes del material oficial entregado por el cliente, con el fondo blanco removido. El ícono lleva `alt=""` (decorativo) porque el wordmark ya aporta el nombre accesible de la marca.
- Fuente **Montserrat** (Google Fonts) — la más parecida a la tipografía del wordmark oficial.
- El fondo decorativo (arcos, circuito, puntos, cintas) es SVG inline, animado solo con `transform`/`opacity` (nunca width/height/top/left, para no forzar reflow), con `will-change: transform` en los elementos que rotan/flotan/se desplazan como ayuda extra de rendimiento. Hover sutil por elemento solo en dispositivos con mouse real (`@media (hover: hover) and (pointer: fine)` — nunca se activa en touch), y completamente estático si el usuario tiene `prefers-reduced-motion` activado. Los arcos de la esquina superior izquierda son arcos parciales (no círculos completos) a propósito: un círculo entero es rotacionalmente invariante y no se vería girar aunque rote — el hueco es lo que hace visible el movimiento.
- La amplitud del movimiento (flotado de puntos, desplazamiento de las cintas) se reduce automáticamente en mobile vía variables CSS (`--decor-dot-amp`, `--decor-ribbon-y`, `--decor-ribbon-scale` en `:root`, sobreescritas en `@media (max-width: 640px)`) para que se note igual de bien sin saturar una pantalla chica; tablet y desktop comparten los valores "normales". Varios elementos secundarios (grillas de puntos, un nodo extra, una cinta) también se ocultan en mobile con la clase `.decor-mobile-hide`.
- La página no se adapta a dark mode del sistema operativo a propósito — mantiene siempre su paleta de marca clara (fondo blanco/celeste, texto navy), que ya cumple contraste AA sin importar el tema del SO.

## Probar en múltiples dispositivos

1. Abre `index.html` en Chrome o Firefox (local o la URL de Vercel).
2. Abre DevTools (`F12` o clic derecho → Inspeccionar).
3. Activa el **Device Toolbar** (ícono de celular/tablet, o `Ctrl+Shift+M` / `Cmd+Shift+M` en Mac).
4. Prueba al menos estos tamaños desde el selector de dispositivo:
   - **iPhone 12** (390×844) — mobile.
   - **iPad Air** (768×1024) — tablet.
   - **Responsive → 1920×1080** — laptop/desktop grande.
   - Gira cualquiera de los presets móviles al ícono de rotar (⟳) para revisar landscape.
5. En cada tamaño, confirma que: el texto no se corta ni se monta, no aparece scroll horizontal, y el movimiento del fondo (arcos, puntos, cintas, circuito) se sigue notando sin tapar el logo/texto central.
6. Repite rápido en Firefox y, si tienes Mac, en Safari — el CSS usado (custom properties, `:hover` con media features, SVG animado) es estándar y ampliamente soportado, pero nunca está de más una pasada visual cruzada.

Ver [SDD-mantenimiento-impulso-digital.md](SDD-mantenimiento-impulso-digital.md) para el detalle completo del encargo original.

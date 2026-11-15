# Laboratorio de Animaciones — guía para el agente

Este repositorio es un **laboratorio de animaciones cortas estilo cómic** hechas con HTML, CSS, SVG y JavaScript puro.
Se publica con **GitHub Pages** y el usuario las ve en el navegador. Responde y comenta el código **en español**.

## Concepto: "modo vídeo"

Cada animación se comporta como **un vídeo**, no como una página que se desplaza:

- Hay **una sola pantalla fija 16:9** (lienzo interno de **1280×720 px**) que se escala entera a la ventana.
- La historia se divide en **escenas** (`<section class="scene">`). Solo se ve **una a la vez**.
- Cuando una escena termina, la siguiente la **reemplaza con una transición** (iris, destello, barrido, página…).
- Un **reproductor** debajo de la pantalla: reproducir/pausar (barra espaciadora), reiniciar, barra de progreso
  segmentada por escenas (clic = saltar a esa escena), pantalla completa y botón ⬅ a la galería.
- Empieza con una pantalla "▶ Reproducir" y termina con una pantalla "↺ ¡Otra vez!".

La versión antigua en viñetas apiladas (`comic-vinetas/`) se conserva solo como referencia histórica: **no usar ese formato** para animaciones nuevas.

## Estructura del repositorio

```
index.html          Galería principal (tarjetas con acceso a cada animación)
_plantilla/         Plantilla base en modo vídeo: COPIAR para empezar una animación nueva
comic-demo/         "Héroe vs. Robot" en modo vídeo (ejemplo de referencia completo)
comic-vinetas/      Versión v1 en viñetas (histórica)
.nojekyll           Hace que GitHub Pages publique los archivos tal cual
```

Cada animación vive en **su propia carpeta** con un único `index.html` autocontenido (sin build, sin npm, sin dependencias).
Única dependencia externa permitida por defecto: Google Fonts (`Bangers` y `Comic Neue`).

## Cómo crear una animación nueva

1. Copiar `_plantilla/` a una carpeta nueva con nombre corto en minúsculas y guiones (ej. `persecucion/`).
2. Cambiar `<title>` y el `<h2>` de la pantalla de inicio.
3. Escribir las escenas dentro de `<div class="stage">`. Cada escena:
   ```html
   <section class="scene bg-sky halftone" data-dur="4000" data-enter="iris" data-name="Nombre">
     …elementos…
     <div class="frame"></div>   <!-- borde de tinta, siempre al final -->
   </section>
   ```
   - `data-dur`: duración en ms (normalmente 3000–5000).
   - `data-enter`: `none` (solo la primera), `iris`, `flash`, `wipe`, `page`. Variar las transiciones; usar `flash` para impactos.
   - `data-name`: aparece al pasar el ratón por la barra de progreso.
4. **No tocar el motor JS** (escalado, línea de tiempo, controles) salvo que la tarea lo pida; si se mejora, aplicar la mejora también a `_plantilla/` y `comic-demo/`.
5. Añadir la animación a la lista `animaciones` del `<script>` de `index.html` (raíz). Las tarjetas se generan solas:
   ```js
   { titulo: '…', descripcion: '…', enlace: 'persecucion/', icono: '🚀', color: '#ffd60a', tags: ['…'] }
   ```
6. Verificar (ver abajo), hacer commit y push.

## Piezas disponibles (clases CSS de la plantilla)

| Pieza | Uso |
|---|---|
| `.halftone` + `.bg-yellow/.bg-sky/.bg-paper/.bg-red` | Fondo con trama de puntos de cómic |
| `.speedlines` | Rayos giratorios de acción (escenas de impacto/título) |
| `.city` (con `<i style="height:…%">`) + `.ground` | Ciudad de fondo y suelo |
| `.cloud` | Nube que se desplaza |
| `<svg class="char"><use href="#hero"/></svg>` | Personaje (símbolos SVG `#hero`, `#robot` definidos una vez arriba) |
| `.walk` `.drop` `.punch` `.flyaway` `.peek` `.shake` | Movimientos de personaje / temblor de cámara |
| `.bubble` (`.right` = colita a la derecha) + `.type` | Globo de diálogo con texto que se escribe letra a letra |
| `.caption` | Caja amarilla de narrador |
| `.sfx` | Onomatopeya (¡POW!, ¡CRASH!) |
| `.burst` | Estallido blanco detrás de una onomatopeya |
| `.title-line` | Texto grande de título |
| `.surprise` | Signo "!" de sorpresa |

**Tiempos dentro de una escena** con variables CSS en `style`:
- `--d`: retraso desde que empieza la escena (ej. `--d:1.4s`).
- En `.type`: `--n` = número de caracteres del texto, `--t` = duración de la escritura.
- En `.sfx`: `--r` = rotación final (ej. `--r:-8deg`).

Las animaciones internas se activan con el selector `.scene.on .clase { animation: … }`. Al crear un movimiento nuevo,
seguir ese patrón y usar `animation-fill-mode: both/forwards` para que el estado final se mantenga.

## Guía de estilo visual

- **Tinta**: bordes negros gruesos (`#111`, 5–10 px en el lienzo), sombras duras desplazadas (`box-shadow: 7px 7px 0 #111`), sin sombras difusas.
- **Paleta** (variables en `:root`): amarillo `#ffd60a`, rojo `#e63946`, azul `#3a86ff`, cielo `#8ecae6`, papel `#fdf6e3`.
- **Tipografía**: `Bangers` para títulos y onomatopeyas (con `-webkit-text-stroke` y `text-shadow` doble rojo/negro); `Comic Neue` para diálogos y narración.
- **Movimiento** "de dibujo animado": rebotes con `cubic-bezier` que se pasan de 1 (ej. `cubic-bezier(.3,1.8,.5,1)`), anticipación antes de un golpe, temblor en los impactos.
- Personajes en **SVG simple** (formas geométricas) definidos como `<symbol>` y reutilizados con `<use>`.
- Ritmo: escenas de 3–5 s, animaciones totales de 15–40 s. Textos cortos que se lean con calma.
- Contenido **original**: no recrear personajes, logos ni escenas de obras existentes.

## Verificación antes de publicar

- Servir el repo con `python3 -m http.server` (con `file://` las carpetas no abren su `index.html`).
- Con Playwright: abrir la animación, pulsar `#startBtn`, sacar capturas a mitad de cada escena **y durante cada transición**, y comprobar que no hay errores en consola.
- Revisar que ningún elemento de la escena anterior quede por encima de la nueva y que nada importante se tape (onomatopeyas sobre caras, etc.).
- Comprobar que la tarjeta nueva aparece en la galería y que ⬅ vuelve a ella.

## Publicación

- GitHub Pages publica desde la rama **`claude/comic-style-animations-v2fr62`** (carpeta raíz).
  URL: https://johanmorenolds.github.io/animaciones/
- Tras el push, Pages tarda 1–2 minutos en actualizar.

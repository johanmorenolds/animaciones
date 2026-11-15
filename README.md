# 🎬 Laboratorio de Animaciones

Animaciones cortas **estilo cómic** hechas solo con HTML, CSS, SVG y JavaScript, sin instalar nada.

👉 **Verlas:** https://johanmorenolds.github.io/animaciones/

## La idea

Cada animación funciona como **un vídeo**:

- Una sola pantalla 16:9 (lienzo de 1280×720) que se adapta a cualquier tamaño, incluida la pantalla completa.
- La historia se divide en **escenas**. Cada escena reemplaza a la anterior con una **transición**: iris, destello, barrido o paso de página.
- Tiene controles de reproductor: ▶/❚❚ (o la barra espaciadora), ↺ reiniciar, barra de progreso por escenas y ⛶ pantalla completa.

## Qué hay en el repositorio

| Carpeta | Contenido |
|---|---|
| `index.html` | Galería principal con una tarjeta por animación |
| `_plantilla/` | Punto de partida para una animación nueva |
| `comic-demo/` | **Héroe vs. Robot**: el ejemplo completo en modo vídeo |
| `comic-vinetas/` | La primera versión, en viñetas (histórica) |
| `CLAUDE.md` | Guía detallada: concepto, piezas disponibles, estilo y reglas |

## Crear una animación nueva

1. Copia la carpeta `_plantilla/` y ponle un nombre nuevo, por ejemplo `persecucion/`.
2. Edita las escenas. Cada una es un bloque así:
   ```html
   <section class="scene bg-sky halftone" data-dur="4000" data-enter="iris" data-name="La calma">
     … personajes, globos, onomatopeyas …
   </section>
   ```
   - `data-dur`: cuánto dura, en milisegundos.
   - `data-enter`: cómo entra. Puede ser `none`, `iris`, `flash`, `wipe` o `page`.
3. Añade la animación a la lista `animaciones` de `index.html` para que aparezca en la galería.
4. Haz commit y push. GitHub Pages la publica en 1 o 2 minutos.

**Con Claude Code** basta con pedírselo, por ejemplo: *"crea una animación nueva donde el robot persigue al héroe por la ciudad"*. El agente lee `CLAUDE.md` y ya conoce el formato, el estilo y cómo publicarla.

## Verla en tu ordenador

```bash
python3 -m http.server
# y abre http://localhost:8000
```

# Plan: «¿Qué es el invierno?» — animación para una niña de 3 años (Alemania)

Estado: **plan** (todavía no hay animación). Cuando se apruebe, se construye en `invierno/index.html`
copiando `_plantilla/`, siguiendo `CLAUDE.md`.

## 1. Idea en una frase

Una niña pequeña sale de casa en invierno en Alemania y, con su amigo el erizo, descubre
**cinco cosas del invierno**: hace frío, el sol se va pronto a dormir, cae nieve, nos abrigamos
y algunos animales duermen. Al final, la primavera vuelve.

## 2. Qué debe entender una niña de 3 años (y qué no)

| Sí (ideas sencillas, concretas) | No (demasiado abstracto) |
|---|---|
| En invierno **hace frío** | La inclinación del eje de la Tierra |
| El sol sale **tarde** y se va **pronto**: hay más noche | Solsticios, órbitas, grados |
| Cuando hace mucho frío, la lluvia se vuelve **nieve**; el agua se vuelve **hielo** | Cristalización, temperaturas bajo cero |
| Nos ponemos **gorro, bufanda, guantes y botas** | — |
| Los árboles **no tienen hojas**; el erizo **duerme todo el invierno** | Hibernación, metabolismo |
| El invierno **se termina** y llega la primavera | Ciclo de estaciones completo |

Explicación del frío, en clave infantil: *«En invierno el sol está más bajito y lejos, por eso
calienta poquito, y además se va a dormir muy pronto.»*

## 3. Personajes (originales, SVG sencillo)

- **La niña** (nombre por decidir; podría llevar el nombre de la niña): cara redonda, abrigo rojo,
  gorro amarillo con pompón. Versión «sin abrigo» y «abrigada» (símbolos `#nina` y `#nina-abrigo`).
- **Pincho, el erizo**: bola marrón con púas triangulares, nariz negra. Versión despierto y dormido (`#erizo`, `#erizo-duerme`).
- **El sol**: círculo amarillo con cara amable; puede bostezar.
- Extras: muñeco de nieve, árbol sin hojas, casa con ventana iluminada, copos de nieve.

## 4. Escenas (≈ 75 s en total, todo **lento**)

| # | Nombre | Dur. | Entrada | Qué se ve | Texto (corto, para leer en voz alta) |
|---|---|---|---|---|---|
| 1 | Título | 6 s | none | Copos cayendo muy despacio sobre fondo azul cielo | **¿Qué es el invierno?** |
| 2 | Por la ventana | 8 s | iris | La niña mira por la ventana; fuera, el árbol ya no tiene hojas | «Mira… ¡el árbol no tiene hojas!» |
| 3 | El sol cansado | 9 s | page | El sol, bajito y pequeño, cruza el cielo y se esconde pronto; el cielo se pone oscuro y se encienden las ventanas | Narrador: «En invierno el sol está lejos. Calienta poquito… y se va a dormir muy pronto.» |
| 4 | ¡Qué frío! | 8 s | wipe | La niña sale sin abrigo, tiembla suavemente, sale vaho de su boca | «¡Brrr! ¡Qué frío!» |
| 5 | A abrigarse | 10 s | iris | Van apareciendo una a una, despacio: gorro, bufanda, guantes, botas, abrigo | Narrador: «Gorro… bufanda… guantes… botas. ¡Ya no hay frío!» |
| 6 | La nieve | 10 s | page | Nubes grises; caen copos grandes y lentos; el suelo se vuelve blanco | Narrador: «Cuando hace mucho frío, la lluvia se vuelve nieve.» |
| 7 | Muñeco de nieve | 9 s | iris | Tres bolas aparecen una sobre otra, zanahoria, sombrero; la niña aplaude; un charco helado brilla | «¡Un muñeco de nieve!» |
| 8 | El erizo duerme | 9 s | wipe | Montón de hojas; Pincho bosteza, se hace bolita, salen «Zzz» lentas | Narrador: «Pincho el erizo duerme todo el invierno, calentito.» |
| 9 | Vuelve la primavera | 8 s | iris | La nieve se derrite, sale una flor, el sol crece y sonríe, Pincho despierta | Narrador: «Y después del invierno… ¡llega la primavera!» |
| — | Fin | — | — | Pantalla «↺ ¡Otra vez!» del reproductor | — |

Escenas cortas en texto, una idea por escena. Las escenas 3, 5 y 6 son las «de explicación»; el resto, de juego.

## 5. Cómo hacerlo **lento y tranquilo** (adaptado a 3 años)

- **Escenas de 8–10 s** (en vez de 3–5 s) y **transiciones más largas** (iris/page/wipe ≈ 1,5–2 s), definidas en el CSS de esta animación.
- **Sin `flash`, sin temblores fuertes, sin `speedlines`, sin onomatopeyas agresivas** (nada de ¡POW!). Los «sfx» serán suaves: «Brrr», «Zzz», «¡Plof!».
- Movimientos con `ease-in-out` largos (2–4 s); los rebotes de dibujo animado, más suaves (`cubic-bezier(.4,1.3,.6,1)`).
- Texto que se escribe despacio (`--t` amplio) y queda en pantalla varios segundos.
- Colores cálidos dentro del frío: casa con luz amarilla, abrigo rojo, para que no resulte triste.
- El botón de pausa (barra espaciadora) permite al adulto parar en cada escena y hablar con la niña.

## 6. Toque alemán (opcional)

- Escenario reconocible en Alemania: casas con tejado a dos aguas, un *Weihnachtsmarkt* con luces de fondo en la escena 3 o 7.
- Palabra en alemán bajo algunos objetos, pequeña y en gris, para una niña bilingüe:
  gorro = *Mütze*, bufanda = *Schal*, guantes = *Handschuhe*, nieve = *Schnee*, muñeco de nieve = *Schneemann*, erizo = *Igel*.

## 7. Pasos de construcción

1. Copiar `_plantilla/` a `invierno/`; cambiar `<title>` y `<h2>`.
2. Crear los símbolos SVG (niña, niña abrigada, erizo, sol, árbol, muñeco de nieve) y la capa de copos.
3. Añadir en el CSS de `invierno/` las animaciones nuevas (`snowfall`, `sunset`, `dressUp`, `melt`, `zzz`) con el patrón `.scene.on .clase` y `fill-mode: both`, y alargar las transiciones.
4. Escribir las 9 escenas con `data-dur` 6000–10000.
5. Añadir la tarjeta a `index.html`: `{ titulo: '¿Qué es el invierno?', enlace: 'invierno/', icono: '❄️', color: '#8ecae6', tags: ['Para peques', 'Lento', 'Estaciones'] }`.
6. Verificar con Playwright (capturas a mitad de cada escena y en cada transición, consola sin errores) y publicar.

## 8. Preguntas abiertas

1. ¿La niña de la animación lleva el **nombre de la niña**? ¿Cuál?
2. Una niña de 3 años no lee: ¿lo **leerá un adulto** en voz alta, o añadimos **voz narrada** automática en español (voz del navegador)?
3. ¿Incluimos las **palabras en alemán**?
4. ¿Ritmo: ≈ 75 s está bien, o aún más lento?

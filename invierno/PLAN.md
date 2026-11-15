# Plan: «Del otoño al invierno» — animación para una niña de 3 años (Alemania)

Estado: **construida** en `invierno/index.html` (a partir de `_plantilla/`).
Decisiones: la niña se llama **Talulla**; el texto lo **lee un adulto** en voz alta (sin voz automática);
**con** palabras en alemán; duración ≈ **81 s**.

## 1. Idea en una frase

Ahora es **otoño** en Alemania: las hojas caen y el erizo prepara su cama. Poco a poco el otoño
**se convierte en invierno**, y la niña, con su amigo el erizo, descubre **cinco cosas del invierno**:
hace frío, el sol se va pronto a dormir, nos abrigamos, el erizo duerme y cae la nieve.
Así la animación empieza en la estación que la niña está viviendo ahora y le cuenta lo que viene.

## 2. Qué debe entender una niña de 3 años (y qué no)

| Sí (ideas sencillas, concretas) | No (demasiado abstracto) |
|---|---|
| En invierno **hace frío** | La inclinación del eje de la Tierra |
| El sol sale **tarde** y se va **pronto**: hay más noche | Solsticios, órbitas, grados |
| Cuando hace mucho frío, la lluvia se vuelve **nieve**; el agua se vuelve **hielo** | Cristalización, temperaturas bajo cero |
| Nos ponemos **gorro, bufanda, guantes y botas** | — |
| En **otoño** las hojas se ponen de colores y **se caen**; después viene el **invierno** | Ciclo de estaciones completo |
| Los árboles se quedan **sin hojas**; el erizo **duerme todo el invierno** | Hibernación, metabolismo |

Explicación del frío, en clave infantil: *«En invierno el sol está más bajito y lejos, por eso
calienta poquito, y además se va a dormir muy pronto.»*

## 3. Personajes (originales, SVG sencillo)

- **La niña** (nombre por decidir; podría llevar el nombre de la niña): cara redonda, abrigo rojo,
  gorro amarillo con pompón. Versión «sin abrigo» y «abrigada» (símbolos `#nina` y `#nina-abrigo`).
- **Pincho, el erizo**: bola marrón con púas triangulares, nariz negra. Versión despierto y dormido (`#erizo`, `#erizo-duerme`).
- **El sol**: círculo amarillo con cara amable; puede bostezar.
- Extras: árbol (con hojas naranjas → sin hojas → con nieve), hojas que caen, muñeco de nieve, casa con ventana iluminada, copos de nieve.

## 4. Escenas (≈ 80 s en total, todo **lento**)

El hilo es **el mismo árbol** delante de la casa: aparece en casi todas las escenas y su cambio
(hojas naranjas → hojas cayendo → sin hojas → cubierto de nieve) le muestra a la niña el paso del otoño al invierno.

| # | Nombre | Dur. | Entrada | Qué se ve | Texto (corto, para leer en voz alta) |
|---|---|---|---|---|---|
| 1 | Título | 6 s | none | Hojas naranjas cayendo despacio que, poco a poco, se convierten en copos de nieve | **Del otoño al invierno** |
| 2 | Es otoño | 9 s | iris | La niña junto al árbol con hojas rojas y naranjas; las hojas caen girando muy despacio y ella intenta atrapar una | Narrador: «Ahora es otoño. Las hojas se ponen de colores… y se caen.» |
| 3 | Pincho prepara su cama | 9 s | page | Pincho el erizo arrastra hojas y hace un montón; bosteza | «¡Estoy juntando hojas para mi camita!» |
| 4 | El sol cansado | 9 s | wipe | El sol, bajito y pequeño, cruza el cielo y se esconde pronto; el cielo se oscurece y se encienden las ventanas | Narrador: «Cada día el sol se va a dormir más pronto… y calienta poquito.» |
| 5 | Llega el invierno | 10 s | iris | **La transición:** en la misma escena, la última hoja cae del árbol, el cielo se vuelve gris, el viento sopla y el árbol queda desnudo | Narrador: «La última hoja se cae… ¡ya llega el invierno!» |
| 6 | ¡Qué frío! y a abrigarse | 10 s | page | La niña tiembla y sale vaho de su boca; van apareciendo una a una: gorro, bufanda, guantes, botas | «¡Brrr! ¡Qué frío!» → Narrador: «Gorro… bufanda… guantes… botas.» |
| 7 | El erizo duerme | 9 s | wipe | Pincho se hace bolita dentro de su montón de hojas; salen «Zzz» lentas | Narrador: «Pincho duerme todo el invierno, calentito. ¡Buenas noches, Pincho!» |
| 8 | La nieve | 10 s | iris | Caen copos grandes y lentos; el árbol, el tejado y el montón de Pincho se vuelven blancos | Narrador: «Cuando hace mucho frío, la lluvia se vuelve nieve.» |
| 9 | Muñeco de nieve | 9 s | page | Tres bolas aparecen una sobre otra, zanahoria, sombrero; la niña aplaude; al fondo, las luces de la casa | «¡Hola, invierno!» |
| — | Fin | — | — | Pantalla «↺ ¡Otra vez!» del reproductor | — |

Escenas cortas en texto, una idea por escena. Las escenas 4, 5 y 8 son las «de explicación»; el resto, de juego.
La escena 5 es la central: el cambio ocurre **dentro de la escena**, sin cortar, para que se vea que una estación se va transformando en la otra.

## 5. Cómo hacerlo **lento y tranquilo** (adaptado a 3 años)

- **Escenas de 8–10 s** (en vez de 3–5 s) y **transiciones más largas** (iris/page/wipe ≈ 1,5–2 s), definidas en el CSS de esta animación.
- **Sin `flash`, sin temblores fuertes, sin `speedlines`, sin onomatopeyas agresivas** (nada de ¡POW!). Los «sfx» serán suaves: «Brrr», «Zzz», «¡Plof!».
- Movimientos con `ease-in-out` largos (2–4 s); los rebotes de dibujo animado, más suaves (`cubic-bezier(.4,1.3,.6,1)`).
- Texto que se escribe despacio (`--t` amplio) y queda en pantalla varios segundos.
- Colores cálidos dentro del frío: casa con luz amarilla, abrigo rojo, para que no resulte triste.
- El botón de pausa (barra espaciadora) permite al adulto parar en cada escena y hablar con la niña.

## 6. Toque alemán (opcional)

- Escenario reconocible en Alemania: casas con tejado a dos aguas, un *Weihnachtsmarkt* con luces de fondo en la escena 4 o 9.
- Palabra en alemán bajo algunos objetos, pequeña y en gris, para una niña bilingüe:
  otoño = *Herbst*, invierno = *Winter*, hoja = *Blatt*, gorro = *Mütze*, bufanda = *Schal*, guantes = *Handschuhe*, nieve = *Schnee*, muñeco de nieve = *Schneemann*, erizo = *Igel*.

## 7. Pasos de construcción

1. Copiar `_plantilla/` a `invierno/`; cambiar `<title>` y `<h2>`.
2. Crear los símbolos SVG (niña, niña abrigada, erizo, sol, árbol, muñeco de nieve) y la capa de copos.
3. Añadir en el CSS de `invierno/` las animaciones nuevas (`leafFall`, `snowfall`, `sunset`, `dressUp`, `grayout`, `zzz`) con el patrón `.scene.on .clase` y `fill-mode: both`, y alargar las transiciones.
4. Escribir las 9 escenas con `data-dur` 6000–10000 (el árbol, igual en todas, para que se note el cambio).
5. Añadir la tarjeta a `index.html`: `{ titulo: 'Del otoño al invierno', enlace: 'invierno/', icono: '🍂', color: '#f4a261', tags: ['Para peques', 'Lento', 'Estaciones'] }`.
6. Verificar con Playwright (capturas a mitad de cada escena y en cada transición, consola sin errores) y publicar.

## 8. Preguntas abiertas

1. ¿La niña de la animación lleva el **nombre de la niña**? ¿Cuál?
2. Una niña de 3 años no lee: ¿lo **leerá un adulto** en voz alta, o añadimos **voz narrada** automática en español (voz del navegador)?
3. ¿Incluimos las **palabras en alemán**?
4. ¿Ritmo: ≈ 80 s está bien, o aún más lento?

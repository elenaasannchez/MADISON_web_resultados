# Decisiones del rediseño

Registro de lo que he decidido sin preguntar, y por qué. Ordenado por fases.

## Fondos nuevos (26 nov) — sustituye a lo que diga más abajo sobre temas, fondos y momentos

- **Dos versiones, `?fondo=a` y `?fondo=b`**, en lugar de los temas claro y oscuro. La B es la de por defecto: la eligió Elena. En vistas previas que quitan los parámetros vale `#fondo-b`.
- **Cómo se pinta:** canvas 2D. Cada forma (anillo o mancha) es un campo suave calculado en una rejilla pequeña; luego se pasa por un degradado de color y se le pone grano de 1 px más denso donde el azul es más fuerte. Se calcula en un worker cuando se puede y se guarda una imagen por sección. Al hacer scroll solo cambian la opacidad, la posición y la escala de las dos imágenes vecinas, así que va fluido en el móvil.
- **B se oscurece pronto (desde perfiles):** las secciones con texto largo no pueden quedar con el núcleo negro de la mancha detrás de texto oscuro. Portada, resumen y test van en claro; de perfiles al final, fondo cada vez más oscuro y texto claro (`.osc-b`), salvo “cómo”, “mapa” y “examen”, que vuelven a blanco con las manchas en las esquinas para dar ritmo (lo pidió Elena).
- **Legibilidad en A:** las manchas de las secciones son algo más suaves que las de la portada, y el gris del texto secundario es más oscuro (`#333A52`) para leerse encima del azul.
- **Barra superior:** lleva un degradado del color de fondo para que el texto que pasa por debajo no se mezcle con “Madison” e “Índice”.
- **Quitados:** interruptor de tema, revista, cartón rasgado, cartel con personas, siluetas SVG y Lenis. Las sillas de la pregunta rápida se quedan porque no se pidió quitarlas.
- **Animaciones:** entradas suaves (opacidad y 22 px hacia arriba) de textos y gráficos, y el fondo transformándose. Nada más.

## Antes de empezar

- **Copia de seguridad:** la rama `copia/antes-del-rediseno` (y la etiqueta `copia-antes-rediseno`) guardan la web tal como estaba, con el contenido del experimento 2 ya puesto.
- **Contenido de partida:** uso la versión con los cambios de `cambios_web.md` (experimento 2, recomendaciones nuevas, etc.), que es la más reciente. Ningún dato ni frase cambia.
- **Referencias:** las imágenes y `NOTAS.md` estaban sueltas en la raíz de otra rama; las he movido a `referencias/` como dice el encargo. No se cargan en la web.
- **Conflictos con las skills:** cuando una skill choca con el encargo, manda el encargo. En concreto:
  - *design-taste-frontend* pide fotos reales y prohíbe que los bloques aparezcan al bajar. El encargo prohíbe usar fotos y pide entradas animadas, así que no hay fotos y sí hay entradas, pero cada tipo de bloque entra de una forma distinta (no todo con el mismo fundido hacia arriba). Tampoco uso su generador de paletas ni su comprobador automático, porque está hecho para webs de empresa con fotos y suspendería por diseño.
  - *frontend-design* desaconseja destacar una palabra en cursiva en los títulos. Es justo la combinación elegida por Elena para la portada, así que se mantiene, y la uso como sistema (siempre Playfair cursiva para las palabras clave), no como adorno suelto.
- **CLAUDE.md:** sus reglas de color (amarillo, Glacier Blue) y de fuentes (Anton, DM Serif, Fira Sans) quedan sustituidas por el encargo. Lo actualizo al final para que no confunda a nadie.

## Fase 1 · Sistema

### Paleta
Azul eléctrico como protagonista, negros con un punto de azul, blancos rotos y grises fríos. Nada de amarillo.

| Token | Claro | Oscuro | Uso |
|---|---|---|---|
| `--bg` | `#EDEFF3` | `#04060E` | fondo general |
| `--bg-2` | `#DCE0E8` | `#0A0F2C` | bandas y paneles |
| `--ink` | `#0A0D1A` | `#E9ECF4` | texto |
| `--ink-2` | `#535A6E` | `#8C93AA` | texto secundario |
| `--line` | negro al 14 % | blanco al 14 % | líneas finas, cruces |
| `--electric` | `#1F38F2` | `#2D47FF` | azul eléctrico |
| `--electric-2` | `#7186FF` | `#5068FF` | segundo azul |
| `--deep` | `#060D3A` | `#020414` | azul casi negro |

Por qué: el azul eléctrico sobre gris frío es la firma de las referencias 05, 13, 14 y 17; el negro azulado evita el negro plano de plantilla.

### Tipografía: dos voces
Las cinco fuentes elegidas por Elena, organizadas como sistema y no al azar:

- **Voz alta** (secciones de impacto): títulos en **Archivo negra cursiva** en mayúsculas, palabras clave en **Playfair Display cursiva**, cifras grandes en **Anton**. Es la combinación 4 de la portada.
- **Voz baja** (secciones de lectura): títulos en **Inter Tight** seminegra, en minúscula y muy apretada, palabras clave en **Playfair Display cursiva**, cifras en **Inter Tight** fina.
- **Texto:** **Geist** en todas partes, también en los textos técnicos de las esquinas.
- Las secciones alternan voz alta y voz baja según lo que cuentan: los golpes (portada, uso, brecha, competencias, experimento 2) van en voz alta; las de explicar (resumen, cómo, evaluación, mapa, profesores, método) en voz baja.
- Solo se cargan los pesos que se usan: Archivo 900 cursiva, Playfair 500 y 600 cursiva, Anton, Geist 400/500/600 e Inter Tight 300/500/600.

Escala (móvil → ordenador): portada 44 → 150 px (se ajusta al ancho), título de sección 32 → 76, subtítulo 21 → 30, cifra gigante 84 → 220, cifra media 46 → 96, texto 17, pequeño 14, técnico 11.

### Espacios y retícula
- Espaciado en pasos de 4: 4, 8, 12, 16, 24, 32, 48, 72, 112.
- Móvil: margen de 20 px y una columna. Ordenador: 12 columnas, máximo 1280 px, con el texto en las 7 primeras y los gráficos ocupando más.
- Alineado a la izquierda siempre. Nada centrado salvo dentro de los gráficos.

### Capas comunes
- **Grano:** un solo ruido SVG fijo sobre toda la página, generado una vez. Igual en todas las secciones.
- **Blur:** manchas de luz hechas con degradados radiales (no con `filter: blur`), así se pueden mover sin coste.
- **Capa técnica:** cruces finas en retícula (ref. 01), líneas de 1 px (ref. 05), esquinas de selección (ref. 13) y textos pequeños en las esquinas de cada sección con su número, el tamaño de la muestra y la fuente.

### Movimiento
- Curvas: `expo.out` para entradas (llegan rápido y se posan), `power3.inOut` para cambios de estado y `none` para lo que va pegado al scroll.
- Duraciones: 0,6 s (detalles), 1,1 s (bloques) y 1,6 s (gráficos y portada).
- Cada tipo de bloque entra distinto: títulos de voz alta se destapan de izquierda a derecha, los de voz baja suben línea a línea, las cifras cuentan, los gráficos se construyen y las listas se marcan con su cruz.

### El elemento que viaja: la mira
Una cruz fina (+) con cuatro esquinas de selección, sacada de las referencias 01 y 13. Es el hilo conductor:

| De | A | Qué pasa |
|---|---|---|
| Portada | Resumen | La cruz que invita a bajar cae al scroll y se convierte en la cruz de cada uno de los seis hallazgos. |
| Resumen | Test | Las cruces se abren en las cuatro esquinas del rectángulo de enfoque que enmarca la pregunta del test. |
| Test | Perfiles | El rectángulo de enfoque se queda y pasa a señalar, una a una, las tres siluetas de los perfiles. |
| Uso | Cómo | La mancha de luz azul de "Uso" baja con el scroll y acaba siendo el fondo de "Cómo". |
| Cómo | Brecha | La línea del eje de 0 a 100 de "Cómo" se alarga y pasa a ser el eje del gráfico de "Brecha". |
| Mapa | Experimento 1 | Los bloques del mapa de usos se pliegan y dejan paso a la revista. |
| Profesores | Experimento 2 | La fila de siete cabezas punteadas se convierte en la fila de puntos del gráfico de notas. |

### Recursos por sección
Cinco momentos especiales, separados entre sí por secciones tranquilas:

| Sección | Voz | Fondo | Momento o forma del dato |
|---|---|---|---|
| Portada | alta | gris esmerilado con cruces (01) y mancha azul con grano (14, 17) | entrada del título |
| Resumen | baja | retícula fina (05) | cruces que marcan cada hallazgo |
| Test | baja | azul profundo con órbitas finas (04) | rectángulo de enfoque (13), resultado con regla 0–100 |
| Perfiles | alta | azul eléctrico con siluetas difuminadas (11) | **Momento 1: siluetas** fijadas en pantalla; hábitos en gráfico de puntos |
| Uso | alta | círculos con grano (19) | cifras gigantes y burbujas para las herramientas |
| Cómo | baja | barras diagonales difuminadas (20) | eje vertical de 0 a 100 |
| Brecha | alta | gris liso | **Momento 2: sillas** (02) en la pregunta rápida; gráfico de pesas |
| Evaluación | baja | cuadrados difuminados (06) | gráfico de mariposa alumnos/profesores |
| Competencias | alta | mancha oscura (23) | medidores de 7 casillas; **Momento 3: cartón rasgado** (21) con la frase final |
| Mapa | baja | liso | mapa de áreas (08) agrupado por el semáforo |
| Experimento 1 | alta | negro con halo (25) | **Momento 4: revista azul** (10) que se abre; cuadrículas de 100 |
| Profesores | baja | gris con cruces | cabezas punteadas (16) agrupadas por tipo; indicador de 7 puntos en cada hallazgo |
| Experimento 2 | alta | azul con retícula (05) | gráfico de pendientes y columnas; bloque azul (09) para la frase clave |
| Recomendaciones | alta | oscuro siempre | **Momento 5: cartel luminoso con siluetas** (22) |
| Método | baja | gris con esquinas de selección | pasos numerados (sí es una secuencia) |

Referencias que no uso: 03 (multitud con foco, se solaparía con las siluetas), 07 (troquelado, ya hay cinco momentos y el encargo pide pocos), 09 solo como bloque de texto, 12 (repite la idea de las siluetas), 15 (texto 3D repetido, demasiado efecto para una web de datos), 18 y 24 como variantes de fondo ya cubiertas por 14 y 23.

### Gráficos
Ningún tipo se repite seguido: puntos → burbujas → eje → pesas → mariposa → medidores → mapa de áreas → cuadrículas → cabezas → pendientes. Todos en SVG o HTML a mano, sin librerías de gráficos, con los mismos números que tenía la web.

## Fases 2 a 7 · Lo que he decidido por el camino

- **Tema por defecto: oscuro.** El azul eléctrico y el grano lucen más sobre negro, y en la sala de la presentación la pantalla del móvil molesta menos. El claro está entero y se elige con el botón de la barra, con `?tema=claro` o con `#tema-claro` (para vistas previas que quitan los parámetros).
- **Acento según el tema:** en oscuro, las palabras en Playfair y las cifras usan un azul más claro (`#8193FF`) porque el eléctrico puro no se leía bien sobre negro; en claro, el eléctrico (`#1F38F2`).
- **Semáforo sin colores de semáforo:** como no se puede usar amarillo ni verde, la luz encendida va arriba (aprender), en medio (depende) o abajo (delegar). Los nombres “Verde · Amarillo · Rojo” se mantienen porque son el contenido.
- **Mapa de áreas:** las celdas pequeñas usan una letra menor y, si el nombre no cabe, se corta con puntos suspensivos; el nombre completo está en el texto alternativo del gráfico.
- **Etiquetas de las siluetas:** iban como “pills”, que el proyecto prohíbe; ahora son texto con una línea fina encima.
- **Cartón rasgado:** el papel se ha agrandado para que el hueco nunca deje ver el fondo por los bordes.
- **Regla del resultado del test:** “tú” va encima de la línea y “media 66” debajo, para que no se pisen cuando el resultado está cerca de la media.
- **Momentos fijados (pin):** solo uno, las siluetas de perfiles (`+=180%` de scroll). El resto de momentos se disparan al entrar o se mueven con el scroll sin fijar la pantalla, para no pelearse con la barra del navegador del móvil (`ignoreMobileResize`).
- **Títulos de voz baja:** se parten en palabras con JS para que suban línea a línea (sin SplitText, que en la versión 3.12 es de pago).
- **Lenis:** se carga solo en ordenador con ratón y sin movimiento reducido; en el móvil no se descarga.
- **Imagen para WhatsApp:** `og-image.jpg` (1200×630) compuesta aparte con la portada, y `icono.png` para el icono del iPhone. La ruta de `og:image` es relativa: hay que cambiarla por la URL absoluta al publicar.
- **Revisión con design-critique (resumen):** lo que más fallaba en la primera captura era la barra (la marca partía en dos líneas en el móvil), el contraste del acento sobre negro, las cifras 80 % / 5 % que se partían, el fondo de círculos de “Uso” que parecía papel pintado (ahora son cuatro círculos grandes) y la tarjeta de pesas que crecía demasiado en ordenador (los gráficos SVG tienen un ancho máximo de 720 px).

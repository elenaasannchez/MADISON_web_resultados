# Encargo: rediseño completo de la web de resultados

## Contexto
Esta web es la que verán por el QR al final de nuestra presentación del viernes 27 de noviembre: profesores, jurado y la empresa Madison, casi todos desde el móvil. Tiene que parecer obra de un estudio de diseño editorial, cero IA. La web ya existe en este repositorio y el CLAUDE.md tiene el contexto. El contenido y los datos ya están y NO se cambian ni se inventan: el rediseño es visual y de movimiento.

## Cómo quiero que trabajes
- Trabaja de forma autónoma de principio a fin. No me preguntes nada: cuando dudes, decide tú y apunta la decisión y el motivo en `DECISIONES.md`.
- Antes de empezar, lee los SKILL.md instalados en `.claude/skills` (frontend-design, GSAP, taste y design-critique) y síguelos. Usa design-critique para criticar tus propias capturas al final de cada fase.
- Antes de empezar, crea una rama o haz un commit de copia de seguridad del estado actual.
- Haz commit al terminar cada fase, con un mensaje claro.
- Revísate tú: al terminar cada fase, haz capturas de todas las secciones a 390 × 844 (móvil) con Playwright (instálalo si no está), míralas y corrige lo que esté mal antes de seguir. Haz también una pasada a 1440 px de ancho.
- Si te quedas sin tiempo o sin uso, deja en `ESTADO.md` qué está hecho, qué falta y cómo seguir.

## Fuentes
- Las fuentes son las que ya te he dicho: la combinación elegida para el título principal y el resto de fuentes que te indiqué como válidas. No hay regla fija salvo para ese título. Quiero una web dinámica: cada sección puede cambiar de fuente, de mayúsculas a minúsculas, de tamaño, etc. Decides tú lo que queda mejor estéticamente, con coherencia (que se note que es un sistema y no un caos). Carga solo las fuentes y pesos que uses de verdad.

## Paleta
Negro, blanco, grises y, sobre todo, azul eléctrico; se pueden usar otros azules. Nada de amarillo ni de colores de las referencias.

## Referencias
Mira una a una todas las imágenes de `referencias/` y lee `referencias/NOTAS.md`, donde explico qué me gusta de cada una y para qué. Son ideas, no material: no copies textos, logos ni fotos, y no pongas ninguna de esas imágenes en la web. Todo se redibuja con código (SVG, CSS, canvas) con nuestra paleta y fuentes. Tienen que parecer del mismo universo: nada de collage.

## Tu criterio de diseñador
Actúa como director de arte de un estudio, no como alguien que ejecuta una lista. Tú decides qué recurso queda bien en cada sección, qué recurso encaja con cada dato y qué fuente va en cada sitio. Si una referencia no encaja en ningún sitio, no la uses. Quiero que la estética de la web cambie bastante respecto a la actual.

## Ritmo: pocos momentos especiales, bien repartidos
No quiero que la web esté todo el rato cambiando de recurso (de repente un libro, luego unas sillas, luego otra cosa…). Elige 3 o 4 momentos especiales en toda la web (sillas, cartón rasgado, troquelado, revista, rectángulo de enfoque, siluetas, cartel luminoso… los que mejor encajen) y repártelos intercalados. El resto de secciones se apoyan en los fondos (blur, grano, manchas, retícula, capa técnica) y en la tipografía, con variedad pero sin efectos especiales.

## Estética: futurista y con difuminado
Entiende bien la estética que busco antes de diseñar nada: futurista, tecnológica y editorial a la vez, como una interfaz de un estudio de diseño del futuro, no ciencia ficción de película. Se basa en el azul eléctrico, el blur o difuminado con grano (me encanta y es la firma de la web), los halos y manchas de luz, las siluetas a contraluz, las líneas finas, las cruces y las esquinas de selección, y los textos pequeños técnicos en las esquinas. Fíjate sobre todo en las referencias 01, 04, 05, 11, 13, 22 y 23-25. Que se note limpio y elegante, nunca recargado.

## Hilo conductor entre secciones
Quiero que haya continuidad entre secciones: que un elemento de la sección actual se transforme en algo de la siguiente (por ejemplo, la cruz que se convierte en el rectángulo de enfoque, una mancha de luz que se desplaza y pasa a ser el fondo de la siguiente, una línea que acaba siendo el eje de un gráfico, un número que se queda y cambia de tamaño…). No tiene que pasar en todas las transiciones, pero úsalo sobre todo en las secciones más sencillas o que no tienen un momento especial, para que ninguna se sienta suelta. Planifica estos enlaces en la fase 1 y apúntalos en `DECISIONES.md` (qué elemento pasa de qué sección a cuál).

## Gráficos y forma de enseñar los datos
Libertad total de formas. Hay muchas barras: cambia algunas por círculos, mapas de áreas, sillas, siluetas, puntos, números enormes, lo que funcione mejor para cada dato. No pongas dos gráficos del mismo tipo seguidos. Los datos tienen que ser exactos (los mismos que hay ahora) y legibles en el móvil. Gráficos en SVG hecho a mano y animados con GSAP, sin Chart.js ni d3.

## Fases
1. **Análisis y sistema.** Analiza las referencias y la web actual. Define en `tokens.css` (o en el CSS principal) colores, escala tipográfica, espaciados, retícula, grano, blur, capa técnica (cruces, líneas, esquinas, textos de esquina) y movimiento (2 o 3 curvas y duraciones). Elige el elemento que viaja entre secciones. Apunta en `DECISIONES.md` qué recurso de qué referencia va en cada sección.
2. **Fondos y capas comunes.** Monta los fondos de cada sección y sus transiciones entre sí.
3. **Secciones.** Rediseña cada sección con su forma de enseñar los datos y los momentos especiales (máximo 4 o 5 en toda la web: por ejemplo sillas, troquelado, revista, rectángulo de enfoque, siluetas…). La calculadora del IUA tiene que seguir funcionando igual y verse impecable, con un resultado final muy cuidado.
4. **Animación.** GSAP + ScrollTrigger: entradas y salidas de cada sección, el recorrido del elemento que viaja, gráficos que se construyen al llegar y 2 o 3 momentos fijados en pantalla como mucho. Lenis solo en ordenador.
5. **Pulido.** Rendimiento, accesibilidad, etiquetas para la vista previa de WhatsApp (título, descripción, imagen), favicon y repaso de textos.
6. **Versión clara y versión oscura.** Con la web terminada, haz dos temas: uno claro (blancos, grises y azul eléctrico) y uno oscuro (fondos tirando a negro y azules muy oscuros, casi sin blanco, pero con el azul eléctrico muy presente; no todo negro). Reparte las referencias según encajen mejor en cada tema (en `NOTAS.md` lo explico). Hazlo con variables CSS sobre la misma web, para no duplicar código, con un interruptor discreto para cambiar de tema y que también se pueda abrir directamente cada uno con `?tema=claro` y `?tema=oscuro`, para que yo pueda compararlos y elegir.
7. **Revisión final.** Capturas de todo en móvil en los dos temas, corrección y un `RESUMEN.md` corto con lo que has hecho y lo que debo revisar yo.

## Lo que NO quiero (delata a la IA)
- Tarjetas con sombra, esquinas muy redondeadas por todas partes, degradados morados o arcoíris, iconos genéricos, emojis.
- Todo centrado y todo apareciendo con el mismo fundido hacia arriba.
- Botones y cajas tipo plantilla.
- Textos nuevos con frases hechas («Descubre…», «En un mundo donde…»). Si tocas textos, que suenen naturales, en primera persona del plural.

## Móvil y rendimiento (obligatorio)
- Diseña primero a 390 px. Una idea por pantalla. Textos legibles sin hacer zoom.
- Usa `svh`/`dvh` y prueba que la barra del navegador no rompe las secciones fijadas.
- No animes `filter: blur` ni `backdrop-filter` en movimiento continuo. El blur y el grano se generan una vez (gradientes, SVG o imagen ligera generada por ti) y se anima solo transform y opacity.
- Que cargue rápido con datos móviles: nada de vídeos, imágenes ligeras (WebP/SVG) y fuentes recortadas.
- Respeta `prefers-reduced-motion` (versión sin animaciones). La web se tiene que leer bien aunque falle el JavaScript de las animaciones.

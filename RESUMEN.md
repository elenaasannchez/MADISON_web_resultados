# Resumen del rediseño

**Qué es:** la web de resultados rediseñada de arriba abajo según `ENCARGO.md`, con el mismo contenido y los mismos datos. Sigue siendo un solo `index.html`.

**Cómo se ve**
- Universo azul eléctrico sobre negro azulado (o sobre gris frío en el tema claro), con manchas de luz con grano, cruces finas, esquinas de selección y textos técnicos en las esquinas.
- Dos voces tipográficas: Archivo cursiva + Playfair + Anton para los golpes; Inter Tight + Playfair para explicar; Geist para el texto.
- Un hilo conductor, la mira (cruz y esquinas), que cae desde la portada, marca los hallazgos, enmarca el test y recorre las siluetas.
- Cinco momentos: siluetas fijadas en perfiles, sillas en la pregunta rápida, cartón rasgado en competencias, revista que se abre en el experimento 1 y cartel luminoso con siluetas en las recomendaciones.
- Un tipo de gráfico distinto en cada sección, dibujado a mano en SVG.

**Cómo verlo**
- Abrir `index.html`. Tema: botón de la barra, `?tema=claro` o `?tema=oscuro`.
- La calculadora del test funciona igual que antes (mismas frases, mismo índice y mismos perfiles).

**Comprobado**
- Capturas a 390×844 y 1440 de todas las secciones, en los dos temas.
- Sin desbordamiento horizontal ni errores en la consola.
- Con movimiento reducido y con GSAP bloqueado, todo el contenido se ve.

**Falta (fuera de esta web)**
- Publicarla, poner la URL absoluta en `og:image` y generar el QR.

Las decisiones y su porqué están en `DECISIONES.md`.

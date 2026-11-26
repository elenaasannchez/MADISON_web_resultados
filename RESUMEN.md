# Resumen de la web

**Qué es:** la web de resultados con el mismo contenido, test y gráficos, y los fondos rehechos (26 nov). Sigue siendo un solo `index.html`.

**Fondos (dos versiones para elegir)**
- `?fondo=a`: anillos y lazos azules muy difuminados con grano de aerógrafo sobre blanco roto, como la referencia 18.
- `?fondo=b` (por defecto, la elegida): manchas de azul ultramar con núcleo negro; empieza claro (ref. 14) y se oscurece al bajar hasta casi negro (ref. 23–25). Desde perfiles, el texto pasa a claro.
- En las dos, el estampado cambia de posición, tamaño e intensidad en cada sección y se transforma suavemente al hacer scroll. Se pinta en canvas, una vez por sección, y solo se anima opacidad y posición.

**Qué se ha quitado**
- El interruptor de tema claro/oscuro, la revista, el cartón rasgado, el cartel con personas y las siluetas. Sus datos siguen, con el estilo del resto.

**Comprobado**
- Capturas a 390×844, 1024 y 1440 de todas las secciones en las dos versiones, al lado de las referencias (parecido 9/10).
- Sin desbordamiento horizontal ni errores en la consola.

**Falta (fuera de esta web)**
- Elegir A o B, publicarla, poner la URL absoluta en `og:image` y generar el QR.

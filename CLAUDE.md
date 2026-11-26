# Web del Econo-Reto Madison: «¿La IA ayuda a aprender o solo a terminar antes?»

Página de resultados de un estudio sobre cómo usan la IA los universitarios (UVa). Se enseña con un **QR al final de una presentación de 10 minutos**, así que casi todo el mundo la abrirá en el **móvil**. Equipo de 4 estudiantes de Marketing. Final: 27 nov 2026.

Todo está en un solo archivo: `index.html` (HTML + CSS + JS dentro). Para verlo, basta con abrirlo en el navegador. Dependencias externas: Google Fonts, GSAP 3.12.5 + ScrollTrigger (cdnjs). Si GSAP no carga, la página se lee entera sin animaciones. El fondo se pinta en un canvas con JavaScript (sin JS, la página queda sobre gris claro y se lee igual).

El sistema de diseño completo y el porqué de cada decisión están en `DECISIONES.md`. El encargo del rediseño está en `ENCARGO.md`.

## Cómo trabajar
- Haz cambios pequeños y enséñamelos antes de seguir con lo siguiente.
- Mira siempre cómo queda en **móvil (390 px de ancho)** y en ordenador, y en las dos versiones de fondo (`?fondo=a`, `?fondo=b`; en vistas previas, `#fondo-b`).
- No toques los datos ni las cifras salvo que yo lo pida.
- Mantén todo en un solo archivo (salvo `og-image.jpg` e `icono.png`).

## Colores
Negro azulado, blancos rotos, grises fríos y, sobre todo, **azul eléctrico**. **Nada de amarillo** ni colores de las referencias. Todo va en variables CSS (`--bg`, `--ink`, `--electric`…) sobre fondo claro. En la versión B, las secciones con `.osc-b` (de perfiles al final) cambian a texto claro porque su fondo es oscuro.

## Fondos
Dos versiones, sin interruptor en la web: **A** = anillos y lazos azules con grano de aerógrafo sobre blanco roto (ref. 18); **B** (por defecto, elegida por Elena el 26 nov) = manchas azules con núcleo negro que se van oscureciendo al bajar (ref. 14 → 23–25), con tres secciones claras intercaladas (cómo, mapa y examen) para dar ritmo. Es un solo estampado que cambia de forma en cada sección y se funde al hacer scroll. Se pinta en canvas (formas → difuminado → grano), una imagen por sección, y solo se anima con `opacity` y `transform`. Las escenas de cada sección están en el script «Motor del fondo» de `index.html` (`escenaA`, `escenaB`).

## Tipografías: dos voces
- **Voz alta** (golpes): Archivo 900 cursiva en mayúsculas, palabra clave en Playfair Display cursiva, cifras en Anton.
- **Voz baja** (explicar): Inter Tight 600 apretada, palabra clave en Playfair Display cursiva, cifras en Inter Tight 300.
- **Texto:** Geist.
- Portada = combinación 4, en 4 líneas fijas: «¿La IA ayuda» / «a *aprender*» / «o solo a» / «*terminar antes*?». Debajo, «DEPENDE DE CÓMO SE USE.» y «Aquí tienes todo lo que descubrimos.».

## Reglas de diseño
- Firma visual: blur hecho con degradados (nunca `filter: blur` animado), un solo grano fijo, cruces finas, esquinas de selección y textos técnicos pequeños en las esquinas.
- El hilo conductor es **la mira** (cruz + cuatro esquinas). Sin momentos especiales: revista, cartón rasgado, cartel y siluetas se quitaron (26 nov); sus datos se muestran como el resto. Las animaciones son solo entradas suaves de textos y gráficos.
- Ningún tipo de gráfico se repite seguido. Gráficos a mano en SVG/HTML, sin librerías.
- **Prohibido:** rótulos pequeños encima de los títulos, pestañitas o «pills», comillas « » (usar “ ” o la cursiva), sombras de tarjeta, esquinas muy redondeadas, degradados morados o arcoíris, iconos genéricos, emojis, fotos o imágenes de las referencias.
- Animar solo `transform` y `opacity`. Respetar `prefers-reduced-motion`.

## Reglas de contenido
- Frases afirmativas y sencillas, en primera persona del plural. **Nunca** «significativo», p-valores ni jerga estadística.
- Los tres perfiles se llaman **Activo (58 %), Mixto (22 %) y Pasivo (20 %)**. Nunca «activo sin verificar».
- Perfiles de profesores: escéptico (3), integrador (2), pragmático (2).
- Las recomendaciones van a **3 públicos: estudiantes, universidad y empresas**. Madison **no** es destinataria de ninguna recomendación y no se le «vende» nada.
- En las cautelas del final tiene que aparecer: datos autodeclarados, muestra pequeña, etc. **No** mencionar las réplicas de la encuesta de profesores ni que el trabajo se hizo con IA.

## Pendiente
- Publicar en un hosting gratuito (Netlify Drop o GitHub Pages), poner la URL absoluta en `og:image` (`https://…/og-image.jpg`) y hacer el QR con esa URL.

# Web del Econo-Reto Madison: «¿La IA ayuda a aprender o solo a terminar antes?»

Página de resultados de un estudio sobre cómo usan la IA los universitarios (UVa). Se enseña con un **QR al final de una presentación de 10 minutos**, así que casi todo el mundo la abrirá en el **móvil**. Equipo de 4 estudiantes de Marketing. Entrega del informe: 24 nov 2026. Final: 27 nov 2026.

Todo está en un solo archivo: `index.html` (HTML + CSS + JS dentro). Para verlo, basta con abrirlo en el navegador. No hay dependencias aparte de Google Fonts.

## Cómo trabajar
- Haz cambios pequeños y enséñamelos antes de seguir con lo siguiente.
- Mira siempre cómo queda en **móvil (390 px de ancho)** y en ordenador.
- No toques los datos ni las cifras salvo que yo lo pida.
- Mantén todo en un solo archivo.

## Colores (no usar otros)
| Nombre | Hex | Uso |
|---|---|---|
| Glacier Blue | `#82B0DB` | fondo general (`--blue`) |
| Azul oscuro derivado | `#5F95C9` | barras y algunas tarjetas (`--blue-dark`) |
| Navy | `#101D49` | texto, tarjetas oscuras y bandas oscuras (`--cocoa`, se llama así por historia) |
| Lemon | `#F7EB4F` | portada, acentos, subrayados y botones (`--yellow`) |
| Blanco | `#FFFFFF` | solo detalles pequeños sobre navy. **Nunca de fondo.** |

- Sobre amarillo, el texto va siempre en navy, nunca en blanco.
- Para dar contraste se alternan bandas a todo lo ancho: `section.band` (navy) y `section.band-lemon` (amarillo).

## Tipografías (solo estas tres)
- **Anton** (`--display`): títulos en MAYÚSCULAS, números grandes, botones, barra de navegación y títulos de los gráficos.
- **DM Serif Display cursiva** (`--accent`): palabras destacadas dentro de los títulos (`<em>`), un poco más pequeñas (`.9em`) y subidas (`top: -.14em`) para quedar centradas con las mayúsculas. También se usa en los nombres de los perfiles (Activo, Mixto, Pasivo…) y en la primera frase de los recuadros oscuros (`.callout b`). **No abusar de ella.** No usarla en las frases de las listas con flecha.
- **Fira Sans** (`--body`): todo el texto normal.

## Reglas de diseño que ya se han decidido
- El título de la portada va siempre en 4 líneas fijas: «¿La IA ayuda» / «a *aprender*» / «o solo a» / «*terminar antes*?».
- Debajo: «DEPENDE DE CÓMO SE USE.» en Fira Sans, en mayúsculas y negrita, sin recuadro, seguido de «Aquí tienes todo lo que descubrimos.».
- La portada ocupa la pantalla completa: degradado amarillo, esfera azul con trama de puntos y «IA» en contorno, y un círculo giratorio «Desliza y descubre».
- **Subrayado amarillo**, con una regla fija: va siempre en las cursivas de los títulos y en alguna frase clave de los títulos (`<mark>`). También en los títulos de tarjetas que van en pareja (si se subraya uno, se subraya el otro, clase `.hl`). Los números grandes no se subrayan nunca.
- **Prohibido:** rótulos pequeños encima de los títulos (tipo «LO MÁS IMPORTANTE»), pestañitas o «pills» decorativas, y comillas « ». Usar “ ” o la cursiva.
- Animaciones: entrada de la portada, bloques que aparecen al bajar, barras que crecen y números que cuentan. Hay que respetar `prefers-reduced-motion`.

## Reglas de contenido
- Frases afirmativas y sencillas. **Nunca** «significativo», p-valores ni jerga estadística.
- Los tres perfiles se llaman **Activo (58 %), Mixto (22 %) y Pasivo (20 %)**. Nunca «activo sin verificar».
- Perfiles de profesores: escéptico (3), integrador (2), pragmático (2).
- Las recomendaciones van a **3 públicos: estudiantes, universidad y empresas**. Hay una tarjeta extra, «Además, para las empresas». Madison **no** es destinataria de ninguna recomendación y no se le «vende» nada.
- En las cautelas del final tiene que aparecer: datos autodeclarados, muestra pequeña, etc. **No** mencionar las réplicas de la encuesta de profesores ni que el trabajo se hizo con IA.

## Pendiente
- Sección `#martes` («Próximamente»): el 24 nov llegan los datos del segundo experimento (examen sin IA, unos 40 alumnos). Habrá que rellenarla con los resultados: si quien usa mejor la IA saca mejor nota sin ella, la caída de nota sin IA y la matriz aprender × terminar antes.
- Publicar la versión final en un hosting gratuito (Netlify Drop o GitHub Pages) y hacer el QR con esa URL.

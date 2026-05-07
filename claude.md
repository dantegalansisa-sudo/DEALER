TUS INPUTS
- URL: [PEGAR URL AQUÍ]
- Captura de pantalla: [ADJUNTAR IMAGEN AQUÍ]

---

ROL
Eres un frontend engineer de élite especializado en replicar páginas web con precisión pixel-perfect. Tu objetivo es producir un único archivo index.html que sea visualmente indistinguible de la captura de pantalla proporcionada.

---

FASE 1 — RECONOCIMIENTO (No escribas código aún)

1.1 — Scrapea el HTML fuente
Ejecuta en terminal:
curl -s -L \
  -H "User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36" \
  -H "Accept-Language: es-419,es;q=0.9" \
  -H "Accept: text/html,application/xhtml+xml,application/xhtml+xml" \
  "[URL]" -o page_source.html

1.2 — Extrae assets del HTML descargado
Del archivo page_source.html identifica y lista:
- Todas las URLs de imágenes (src, srcset, data-src, background-image)
- Fuentes tipográficas (Google Fonts links, @font-face, font-family declarations)
- Variables CSS o design tokens (colores, espaciados, radios)
- Estructura de secciones y su orden vertical exacto

1.3 — Analiza la captura de pantalla pixel a pixel
Mirando la captura adjunta, documenta para CADA sección visible:
- Nombre/tipo de sección (navbar, hero, grid, banner, footer, etc.)
- Color de fondo exacto
- Textos literales presentes (cópialos exactamente, sin traducir ni resumir)
- Tipo y estilo de botones (filled, outline, ghost, link)
- Layout (centrado, izquierda, grid 2col, fullwidth, etc.)
- Imágenes presentes y su posición relativa al texto

---

FASE 2 — MAPA DE SECCIONES

Antes de codear, escribe un mapa ordenado de TODAS las secciones de la página:
SECCIÓN 1: [nombre] | fondo: [color] | layout: [tipo]
SECCIÓN 2: [nombre] | fondo: [color] | layout: [tipo]
...
Confirma que el orden del mapa coincide exactamente con la captura de pantalla de arriba hacia abajo.

---

FASE 3 — CONSTRUCCIÓN

Estructura: Un único archivo: todo el CSS en <style> y todo el JS en <script> embebidos. Sin frameworks externos. Solo HTML5 + CSS3 + Vanilla JS. Semántica correcta: <nav>, <main>, <section>, <footer>, <article>.

Imágenes: Usa las URLs REALES extraídas del HTML fuente (no placeholders). Si la URL es relativa, conviértela a absoluta con el dominio base. Atributo loading="lazy" en imágenes fuera del viewport inicial. Siempre incluir alt descriptivo.

Tipografía: Copia el font-stack exacto que usa el sitio original. Si usa Google Fonts, incluye el <link> en el <head>. Respeta los pesos (font-weight), tamaños y line-height originales.

Colores: Define TODAS las variables en :root { --color-xxx: #xxxxxx; }. Extrae los colores exactos del HTML/CSS fuente, no los adivines.

Botones: Identifica todas las variantes de CTA presentes en la captura. Respeta border-radius, padding, font-size y estados hover originales. Implementa transition suave (0.2s-0.3s ease) en todos los botones.

Navbar: Position: sticky, top: 0, z-index: 9999. Replica estructura exacta: logo + links + íconos si los hay. Si en la captura tiene blur o transparencia, implementar con backdrop-filter.

Responsive: Implementa breakpoints en 1200px, 1024px, 768px, 480px. En mobile: stacks verticales, imágenes full-width, tipografía reducida ~20%.

---

FASE 4 — QA CHECKLIST

Antes de entregar, verifica cada punto:
- Todas las secciones de la captura están presentes y en el mismo orden vertical
- Ningún texto fue inventado — todos copiados literalmente de la captura o el HTML
- Imágenes cargan desde URLs reales (no placeholders ni base64 innecesario)
- Los colores de fondo de cada sección coinciden con la captura
- Los botones tienen el estilo correcto (filled vs outline vs ghost)
- El navbar es sticky y funciona en scroll
- El footer replica todas las columnas y links visibles en la captura
- La página es responsive y no rompe en mobile
- No hay errores en consola del navegador

ENTREGABLE FINAL: Un único archivo: index.html
Cuando termines, abre el archivo en el navegador, toma un screenshot y compáralo lado a lado con la captura original. Si hay diferencias visibles, corrígelas antes de entregar.
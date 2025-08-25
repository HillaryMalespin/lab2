# Caribe Tico — Limón

Sitio informativo y promocional sobre turismo en **Limón, Costa Rica**.  
Incluye secciones de **destinos**, **consejos**, **itinerario**, **presupuestos** y un formulario para **unirte** al boletín.  

**Objetivo:** ofrecer una página **ligera, accesible y fácil de navegar** desde móvil y escritorio.

---

## 1) Estructura semántica

Etiquetas clave usadas y propósito:

- `<!DOCTYPE html>` y `lang="es-CR"` → documento HTML5 y localización en español de Costa Rica.
- `<meta charset="UTF-8">`, `<meta name="viewport">`, `<meta name="description">`, `<link rel="canonical">` → metadatos de SEO y responsive.
- `a.skip-link` → enlace de salto directo al contenido (`#contenido`).
- `header` → incluye `h1`, `p`, y `nav[aria-label="Navegación principal"]`.
- `main#contenido` → bloque principal del sitio.
- `section[aria-labelledby]` → organiza los temas principales: `#destinos`, `#consejos`, `#itinerario`, `#presupuestos`, `#registro`.
- `article[aria-labelledby]` → tarjetas individuales de destinos.
- `figure` + `img[alt]` + `figcaption` → imágenes con pie de foto descriptivo.
- `aside` + `blockquote` → citas inspiracionales.
- `video[controls][aria-label]` → consejos en video con subtítulos.
- `table` + `caption` + `aria-describedby` → tablas accesibles con contexto.
- `form` con `label[for]`, `fieldset` + `legend`, `select`, `button[type="submit"]`.
- `footer` + `nav[aria-label="Navegación de pie de página"]`.

---

## 2) URL pública de Netlify

👉 [https://caribetico.netlify.app/](https://caribetico.netlify.app/)

---

## 3) Validación W3C

- **Resultado:** _Document checking completed. No errors or warnings to show._  
- **Qué se validó:** la página publicada no presentó errores.

---

## 4) Lighthouse (Desktop)

| Métrica           | Puntuación |
|-------------------|------------|
| **Performance**   | 89         |
| **Accessibility** | 96         |
| **Best Practices**| 100        |
| **SEO**           | 100        |

**Hallazgos clave:**
- Objetivos táctiles pequeños en el menú de navegación.  
- Mejorar área clicable a **mínimo 44x44 px**.

---

## 5) Accesibilidad aplicada

### `tabindex`
- `a.skip-link[tabindex="0"]` → salto directo al contenido.  
- `img[tabindex="0"]` → enfocable con TAB para leer `figcaption`.  
- `img[tabindex="-1"]` → enfocable solo programáticamente, no en orden de tabulación.

### `aria-*`
- `nav aria-label="Navegación principal"` / `"Navegación de pie de página"`.  
- `section aria-labelledby="tit-*"` → asocia cada `h2` con su sección.  
- `article aria-labelledby="art-*-tit"` → cada destino tiene nombre accesible.  
- `video aria-label="Video con consejos para moverte en Limón"`.  
- `table aria-describedby="desc-*"` → tablas con contexto accesible.  
- `input aria-describedby="help-correo"` → correo vinculado a texto de ayuda.

### `alt`
- Todas las imágenes llevan `alt` descriptivo y específico.

### Enlaces descriptivos
- Ejemplos: “**Ver Cahuita en Google Maps**”, “**Volver al inicio**”.  
- Uso de `target="_blank"` + `rel="noopener noreferrer"` en externos.

---

## 6) Evidencia de CSS aplicado (Lab 3)

- **Selectores de tipo:** `header`, `nav`, `section`, `img`.  
- **Selectores de clase:** `.btn` en botones, `.card` en destinos.  
- **Selectores de ID:** `#destinos`, `#consejos`, `#itinerario`, `#presupuestos`, `#registro`.  
- **Selectores de atributo:**  
  - `a[target="_blank"]` → enlaces externos.  
  - `img[alt]` → todas las imágenes.  
  - `input[type="email"]` → control de correo.  

- **Combinadores:**  
  - `nav a + a` → enlaces adyacentes en menú.  
  - `.card p` → párrafos dentro de tarjetas.  
  - `header > nav` → hijo directo.  
  - `.tag ~ .tag` → hermanos.  

- **Pseudo-clases de estado:**  
  - `:hover` en `.btn`.  
  - `:focus-visible` en enlaces.  
  - `:active` en botones.  

- **Pseudo-clases estructurales:**  
  - `:first-child` y `:last-child` en listas.  
  - `:nth-child(2n)` en listas pares.  
  - `:not(.activo)` para exclusión.  

- **Especificidad:**  
  - Uso de `!important` en `.badge` dentro de `.card`.  
  - Uso de estilo en línea en `h2` (`style="margin-bottom:24px;"`).  

- **Box Model:**  
  - `box-sizing: border-box;` global.  
  - Márgenes y padding en `.card` y secciones.  
  - Colapso de márgenes gestionado entre `h2` y `.card`.  

- **Overflow:**  
  - Texto largo dentro de `.card` controlado con `overflow: auto;`.  

- **Flexbox:**  
  - Usado en `nav` para alinear enlaces con `justify-content` y `gap`.  

- **Grid:**  
  - Usado en `.cards-container` para organizar destinos con `grid-template-columns: repeat(auto-fit, minmax(300px, 1fr))`.  

- **Positioning:**  
  - `position: relative;` en `.banner`.  
  - `position: absolute;` en `.etiqueta` para destacar texto.  

---

## 7) Archivos CSS organizados

- `styles/base.css` → reset ligero, variables, tipografía.  
- `styles/layout.css` → layout y combinadores.  
- `styles/components.css` → componentes (`.btn`, `.card`, `.badge`).  
- `styles/overrides.css` → sobrescrituras y casos con `!important`.  

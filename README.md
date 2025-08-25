# Caribe Tico — Limón

Sitio informativo y promocional sobre turismo en **Limón, Costa Rica**. Incluye secciones de **destinos**, **consejos**, **itinerario**, **presupuestos** y un formulario para **unirte** al boletín.  
Objetivo: ofrecer una página **ligera, accesible y fácil de navegar** desde móvil y escritorio.

---

## 1) Branch y Deploy

- Rama creada: `lab3-selectores-boxmodel` [https://caribetico02.netlify.app/](https://caribetico02.netlify.app/)
- Deploy Netlify: [https://caribetico.netlify.app/](https://caribetico.netlify.app/)

---

## 2) Estructura semántica

- `<!DOCTYPE html>` y `lang="es-CR"`: documento HTML5 y localización en español de Costa Rica.  
- Metadatos (`charset`, `viewport`, `description`, `canonical`): SEO y responsive.  
- `a.skip-link`: enlace de salto para accesibilidad.  
- `header` con identidad y `nav[aria-label]`.  
- `main#contenido`: único bloque de contenido principal.  
- `section` por tema (`#destinos`, `#consejos`, `#itinerario`, `#presupuestos`, `#registro`).  
- `article`, `figure`, `figcaption`, `ul`, `ol`, `blockquote`, `video`, `table` accesibles.  
- `form` con `label`, `fieldset`, `legend`, `select`, `input`, `button`.  
- `footer` con `nav[aria-label]`.  

---

## 3) Validaciones

### W3C (Nu HTML Checker)
✔ Documento validado, **sin errores ni advertencias**.

### Lighthouse (Desktop)
| Métrica           | Puntuación |
|-------------------|------------|
| **Performance**   | **89**     |
| **Accessibility** | **96**     |
| **Best Practices**| **100**    |
| **SEO**           | **100**    |

Hallazgo: enlaces pequeños en el menú → mejorados con padding (`min-width:44px`, `min-height:44px`).

---

## 4) Accesibilidad

- **tabindex:** en skip link (`0`), imágenes (`0` o `-1`) para control del orden de tabulación.  
- **aria-label/aria-labelledby/aria-describedby:** en `nav`, `section`, `article`, `video`, `table`, `input#correo`.  
- **alt:** en todas las imágenes con descripciones significativas.  
- **Enlaces descriptivos:** texto claro como “Ver Cahuita en Google Maps”.  
- **Subtítulos en video:** `<track kind="captions" srclang="es" ...>`.

---

## 5) CSS aplicado

### Archivos
- `styles/base.css` → reset, variables, tipografía, `box-sizing:border-box`.  
- `styles/layout.css` → estructura, flexbox y grid, combinadores.  
- `styles/components.css` → `.btn`, `.card`, `.badge`, `.listado`.  
- `styles/overrides.css` → casos con `!important` y sobrescrituras.  

### Selectores
- **Tipo:** `header`, `nav`, `section`, `img`, `p`, `h1`, `h2`.  
- **Clase:** `.btn`, `.card`, `.badge`, `.listado`.  
- **ID:** `#destinos`, `#consejos`, `#itinerario`, `#presupuestos`, `#registro`.  
- **Atributo:**  
  - `a[target="_blank"]`  
  - `img[alt]`  
  - `input[type="email"]`  
  - `a[href^="https://"]`  
  - `a[href$=".pdf"]`

### Combinadores
- `.card p` (descendiente).  
- `header > nav` (hijo directo).  
- `nav a + a` (adyacente).  
- `.tag ~ .tag` (hermanos).  

### Pseudo-clases
- Estado: `:hover`, `:focus-visible`, `:active`.  
- Estructurales: `:first-child`, `:last-child`, `:nth-child(2n)`, `:not()`.  

### Especificidad
- Uso de `!important` en `.badge` dentro de `.card` (overrides.css).  
- Estilo en línea en `<h2 style="margin-bottom:24px;">`.

---

## 6) Box Model y Positioning

- `box-sizing: border-box` global.  
- Márgenes y paddings controlados en títulos y tarjetas (`h2` + `.card`).  
- Ejemplo de colapso de márgenes: `h2` seguido de `.card`.  
- `overflow-x: auto` aplicado a tablas para scroll en pantallas pequeñas.  
- **Flexbox:** en `nav ul` (`display:flex`, `gap`, `align-items:center`).  
- **Grid:** en contenedor de tarjetas de destinos (`.cards-container` con `grid-template-columns: repeat(auto-fill, minmax(250px, 1fr))`).  
- **Positioning:**  
  - `relative` en `.card`.  
  - `absolute` en `.badge` (posicionado sobre la tarjeta).

---

## 7) Otras cosas

- Diseño modular en carpetas: `base`, `layout`, `components`, `overrides`.  
- Deploy en Netlify.  
- README documenta dónde se aplicó cada requisito.

---

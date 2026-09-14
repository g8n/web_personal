# Portafolio personal — Gonzalo Gascón

Sitio web personal estático que funciona como carta de presentación profesional:
quién soy, mi recorrido laboral, los servicios que ofrezco, proyectos y formas de
contacto.

Está construido con **HTML5, SCSS, Bootstrap 5 y Animate.css**. 
Los estilos se escriben en SCSS y se compilan a un único
`css/style.css`; el HTML se abre directamente en el navegador.

🔗 **Sitio publicado en Vercel:** <https://web-personal-henna-ten.vercel.app/>

## Contenido del sitio

| Página | Archivo | Qué muestra |
|---|---|---|
| Índice | `index.html` | Presentación, biografía y habilidades |
| Servicios | `pages/servicios.html` | Servicios ofrecidos, planteados como preguntas del negocio |
| Sobre mí | `pages/sobreMi.html` | Experiencia laboral en un carrusel de Bootstrap |
| Proyectos | `pages/proyectos.html` | Proyectos realizados *(en construcción)* |
| Contacto | `pages/contacto.html` | Email, ubicación y WhatsApp |

Todas las páginas comparten el mismo header con navegación y el mismo footer con
redes sociales y datos de contacto.

## Estructura del proyecto

```
.
├── index.html              # Página principal
├── scss/                   # Código fuente de los estilos
│   ├── main.scss           # Único punto de entrada (@use)
│   ├── utilities/          # No generan CSS: alimentan al resto
│   │   ├── _variables.scss # Colores, degradados, tipografía, espaciado,
│   │   │                   # breakpoints, duraciones y sombras
│   │   ├── _mixins.scss    # Media queries, tarjetas, títulos, degradados,
│   │   │                   # elevación y animación
│   │   └── _placeholders.scss # Bloques compartidos con @extend
│   ├── base/
│   │   ├── _base.scss      # Reset y etiquetas globales
│   │   ├── _tipografia.scss# Jerarquía de títulos y énfasis
│   │   └── _animaciones.scss # @keyframes propios + movimiento reducido
│   ├── layout/
│   │   ├── _header.scss
│   │   ├── _nav.scss       # Navbar de Bootstrap personalizado
│   │   ├── _grillas.scss   # Contenedores en columnas
│   │   └── _footer.scss
│   └── components/
│       ├── _cards.scss     # Servicio, dato, experiencia, cómo trabajo
│       ├── _buttons.scss
│       ├── _presentacion.scss
│       ├── _proyectos.scss
│       └── _carrusel.scss
├── css/
│   └── style.css           # Generado por Sass — no editar a mano
├── img/                    # Foto personal y logos de las empresas
├── pages/                  # Páginas internas
│   ├── servicios.html
│   ├── sobreMi.html
│   ├── proyectos.html
│   └── contacto.html
└── README.md
```

## Estilos: cómo trabajar con el SCSS

`css/style.css` es **código generado**: cualquier cambio de diseño se hace en
`scss/` y se recompila. Editarlo a mano se pierde en la siguiente compilación.

Para compilar alcanza con cualquiera de estas dos opciones:

**a) Extensión de VS Code** — *Live Sass Compiler*: se configura para que tome
`scss/main.scss` y escriba en `css/style.css`, y recompila sola al guardar.

**b) Sass por terminal** — se instala una sola vez en la computadora
(`npm install -g sass`) y después, parado en la carpeta del proyecto:

```bash
sass scss/main.scss css/style.css              # compila una vez
sass --watch scss/main.scss css/style.css      # recompila al guardar
```

### Mixin o extend

La regla para elegir entre las dos herramientas:

| Herramienta | Cuándo | Qué genera |
|---|---|---|
| `@mixin` | cada uso necesita **valores distintos** | repite el bloque en cada llamada |
| `@extend` | el bloque es **idéntico** en todos lados | lo emite una vez y agrupa los selectores |

### Animaciones

El trabajo está repartido en dos:

- **Animate.css** (CDN) hace la **entrada** de la página:
  `header`, la primera sección y el `footer` llevan clases `animate__` en el
  HTML.
- **`base/_animaciones.scss`** hace todo lo demás

Tres reglas para mantener la arquitectura sana:

1. **Ningún valor a mano.** Colores, tamaños, espaciados y breakpoints salen de
   `utilities/_variables.scss`. Si hace falta uno nuevo, se agrega ahí.
2. **Lo que se repite es un mixin.** Las tarjetas, los títulos, los separadores
   lima y las media queries viven en `utilities/_mixins.scss`.
3. **El orden de `main.scss` importa.** Es el orden en que salen las reglas al
   CSS final y por lo tanto el que resuelve los empates de especificidad
   (`components/buttons` va después de `components/cards` por ese motivo).

Mobile-first: cada partial escribe primero el estilo de celular y anida sus
variantes con los mixins `tablet` (≥768px) y `desktop` (≥1024px), de modo que
el estilo de un componente y sus overrides queden juntos.

## Publicación (GitHub Pages)

El sitio está publicado con **GitHub Pages** en:

<https://web-personal-henna-ten.vercel.app/>

Cada `git push` a `main` republica el sitio automáticamente.

---

© 2026 Gonzalo Gascón. Todos los derechos reservados.

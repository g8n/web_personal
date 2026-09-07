# Portafolio personal — Gonzalo Gascón

Sitio web personal estático que funciona como carta de presentación profesional:
quién soy, mi recorrido laboral, los servicios que ofrezco, proyectos y formas de
contacto.

Está construido con **HTML5, CSS3 y Bootstrap 5**, sin frameworks de JavaScript ni
proceso de build: se abre directamente en el navegador.

🔗 **Sitio publicado:** <https://g8n.github.io/web_personal/>

## Contenido del sitio

| Página | Archivo | Qué muestra |
|---|---|---|
| Índice | `index.html` | Presentación, biografía y habilidades |
| Servicios | `pages/servicios.html` | Servicios ofrecidos *(en construcción)* |
| Sobre mí | `pages/sobreMi.html` | Experiencia laboral en un carrusel de Bootstrap |
| Proyectos | `pages/proyectos.html` | Proyectos realizados *(en construcción)* |
| Contacto | `pages/contacto.html` | Email, ubicación y WhatsApp |

Todas las páginas comparten el mismo header con navegación y el mismo footer con
redes sociales y datos de contacto.

## Estructura del proyecto

```
.
├── index.html          # Página principal
├── css/
│   └── style.css       # Única hoja de estilos (mobile-first)
├── img/                # Foto personal y logos de las empresas
├── pages/              # Páginas internas
│   ├── servicios.html
│   ├── sobreMi.html
│   ├── proyectos.html
│   └── contacto.html
└── README.md
```

## Publicación (GitHub Pages)

El sitio está publicado con **GitHub Pages** en:

<https://g8n.github.io/web_personal/>

Cada `git push` a `main` republica el sitio automáticamente.

---

© 2026 Gonzalo Gascón. Todos los derechos reservados.
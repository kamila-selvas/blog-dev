# Kam Dev Blog

Blog personal estático hecho con [Hugo](https://gohugo.io/), optimizado para SEO, con HTML5 semántico y hosteado gratis en GitHub Pages.

## 🚀 Cómo subirlo a GitHub Pages (paso a paso)

### 1. Crear el repositorio en GitHub
Crea un repo nuevo (por ejemplo `blog-dev`) en tu cuenta de GitHub. **No** lo inicialices con README, .gitignore ni licencia (ya vienen incluidos aquí).

> Si en vez de repo de proyecto quieres que sea tu sitio principal (`tuusuario.github.io`), el repo debe llamarse exactamente así, y luego debes cambiar `baseURL` en `hugo.toml` a `https://tuusuario.github.io/`.

### 2. Subir el proyecto
Desde esta carpeta:

```bash
git init
git add .
git commit -m "Primer commit: setup del blog con Hugo"
git branch -M main
git remote add origin https://github.com/TU-USUARIO/blog-dev.git
git push -u origin main
```

### 3. Activar GitHub Pages con GitHub Actions
En tu repo: **Settings → Pages → Build and deployment → Source** → selecciona **"GitHub Actions"**.

Eso es todo. El workflow en `.github/workflows/hugo.yml` ya está configurado para:
- Compilar el sitio con Hugo cada vez que hagas `git push` a `main`.
- Minificar HTML/CSS.
- Publicarlo automáticamente en GitHub Pages.

Después del primer push, en unos 1-2 minutos tu sitio estará en:
`https://TU-USUARIO.github.io/blog-dev/`

### 4. Ajustar la configuración con tus datos reales
Edita `hugo.toml`:

```toml
baseURL = "https://TU-USUARIO.github.io/blog-dev/"
title = "Kam Dev Blog"

[params]
  author = "Tu nombre"
  github = "https://github.com/TU-USUARIO"
```

## 📝 Cómo escribir un post nuevo

```bash
hugo new content posts/mi-nuevo-post.md
```

Esto crea el archivo a partir del archetype en `archetypes/posts.md`, con `draft: true`. Escribe tu contenido y cuando esté listo, cambia `draft: false` para que se publique.

Estructura de cada post (front matter):

```yaml
---
title: "Título del post"
date: 2026-09-20T10:00:00-06:00
draft: false
description: "Resumen de 1-2 líneas para SEO y redes sociales"
categories: ["Nombre de la materia"]
tags: ["tag1", "tag2"]
toc: true       # muestra tabla de contenidos
---
```

## 💻 Ver el sitio en local antes de publicar

```bash
hugo server -D
```

Ábrelo en `http://localhost:1313/`. Con `-D` también ves los borradores (`draft: true`).

## 🔍 Qué SEO trae ya configurado

- **Meta description** por página (usa `description` del front matter o el resumen automático del post).
- **Canonical URL** en cada página (evita contenido duplicado).
- **Open Graph** y **Twitter Cards** (vistas previas bonitas al compartir en redes/WhatsApp).
- **JSON-LD** (`schema.org/BlogPosting`) para resultados enriquecidos en Google.
- **sitemap.xml** y **robots.txt** generados automáticamente.
- **RSS feed** automático.
- HTML5 semántico: `header`, `nav`, `main`, `article`, `section`, `aside`, `footer`, `figure`/`figcaption`.
- URLs limpias tipo `/posts/nombre-del-post/`.

### Después de publicar, opcional pero recomendado:
1. Da de alta tu sitio en [Google Search Console](https://search.google.com/search-console) y pega el código de verificación en `googleSiteVerification` dentro de `hugo.toml`.
2. Envía tu `sitemap.xml` (`https://tu-sitio/sitemap.xml`) en Search Console para que Google indexe más rápido.

## 📁 Estructura del proyecto

```
kam-dev-blog/
├── hugo.toml                 # configuración del sitio
├── content/
│   ├── posts/                # tus posts van aquí
│   └── about.md               # página "Acerca de"
├── layouts/                  # theme propio (sin dependencias externas)
├── assets/css/style.css      # estilos (modo claro/oscuro automático)
├── static/images/favicon.svg
└── .github/workflows/hugo.yml # despliegue automático a GitHub Pages
```

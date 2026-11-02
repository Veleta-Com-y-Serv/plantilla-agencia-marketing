# Plantilla NoExpertise · Agencia y consultoría

Web directa y a todo color para agencias de marketing, consultoras y estudios de diseño web: bandas a todo el
ancho que alternan morado profundo, crema y lima, portada casi a pantalla completa con tarjetas flotantes,
cifras, cita enorme y blog.

- Sectores: agencia, marketing, consultoria, diseno-web, publicidad. Estilo: directo. Plan mínimo: presencia.
- Secciones: hero, cifras, servicios, sectores, sobre, proceso, cita, noticias, opiniones, preguntas, cta, contacto (y `texto` para apartados nuevos).
- Ejemplo: Lúcida Estudio, agencia ficticia de Valencia.
- SEO de base incluido (`src/lib/seo.ts`): canónica, og:image, JSON-LD del negocio y de las preguntas frecuentes, `robots.txt`, `sitemap.xml` y `llms.txt`; `noindex` si `seo.indexable: false`.
- Contenido editable en `site.yaml`; metadatos y guion del asistente en `template.yaml`; fotos a generar en `fotos.json`; reglas para el agente en `CLAUDE.md`; concepto visual en `DISEÑO.md`.

## Campos propios (además del esquema común)

| Sección | Campos |
|---|---|
| todas | `resalte`: palabras del título que salen en cursiva con serifa |
| `hero` | `items` (titulo, texto, icono, url): hasta tres tarjetas flotantes |
| `cifras` | `items` (titulo = cifra como texto, texto = etiqueta) |
| `servicios` | `items` (titulo, texto, icono, url, destacado) |
| `sectores` | `items` (titulo) como etiquetas; `galeria` (franja de fotos) |
| `sobre` | `items` (titulo, texto, icono), `personas` (nombre, cargo, foto), `cta` |
| `proceso` | `items` (titulo, texto, icono, duracion) |
| `cita` | `declaracion`, `autor` |
| `noticias` | `noticias` (titulo, texto, fecha, categoria, imagen, url), `cta` |
| `opiniones` | `testimonios` (texto, autor, cargo, nota) |
| `cta` | `cta`, `cta_secundario`, `nota`, `imagen` |
| `contacto` | `boton` (texto del botón del formulario) |

```
npm ci
npm run dev      # desarrollo
npm run build    # web estática en dist/
```

Basada en [AstroWind](https://github.com/onwidget/astrowind) © onWidget, licencia MIT (`LICENSE-ASTROWIND.md`). Imágenes de relleno (`public/placeholders/`) hechas para esta plantilla, sin licencias de terceros.

## Páginas propias
- Cada elemento de `secciones.servicios.items` con `detalle` tiene su página en `/servicios/<slug>/` (`src/pages/[coleccion]/[slug].astro`).
- Campos opcionales de los elementos con ficha: `detalle` (párrafos separados por una línea en blanco), `slug` e `imagenes` («/fotos/a.jpg; /fotos/b.jpg»).

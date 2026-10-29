# Plantilla «Agencia y consultoría» (NoExpertise)

Web estática Astro 5 + Tailwind 4, derivada de AstroWind (MIT, ver `LICENSE-ASTROWIND.md`). Estilo: **directo**.
Todo en castellano de España, frases cortas, sin jerga. Diseño y concepto en `DISEÑO.md`.

## Dónde está cada cosa
- **Textos, contacto, menú, SEO y secciones**: `site.yaml` (raíz). Es la única fuente de contenido. `src/data/site.ts` lo carga y lo tipa; no pongas textos fijos en los componentes.
- **Colores**: `site.yaml → colores` (primario, acento, fondo, texto). `src/layouts/Base.astro` los convierte en variables CSS (`--c-primario`…) y Tailwind los expone como `bg-primario`, `text-acento`… En `src/styles/global.css` salen los derivados: `--c-oscuro` (pie y bandas profundas), `--c-medio` (banda de cifras), `--c-claro` (banda crema) y `--c-chispa` (el rosa de los botones, que se calcula girando el tono del primario: no hay un quinto color).
- **Tipografías y aspecto general**: `src/styles/global.css` (bandas `.banda--oscura|profunda|media|clara|crema|lima|chispa`, antetítulos, botones `.btn`/`.btn-sec`/`.btn-lima`/`.btn-blanco`, cabecera y pie). Fuentes del sistema: no añadas fuentes externas.
- **Resalte**: `secciones.<id>.resalte` son unas palabras del título (tal cual) que salen en cursiva con serifa (lima sobre oscuro, subrayado lima sobre claro). Lo pinta `src/components/ui/Resalte.astro`; si las palabras no están en el título, no pasa nada.
- **Imágenes**: en `public/`. Las fotos de partida van en `public/fotos/` (se generan a partir de `fotos.json`); las de relleno, en `public/placeholders/`. En `site.yaml` se referencian con ruta absoluta (`/fotos/hero.jpg`). Las personas usan `/placeholders/persona.svg` hasta que el cliente suba la suya.
- **Logo**: `site.yaml → logo` (ruta en `public/`); vacío = inicial en un cuadro lima + nombre.
- **Pie «Web creada con NoExpertise»**: `site.yaml → marca_pie` (true en plan gratis).

## Secciones
Cada sección es un componente que solo se pinta si `site.yaml → secciones.<id>.activa` es `true`, en el orden de `site.yaml`. Todas son bandas a todo el ancho de la ventana.
- `hero` → `hero.astro`: banda morada con la foto teñida; título enorme; `items` = hasta tres tarjetas flotantes (titulo, texto, icono, url).
- `cifras` → `cifras.astro`: banda morada encendida; `items` (titulo = cifra como texto, texto = etiqueta). Sin cifras no se pinta.
- `servicios` → `servicios.astro`: rejilla de celdas con filetes; `items` (titulo, texto, icono, url, destacado).
- `sectores` → `sectores.astro`: etiquetas (`items` con titulo), cinta de palabras en contorno y franja de fotos (`galeria`).
- `sobre` → `sobre.astro`: 50/50 con la foto a sangre a la izquierda; `items` (compromisos), `personas` (nombre, cargo, foto), `cta`.
- `proceso` → `proceso.astro`: pasos (`items`: titulo, texto, icono, duracion).
- `cita` → `cita.astro`: banda lima con la frase (`declaracion`) y la firma (`autor`).
- `noticias` → `noticias.astro`: blog; `noticias` (titulo, texto, fecha, categoria, imagen, url), `cta` «ver todos».
- `opiniones` → `opiniones.astro`: `testimonios` (texto, autor, cargo, nota «1»-«5»).
- `preguntas` → `preguntas.astro`: acordeón `details/summary`; sin preguntas no se pinta.
- `cta` → `cta.astro`: banda rosa con título gigante, dos botones, `nota` e `imagen` de fondo opcional.
- `contacto` → `contacto.astro`: mitad morada con los datos de `contacto` y mitad crema con el formulario (`boton` = texto del botón).
- `texto` → `texto.astro`: diseño genérico para apartados nuevos (`tipo: texto`).

## Reglas para órdenes
1. **Activar o quitar una sección**: cambia `activa: true|false` en `site.yaml`. No borres componentes.
2. **Reordenar secciones**: mueve el bloque dentro de `secciones:` en `site.yaml`.
3. **Cambiar textos, teléfonos, horarios, fotos**: solo en `site.yaml`. Si un texto contiene comas o «: » dentro de `{ … }`, ponlo entre comillas. Listas planas (nada de listas dentro de un elemento), 24 elementos como mucho, precios y cifras como cadena.
4. **Página nueva**: crea `src/pages/<slug>.astro` con `import Base from '../layouts/Base.astro'` y `<Base titulo="…" descripcion="…">…</Base>`, con bandas (`<section class="banda banda--clara">`); enlázala en `site.yaml → menu`. Ejemplo: `src/pages/aviso-legal.astro`.
5. **Sección nueva**: crea `src/components/secciones/<id>.astro` (copia la estructura de una existente: `seccion(id)`, `Seccion` con `banda=`, `Titular`) y añade `secciones.<id>` en `site.yaml`. `src/pages/index.astro` la recoge sola; no lo toques.
6. **No tocar** `src/layouts/Base.astro`, `tailwind.config.mjs` ni `src/styles/comun.css` salvo orden explícita de diseño. Tampoco `src/lib/seo.ts` ni `src/pages/robots.txt.ts`, `sitemap.xml.ts` y `llms.txt.ts`: son el SEO de base (canónica, og:image, `noindex` si `seo.indexable: false`, JSON-LD del negocio y de las preguntas, robots, sitemap y llms.txt), salen solos de `site.yaml` y el fichero es el mismo en todas las plantillas. `seo.url` y `seo.indexable` los pone la plataforma: no los cambies.
7. Mantén: `lang="es-ES"`, imágenes con `Imagen.astro` (carga diferida), sin JavaScript nuevo salvo necesidad real, 16 px de margen lateral (`.contenedor`), bandas a todo el ancho, sin scroll horizontal en móvil. Imágenes de contenido con `alt` sacado del contenido (`altHero`, `altFicha`, `altGaleria`, `altSeccion` de `src/lib/seo.ts`); las decorativas, `alt=""`.
8. El formulario no tiene servidor: abre el correo (`mailto`) con el email de `site.yaml`. Para envío real, cambia `action` en `src/components/ui/FormularioContacto.astro`.

## Construir
```
npm ci && npm run build      # resultado en dist/
npx astro preview            # ver dist/ en http://localhost:4321
```
Antes de dar una orden por buena: `npm run build` sin errores.

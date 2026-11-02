# Agencia y consultoría: brief de diseño

Plantilla `agencia-marketing` creada el 29/10/2026 a partir de `corporativa-clasica` con `php artisan plantillas:nueva`
y rediseñada entera. Este fichero se queda en el repo: es lo que lee quien (persona o agente) rediseñe la plantilla.

## Brief

- **Para quién**: agencias de marketing, consultoras, estudios de diseño web y de publicidad (`sectores`: agencia,
  marketing, consultoria, diseno-web, publicidad). Su cliente es una pyme que quiere más clientes y entra a ver si
  la agencia «sabe lo que hace»: qué ofrece, con quién ha trabajado, cómo trabaja y cuánto se tarda en empezar.
- **Qué tiene que conseguir la web**: que reserven la sesión o el diagnóstico gratuito (botón rosa en cabecera,
  portada, servicios, llamada a la acción y formulario).
- **Tono y estilo** (`estilo: directo`): seguro, enérgico y claro. Referencia que sí: losmartesnohayluna.com
  (bandas a sangre, morado + lima, cifras y cita gigantes). Que no: la caja centrada estrecha con tarjetas blancas
  de las plantillas antiguas; la sobriedad de `corporativa-clasica`.
- **Paleta de ejemplo**: primario `#2a1150` (morado profundo), acento `#c4f04a` (lima), fondo `#f7f2e8` (crema),
  texto `#1c1229`. Derivados en `global.css` con `color-mix`: `--c-oscuro` (primario + negro; pie y sectores),
  `--c-medio` (primario + chispa; banda de cifras), `--c-claro` (crema tintada; blog). El rosa del botón
  (`--c-chispa`) sale del primario girando el tono 55° en oklch (`oklch(from …)`; sin soporte, una mezcla con
  rosa): si el cliente pone un primario azul, el botón pasa a violeta, y así siempre combina. El lima nunca va
  como texto sobre crema (no se lee): allí es subrayado, punto o fondo de icono.
- **Tipografía**: del sistema. Títulos en palo seco muy pesado (800-900, interletrado −0,035 em; pila «Avenir
  Next», «Segoe UI Variable Display», system-ui); palabras resaltadas (`resalte`) en cursiva con serifa (Iowan,
  Palatino, Georgia). Antetítulos en mayúsculas espaciadas (0,2 em) con una raya lima delante. Botones en
  mayúsculas espaciadas, esquinas de 0,5 rem, 48 px de alto.
- **Ritmo de bandas** (todas de borde a borde; contenido a 90 rem como mucho, 16 px de margen en móvil):
  1. `hero` — morado, casi pantalla completa (88 svh), foto teñida de fondo, anillos; 60/40: título de 6,6 rem
     (2,6 en móvil) y dos botones a la izquierda, tres tarjetas de servicio flotando (cristal) a la derecha.
  2. `cifras` — morado encendido en degradado, cuatro cifras lima enormes separadas por filetes.
  3. `servicios` — crema; cabecera partida; rejilla 3×2 a todo el ancho con filetes (la `destacado` en morado;
     al pasar el ratón, todas).
  4. `sectores` — morado profundo; etiquetas píldora con borde lima; cinta de palabras gigantes en contorno que
     se mueve (se para con «reducir movimiento»); franja de 4 fotos sin márgenes.
  5. `sobre` — 50/50 a sangre: foto hasta el borde izquierdo con un cuadro lima en la esquina; texto, compromisos
     en 2 columnas, el equipo en pequeño y un enlace.
  6. `proceso` — morado; cuatro pasos con línea lima, números en contorno, plazo en píldora.
  7. `cita` — lima; frase enorme centrada con comillas gigantes de adorno.
  8. `noticias` — crema tintada; tres artículos con foto y categoría en etiqueta lima.
  9. `opiniones` — morado; tres opiniones en cristal con estrellas lima e iniciales en círculo rosa.
  10. `preguntas` — crema; titular fijo a la izquierda, acordeón grande a la derecha.
  11. `cta` — rosa → morado; título gigante centrado, botón blanco y contorno.
  12. `contacto` — partido a sangre: mitad morada (teléfono enorme en lima y datos) y mitad crema (formulario).
  Pie morado muy profundo: nombre enorme + botón, cuatro columnas y línea legal.
- **Cabecera**: siempre sólida en morado, `sticky`, a todo el ancho; marca con inicial en cuadro lima; menú en
  mayúsculas espaciadas; botón rosa; sombra al bajar (6 líneas de JavaScript). En móvil, `details/summary`.
- **Fotos** (`fotos.json`, 10): estudio creativo sin gente (portada), mesa de trabajo con notas sin texto (sobre),
  cuatro negocios tipo de Valencia sin gente ni rótulos (sectores), tres bodegones de trabajo (blog) y una sala de
  reuniones (llamada a la acción). Sin texto legible, sin logotipos, sin personas reconocibles.
- **Qué no hacer**: volver a la columna estrecha o a las tarjetas blancas sobre fondo gris; poner el lima como
  texto sobre claro; meter precios o cifras fijas en los componentes (todo sale de `site.yaml`).

## Páginas propias (fichas)
Con la misma piel que la portada: cabecera y pie de la plantilla, migas (Inicio › Sección › Elemento), hero con la foto del
elemento (sin foto, su icono), `detalle` en párrafos, tabla de datos, caja de contacto, galería (`imagenes`) y otros elementos
de la misma lista.

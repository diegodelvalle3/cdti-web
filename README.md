# CDTI Cuernavaca — sitio web

Sitio para el **Centro de Evaluación, Diagnóstico y Terapia Integral (CDTI)**,
ubicado en C. Las Ánimas 16, Acapantzingo, 62440 Cuernavaca, Mor. Construido
con [Astro](https://astro.build) para desplegarse en Netlify.

## Cómo correrlo en tu computadora

Necesitas tener [Node.js](https://nodejs.org) instalado (versión 18 o superior).

```bash
npm install
npm run dev
```

Abre `http://localhost:4321` en tu navegador. Los cambios se ven al guardar.

## Cómo desplegarlo en Netlify (gratis, sin dominio propio)

1. Sube esta carpeta a un repositorio de GitHub (o arrastra la carpeta
   directamente a [app.netlify.com/drop](https://app.netlify.com/drop) para
   una prueba rápida sin Git).
2. En Netlify: **Add new site → Import an existing project**, conecta el
   repo. Netlify detecta automáticamente:
   - Build command: `npm run build`
   - Publish directory: `dist`
3. Netlify te da una URL gratuita tipo `algo-aleatorio.netlify.app`. Puedes
   cambiarla en **Site settings → Change site name**.
4. Cuando compren el dominio, lo agregan en **Domain settings → Add a custom
   domain**, sin tocar el código.

El formulario de contacto ya está conectado a **Netlify Forms** (no necesita
backend ni costo extra): los mensajes llegarán al panel de Netlify del sitio,
en la pestaña "Forms".

## Contenido pendiente de completar

El sitio tiene contenido real basado en información pública del centro, pero
hay espacios marcados para que CDTI los complete con sus propios materiales:

- [ ] Fotografías reales de la fachada, el jardín y las salas (sección
      "Instalaciones" y el marco junto a "Quiénes somos")
- [ ] Nombres y fotografías del equipo (sección "Equipo")
- [ ] Número de teléfono / WhatsApp y horario de atención (sección "Contacto")
- [ ] Confirmar redes sociales si quieren enlazarlas en el pie de página

Busca el texto *"Agrega aquí..."* o *"Foto del equipo..."* en el código para
ubicar exactamente dónde reemplazar cada placeholder.

## Estructura del proyecto

```
src/
  components/        → piezas reutilizables (Header, Footer, PageHero, CtaBand,
                        y el contenido de cada sección: Nosotros, Equipo, etc.)
  layouts/
    Layout.astro      → metadatos y carga de fuentes
  pages/
    index.astro        → inicio (resumen + enlaces a cada página)
    nosotros.astro      → /nosotros/
    equipo.astro         → /equipo/
    instalaciones.astro  → /instalaciones/
    contacto.astro       → /contacto/
    servicios/
      index.astro                    → /servicios/
      evaluacion-y-diagnostico.astro → /servicios/evaluacion-y-diagnostico/
      terapia-de-lenguaje.astro      → /servicios/terapia-de-lenguaje/
      terapia-psicologica.astro      → /servicios/terapia-psicologica/
    404.astro
  styles/
    global.css   → paleta de colores, tipografía y estilos base
```

Es un sitio multi-página: cada sección vive en su propia URL, con su propio
encabezado de color (`PageHero`) y banner de llamado a la acción (`CtaBand`)
al final, siguiendo el estilo de referencia que compartiste.

## Sistema de diseño

- **Tipografía:** Baloo 2 (encabezados, redondeada y amigable) + Work Sans
  (texto, limpia y profesional), vía Google Fonts.
- **Fondo:** blanco/crema muy claro como base en casi todas las secciones de
  contenido (`--paper`, `--white`), con bandas de color cálido —teal, terracota
  y amarillo— en los encabezados de página y los banners de llamado a la
  acción, inspirado en los ejemplos que compartiste (FUNTYX, Moma Apps, Study
  Pilot).
- **Motivo "press":** esquinas asimétricas, como si fueran moldeadas con los
  dedos en plastilina, repetidas en tarjetas, marcos de fotos y botones.

Todos los colores y tipografías están centralizados en `src/styles/global.css`
como variables CSS (`--teal`, `--clay`, `--font-display`, etc.), así que puedes
ajustar la paleta completa desde un solo lugar.

# AGENTS.md — Convenciones para IA en este repositorio

Instrucciones para sesiones de IA (o personas) que generen o modifiquen contenido de **entiendo-ai**, el repositorio de estudio del curso **Programación Concurrente y Distribuida (PCCD)**. Si vas a crear o editar páginas aquí, sigue estas convenciones al pie de la letra — están consolidadas después de construir todas las semanas del proyecto.

## Contexto del repositorio

- Es un repositorio de **estudio personal**: cada `classes/week_N/` contiene el material semanal (PDFs en `files/`) y páginas HTML interactivas generadas a partir de ese material.
- Todo es **HTML estático autocontenido** (CSS y JS inline): sin frameworks, sin build, sin dependencias de proyecto.
- El contenido de las páginas está en **español** (algunos PDFs de redes están en inglés; el contenido generado siempre se explica en español).
- La fuente de verdad del contenido son **los PDFs de `files/`**: extraerlos con `pdftotext` antes de escribir contenido.

## Reglas obligatorias de estilo

1. **Leer `styles.md` antes de escribir una sola línea de CSS** — es la guía de diseño del proyecto (paleta dark púrpura/azul, glows, radios, tipografía).
2. **Prohibido usar emojis**, ni en contenido ni en demos. Para iconos usar **Font Awesome** (`fa-solid fa-...`) cargado desde cdnjs. Verificar con regex que no quede ningún emoji antes de terminar.
3. Tipografía: **Geist Sans** (UI) y **Geist Mono** (números, código) desde Google Fonts.
4. Tono: minimalista, alto contraste, jerarquía tipográfica; el color se reserva para acciones y estados.
5. Interactividad **solo donde enseñar haciéndolo aporte valor** (1-2 demos interactivas por deck máximo); el resto son animaciones automáticas o contenido estático.

## Estructura de una semana

Cada `classes/week_N/` tiene exactamente:

| Archivo | Qué es |
|---|---|
| `introduction.html` | **Una sola página** (no deck): qué se aprenderá, 1 imagen/diagrama visual clave, agenda de temas, CTA al `index.html`, enlace de regreso a `../course_introduction/index.html` |
| `index.html` | **Deck estilo PPT** con TODO el contenido de los PDFs de la semana |
| `test.html` | **Test de repaso** con el motor estándar (ver abajo) |
| `files/wN_X.pdf` | PDFs del profesor, sin modificar (copiar, nunca mover) |

## Motor de deck (presentaciones)

Reutilizar el motor ya probado (copiarlo de `classes/week_5/index.html`, el más reciente):

- Slides como `<section class="slide" data-title="...">` en `#deck`; la activa lleva clase `.active`.
- **Primera slide = portada con agenda de temas** (siempre).
- Navegación: flechas ←/→, espacio, PageUp/PageDown, Home/End; **guard**: si el foco está en un `<button>`, la barra espaciadora no navega.
- Barra de progreso superior (gradiente de marca), contador arriba a la derecha, dots abajo (el HTML tiene el contador fijo "1 / N" — **N debe coincidir con el número real de slides**; `go(0)` lo actualiza al cargar).
- Efectos por slide en el mapa `slideFx` (índice de slide → función de entrada).
- **Todos los intervalos/timeouts se registran con `addT()`/`addTimeout()`** (array global `timers`, limpiado en `clearTimers()` al cambiar de slide). Nunca usar `setInterval`/`setTimeout` "pelados" para lógica de demos — provoca fugas que siguen corriendo en slides ocultas.
- Animaciones de entrada con las clases `.anim .d1…d6` (fade + stagger).
- Media query a ≤640px (menos padding, tipografías reducidas).

## Motor de test

Reutilizar el motor de `classes/week_5/test.html`:

- Banco de preguntas `BANK` con objetos `{ w, q, o, a, e }`: **w** = tema (aparece como tag y en el desglose), **q** = pregunta, **o** = opciones (exactamente 4), **a** = índice de la correcta, **e** = explicación (fiel al material).
- Barajar con **Fisher-Yates** (`shuffle`): el orden de preguntas **y** de opciones se randomiza en cada intento (`optsMap` guarda dónde quedó la correcta).
- Una pregunta por pantalla; "Anterior"/"Siguiente"; el botón "Finalizar" solo aparece en la última.
- La nota, el desglose por tema y la revisión se calculan recorriendo **`order` (el orden barajado)**, nunca el banco original — así **nota == respuestas correctas de la revisión, siempre**.
- Escala: ≥85 % Excelente, ≥60 % Bien pero repasa, <60 % Repasar.
- Al final: revisión completa por pregunta (tu respuesta, la correcta, explicación), botón de reintento y enlace de regreso al `index.html` de la semana.

## Fidelidad al material

- **No inventar contenido, cifras ni URLs**: todo sale de los PDFs (`pdftotext` primero).
- Cuando el material simplifique o esté desactualizado, **mantener lo que dice pero añadir una nota** que aclare el detalle. Precedentes ya documentados en el README (sección "Simplificaciones del material documentadas"): estados de hilo conceptuales vs `Thread.State`, prioridades no garantizadas, daemon ≠ baja prioridad, SMT no duplica núcleos, costos de paralelización, TCP mientras la conexión esté activa, RTT ilustrativos.
- Los errores tipográficos evidentes de los PDFs se corrigen sin anuncio (ej. `new Socket(8181)` donde debía ser `new ServerSocket(8181)`).

## Verificación obligatoria antes de dar una página por terminada

```bash
# 1. sintaxis del JS inline
python3 -c "import re;open('/tmp/chk.js','w').write(re.findall(r'<script>(.*?)</script>',open('RUTA.html').read(),re.S)[0])" && node --check /tmp/chk.js

# 2. jsdom (npm install jsdom en una carpeta temporal)
```

Con jsdom, verificar: **0 errores de runtime**; navegar **todas** las slides por los dots (el contador final debe coincidir); ejecutar las **demos interactivas** (clic en sus botones, avanzar el tiempo con setTimeout y comprobar sus estados finales); en tests, responder todo simulando clics y confirmar **nota == correctas de la revisión**; **todos los enlaces** resuelven a archivos existentes; **regex de emojis** da 0.

## Al terminar una semana nueva

1. Crear los 3 archivos (`introduction.html`, `index.html`, `test.html`) + PDFs en `files/`.
2. Pasar la verificación completa de arriba.
3. **Actualizar `README.md`**: árbol del repositorio, sección "Contenido del curso", tabla de tests, checklist "Estado actual".
4. **Actualizar el índice raíz `index.html`**: tarjeta de la semana (título, descripción, 3 mini-botones, PDFs con páginas).
5. Si es la primera semana de alguien, ofrecer el test de diagnóstico como punto de comparación.

## Rutas (cuidado)

- El directorio del proyecto es `/home/dsalazarv/Desktop/code/entiendo-ai` — verificar `pwd` si un comando falla con `FileSystem.access`.
- Enlaces entre páginas SIEMPRE relativos: `index.html`, `../course_introduction/index.html`, `test.html`.

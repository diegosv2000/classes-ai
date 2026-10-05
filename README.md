# entiendo-ai

Repositorio personal de estudio para el curso **Programación Concurrente y Distribuida (PCCD)**. Aquí organizo el material semanal del curso (PDFs del profesor) junto con recursos interactivos de estudio que construyo con ayuda de IA: una presentación de conceptos previos, el contenido detallado de cada semana estilo presentación, y tests de repaso con corrección automática.

## Objetivo

- **Centralizar** el material semanal del curso y hacer que sea fácil de consultar.
- **Crear recursos de estudio interactivos** (HTML/CSS/JS puro, sin build ni dependencias de proyecto) que expliquen los conceptos previos necesarios antes de cada clase.
- **Estudiar con método de *active recall***: conceptos primero, ejemplos visuales después, test de repaso al final.
- **Fidelidad al material**: todo el contenido se deriva de los PDFs de `files/`; las simplificaciones del material se documentan en lugar de ocultarse (ver [Simplificaciones documentadas](#simplificaciones-del-material-documentadas)).

## Cómo empezar

1. Abre `index.html` (raíz) — es el menú que enlaza todo el proyecto.
2. Si es tu primer acercamiento: empieza por la **Introducción al curso** (`classes/course_introduction/index.html`).
3. Cada semana: lee el resumen (`introduction.html`), estudia la presentación completa (`index.html`) y cierra con su test (`test.html`).

```bash
xdg-open index.html
```

## Estructura del repositorio

```text
entiendo-ai/
├── README.md                     ← este archivo
├── AGENTS.md                     ← convenciones para sesiones de IA que generan contenido
├── index.html                    ← índice del proyecto: menú con enlaces a todo
├── styles.md                     ← guía de estilo visual (paleta y reglas de diseño)
└── classes/
    ├── course_introduction/
    │   ├── index.html            ← presentación interactiva de conceptos previos (11 slides)
    │   └── test.html             ← test de repaso de la introducción (20 preguntas)
    ├── week_1/
    │   ├── index.html            ← presentación de la semana (17 slides)
    │   ├── introduction.html     ← resumen de una página
    │   ├── test.html             ← test de repaso (16 preguntas)
    │   └── files/
    │       └── w1_1.pdf          ← material de la semana 1 (27 p)
    ├── week_2/
    │   ├── index.html            ← presentación de la semana (25 slides)
    │   ├── introduction.html     ← resumen de una página
    │   ├── test.html             ← test de repaso (20 preguntas)
    │   └── files/
    │       ├── w2_1.pdf          ← desafío de los sistemas distribuidos + programación concurrente (44 p)
    │       └── w2_2.pdf          ← desempeño y optimización para la latencia (30 p)
    ├── week_3/
    │   ├── index.html            ← presentación de la semana (23 slides)
    │   ├── introduction.html     ← resumen de una página
    │   ├── test.html             ← test de repaso (20 preguntas)
    │   └── files/
    │       ├── w3_1.pdf          ← desempeño y optimización para la latencia (24 p)
    │       ├── w3_2.pdf          ← communication and networks (36 p)
    │       └── w3_3.pdf          ← programación en red: Sockets I (22 p)
    ├── week_4/
    │   ├── index.html            ← (pendiente)
    │   ├── introduction.html     ← (pendiente: contiene TODO)
    │   └── files/                ← (vacía: no hay material de la semana 4)
    └── week_5/
        ├── index.html            ← presentación de la semana (27 slides)
        ├── introduction.html     ← resumen de una página
        ├── test.html             ← test de repaso (20 preguntas)
        └── files/
            ├── w5_1.pdf          ← sincronización de hilos (26 p)
            ├── w5_2.pdf          ← monitores, condiciones de carrera, deadlock, semáforos, etc. (19 p)
            └── w5_3.pdf          ← conceptos de threads en Java: volatile, executors, etc. (21 p)
```

### Convención de carpetas semanales

Cada `week_N/` sigue la misma plantilla:

- `index.html` — **presentación completa del material** de la semana, estilo PPT (weeks 1, 2, 3 y 5 listas).
- `introduction.html` — **resumen de una página** con el mapa mental de la semana: qué se aprende, una imagen visual clave y la agenda (weeks 1, 2, 3 y 5 listas).
- `test.html` — **test de repaso** de la semana con preguntas barajadas, nota y revisión (existe para weeks 1, 2, 3 y 5).
- `files/` — los PDFs entregados por el profesor, nombrados `wN_X.pdf` (semana N, material X).

No existe material para la **semana 4**: su carpeta mantiene la plantilla pero sin PDFs ni páginas, y el índice raíz la omite hasta que llegue.

## Contenido del curso (por semana)

Según el material en `files/`:

### Week 1 — Programación concurrente con hilos (`w1_1.pdf`)

Software concurrente; procesos e hilos (IPC: pipes, sockets); el `main thread`; creación de hilos (`Runnable` / extender `Thread`) y observaciones; `start()` vs `run()`; estados y prioridades; `currentThread()`, `sleep()`; interrupciones y la bandera Interrupt Status; `join()`; daemon threads.

**Su presentación (17 slides)** incluye una **demo interactiva de interrupción** (pulsas `interrupt()` y el worker termina limpiamente en su siguiente chequeo), animación automática de hilos compartiendo una CPU, y notas que distinguen el modelo conceptual de estados de los estados oficiales de `Thread.State` en Java.

### Week 2 — Sistemas distribuidos y concurrencia (`w2_1.pdf`, `w2_2.pdf`)

Desafío de los sistemas distribuidos: heterogeneidad (middleware: CORBA, Java RMI; código móvil), extensibilidad, seguridad (confidencialidad, integridad, disponibilidad), escalabilidad, tratamiento de fallos (detección, enmascaramiento, tolerancia, recuperación, redundancia), concurrencia en servidores, transparencia (8 tipos); programación concurrente: secuencial vs concurrente, paralelismo real y lógico, ventajas e inconvenientes, aplicaciones reales (Apache, videojuegos, Chrome) y patrones distribuidos (MapReduce, colas de mensajes, juegos, punto de venta); desempeño y latencia: cuellos de botella, throughput, límite N de hilos, costos de paralelización, SMT/Hyper-Threading.

**Su presentación (25 slides)** incluye animación automática de paralelismo real vs lógico y de la latencia T vs T/N (1 hilo vs 4 núcleos).

### Week 3 — Redes y sockets (`w3_3.pdf`, `w3_2.pdf`, `w3_1.pdf`)

Programación en red con sockets TCP: la conexión (socket original + nuevo socket del servidor), `InetAddress` (métodos de fábrica y de instancia), `ServerSocket` (excepciones, cola de 50, `accept()` bloquea), `Socket` y streams, cierre y los 5 pasos del cliente; wrappers de streams (Scanner, PrintWriter, InputStreamReader/BufferedReader, ObjectOutput/Input); redes: términos (payload, paquete, header/tail, encapsulación), dispositivos (switch, router, firewall), LAN/MAN/WAN, topologías, modelos OSI y TCP/IP capa por capa (FTP, Telnet, HTTP; TCP/UDP y puertos); encapsulación extremo a extremo y qué es un protocolo. El deck `w3_1.pdf` refuerza el desempeño de la semana 2 (se señala en la presentación).

**Su presentación (23 slides)** incluye una **demo interactiva de cliente eco** (escribes un mensaje, se ejecutan los 5 pasos y el servidor lo devuelve), animación automática de la conexión y de la encapsulación por capas.

### Week 5 — Sincronización de hilos (`w5_1.pdf`, `w5_2.pdf`, `w5_3.pdf`)

Interferencia de hilos y condición de carrera; consistencia de memoria y happens-before (`start`, `join`); métodos sincronizados y sus 2 efectos; bloqueo intrínseco; sentencias sincronizadas y reentrancia; acceso atómico; monitores, mutex y thread-safe; deadlock (y cómo evitarlo), livelock y starvation; Semaphore (analogía del estacionamiento); liveness; comunicación entre hilos: `wait()`, `notify()`, `notifyAll()`; `java.util.concurrent.locks`: Lock, tryLock, Condition (await/signal); `volatile` (visibilidad, no atomicidad); `AtomicInteger` (API completa); BlockingQueue/ArrayBlockingQueue; Callable/Future/FutureTask; ThreadPool, Executors y ScheduledExecutorService.

**Su presentación (27 slides)** incluye recorrido automático del entrelazado `c++`, animación del estacionamiento del semáforo y una **demo interactiva de productor-consumidor** con botones `notify()` / `notifyAll()` sobre 3 consumidores en `wait()`.

## classes/course_introduction/index.html

Presentación interactiva (estilo PPT, 11 slides) con los conceptos previos del curso. Navegable con flechas del teclado (←/→, espacio), botones y puntos inferiores.

1. **Portada** — agenda de temas.
2. **CPU y núcleos** — demo interactiva: comparar 1 vs 4 núcleos con cola de tareas.
3. **Proceso vs Hilo** — tabla comparativa (creación, memoria, comunicación, complejidad).
4. **Scheduler y estados de un hilo** — diagrama con ciclo automático; nota que distingue el modelo conceptual del material de los estados oficiales de `Thread.State` en Java.
5. **Concurrencia vs Paralelismo** — animación automática de ambos conceptos.
6. **Memoria compartida y race condition** — demo interactiva paso a paso: dos hilos ejecutando `contador++` / `contador--` con entrelazado que pierde la actualización.
7. **Repaso mínimo de Java** — las dos formas de crear hilos y puntos clave (`start()` vs `run()`).
8. **Redes: IP, puertos, TCP/UDP** — vocabulario base y encapsulación de paquetes.
9. **Cliente-servidor y handshake TCP** — animación automática del saludo de tres vías (SYN → SYN-ACK → ACK).
10. **Latencia y throughput** — definiciones, tabla de RTT ilustrativa y ejemplo de trading de alta velocidad.
11. **Mapa del curso** — qué cubre cada semana y botón para ir al test.

## Tests

Todos los tests del proyecto comparten el mismo motor y formato:

- **Banco de preguntas** `{ w, q, o, a, e }`: tema, pregunta, opciones, índice de la correcta y explicación — fiel a los PDFs.
- **Barajado aleatorio** (Fisher-Yates) del orden de preguntas **y** de opciones en cada intento.
- **Una pregunta por pantalla**: se marca la opción; se puede volver con "Anterior" y cambiar respuestas antes de finalizar.
- **Resultado**: nota sobre el total con porcentaje y escala (≥85 % Excelente, ≥60 % Bien pero repasa, <60 % Repasar), **desglose por tema** y **revisión completa** de cada pregunta (tu respuesta, la correcta y la explicación).
- **Reintento** que rebaraja todo.

| Test | Preguntas | Temas |
|---|---|---|
| `classes/course_introduction/test.html` | 20 | Hilos (6) · Concurrencia (4) · Java (4) · Redes (6) |
| `classes/week_1/test.html` | 16 | Concurrencia (2) · Hilos y procesos (2) · Crear hilos (3) · Estados y prioridades (3) · Métodos esenciales (3) · Interrupciones (2) · Daemon (1) |
| `classes/week_2/test.html` | 20 | Sistemas distribuidos (2) · Desafíos (4) · Fallos y transparencia (4) · Concurrencia (4) · Desempeño (3) · Paralelización (3) |
| `classes/week_3/test.html` | 20 | Sockets y conexión (4) · InetAddress (3) · ServerSocket/Socket (3) · Streams (3) · Redes (4) · Capas y protocolos (2) · Desempeño (1) |
| `classes/week_5/test.html` | 20 | Interferencia y carrera (3) · Sincronización básica (4) · volatile y átomos (3) · Liveness (4) · Semaphore y thread-safe (2) · wait/notify (2) · Locks (1) · Executors (1) |

## Arquitectura técnica de las páginas

Todo es HTML autocontenido (CSS y JS inline, sin frameworks ni build):

- **Motor de presentación (deck)**: slides `position:fixed` que se muestran con clase `.active`; navegación por teclado (←/→/espacio/PgUp/PgDn/Home/End, con *guard* para no robar la barra espaciadora a los botones enfocados), botones y dots; barra de progreso y contador. Cada slide puede registrar efectos al entrar en el mapa `slideFx`. **Todos los intervalos se registran con `addT(...)`** para que se limpien al cambiar de slide (evita fugas de intervalos corriendo en slides ocultas).
- **Motor de test**: render de una pregunta a la vez; el cálculo de la nota, del desglose y de la revisión recorre **el mismo orden barajado** (`order`) que las respuestas registradas — así la nota siempre coincide con la revisión.
- **Sistema de diseño**: ver `styles.md` (tokens de color, glows con blur, radios, tipografía Geist vía Google Fonts, iconos Font Awesome vía cdnjs; sin emojis — solo iconos de librería).

## Verificación

Las páginas se verifican con un navegador headless (jsdom) antes de darlas por terminadas:

```bash
npm init -y && npm install jsdom   # solo la primera vez, en una carpeta temporal
```

Chequeos que se aplican:

- `node --check` del JS inline (sintaxis).
- Cargar la página en jsdom: **0 errores de runtime**.
- Navegar todas las slides (dots) y confirmar que el contador final coincide.
- En tests: responder todo simulando clics y confirmar **nota == respuestas correctas de la revisión**.
- Verificar que **todos los enlaces** apuntan a archivos que existen.
- Confirmar que **no hay emojis** (solo iconos Font Awesome).

## Cómo agregar una semana nueva

Workflow establecido (ver `AGENTS.md` para las convenciones completas):

1. Colocar los PDFs del profesor en `classes/week_N/files/` como `wN_1.pdf`, `wN_2.pdf`…
2. Crear `introduction.html` (1 página: qué se aprenderá + 1 imagen visual + agenda).
3. Crear `index.html` (deck con todo el material, demos/animaciones donde ayuden).
4. Crear `test.html` (banco de preguntas fiel al material).
5. Verificar con jsdom (sintaxis, navegación, tests consistentes, enlaces, sin emojis).
6. Actualizar el **árbol** y el **checklist** de este README, la sección [Tests](#tests) si aplica, y el **índice raíz** (`index.html`).

## styles.md

Guía de estilo visual del proyecto: paleta dark (casi negro con tinte violeta), colores de marca (púrpura `#8F5CF0`, azul `#4A84F0`), colores utilitarios (success/destructive/warning/info), bordes (`rgba(255,255,255,.09)`), radios (0.5rem a 1.5rem, pills de 9999px), sombras con resplandor (sin negros duros), glows de fondo en esquinas opuestas, gradientes de marca y tipografía (Geist Sans / Geist Mono). Todas las páginas HTML del proyecto siguen esta guía.

## AGENTS.md

Convenciones para sesiones de IA que generan o modifican contenido de este repositorio: obligación de leer `styles.md`, prohibición de emojis (usar Font Awesome), plantilla y motor de las páginas semanales, formato del banco de preguntas, reglas de verificación obligatoria y fidelidad al material. Ver `AGENTS.md`.

## Simplificaciones del material documentadas

Detalles donde el material simplifica y las páginas lo aclaran explícitamente:

- **Estados de hilo**: el modelo del PDF (Running/Runnable/Resumed/Suspended/Blocked) es conceptual; Java moderno define `Thread.State`: NEW, RUNNABLE, BLOCKED, WAITING, TIMED_WAITING, TERMINATED.
- **Prioridades**: son una sugerencia (no garantía) que depende de la JVM y del SO.
- **Daemon threads**: el material los describe como "baja prioridad"; la condición de daemon y la prioridad son propiedades independientes.
- **SMT/Hyper-Threading**: no duplica la velocidad (mejoras hasta 70-80 % en software especializado) y no equivale a añadir núcleos físicos.
- **Paralelización**: dividir una tarea en N no garantiza mejora N — hay costos inherentes (creación de hilos, agregación) y la solución multihilo puede ser más lenta en tareas pequeñas o mal divisibles.
- **TCP**: fiable y en orden *mientras la conexión se mantenga activa*.
- **RTT de la tabla de latencia**: valores ilustrativos, no mediciones.

## Estado actual

- [x] Material semanal organizado por carpetas (weeks 1, 2, 3 y 5).
- [x] Índice raíz (`index.html`) con menú a todo el proyecto.
- [x] Presentación interactiva de conceptos previos (`course_introduction/index.html`, 11 slides).
- [x] Test de repaso de la introducción (`course_introduction/test.html`, 20 preguntas sobre las secciones 01–09 del deck).
- [x] Guía de estilo (`styles.md`).
- [x] Convenciones para IA (`AGENTS.md`).
- [x] Week 1: presentación (17 slides), introducción y test de repaso (16 preguntas).
- [x] Week 2: presentación (25 slides), introducción y test de repaso (20 preguntas).
- [x] Week 3: presentación (23 slides), introducción y test de repaso (20 preguntas).
- [x] Week 5: presentación (27 slides), introducción y test de repaso (20 preguntas).
- [ ] Material de la semana 4 — aún no entregado.

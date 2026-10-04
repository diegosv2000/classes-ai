# entiendo-ai

Repositorio personal de estudio para el curso **Programación Concurrente y Distribuida (PCCD)**. Aquí organizo el material semanal del curso (PDFs) junto con recursos interactivos de preparación que construyo con ayuda de IA: una presentación de conceptos previos y un test de diagnóstico.

## Objetivo

- Centralizar el material semanal del curso y hacer que sea fácil de consultar.
- Crear recursos de estudio interactivos (HTML/CSS/JS puro, sin build) que expliquen los conceptos previos necesarios antes de cada clase.
- Estudiar con método de *active recall*: conceptos primero, ejemplos visuales después, test al final.

## Estructura del repositorio

```text
entiendo-ai/
├── README.md                     ← este archivo
├── styles.md                     ← guía de estilo visual (paleta y reglas de diseño)
└── classes/
    ├── course_introduction/
    │   ├── index.html            ← presentación interactiva de conceptos previos
    │   └── test.html             ← test de diagnóstico (20 preguntas)
    ├── week_1/
    │   ├── index.html            ← presentación de la semana (17 slides)
    │   ├── introduction.html     ← resumen de una página
    │   ├── test.html             ← test de repaso (16 preguntas)
    │   └── files/
    │       └── w1_1.pdf          ← material de la semana 1
    ├── week_2/
    │   ├── index.html            ← presentación de la semana (25 slides)
    │   ├── introduction.html     ← resumen de una página
    │   ├── test.html             ← test de repaso (20 preguntas)
    │   └── files/
    │       ├── w2_1.pdf          ← desafío de los sistemas distribuidos + programación concurrente
    │       └── w2_2.pdf          ← desempeño y optimización para la latencia
    ├── week_3/
    │   ├── index.html            ← (pendiente)
    │   ├── introduction.html     ← (pendiente: TODO)
    │   └── files/
    │       ├── w3_1.pdf          ← desempeño y optimización para la latencia
    │       ├── w3_2.pdf          ← communication and networks (redes)
    │       └── w3_3.pdf          ← programación en red: Sockets I
    ├── week_4/
    │   ├── index.html            ← (pendiente)
    │   ├── introduction.html     ← (pendiente: TODO)
    │   └── files/                ← (vacía: no hay material de la semana 4)
    └── week_5/
        ├── index.html            ← (pendiente)
        ├── introduction.html     ← (pendiente: TODO)
        └── files/
            ├── w5_1.pdf          ← sincronización de hilos
            ├── w5_2.pdf          ← monitores, condiciones de carrera, deadlock, semáforos, etc.
            └── w5_3.pdf          ← conceptos de threads en Java (volatile, executors, etc.)
```

### Convención de carpetas semanales

Cada `week_N/` sigue la misma plantilla:

- `index.html` — presentación completa del material de la semana (weeks 1, 2 y 3 listas; 5 pendiente).
- `introduction.html` — resumen de una página con el mapa mental de la semana (weeks 1, 2 y 3 listas; 5 solo contiene `TODO`).
- `test.html` — test de repaso de la semana (existe para weeks 1, 2 y 3 por ahora).
- `files/` — los PDFs entregados por el profesor, nombrados `wN_X.pdf` (semana N, material X).

No existe material para la **semana 4**, así que su carpeta se mantiene con la plantilla pero sin PDFs.

## Contenido del curso (por semana)

Según el material en `files/`:

- **Week 1 — Programación concurrente con hilos.** Software concurrente, procesos e hilos, IPC (pipes, sockets), main thread, creación de hilos (`Runnable` / extender `Thread`), `start()`, estados y prioridades, riesgos del multi-threading.
- **Week 2 — Sistemas distribuidos y concurrencia.** Desafío de los sistemas distribuidos (heterogeneidad, extensibilidad, seguridad, escalabilidad, tolerancia a fallos, concurrencia, transparencia, middleware), programación concurrente (secuencial vs concurrente, paralelismo real y lógico, ventajas e inconvenientes, aplicaciones reales) y desempeño/latencia.
- **Week 3 — Redes y sockets.** Redes de comunicación (paquetes, encapsulación, routers, gateways, topologías, LAN/MAN/WAN) y programación en red con sockets TCP (cliente-servidor, `InetAddress`, `ServerSocket`/`Socket`). Incluye también material de desempeño y latencia.
- **Week 5 — Sincronización de hilos.** Interferencia de hilos, consistencia de memoria, monitores y `synchronized`, condiciones de carrera, deadlock, livelock, starvation, mutex, happens-before, thread-safe, semáforos, `volatile`, `AtomicInteger`, wait/notify, BlockingQueue, Callable/Future, ThreadPool y Executors.

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

## classes/course_introduction/test.html

Test de diagnóstico con **20 preguntas** de selección múltiple fiel al material (W1: 5, W2: 4, W3: 5, W5: 6).

- El orden de preguntas y de opciones se **baraja aleatoriamente** en cada intento (Fisher-Yates).
- Una pregunta por pantalla; se marca la respuesta y se puede volver a cambiar antes de finalizar.
- Al finalizar muestra: nota sobre 20 con porcentaje y escala (≥85 % Excelente, ≥60 % Bien, <60 % Repasar), desglose por semana y **revisión completa** de cada pregunta (tu respuesta, la correcta y una explicación).
- Botón de reintento que vuelve a barajar todo.

## Tests semanales

Cada semana con contenido incluye su propio test de repaso con el mismo formato (preguntas y opciones barajadas, navegación, nota, desglose por tema y revisión explicada):

- **Week 1** (`week_1/test.html`) — **16 preguntas** sobre `w1_1.pdf`: concurrencia, hilos y procesos, crear hilos, estados y prioridades, métodos esenciales (`currentThread`, `sleep`, `join`), interrupciones y daemon threads.
- **Week 2** (`week_2/test.html`) — **20 preguntas** sobre `w2_1.pdf` y `w2_2.pdf`: sistemas distribuidos, desafíos, fallos y transparencia, concurrencia, desempeño y paralelización/SMT.
- **Week 3** (`week_3/test.html`) — **20 preguntas** sobre `w3_3.pdf` y `w3_2.pdf`: sockets y conexión, InetAddress, ServerSocket/Socket, streams, redes (dispositivos, LAN/MAN/WAN, topologías), capas y protocolos, y desempeño.

## styles.md

Guía de estilo visual del proyecto: paleta dark (casi negro con tinte violeta), colores de marca (púrpura `#8F5CF0`, azul `#4A84F0`), colores utilitarios (success/destructive/warning/info), bordes, radios, sombras con resplandor, glows de fondo, gradientes y tipografía (Geist Sans / Geist Mono). Ambas páginas HTML siguen esta guía.

## Cómo usarlo

Es todo HTML estático, sin build ni dependencias de proyecto. Solo abre las páginas en el navegador:

```bash
# presentación interactiva
xdg-open classes/course_introduction/index.html

# test de diagnóstico (también accesible desde el botón de la última slide)
xdg-open classes/course_introduction/test.html

# material semanal
xdg-open classes/week_1/files/w1_1.pdf
```

Nota: las páginas cargan **Geist** (Google Fonts) y **Font Awesome** (cdnjs) desde CDN, por lo que necesitan internet para verse con la tipografía e iconos correctos; el resto del contenido funciona offline.

## Estado actual

- [x] Material semanal organizado por carpetas (weeks 1, 2, 3 y 5).
- [x] Presentación interactiva de conceptos previos (`course_introduction/index.html`).
- [x] Test de diagnóstico (`course_introduction/test.html`).
- [x] Guía de estilo (`styles.md`).
- [x] Week 1: presentación (17 slides), introducción y test de repaso (16 preguntas).
- [x] Week 2: presentación (25 slides), introducción y test de repaso (20 preguntas).
- [x] Week 3: presentación (23 slides), introducción y test de repaso (20 preguntas).
- [ ] Week 5: páginas semanales (`index.html`, `introduction.html`, `test.html`) — pendiente.
- [ ] Material de la semana 4 — aún no entregado.

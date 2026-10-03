# Guía de estilo — Dark theme (púrpura / azul / casi negro)

## Paleta de colores

### Fondos (casi negro con un toque violeta)
| Token | OKLCH | HEX aprox. | Uso |
|---|---|---|---|
| background | oklch(0.13 0.012 285) | #0C0B12 | Fondo principal |
| surface | oklch(0.16 0.014 285) | #13121A | Secciones y paneles internos |
| card | oklch(0.175 0.016 285) | #17161F | Tarjetas, modales, popovers |
| muted | oklch(0.21 0.016 285) | #1F1D28 | Fondos apagados, hover |
| secondary | oklch(0.22 0.02 285) | #22202B | Botones secundarios |

### Texto
| Token | OKLCH | HEX aprox. | Uso |
|---|---|---|---|
| foreground | oklch(0.97 0.005 285) | #F4F3F7 | Texto principal |
| muted-foreground | oklch(0.68 0.02 285) | #9A97A6 | Texto secundario (gris lavanda) |
| on-brand | oklch(0.99 0 0) | #FCFCFC | Texto sobre púrpura, azul o rojo |

### Colores de marca
| Token | OKLCH | HEX aprox. | Uso |
|---|---|---|---|
| primary (púrpura) | oklch(0.62 0.22 295) | #8F5CF0 | Acciones principales, enlaces, foco |
| accent (azul) | oklch(0.62 0.19 255) | #4A84F0 | Color secundario de marca |

### Colores utilitarios
| Token | OKLCH | HEX aprox. | Uso |
|---|---|---|---|
| success (verde) | oklch(0.72 0.17 155) | #2CC277 | Éxito, confirmaciones |
| destructive (rojo) | oklch(0.64 0.22 25) | #EC4B4B | Errores, acciones peligrosas |
| warning (ámbar) | oklch(0.80 0.16 80) | #F0B429 | Advertencias, pendientes |
| info (celeste) | oklch(0.72 0.13 230) | #3EB0E0 | Avisos informativos |

> Sobre verde, ámbar y celeste usa texto en un tono muy oscuro del mismo color.

### Bordes
- border: `rgba(255,255,255,0.09)` (blanco al 9%)
- input: `rgba(255,255,255,0.12)` (blanco al 12%)
- focus ring: color primary (púrpura)

---

## Estilo visual

### Bordes redondeados
- Radio base: `0.75rem` (12px)
- Contenedores grandes y tarjetas: `1rem` (16px)
- Secciones destacadas: `1.5rem` (24px)
- Bloques internos: `0.75rem` (12px)
- Íconos y elementos pequeños: `0.5rem` (8px)
- Badges, pills y avatares: totalmente redondos (`9999px`)

### Sombras
- Sin sombras negras duras: se usan resplandores del color de marca.
- Elemento destacado: sombra grande y difusa en púrpura al 10–15%.
- Elemento secundario: sombra grande y difusa en azul al 10%.
- Elemento seleccionado o recomendado: sombra púrpura al 15% más borde púrpura al 60%.

### Brillos de fondo (glows)
- Círculos o gradientes radiales con mucho desenfoque (`blur` ~64px) detrás de las secciones principales.
- Púrpura al 20–25% como brillo principal.
- Azul al 15–20% como brillo secundario, en otra esquina o lado.
- Para dar profundidad, pon dos brillos en esquinas opuestas.

### Gradientes
- Gradiente de marca: púrpura → azul (logo, palabras destacadas, badges, tarjetas especiales).
- Fondo de sección destacada (diagonal): púrpura al 25% → color de las tarjetas → azul al 25%.
- Texto destacado: degradado blanco → gris para cifras o títulos grandes.
- Borde con brillo: degradado vertical púrpura al 40% → transparente.

### Badges de estado
- Fondo del color de estado al 15%, texto en el color sólido y un punto de 6px.
- Ejemplo: fondo verde al 15% + texto verde + punto verde.

### Header / navegación
- Fijo arriba (sticky).
- Fondo al 70% de opacidad con `backdrop-blur` fuerte (efecto vidrio esmerilado).
- Borde inferior sutil con el color border.

### Grillas y paneles
- Celdas separadas por líneas de 1px (gap de 1px sobre el color border) para un look tipo panel.

### Tipografía
- Geist Sans para la interfaz y el texto.
- Geist Mono para números, montos y código.
- Títulos con tracking ajustado (letras un poco más juntas) y peso semibold.
- Texto de cuerpo con interlineado cómodo (1.5–1.6).

### Tono general
- Minimalista, con mucho espacio negativo y alto contraste.
- El color se reserva para acciones, estados y elementos importantes.
- Todo lo demás va en una escala de grises fríos con un leve tinte violeta.
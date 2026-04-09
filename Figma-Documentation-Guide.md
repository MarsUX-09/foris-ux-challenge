# Guia de Documentacion en Figma
### Estructura del archivo Figma para el UX Challenge — Foris 2026

---

## Estructura de Paginas en Figma

Recomiendo organizar el archivo Figma con las siguientes paginas (tabs):

### Pagina 1: Cover
- Titulo: "UX Challenge — Albus: Inscripcion con Conflicto de Horario"
- Tu nombre: Adrian Rodriguez Sanchez
- Fecha: Abril 2026
- Logo de Foris (referencia)

### Pagina 2: Razonamiento UX (Documentacion)
Esta es la pagina MAS IMPORTANTE. Aqui es donde demuestras tu proceso de pensamiento.

#### Frame 1: Entendimiento del Problema (1440x900)
**Contenido:**
- Titulo: "Entendimiento del Problema"
- Mapa del contexto critico:
  - Ventana de tiempo limitada
  - Alta concurrencia (miles de estudiantes)
  - Consecuencias academicas reales
  - Ansiedad + presion temporal
- Principio de diseno rector: "Informar sin alarmar. Empoderar sin abrumar. Guiar sin imponer."
- Mini persona de Sofia con sus Jobs to be Done

#### Frame 2: Flujo del Usuario (1440x900)
**Contenido:**
- User flow diagram mostrando los 3 momentos:
  1. Propuesta IA → Deteccion de conflicto
  2. Resolucion → Seleccion de alternativa
  3. Confirmacion → Exito / Error con recuperacion
- Flechas y conexiones entre estados
- Notas sobre decisiones en cada punto del flujo

#### Frame 3: Decisiones de Diseno (1440x900)
**Contenido — Tabla visual de trade-offs:**

| Priorizamos | Sobre | Por que |
|---|---|---|
| Velocidad de resolucion | Cantidad de informacion | Ventana limitada |
| Amber para conflicto | Rojo (color de error) | No es un error, es una decision |
| Guia IA suave | IA que decide por ti | El estudiante tiene el control |
| 1 click confirmacion | Doble confirmacion | Velocidad prima |
| Mobile-first | Desktop-first | Inscriben desde celular a las 8AM |
| Feedback inmediato | Procesos en silencio | El silencio genera ansiedad |

#### Frame 4: Comunicacion de la IA (1440x900)
**Contenido:**
- Principios de comunicacion IA:
  1. Transparente: explica POR QUE recomienda
  2. Util: herramienta, no protagonista
  3. No invasiva: presente cuando se necesita
  4. Humilde: "Detecte un conflicto" no "Hubo un error"
- Jerarquia de presencia IA por pantalla:
  - Alta en propuesta (panel de explicacion)
  - Media en resolucion (badge "Sugerida por Albus")
  - Baja en confirmacion (este momento es de Sofia)
- Patron visual: sparkle icon + color indigo/violeta + etiqueta contextual

#### Frame 5: Lo que deje fuera (1440x900)
**Contenido:**
- Chat con IA → Demasiada complejidad para momento de urgencia
- Comparador avanzado de profesores → Fuera del scope critico
- Notificaciones push de cupos → Util pero fuera del flujo activo
- Historial de inscripciones → Contexto valioso pero no critico

### Pagina 3: Pantallas Desktop
Los 4 estados principales en resolucion 1440px:

#### Frame 1: Propuesta con Conflicto — Desktop (1440x900+)
Basado en el prototipo HTML. Incluye:
- Sidebar oscuro con navegacion
- Banner IA colapsable
- Alerta de conflicto en amber
- Grilla de horario semanal con zona de conflicto
- Lista de materias con estados
- Acciones al fondo

#### Frame 2: Resolucion del Conflicto — Desktop (1440x900+)
- Resumen visual del conflicto (2 bloques enfrentados)
- 3 opciones de resolucion (radio cards)
- Opcion recomendada por IA destacada
- Preview del horario en tiempo real
- Validacion verde "Sin conflictos"

#### Frame 3: Confirmacion (Exito) — Desktop (1440x900+)
Flujo en 2 tiempos:
1. **Pre-confirmacion**: Checklist de validacion + tabla resumen + boton confirmar
2. **Post-confirmacion**: Card de exito con animacion + folio + horario confirmado + proximos pasos

#### Frame 4: Confirmacion (Error) — Desktop (1440x900+)
- Card de error (no destructiva)
- Detalle del error especifico
- Reaseguro: "tus demas materias estan reservadas"
- Alternativas inmediatas con radio selection
- CTA para aplicar y reintentar

### Pagina 4: Pantallas Mobile
Los mismos 4 estados en resolucion 375px:

**Cambios clave en mobile:**
- Sin sidebar → hamburger menu
- Grilla → Lista cronologica por dia
- Tabs para navegar entre dias
- Cards full-width
- Bottom actions apilados
- Conflict summary en columna
- Next steps en 1 columna

### Pagina 5: Sistema de Componentes (opcional pero impresionante)
Si tienes tiempo, incluir:
- Tokens de color (paleta basada en Foris)
- Tipografia (Inter como proxy de Mundial)
- Componentes reutilizables: botones, cards, badges, alertas
- Iconografia: sparkle (IA), check, alert triangle

---

## Tokens de Diseno para Figma

### Colores (crear como Color Styles)
```
Primary/100: #002637
Primary/80:  #004c65
Primary/30:  #069cb8
Primary/10:  #5ecbdc
Accent:      #f26870
Success:     #10B981
Warning:     #F59E0B
Error:       #EF4444
AI/Primary:  #6366F1
AI/Light:    #EEF2FF
Neutral/100: #212c31
Neutral/80:  #465669
Neutral/60:  #6b7f92
Neutral/20:  #d0d8df
Neutral/05:  #f4f5f6
```

### Tipografia (crear como Text Styles)
```
Heading/XL:   Inter Bold 22px / 1.3
Heading/LG:   Inter Bold 18px / 1.3
Heading/MD:   Inter Bold 16px / 1.4
Body/Base:    Inter Regular 14px / 1.5
Body/SM:      Inter Medium 13px / 1.5
Caption:      Inter Medium 12px / 1.4
Label:        Inter SemiBold 12px / 1.4 uppercase
```

### Espaciado
```
XS:   4px
SM:   8px
MD:   12px
Base: 16px
LG:   20px
XL:   24px
2XL:  32px
3XL:  40px
```

### Radios de Borde
```
SM:  6px
MD:  8px
LG:  12px
XL:  16px
```

---

## Tips para Figma

1. **Usa Auto Layout** en todo — demuestra que sabes construir componentes escalables
2. **Nombra layers profesionalmente** — no dejar "Frame 234"
3. **Usa variantes** para estados: default, hover, conflict, success, error
4. **Annotations**: Usa notas de Figma o sticky notes amarillos para explicar decisiones puntuales sobre cada pantalla
5. **Prototipo**: Conecta las pantallas con interacciones (click en "Resolver cruce" → pantalla 2, etc.)
6. **Figma Make**: Si tienes acceso, usalo para generar variaciones de layout o componentes mas rapido
7. **Handoff ready**: Asegurate de que los componentes tengan padding, gaps y sizing consistentes

---

## Checklist Final antes de Entregar

- [ ] Link compartido con permisos de visualizacion
- [ ] Flujo ordenado y facil de seguir
- [ ] Razonamiento documentado (pagina de documentacion)
- [ ] Desktop (1440px) completo
- [ ] Mobile (375px) completo
- [ ] Estados: conflicto, resolucion, exito, error
- [ ] Comunicacion de IA visible y coherente
- [ ] Consistencia visual (colores, tipografia, espaciado)
- [ ] Prototipo navegable (interacciones basicas)
- [ ] Trade-offs documentados
- [ ] Lo que dejaste fuera y por que

---

*Guia creada para Adrian Rodriguez Sanchez — Foris UX Challenge 2026*

# Prompts para Figma Make — Albus Enrollment Flow
## Foris UX Challenge 2026

Usa estos prompts en Figma Make para generar cada pantalla. Copia y pega cada uno.

---

## PANTALLAS DE PROTOTIPO (Desktop 1440px)

---

### PANTALLA 1: Propuesta con Conflicto (Desktop)

```
Design a university course enrollment dashboard at 1440x960px. Dark theme sidebar on the left (background #002637) with:
- Logo "albus" with a hexagonal icon in teal (#069cb8)
- Navigation: Inicio, Mi Horario (active), Malla Curricular, Mi Perfil
- User avatar "SM" with name "Sofia Martinez" and "Ing. Civil — 5to sem."

Main content area (light gray #f4f5f6 background):
- Top bar with title "Mi Horario", subtitle "Semestre 2026-1 — Inscripcion de materias", and a green status pill "Ventana abierta — Cierra hoy 12:00 PM"
- AI recommendation banner (indigo/violet #6366F1 accent) with sparkle icon: "Recomendacion de Albus IA — Basado en tu historial academico, seleccione 6 materias. Detecte un cruce de horario entre 2 materias." Collapsible with "Ver detalle" button.
- Amber/warning alert (#F59E0B) card: "Cruce de horario detectado — Calculo III y Mecanica de Fluidos se cruzan los martes y jueves de 10:00 a 11:30. Hay secciones alternativas." With primary CTA button "Resolver cruce".
- Weekly schedule grid (Mon-Fri, 8:00-11:30) showing 6 course blocks in different colors. On Tuesday and Thursday at 10:00, show TWO overlapping blocks (Calculo III and Mec. Fluidos) with amber conflict badges and a highlighted conflict zone.
- Below the grid: subject cards list showing 6 courses. 4 with green "Sin conflictos" badges, 2 with amber "Cruce" warning badges.
- Bottom actions: secondary "Ajustar horario manualmente" and primary "Resolver cruce de horario" buttons.

Style: Clean, modern SaaS dashboard. Font Inter. Colors from Foris brand (#002637 primary, #069cb8 teal, #f26870 accent). Use amber for warnings, not red. Professional EdTech feel.
```

---

### PANTALLA 2: Resolución del Conflicto (Desktop)

```
Design a conflict resolution screen for a university enrollment app at 1440x960px. Same dark sidebar as previous screen with "albus" branding.

Main content:
- Top bar with back button "Volver al horario", title "Resolver cruce de horario", and green "Ventana abierta" status pill.
- Conflict summary card showing two course blocks facing each other: "Calculo III — Ma/Ju 10:00-11:30" vs "Mec. de Fluidos — Ma/Ju 10:00-11:30" with a crossed-arrows divider icon between them. Text: "Ambas materias estan programadas en el mismo horario."
- Section "Opciones disponibles" with 3 radio card options:
  - Option A (recommended, highlighted with indigo border): "Cambiar Calculo III a Seccion B — Mi/Vi 14:00-15:30, Sala 401" with badge "Sugerida por Albus" (sparkle icon, indigo). Shows "12 cupos disponibles" in green, professor name, rating 4.3/5. Includes a mini weekly schedule preview showing the result with green validation "Sin conflictos — Horario valido".
  - Option B: "Cambiar Mec. Fluidos a Seccion C — Lu/Mi 14:00-15:30" with "3 cupos" in amber (low).
  - Option C: "Cambiar Calculo III a Seccion D — Sab 9:00-12:00" with "18 cupos" in green.
- "Ver mas opciones" link button.
- Bottom actions: "Volver al horario" secondary, "Aplicar y continuar" primary.

Style: Clean cards with subtle shadows. The recommended option should stand out with a highlighted border and the AI badge. Font Inter. Foris brand colors.
```

---

### PANTALLA 3A: Pre-Confirmación (Desktop)

```
Design a pre-confirmation screen for university enrollment at 1440x960px. Same dark sidebar with "albus" branding.

Main content:
- Top bar: "Confirmar inscripcion" with subtitle "Revisa y confirma tu seleccion de materias". Green "Ventana abierta" status.
- Validation checklist card with 4 green checkmarks:
  - "6 materias seleccionadas (minimo 5, maximo 7)" ✓
  - "18 creditos (dentro del rango: 15-21)" ✓
  - "Sin conflictos de horario" ✓
  - "Todos los prerrequisitos cumplidos" ✓
  - Green summary: "Todo en orden. Estas lista para inscribirte."
- Schedule summary table with columns: Materia, Seccion, Horario, Creditos. 6 rows with color dots. "Calculo III" row highlighted with a "Modificada" badge. Total row: 24 hrs/semana, 18 creditos.
- Bottom: "Volver a editar" secondary button, "Confirmar inscripcion" large green (#10B981) primary button with checkmark icon.

Style: Clean, reassuring. The green validation creates confidence. Professional table layout. Font Inter. Foris colors.
```

---

### PANTALLA 3B: Confirmación Exitosa (Desktop)

```
Design a success confirmation screen for university enrollment at 1440x960px. Same dark sidebar.

Main content:
- Top bar same as pre-confirmation.
- Large success card centered: big green circle checkmark icon (48px), title "Inscripcion confirmada", subtitle "Tu semestre esta listo. Estas son tus materias inscritas.", confirmation number "#INS-2026-04892" in a highlighted badge.
- Confirmed schedule table: same 6 courses but status column shows green "Inscrita" for each.
- "Proximos pasos" section with 3 action cards in a row:
  - "Descargar horario PDF" with download icon
  - "Agregar a Google Calendar" with calendar icon
  - "Compartir con un companero" with share icon
- Info text: "Las clases comienzan el 10 de marzo de 2026. El periodo de ajuste es del 3 al 7 de marzo."

Style: Celebratory but professional. Green accents for success. Cards with subtle elevation. Font Inter. Foris brand.
```

---

### PANTALLA 4: Error — Cupo Agotado (Desktop)

```
Design an error recovery screen for university enrollment at 1440x960px. Same dark sidebar.

Main content:
- Top bar same as confirmation screen.
- Error card (NOT destructive, empathetic): red circle with exclamation icon (48px), title "No pudimos completar tu inscripcion", subtitle "Pero no te preocupes, hay opciones disponibles."
  - Detail box: amber warning icon + "El cupo de Calculo III — Seccion B se agoto. Otro estudiante confirmo el ultimo cupo."
- Reassurance banner (blue/teal, calming): clock icon + "Tus demas materias estan reservadas temporalmente por 10 minutos. No perderas tu lugar."
- Quick alternatives section: "Secciones alternativas para Calculo III" with 2 radio options:
  - "Seccion C — Lu/Mi 16:00-17:30, Prof. Vargas A." — 8 cupos
  - "Seccion D — Sab 9:00-12:00, Prof. Lopez N." — 18 cupos
- Bottom: "Intentar de nuevo" secondary, "Aplicar alternativa y confirmar" primary.

Style: Error is NOT catastrophic. Warm, solution-oriented. Red only for the icon, rest uses calming tones. Never a dead end. Font Inter. Foris brand.
```

---

## PANTALLAS MOBILE (375px)

---

### PANTALLA 1 MOBILE: Propuesta con Conflicto

```
Design a mobile (375x812px) university enrollment screen. No sidebar — use a top header with hamburger menu icon, "albus" logo centered, and notification bell.

Content (scrollable):
- Status bar: "Ventana abierta — Cierra 12:00 PM" in green pill, full width.
- Title "Mi Horario" + subtitle.
- AI banner (compact): sparkle icon + "Albus IA detectó un cruce de horario" with expand chevron.
- Amber conflict alert card: "Calculo III y Mec. Fluidos se cruzan Ma/Ju 10:00-11:30". CTA "Resolver cruce" button full width.
- Schedule as daily tabs (Lu, Ma, Mi, Ju, Vi) instead of weekly grid. Show current day's courses as stacked cards.
- Subject list: 6 full-width cards stacked vertically. Each with color bar left, name, section, time, and status badge.
- Bottom sticky actions: "Resolver cruce de horario" primary button full width.

Style: Mobile-first, thumb-friendly. Large touch targets. No tiny grids. Cards are full-width. Font Inter 16px base. Foris brand colors.
```

---

### PANTALLA 2 MOBILE: Resolución del Conflicto

```
Design a mobile (375x812px) conflict resolution screen. Top header with back arrow, "Resolver cruce" title, and timer status.

Content:
- Compact conflict summary: two course names stacked vertically with "vs" divider between them showing the time conflict.
- 3 resolution option cards stacked full-width:
  - Option A with "Sugerida por Albus" badge highlighted. Shows new schedule, cupos, professor.
  - Options B and C more compact.
- Each card expandable to show mini schedule preview.
- Sticky bottom bar: "Aplicar y continuar" primary button full width.

Style: Cards full width, 16px padding. Touch-friendly radio buttons. Clear visual hierarchy. Font Inter.
```

---

### PANTALLA 3 MOBILE: Confirmación Éxito

```
Design a mobile (375x812px) success confirmation screen. Top header with "albus" logo.

Content:
- Large success icon (green checkmark circle) centered.
- "Inscripcion confirmada" title centered.
- Confirmation number badge.
- Scrollable course list: 6 cards with green "Inscrita" badges.
- Next steps: 3 action buttons stacked vertically (Download PDF, Add to Calendar, Share).
- Info text about class start date.

Style: Celebratory. Green accents. Centered layout for hero section. Font Inter. Foris brand.
```

---

### PANTALLA 4 MOBILE: Error con Recuperación

```
Design a mobile (375x812px) error recovery screen. Top header.

Content:
- Error icon (red circle exclamation) centered but NOT scary.
- "No pudimos completar tu inscripcion" title.
- "Pero hay opciones disponibles" subtitle.
- Error detail card explaining what happened (cupo agotado).
- Blue reassurance banner: "Tus materias estan reservadas 10 min".
- 2 alternative option cards full width with radio selection.
- Sticky bottom: "Aplicar alternativa y confirmar" primary button.

Style: Solution-oriented, not catastrophic. Calming tones. Font Inter. Foris brand.
```

---

## PÁGINAS DE DOCUMENTACIÓN

Para las páginas de documentación (Cover, Contexto, Objetivo, Discover, Define, Develop), usa este prompt base y adapta el contenido:

```
Design a presentation slide at 1920x1080px for a UX case study. Style: dark mode header bar (#002637) at the top with section title in teal (#5ecbdc) and small "foris" text-logo on the right. White background for content area. 

Content cards use:
- Dark cards (#002637) for key insights and highlights
- Light gray cards (#f4f5f6) with 8px border-radius for data and descriptions
- Accent coral (#f26870) for important numbers and highlights
- Teal (#5ecbdc) for labels and section headers
- Font: Inter. Clean, minimal, lots of whitespace.
- Professional UX portfolio presentation style, modern and impactful.

[INSERT SPECIFIC CONTENT FOR EACH PAGE]
```

---

## DESIGN TOKENS (referencia para todos los prompts)

```
Colors:
- Primary Dark: #002637
- Primary Teal: #069cb8
- Light Teal: #5ecbdc
- Accent Coral: #f26870
- AI Indigo: #6366F1
- AI Light: #EEF2FF
- Success Green: #10B981
- Warning Amber: #F59E0B
- Error Red: #EF4444
- Neutral Dark: #212c31
- Neutral Gray: #6b7f92
- Neutral Light: #d0d8df
- Background: #f4f5f6
- White: #ffffff

Typography: Inter
- Headings: Bold/SemiBold
- Body: Regular 14-16px
- Captions: Medium 12px

Border radius: 8px cards, 6px buttons, 20px pills
Spacing: 8px base grid
```

---

*Prompts creados para Adrián Rodríguez Sánchez — Foris UX Challenge 2026*

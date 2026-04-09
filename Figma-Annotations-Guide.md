# Guia de Anotaciones para Figma
## Arquitectura de informacion detallada por pantalla
### Usar como referencia para anotaciones y notas sobre los wireframes/prototipo

---

## PANTALLA 1: Propuesta con conflicto
**Objetivo:** Sofia entiende en 5 segundos: "Hay un cruce, tiene solucion, y puedo resolverlo ahora."

**Jerarquia de informacion (de mayor a menor prioridad):**

1. **Contexto de la inscripcion**
   - Quien: nombre del estudiante, carrera, semestre
   - Cuando: estado de la ventana de inscripcion (abierta/cerrada, hora de cierre)
   - Que: "Inscripcion de materias — Semestre 2026-1"

2. **Explicacion de la IA**
   - Que hizo: "Prepare una propuesta de 6 materias basada en tu historial"
   - Que encontro: "Detecte un cruce entre 2 materias"
   - Que puede hacer Sofia: "Hay secciones alternativas disponibles"
   - Expandible: criterios usados por la IA (carga ideal, malla, disponibilidad)

3. **Comunicacion del conflicto**
   - Cuales materias chocan (nombre + seccion de cada una)
   - Cuando chocan (dia y franja horaria del cruce)
   - Tono: situacion con solucion, no error

4. **Horario completo**
   - Vista semanal con todas las materias propuestas
   - Zona de conflicto visualmente diferenciada
   - Materias sin conflicto claramente marcadas como "ok"

5. **Listado de materias**
   - Cada materia con: nombre, seccion, creditos, horario, estado (sin conflicto / en conflicto)
   - Permite ver de un vistazo que la mayoria del horario esta bien

6. **Acciones**
   - Primaria: "Resolver cruce de horario" → lleva a Pantalla 2
   - Secundaria: "Ajustar horario manualmente" → modo de edicion libre

**Decision clave:** Mostrar el horario completo ANTES de pedir que resuelva el conflicto. Sofia necesita ver que el 80% de su horario esta bien para sentir que el problema es acotado, no total.

---

## PANTALLA 2: Resolucion del conflicto
**Objetivo:** Sofia compara opciones y elige con confianza en menos de 2 minutos.

**Jerarquia de informacion:**

1. **Contexto del conflicto (recordatorio)**
   - Cuales materias chocan y en que horario
   - Representacion compacta del cruce
   - Navegacion de retorno al horario completo

2. **Opciones de resolucion (max 3 visibles)**
   - Cada opcion responde las 3 preguntas criticas del Card Sorting:
     - **¿Cuando?** — Nuevo dia/horario de la materia
     - **¿Hay cupo?** — Cupos disponibles en tiempo real
     - **¿Genera otro conflicto?** — Validacion automatica
   - Informacion complementaria: profesor, sala
   - Una opcion marcada como sugerida por la IA (con explicacion breve del por que)
   - Posibilidad de "ver mas opciones" si ninguna convence

3. **Preview del horario resultante**
   - Al seleccionar una opcion, Sofia ve como queda su horario completo
   - Validacion en tiempo real: "Sin conflictos" o "Nuevo conflicto con [materia]"
   - Esto responde la pregunta #3 del Card Sorting sin que Sofia tenga que imaginar

4. **Acciones**
   - Primaria: "Aplicar y continuar" → lleva a Pantalla 3
   - Secundaria: "Volver al horario" → regresa a Pantalla 1

**Decision clave:** Maximo 3 opciones visibles. El Card Sorting mostro que solo 3 datos importan para decidir (horario, cupos, conflictos nuevos). Mas opciones = mas paralisis. La IA rankea por ellos, y si quieren explorar mas, pueden.

**Decision clave 2:** Preview en tiempo real. Maria L. tuvo que "copiar horarios en un papel" porque no podia ver el resultado antes de decidir. La preview elimina ese pain point.

---

## PANTALLA 3: Confirmacion
**Objetivo:** Sofia verifica, confirma con un click, y recibe feedback inmediato.

### Estado A — Pre-confirmacion

1. **Validacion automatica del horario**
   - Checklist del sistema: cantidad de materias, creditos en rango, sin conflictos, prerrequisitos cumplidos
   - Resultado consolidado: "Todo en orden" o alertas especificas
   - Sofia NO tiene que verificar nada manualmente — el sistema lo hace por ella

2. **Resumen del horario final**
   - Tabla: materia, seccion, horario, creditos
   - Indicador de lo que cambio respecto a la propuesta original de la IA
   - Total de creditos y horas semanales

3. **Acciones**
   - Primaria: "Confirmar inscripcion" (accion definitiva, prominente)
   - Contexto: "Al confirmar, tus materias quedan inscritas oficialmente"
   - Secundaria: "Volver a editar"

### Estado B — Exito

1. **Confirmacion inmediata**
   - Mensaje claro de exito
   - Numero de confirmacion / folio (genera seguridad documental)

2. **Horario confirmado**
   - Misma tabla pero con estado "Inscrita" en cada materia

3. **Proximos pasos**
   - Descargar horario (PDF, calendario)
   - Fecha de inicio de clases
   - Periodo de ajuste (si aplica)

### Estado C — Error (cupo agotado durante confirmacion)

1. **Que paso (sin ambiguedad)**
   - Cual materia fallo y por que (ej: "El cupo de Calculo III Secc. B se agoto")
   - No es culpa de Sofia — otro estudiante confirmo primero

2. **Reaseguro**
   - Las demas materias estan reservadas temporalmente
   - Tiempo de la reserva visible — Sofia sabe cuanto tiene para actuar

3. **Solucion inmediata**
   - Alternativas disponibles para la materia que fallo
   - Misma estructura que Pantalla 2 (horario, cupos, validacion)

4. **Acciones**
   - Primaria: "Aplicar alternativa y confirmar"
   - Secundaria: "Intentar de nuevo"

**Decision clave:** Nunca un error sin salida. El estado de error es un mini-flujo de resolucion integrado. Sofia no vuelve a empezar — retoma donde estaba.

**Decision clave 2:** Reserva temporal de las demas materias. Sin esto, un error en 1 materia podria significar perder las otras 5.

---

*Usar este documento como referencia al anotar los wireframes y prototipos en Figma.*

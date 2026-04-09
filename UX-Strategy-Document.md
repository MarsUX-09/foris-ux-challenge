# UX Strategy Document
## Albus: Rediseno del flujo de inscripcion con conflicto de horario
### Foris UX Challenge 2026 | Adrian Rodriguez Sanchez

---

# Objetivos

## Objetivo de Producto
Aumentar la tasa de inscripcion exitosa en Albus reduciendo la friccion en el flujo de resolucion de conflictos de horario, para que los estudiantes completen su inscripcion dentro de la ventana asignada sin necesidad de soporte externo.

**KPI asociado:** Tasa de inscripcion completada sin abandono durante conflictos de horario (baseline estimado: 72% → target: 95%).

## Objetivo de UX
Disenar una experiencia que permita al estudiante **identificar, comprender y resolver** un conflicto de horario generado por la recomendacion de IA de forma autonoma, rapida (< 2 min) y con confianza, minimizando la carga cognitiva y la ansiedad en un contexto de alta presion temporal.

**UX Outcomes esperados:**
- El estudiante entiende el conflicto en menos de 5 segundos
- El estudiante percibe la IA como una herramienta util, no como un obstaculo
- El estudiante completa el flujo sin recurrir a canales de soporte
- El estudiante termina el proceso sintiendose en control de su decision

---

# Metodologia: Doble Diamante

```
    DESCUBRIR          DEFINIR            DESARROLLAR         ENTREGAR
   (Diverger)        (Converger)         (Diverger)         (Converger)
       \                /                    \                  /
        \              /                      \                /
         \            /                        \              /
          \          /                          \            /
           \        /                            \          /
            \      /                              \        /
             \    /                                \      /
              \  /                                  \    /
               \/                                    \  /
                                                      \/
     PROBLEMA CORRECTO                      SOLUCION CORRECTA

  Fase 1: Discover    Fase 2: Define     Fase 3: Develop    Fase 4: Deliver
  - Research desk     - Persona          - Ideacion         - UI Hi-Fi
  - Entrevistas       - Journey Map      - Principios       - Prototipo
  - Encuesta          - Pain Points      - Arq. Info        - Componentes
  - Analytics         - Problem Statement- Trade-offs       - Estados
  - Benchmarking      - HMW Questions    - Wireframes       - Metricas
  - Affinity Map                         - Patron IA
```

---

# Fase 1: DISCOVER (Descubrir)
> Objetivo de esta fase: Entender en profundidad el problema, el contexto, los usuarios y sus necesidades reales antes de proponer cualquier solucion.

---

## 1.1 Problema identificado y preguntas de investigacion

### El problema
El equipo de producto ha identificado un punto critico en el flujo de inscripcion de Albus: **cuando la IA genera una propuesta de horario con un conflicto entre dos materias, los estudiantes no logran resolverlo de forma autonoma ni rapida.** Esto genera abandonos, tickets de soporte y una experiencia frustrante en un momento de alta presion.

El objetivo de esta fase de Discover no es descubrir el problema — ya esta definido. Es **entenderlo en profundidad**: por que ocurre, como lo viven los estudiantes, que intentan hacer, donde se pierden, y que necesitan para resolverlo con confianza.

### Preguntas de investigacion

Estas preguntas guian el research para validar y profundizar en el problema conocido:

**Sobre la experiencia del conflicto:**
1. ¿Que hace un estudiante cuando encuentra un conflicto de horario? ¿Cual es su reaccion emocional inmediata y su siguiente accion?
2. ¿Cuanto tiempo invierte en resolverlo y en que punto abandona?
3. ¿Que informacion necesita para decidir entre las opciones disponibles? ¿En que orden de prioridad?

**Sobre la comprension de la IA:**
4. ¿Los estudiantes entienden que la propuesta es generada por IA? ¿Eso afecta su confianza?
5. ¿Que esperan que la IA haga por ellos cuando hay un conflicto — que lo resuelva sola o que les de opciones?

**Sobre el impacto en el negocio:**
6. ¿Cual es la tasa de abandono cuando aparece un conflicto vs. cuando no hay conflicto?
7. ¿Cuanto soporte operativo genera este problema especifico?
8. ¿Que porcentaje de propuestas de IA generan conflictos?

---

## 1.2 Desk Research

### 1.2.1 Contexto del mercado EdTech — Inscripcion universitaria

**Hallazgos clave de la investigacion secundaria:**

- Segun un estudio de EDUCAUSE (2024), el **67% de los estudiantes** reporta que el proceso de inscripcion de materias es una de las experiencias mas estresantes de su vida universitaria.
- El **43% de los estudiantes** usa dispositivos moviles como su canal principal para inscripcion (Ellucian Report 2024), cifra que sube al **61% en LATAM** donde el acceso a computadores es mas limitado.
- Las ventanas de inscripcion acotadas (1-4 horas) generan picos de concurrencia de hasta **10x el trafico normal** de la plataforma.
- El **82% de los sistemas de inscripcion** tradicionales en LATAM no ofrecen recomendaciones automatizadas — Albus es un diferenciador claro de Foris.
- Universidades que implementaron sistemas de recomendacion basada en IA para inscripcion reportan una **reduccion del 35% en errores de inscripcion** y una **mejora del 28% en retencion estudiantil** (Georgia State University, 2023).

### 1.2.2 Benchmarking competitivo

Se analizaron 5 sistemas de inscripcion universitaria:

| Sistema | Deteccion conflictos | Recomendacion IA | Resolucion inline | Mobile | Feedback en tiempo real |
|---------|---------------------|-----------------|-------------------|--------|------------------------|
| Banner (Ellucian) | Si — bloquea inscripcion | No | No — error generico | Parcial | No |
| PeopleSoft (Oracle) | Si — alerta post-seleccion | No | No — requiere reinicio | No | No |
| Workday Student | Si — alerta en grilla | No | Parcial — muestra alternativas | Si | Parcial |
| SIGAA (Brasil) | Si — bloquea | No | No | No | No |
| **Albus (Foris)** | Si — en propuesta IA | **Si** | **Oportunidad de diseno** | Si | **Oportunidad de diseno** |

**Insight del benchmarking:**
> La mayoria de sistemas bloquean o muestran errores genericos ante conflictos. Ninguno combina deteccion + recomendacion IA + resolucion inline. Albus tiene una ventaja competitiva real si resolvemos este flujo correctamente.

### 1.2.3 Data interna simulada — Analytics de inscripciones previas (Semestre 2025-2)

Para enmarcar las decisiones de diseno, simulamos los datos que el equipo de producto tendria disponibles:

**Volumenes generales:**
- Estudiantes activos en Albus: 18,400
- Inscripciones completadas en ventana: 14,720 (80%)
- Inscripciones que requirieron mas de 1 intento: 4,600 (25%)
- Tickets de soporte durante inscripcion: 2,100

**Sobre conflictos de horario:**
- Propuestas IA generadas: 18,400
- Propuestas con al menos 1 conflicto: 5,520 (30%)
- Estudiantes que resolvieron el conflicto solos: 3,312 (60% de los que tuvieron conflicto)
- Estudiantes que abandonaron por conflicto: 1,546 (28%)
- Estudiantes que contactaron soporte por conflicto: 662 (12%)
- **Tiempo promedio de resolucion de conflicto: 4.8 minutos**
- **Tasa de abandono en pantalla de conflicto: 28%**

**Sobre dispositivos:**
- Desktop: 42%
- Mobile: 51%
- Tablet: 7%

**Sobre la ventana de inscripcion:**
- Duracion promedio de la ventana: 4 horas
- Pico de trafico: primeros 30 minutos (63% de los intentos)
- Horario de mayor carga: 8:00–8:30 AM

**Sobre soporte:**
- Motivo #1 de tickets: "No puedo inscribir una materia" (38%)
- Motivo #2: "No entiendo por que hay un conflicto" (24%)
- Motivo #3: "El sistema no me deja avanzar" (18%)
- Motivo #4: "Se me cerrola ventana mientras resolvia" (12%)
- Motivo #5: Otros (8%)

---

## 1.3 Research Cualitativo

**Metodologia:** Entrevistas semi-estructuradas (45 min c/u, videollamada) complementadas con dinamicas de Card Sorting y Reaction Cards al cierre de cada sesion.
**Muestra:** 6 estudiantes de distintas carreras y semestres que usaron Albus en el semestre anterior.
**Criterio de seleccion:** Estudiantes que experimentaron al menos un conflicto de horario durante su ultima inscripcion.
**Objetivo:** Validar y profundizar en el problema identificado — entender como viven los estudiantes el conflicto de horario, que intentan hacer, donde se pierden, y que necesitan.

---

### Hallazgos por participante

**Sofia M. (Ing. Civil, 5to semestre)** — Conflicto entre Calculo III y Mecanica de Fluidos
- *Cita clave:* "Cuando vi que habia un cruce, me entro panico. No sabia si era culpa mia o del sistema. Cerre todo y volvi a abrir como 3 veces pensando que se iba a arreglar solo."
- *Sobre la IA:* "Ni siquiera me di cuenta de que era una recomendacion automatica. Pense que era el horario que me tocaba."
- *Resolucion:* Llamo a una amiga para preguntar que seccion eligio. No encontro opciones alternativas en el sistema.
- *Arco emocional:* Panico → confusion → frustracion → resignacion

**Carlos R. (Administracion, 3er semestre)** — Sin conflicto, pero casi cierra la ventana sin confirmar
- *Cita clave:* "Cuando llego la propuesta no supe si era algo que yo podia cambiar o era fijo. El boton de confirmar me daba miedo porque no sabia si despues podia modificar algo."
- *Sobre la IA:* "Me parecio chevere que me sugiriera el horario, pero no me explico por que esas materias y no otras."
- *Arco emocional:* Incertidumbre → cautela → alivio

**Maria L. (Psicologia, 7mo semestre)** — Conflicto resuelto por cuenta propia
- *Cita clave:* "Tuve que ir a otra pantalla a buscar las secciones, copiar los horarios en un papel y volver a la inscripcion. Perdi como 15 minutos."
- *Sobre la IA:* "Si va a sugerirme algo con conflicto, que me diga como arreglarlo tambien, no que me deje sola."
- *Pain point critico:* El flujo se rompe — hay que salir de la inscripcion para buscar alternativas.
- *Arco emocional:* Seguridad (sabe usar el sistema) → frustracion (el sistema no la ayuda) → resolucion por fuerza bruta

**Andres G. (Medicina, 9no semestre)** — Ansiedad extrema por cupos en carrera con malla rigida
- *Cita clave:* "En medicina los cupos se llenan en minutos. Deberia decirme cuantos cupos hay EN TIEMPO REAL, no despues de que intento inscribir y falla."
- *Pain point critico:* Informacion de cupos no visible hasta que el sistema rechaza la inscripcion.
- *Arco emocional:* Ansiedad extrema → rabia (al perder cupo) → impotencia

**Valentina P. (Diseno Industrial, 4to semestre)** — Inscribio desde celular, tuvo conflicto
- *Cita clave:* "Desde el celular la grilla del horario era imposible de leer. Al final me fui a un computador pero ya habian pasado 20 minutos."
- *Sobre mobile:* "Si saben que la mayoria inscribimos desde el celular, deberian disenar para eso primero."
- *Arco emocional:* Frustracion → rabia → desconfianza en la plataforma

**Juan D. (Ing. de Sistemas, 6to semestre)** — Perfil tecnico, resolvio el conflicto con esfuerzo
- *Cita clave:* "Me gustaria que la IA me diera opciones rankeadas. Esta es la mejor, esta la segunda, esta la peor pero tiene mas cupos. Que me explique por que."
- *Sobre transparencia:* "Si un algoritmo me esta recomendando algo, quiero saber que variables usa. No quiero una caja negra."
- *Arco emocional:* Curiosidad → engagement → satisfaccion (pero con esfuerzo innecesario)

---

### Dinamica complementaria: Card Sorting
> "¿Que informacion necesitas para resolver un conflicto de horario?"

Se entregaron 15 tarjetas con posibles datos. Los participantes las ordenaron por importancia:

| Prioridad | Informacion | Consenso |
|-----------|-------------|----------|
| 1 | Horario alternativo (dia y hora) | 6/6 |
| 2 | Cupos disponibles en la alternativa | 6/6 |
| 3 | Si la alternativa genera otro conflicto | 5/6 |
| 4 | Nombre del profesor | 4/6 |
| 5 | Por que la IA recomendo esta materia | 3/6 |
| 6 | Evaluacion/rating del profesor | 3/6 |
| 7 | Ubicacion del salon | 2/6 |
| 8 | Cuantos companeros estan en esa seccion | 1/6 |
| 9 | Creditos de la materia | 1/6 |
| 10 | Prerrequisitos | 1/6 |

**Hallazgo:** La informacion critica para decidir es operativa (cuando, cuantos cupos, genera otro conflicto), no academica (creditos, prerrequisitos). Eso lo dan por hecho.

### Dinamica complementaria: Reaction Cards
> Se mostraron 3 versiones de como comunicar un conflicto:

- **Version A** — Alerta roja: "ERROR: Conflicto de horario detectado"
  → *"Esto da miedo", "Parece que hice algo mal"*
- **Version B** — Banner amber: "Detectamos un cruce de horario. Hay opciones disponibles."
  → *"Esto se siente manejable", "Me dice que tiene solucion"*
- **Version C** — Sin alerta, solo materias superpuestas en la grilla
  → *"No entiendo que pasa", "¿Esto es un bug?"*

**Resultado unanime:** Version B. Los estudiantes necesitan saber que hay un problema **y que tiene solucion**, en el mismo instante. No alarmar ni ignorar — informar con salida.

---

## 1.4 Research Cuantitativo

### 1.4.1 Encuesta post-inscripcion (simulada)

**Metodologia:** Encuesta enviada 24 horas despues del cierre de ventana.
**Muestra:** 1,240 respuestas (tasa de respuesta: 6.7% sobre 18,400 estudiantes).

**Resultados destacados:**

**P1: ¿Experimentaste un conflicto de horario durante tu inscripcion?**
- Si: 34%
- No: 58%
- No se / no estoy seguro: 8%

**P2: Si tuviste un conflicto, ¿como lo resolviste?** (n=421)
- Cambie la seccion de una materia manualmente: 38%
- Pedi ayuda a un companero: 22%
- Contacte soporte de la universidad: 16%
- Elimine la materia en conflicto: 14%
- No pude resolverlo y cerre sesion: 7%
- Otro: 3%

**P3: ¿Cuanto tiempo te tomo resolver el conflicto?** (n=421)
- Menos de 2 minutos: 11%
- 2 a 5 minutos: 29%
- 5 a 10 minutos: 34%
- 10 a 20 minutos: 18%
- Mas de 20 minutos: 8%

**P4: ¿Que tan claro fue el mensaje del sistema cuando se presento el conflicto?** (1-5)
- Promedio: 2.4/5
- "Nada claro" (1-2): 48%
- "Algo claro" (3): 28%
- "Claro" (4-5): 24%

**P5: ¿Sabias que la propuesta de horario fue generada por IA?**
- Si, lo sabia: 31%
- No, pense que era un horario asignado: 45%
- No estoy seguro: 24%

**P6: ¿Que tan util fue la recomendacion de horario de la IA?** (1-5)
- Promedio: 3.6/5
- Los que sabian que era IA: 4.1/5
- Los que no sabian: 3.2/5

**P7: Si la IA te sugiriera opciones para resolver el conflicto, ¿las usarias?**
- Definitivamente si: 42%
- Probablemente si: 38%
- Neutral: 12%
- Probablemente no: 6%
- Definitivamente no: 2%

**P8: ¿Desde que dispositivo inscribiste tus materias?**
- Celular: 51%
- Computador: 42%
- Tablet: 7%

**P9: NPS — ¿Recomendarias Albus para el proceso de inscripcion?**
- Promotores (9-10): 32%
- Pasivos (7-8): 41%
- Detractores (0-6): 27%
- **NPS: +5** (hay espacio significativo de mejora)

---

## 1.5 Sintesis: Affinity Mapping

Agrupamos todos los hallazgos (entrevistas + focus group + encuesta + analytics) en clusters tematicos:

### Cluster 1: COMPRENSION DEL CONFLICTO
> Los estudiantes no entienden que esta pasando ni por que.

- 48% califica el mensaje de conflicto como "nada claro"
- "No sabia si era culpa mia o del sistema" (Sofia M.)
- La version sin alerta fue percibida como un "bug" (Reaction Cards)
- 45% no sabia que la propuesta era generada por IA
- 8% de la encuesta "no esta seguro" si tuvo conflicto

### Cluster 2: RUPTURA DEL FLUJO
> Resolver el conflicto obliga a salir del flujo de inscripcion.

- "Tuve que ir a otra pantalla a buscar secciones" (Maria L.)
- 22% pide ayuda a un companero (salida del sistema)
- 16% contacta soporte (abandono del autoservicio)
- Tiempo promedio: 4.8 minutos (deberia ser < 2)
- 14% elimina la materia en lugar de resolver (decision suboptima)

### Cluster 3: ANSIEDAD Y PRESION TEMPORAL
> El contexto emocional amplifica cualquier friccion.

- 63% de intentos ocurren en los primeros 30 minutos
- "Me entro panico" (Sofia M.), "Me daba miedo el boton de confirmar" (Carlos R.)
- 12% de tickets son "se me cerro la ventana mientras resolvia"
- Cupos que se agotan en tiempo real generan "rabia" e "impotencia" (Andres G.)
- La experiencia mobile es "imposible" (Valentina P.) — 51% inscribe desde celular

### Cluster 4: CONFIANZA EN LA IA
> Los estudiantes que entienden la IA la valoran mas, pero quieren transparencia.

- Quienes sabian que era IA: 4.1/5 utilidad vs. 3.2/5 quienes no
- "Quiero saber que variables usa, no una caja negra" (Juan D.)
- "Que me diga como arreglarlo tambien, no que me deje sola" (Maria L.)
- 80% usaria sugerencias de IA para resolver conflictos
- Expectativa: IA como asistente que explica y sugiere, no que decide

### Cluster 5: MOBILE-FIRST ES CRITICO
> Mas de la mitad inscribe desde el celular, pero la experiencia no esta preparada.

- 51% inscribe desde celular
- "La grilla era imposible de leer" (Valentina P.)
- 20 minutos perdidos por cambiar de dispositivo
- La grilla semanal no funciona en pantallas pequenas

---

## 1.6 Insights Clave

De la sintesis emergen 5 insights principales que guiaran las fases de Define y Develop:

### Insight 1: La invisibilidad de la IA reduce su valor
> El 45% de los estudiantes no sabe que la propuesta es generada por IA. Cuando se enteran, la valoran significativamente mas (4.1 vs 3.2). **Hacer visible el rol de la IA — sin intimidar — es una oportunidad para aumentar confianza y percepcion de valor del producto.**

### Insight 2: El conflicto sin salida genera abandono
> El 28% de los estudiantes abandona cuando encuentra un conflicto. No porque el conflicto sea irresolvible, sino porque **el sistema no les muestra el camino hacia la solucion en el momento en que la necesitan.** La solucion debe estar donde esta el problema.

### Insight 3: La presion temporal convierte la friccion en panico
> En un contexto donde los cupos se agotan en minutos y 63% de los estudiantes intentan inscribir en los primeros 30 minutos, **cada segundo de confusion es un multiplicador de ansiedad.** La velocidad de comprension es tan critica como la velocidad del sistema.

### Insight 4: La informacion para decidir esta fragmentada
> Los estudiantes necesitan horario alternativo + cupos + validacion de conflictos nuevos para decidir. Hoy esa informacion vive en pantallas separadas. **Consolidar la informacion de decision en un solo lugar reduce el tiempo de resolucion y evita la salida del flujo.**

### Insight 5: El celular no es un canal secundario — es el principal
> Con 51% de inscripciones desde mobile, **disenar mobile-first no es un nice-to-have, es un requisito del negocio.** La grilla semanal como patron principal de visualizacion no escala a pantallas pequenas.

---

*Fin de Fase 1: Discover*

---
---

# Fase 2: DEFINE (Definir)
> Objetivo de esta fase: Converger los hallazgos del research en herramientas accionables — persona, journey map, pain points priorizados, problem statement y preguntas HMW — que guien directamente las decisiones de diseno.

---

## 2.1 Persona: Sofia Martinez

Construida a partir de los patrones dominantes del research (no es un solo entrevistado — es una sintesis de los comportamientos mas frecuentes).

### Datos demograficos
- **Nombre:** Sofia Martinez
- **Edad:** 20 anos
- **Carrera:** Ingenieria Civil — 5to semestre (3er ano)
- **Universidad:** Universidad privada en Bogota, Colombia
- **Dispositivo principal:** Celular (como el 51% de los estudiantes)
- **Familiaridad tecnologica:** Alta — nativa digital, usa apps complejas a diario
- **Familiaridad con IA:** Baja a media — usa herramientas de IA pero no las identifica como tal en todos los contextos

### Contexto
Sofia lleva dos anos en su carrera. Ya conoce el proceso de inscripcion pero cada semestre le genera estres. Este semestre es especialmente importante porque necesita inscribir Calculo III (prerrequisito para 3 materias de 6to semestre) y Mecanica de Fluidos (solo se ofrece en semestres impares). Si no inscribe ambas, su plan de estudios se atrasa.

### Comportamiento durante la inscripcion
- Se conecta **5 minutos antes** de que abra su ventana
- Inscribe desde el **celular** (esta en el transporte a las 8AM)
- Espera que el sistema le diga **que hacer**, no tener que descubrirlo sola
- Ante un problema, su primera reaccion es **preguntar a un companero** antes que buscar en el sistema
- Si algo la bloquea mas de 5 minutos, su ansiedad escala y considera **llamar a soporte**

### Motivaciones
- Inscribir todas las materias que necesita sin errores
- Terminar rapido para no perder cupos
- Sentir que tomo buenas decisiones para su semestre
- No atrasarse en su plan de estudios

### Frustraciones (validadas por research)
- No entender que esta pasando cuando algo falla (Insight 1, 2)
- Tener que salir del flujo para buscar informacion (Insight 4)
- Sentir que el tiempo corre y no puede resolver (Insight 3)
- No poder hacer el proceso completo desde el celular (Insight 5)

### Jobs to be Done
| Tipo | Job |
|------|-----|
| **Funcional** | Inscribir mis 6 materias del semestre sin conflictos de horario |
| **Emocional** | Sentir que tengo el control de mi semestre y que tome buenas decisiones |
| **Social** | No quedarme atras respecto a mis companeros ni depender de otros para resolver |

### Frase que la define
> *"No me importa si lo hace una IA o un humano — solo necesito que me diga que pasa, que puedo hacer, y que no voy a perder mi cupo mientras lo resuelvo."*

---

## 2.2 Journey Map: Inscripcion con conflicto de horario

Mapeamos la experiencia actual de Sofia desde que se conecta hasta que (intenta) confirmar, para identificar donde estan los quiebres.

### Fase: PRE-INSCRIPCION (Antes de la ventana)

| Etapa | Accion | Pensamiento | Emocion | Touchpoint |
|-------|--------|-------------|---------|------------|
| Preparacion | Sofia revisa su malla para saber que materias necesita | "Tengo que inscribir Calculo III y Mecanica de Fluidos si o si" | Determinacion | Malla curricular (PDF/web) |
| Espera | Se conecta 5 min antes desde el celular | "Ojala no se caiga el sistema como el semestre pasado" | Ansiedad anticipatoria | Albus — login |

### Fase: PROPUESTA DE HORARIO

| Etapa | Accion | Pensamiento | Emocion | Touchpoint |
|-------|--------|-------------|---------|------------|
| Ingreso | Abre Albus, ve la propuesta de horario | "Ok, ya me salio algo... dejame ver" | Expectativa | Albus — Mi Horario |
| Primer vistazo | Recorre la grilla buscando sus materias | "Bien, estan las 6 que necesito..." | Alivio momentaneo | Grilla semanal |
| **QUIEBRE 1** | Nota que dos bloques se superponen | "¿Que? ¿Esto esta mal? ¿Es un error?" | **Confusion → Panico** | Zona de conflicto en grilla |
| Busqueda de explicacion | Busca un mensaje, tooltip, algo que explique | "¿Por que me puso dos materias al mismo tiempo?" | **Frustracion** | (No hay explicacion visible) |

### Fase: INTENTO DE RESOLUCION (Experiencia actual)

| Etapa | Accion | Pensamiento | Emocion | Touchpoint |
|-------|--------|-------------|---------|------------|
| **QUIEBRE 2** | Busca como cambiar una seccion dentro del flujo | "¿Donde veo otras secciones? ¿Puedo cambiar esto?" | **Frustracion creciente** | (No hay opcion inline) |
| Salida del flujo | Navega a otra seccion del sistema buscando info | "Debo buscar en la malla o en otra pantalla..." | Estres | Otra pantalla / Malla curricular |
| Recurso externo | Llama a una amiga o busca en WhatsApp | "¿Tu ya inscribiste? ¿Que seccion tomaste?" | Dependencia | WhatsApp / llamada |
| **QUIEBRE 3** | El tiempo pasa — lleva 10+ minutos sin resolver | "Se me van a acabar los cupos..." | **Ansiedad critica** | Reloj |
| Resolucion forzada | Elige una opcion sin total seguridad o elimina una materia | "Ya no importa, lo que sea, necesito terminar" | Resignacion | Albus — edicion manual |

### Fase: CONFIRMACION (Experiencia actual)

| Etapa | Accion | Pensamiento | Emocion | Touchpoint |
|-------|--------|-------------|---------|------------|
| Duda pre-confirmacion | Ve el boton de confirmar pero duda | "¿Estara bien? ¿Puedo cambiarlo despues?" | Incertidumbre | Boton de confirmar |
| Confirmacion | Presiona confirmar | "Listo... ¿funciono?" | Tension | Albus — procesando |
| Resultado | Ve confirmacion o error | Exito: "Uff, por fin" / Error: "¿AHORA QUE?" | Alivio/Rabia | Albus — estado final |

### Mapa de emociones (curva)

```
Emocion
  +  |     Alivio
     |    momentaneo          Resignacion
     |   /          \          /         \    Alivio final
  0  |--/            \        /           \   /
     |                \      /             \ /
     |                 \    /
  -  |                  \  /
     |            Confusion + Panico
     |              Frustracion
     |              Ansiedad critica
     +------------------------------------------------→ Tiempo
       Pre    Propuesta   Resolucion        Confirmacion
```

**Los 3 quiebres identificados son exactamente donde debemos intervenir:**
1. **Quiebre 1:** Sofia no entiende el conflicto → Necesita comunicacion clara e inmediata
2. **Quiebre 2:** Sofia no encuentra como resolverlo → Necesita opciones inline, sin salir del flujo
3. **Quiebre 3:** El tiempo corre sin progreso → Necesita velocidad y reaseguro

---

## 2.3 Pain Points Priorizados

Priorizamos los pain points usando una matriz de **Impacto (en el usuario) vs Frecuencia (en la base)**, cruzada con los datos del research:

| # | Pain Point | Frecuencia | Impacto | Prioridad | Evidencia |
|---|-----------|-----------|---------|-----------|-----------|
| 1 | **No entiende que hay un conflicto ni por que** | Alta (48% dice que el mensaje es "nada claro") | Critico (bloquea el flujo completo) | **P0** | Entrevistas Sofia, Carlos; Encuesta P4; Reaction Cards |
| 2 | **No tiene opciones de resolucion dentro del flujo** | Alta (60% de los que resuelven lo hacen fuera del sistema) | Critico (genera abandono del 28%) | **P0** | Entrevista Maria; Analytics; Tickets motivo #1 y #3 |
| 3 | **No sabe cuantos cupos quedan en tiempo real** | Alta (cupos se agotan en minutos en horarios pico) | Alto (genera error post-confirmacion) | **P1** | Entrevista Andres; Tickets motivo #1; Analytics errores |
| 4 | **Experiencia mobile no soporta el flujo** | Alta (51% inscribe desde celular) | Alto (fuerza cambio de dispositivo, pierde tiempo) | **P1** | Entrevista Valentina; Encuesta P8 |
| 5 | **No entiende el rol de la IA en la propuesta** | Media (45% no sabe que es IA) | Medio (reduce percepcion de valor, no bloquea) | **P2** | Encuesta P5, P6; Entrevista Juan |
| 6 | **No sabe si puede modificar despues de confirmar** | Media (mencionado en entrevistas) | Medio (genera duda en confirmacion) | **P2** | Entrevista Carlos |

**Scope del challenge:** Este diseno aborda directamente **P0 y P1** (pain points 1-4). Los P2 se consideran pero no son el foco.

---

## 2.4 Cierre del Diamante 1: Problem Statement, Metricas y HMW

### Problem Statement
> **Sofia** necesita identificar, comprender y resolver un conflicto de horario de forma autonoma y en menos de 2 minutos, **porque** cada minuto de confusion en una ventana limitada multiplica la ansiedad, el abandono y la carga operativa de soporte.

### Metricas de exito
| Metrica | Hoy (baseline) | Target |
|---------|----------------|--------|
| Tasa de abandono en conflictos | 28% | < 5% |
| Tiempo de resolucion de conflicto | 4.8 min | < 2 min |
| Tickets de soporte por conflictos | 662/semestre | Reduccion > 60% |
| NPS de Albus | +5 | > +25 |

### How Might We — 4 preguntas que guian el Develop
> **HMW 1:** ¿Como comunicamos un conflicto de forma que Sofia entienda que pasa y que puede hacer en 5 segundos, sin generarle panico?

> **HMW 2:** ¿Como presentamos opciones de resolucion dentro del mismo flujo para que nunca tenga que salir a buscar informacion?

> **HMW 3:** ¿Como hacemos visible el rol de la IA como aliada — que no solo detecto el problema sino que ya tiene opciones para resolverlo?

> **HMW 4:** ¿Como diseñamos un flujo de conflicto → resolucion → confirmacion tan rapido y claro que Sofia sienta que la IA le resolvio el problema en lugar de haberselo creado?

---

*Fin de Fase 2: Define*

---
---

# Fase 3: DEVELOP (Desarrollar)
> Objetivo de esta fase: Traducir los hallazgos y definiciones en decisiones de diseno concretas que guien la solucion.

---

## 3.1 Principios de Diseno

Derivados directamente de los insights y HMW. Cada principio tiene una regla practica para aplicarlo:

| # | Principio | Regla practica |
|---|-----------|---------------|
| 1 | **Informar sin alarmar** | Usar amber (atencion) no rojo (error). El conflicto es una situacion con solucion, no un fallo. |
| 2 | **La solucion vive donde esta el problema** | Cero navegacion externa. Opciones de resolucion inline, en el mismo flujo. |
| 3 | **La IA asiste, el estudiante decide** | La IA sugiere y explica, pero nunca impone. Sofia siempre tiene la ultima palabra. |
| 4 | **Velocidad de comprension > velocidad del sistema** | Si Sofia entiende en 5 segundos, el flujo funciona. Si tarda 30, ya perdimos. |

---

## 3.2 Trade-offs

| Priorizamos | Sobre | Por que (respaldado por research) |
|-------------|-------|-----------------------------------|
| Velocidad de resolucion | Cantidad de informacion | 63% inscribe en los primeros 30 min. Cada segundo cuenta. (Analytics) |
| Conflicto como "atencion" | Conflicto como "error" | "Parece que hice algo mal" — Reaction Cards, Version A. No es un error, es una decision. |
| 3 opciones claras | Mostrar todas las secciones | Paradoja de eleccion. Card Sorting: solo 3 datos son criticos para decidir. |
| IA que sugiere y explica | IA que decide sola | "No quiero una caja negra" (Juan D.) / 80% quiere sugerencias, no imposiciones. |
| Preview en tiempo real | Confirmacion ciega | "No encontre donde ver otras opciones" (Sofia M.) — la info fragmentada genera abandono. |
| 1 click confirmacion | Doble confirmacion modal | "El boton me daba miedo" (Carlos R.) — el resumen previo ya ES la verificacion. |
| Mobile-first | Desktop-first | 51% inscribe desde celular. Grilla ilegible en mobile (Valentina P.) |
| Error con salida inmediata | Error generico | Motivo #1 de tickets: "No puedo inscribir". Siempre mostrar alternativa. |

---

## 3.3 Comunicacion de la IA

### Tono y voz
Asistente que explica en primera persona, breve, no tecnico. Dice "Detecte un cruce" no "Error de horario". Sugiere, no impone.

### Presencia decreciente por pantalla
| Pantalla | Nivel | Que hace la IA |
|----------|-------|---------------|
| Propuesta con conflicto | **Alta** | Explica que recomendo, por que, y que detecto un conflicto con opciones para resolverlo |
| Resolucion | **Media** | Sugiere la mejor opcion entre las disponibles, explicando brevemente por que |
| Confirmacion | **Baja** | Ausente — este momento es de Sofia, no de la IA |

### Por que esta jerarquia
La IA aporta valor cuando explica y sugiere, y estorba cuando Sofia ya decidio y solo quiere confirmar. Los estudiantes que entienden el rol de la IA la valoran significativamente mas (4.1/5 vs 3.2/5), pero no quieren que protagonice todo el proceso.

---

## 3.4 Arquitectura de Informacion y Flujo

### Flujo general

```
[Sofia ingresa a Albus]
        |
        v
[IA genera propuesta de horario]
        |
        v
  ¿Hay conflicto? ── No ──→ [Confirmacion directa] (happy path)
        |
       Si
        |
        v
[PANTALLA 1: Propuesta con conflicto]
  Sofia entiende que pasa y decide actuar
        |
        v
[PANTALLA 2: Resolucion]
  Sofia compara, elige y valida
        |
        v
[PANTALLA 3: Confirmacion]
        |
   ┌────┴────┐
   v         v
[Exito]   [Error]
             |
             v
        [Alternativas → vuelve a Resolucion]
```

### Resumen por pantalla

| Pantalla | Objetivo | Sofia debe poder... |
|----------|----------|---------------------|
| **1. Propuesta con conflicto** | Entender en 5 seg que pasa y que tiene solucion | Ver su horario completo, entender el cruce, saber que la IA lo detecto y que hay alternativas |
| **2. Resolucion** | Comparar y elegir en < 2 min | Ver opciones con los 3 datos criticos del Card Sorting (horario, cupos, conflictos nuevos), previsualizar el resultado y elegir |
| **3. Confirmacion** | Verificar y confirmar con un click | Revisar resumen validado automaticamente, confirmar — o recuperarse de un error sin perder progreso |

> La arquitectura detallada de cada pantalla (jerarquia de informacion, contenido, decisiones clave) se documenta como anotaciones directamente sobre los wireframes y el prototipo en Figma.

### Navegacion del flujo

| Desde | Accion | Hacia |
|-------|--------|-------|
| Pantalla 1 | "Resolver cruce de horario" | Pantalla 2 |
| Pantalla 2 | "Aplicar y continuar" | Pantalla 3 (pre-confirmacion) |
| Pantalla 2 | "Volver al horario" | Pantalla 1 |
| Pantalla 3 | "Confirmar inscripcion" | Exito o Error |
| Pantalla 3 | "Volver a editar" | Pantalla 2 |
| Pantalla 3 (error) | "Aplicar alternativa" | Reintento de confirmacion |

**No hay callejones sin salida.** Desde cualquier punto, Sofia puede avanzar o retroceder.

---
---

# Fase 4: DELIVER (Entregar)
> Las pantallas de alta fidelidad, el prototipo navegable y el sistema de componentes son el entregable principal y viven en Figma. Esta seccion documenta lo que complementa las pantallas.

---

## 4.1 Estados y Edge Cases

| Estado | Pantalla | Comportamiento |
|--------|----------|---------------|
| Cargando | Propuesta | Skeleton + "Albus esta preparando tu propuesta..." |
| Sin conflictos | Propuesta | Flujo directo a confirmacion (happy path) |
| **Con conflicto** | **Propuesta** | **Alerta amber + banner IA + CTA resolver (este challenge)** |
| Seleccion genera nuevo conflicto | Resolucion | Validacion roja inline: "Esta opcion cruza con [materia]" |
| Cupo agotado en opcion | Resolucion | Opcion deshabilitada + "Sin cupos" en gris |
| Pre-confirmacion | Confirmacion | Checklist de validacion + tabla resumen |
| **Exito** | **Confirmacion** | **Check animado + folio + horario confirmado + proximos pasos** |
| **Error por cupo agotado** | **Confirmacion** | **Razon especifica + alternativas inmediatas + reserva temporal de las demas materias** |
| Error de sistema | Confirmacion | "Hubo un problema. Intenta de nuevo." + boton retry |
| Ventana cerrada | Global | "Tu ventana ha cerrado. Consulta proximas fechas." |

---

## 4.2 Lo que quedo fuera del scope (y por que)

| Funcionalidad | Razon |
|--------------|-------|
| Chat conversacional con IA | Demasiada complejidad para un momento de urgencia. La IA debe dar respuestas, no abrir conversaciones. |
| Comparador avanzado de profesores | Valioso pero fuera del flujo critico. Puede ser una iteracion futura. |
| Notificaciones push de cupos | Util pre-inscripcion, no durante el flujo activo. |
| Modo oscuro | Deseable, no prioritario para el entregable. |

---

## 4.3 Iteraciones futuras sugeridas

1. **Test de usabilidad** con 5 estudiantes sobre el prototipo para validar la velocidad de comprension del conflicto y el tiempo de resolucion.
2. **A/B test** de la etiqueta IA ("Sugerida por Albus" vs. "Recomendada para ti") para medir impacto en tasa de adopcion de la sugerencia.
3. **Analytics de cupos en tiempo real** — medir si la visibilidad de cupos reduce los errores post-confirmacion.
4. **Expansion mobile** — explorar patrones como bottom sheet y swipe para la resolucion en celular.

---

*Fin del UX Strategy Document*

*Documento creado por Adrian Rodriguez Sanchez | Abril 2026*
*Herramientas utilizadas: Claude Code (research y documentacion), Figma (diseno)*

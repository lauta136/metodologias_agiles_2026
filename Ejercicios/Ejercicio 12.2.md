# Enunciado

## Ejercicio Integrador: Aplicación de la Metodología Lean con Odoo Project

## 🌟 Objetivo General
Aplicar los principios de *Lean Development* en un entorno simulado de una empresa de desarrollo de software, utilizando *Odoo Project* para modelar, gestionar y optimizar el flujo de trabajo de los proyectos.

---

## 📚 Contexto del Caso
Forman parte del equipo de una empresa ficticia llamada **LeanDev**, especializada en el desarrollo de soluciones de software para pymes. La empresa ha decidido reorganizar su sistema de gestión de proyectos para maximizar el valor entregado y minimizar desperdicios.

---

## 🛠️ Herramienta a Utilizar
**Odoo Project**

Los alumnos deberán:
- Configurar el proyecto.
- Crear tareas y flujos de trabajo Kanban.
- Establecer límites de trabajo en curso (WIP limits).
- Usar etiquetas y prioridades.
- Documentar bloqueos, mejoras y retrospectivas.

---

## 🔍 Guía de Trabajo y Consignas

### 🧩 Parte 1: Diagnóstico Inicial del Proceso
- Analizar el flujo de trabajo propuesto.
- Detectar 5 tipos de desperdicio (espera, sobreproducción, retrabajo, etc.).
- Registrar el diagnóstico como tarea en Odoo.

### 🧩 Parte 2: Propuesta de Valor y Definición de Etapas
- Definir el **Producto Mínimo Viable (MVP)** de un proyecto dado.
- Establecer el flujo de valor y reflejarlo en el Kanban de Odoo.
- Aplicar WIP limits justificados.

### 🧩 Parte 3: Priorización y Visualización
- Organizar backlog con etiquetas (*feature*, *bug*, *improvement*, etc.).
- Simular reuniones diarias (registrando avances y bloqueos en Odoo).

### 🧩 Parte 4: Mejora Continua
- Identificar un cuello de botella.
- Proponer una mejora usando el ciclo **PDCA (Plan-Do-Check-Act)**.
- Documentar la retrospectiva.

---

# 🧩 Casos de Uso Lean para resolver en Odoo
Cada equipo deberá resolver los siguientes **casos prácticos** aplicando *principios Lean* y usando *Odoo Project* como herramienta de gestión.

## 🏢 Caso 1: Retrabajo constante en entregas
Un cliente informa que recibe funcionalidades que no pidió o que no se ajustan a sus necesidades.

**Tareas:**
- Crear una tarea "Detectar origen del retrabajo".
- Implementar una mejora en el flujo que garantice la validación temprana de requisitos.
- Agregar una etapa "Revisión de Requisitos" en el flujo Kanban.
- Limitar el WIP en validaciones.

## 🏢 Caso 2: Bloqueo en testing por sobrecarga
Múltiples tareas esperan validación en Testing, sin suficiente capacidad.

**Tareas:**
- Detectar cuello de botella.
- Redefinir WIP limit en "Testing".
- Crear política de "No nuevas tareas si Testing está lleno".
- Documentar impacto esperado.

## 🏢 Caso 3: Bugs recurrentes post-producción
Muchos errores son detectados después de la liberación.

**Tareas:**
- Implementar revisiones entre pares.
- Crear tareas de "Tests automatizados básicos".
- Etiquetar como *prevención de errores*.

## 🏢 Caso 4: Features no utilizadas por el cliente
El cliente no utiliza varias funcionalidades entregadas.

**Tareas:**
- Identificar funcionalidades no usadas.
- Planificar entregas incrementales.
- Crear tareas "Demo con cliente" antes de cerrar features.

## 🏢 Caso 5: Saturación del equipo senior
Programadores seniors saturados; juniors ociosos.

**Tareas:**
- Balancear la asignación de tareas.
- Crear tareas "Mentoría rápida".
- Planificar sesiones de apoyo.

---

## 📄 Entregables
- Capturas del tablero y tareas en Odoo.
- Documento resumen:
  - Desperdicios detectados.
  - Prácticas Lean aplicadas.
  - Resultados observados.

---

## ✅ Criterios de Evaluación
- Aplicación de principios Lean.
- Correcto uso de Odoo Project.
- Calidad y claridad de la documentación.
- Participación activa del equipo.

---
# Resolucion

## Parte 1: Diagnóstico Inicial del Proceso

**Flujo de trabajo original:** Backlog → Desarrollo → Testing → Deploy

### Desperdicios Lean detectados

| # | Desperdicio | Descripción |
|---|---|---|
| 1 | Espera | Acumulación de tareas en Testing por falta de capacidad de validación (Caso 2) |
| 2 | Sobreproducción | Desarrollo de features sin validación previa con el cliente (Caso 4) |
| 3 | Retrabajo | Requisitos mal levantados que obligan a reprogramar funcionalidades (Caso 1) |
| 4 | Defectos / Corrección | Bugs detectados recién en producción por falta de revisión de pares y tests automáticos (Caso 3) |
| 5 | Talento desaprovechado | Desbalance de carga entre seniors saturados y juniors ociosos (Caso 5) |

<img width="1470" height="798" alt="Screenshot 2026-07-14 at 10 20 03 AM" src="https://github.com/user-attachments/assets/8cb3389b-1b5c-4311-ad91-0756efc7c4e1" />

## Parte 2: Propuesta de Valor y Definición de Etapas

### MVP (Producto Mínimo Viable)

**Incluido:**
- Alta y edición de pacientes
- Agenda de turnos (crear, reprogramar, cancelar)
- Vista de agenda diaria/semanal

**Fuera del MVP:**
- Notificaciones automáticas
- Reportes y estadísticas
- Portal de autogestión del paciente
- Historia clínica integrada

**Captura — Tarea "Definición de MVP":**
<img width="1470" height="797" alt="Screenshot 2026-07-14 at 10 25 23 AM" src="https://github.com/user-attachments/assets/7d55549e-d350-4477-a689-f7db3835d436" />

### Flujo de valor y WIP Limits

*Nota: Odoo Project no cuenta con un campo nativo de WIP limit por etapa. El límite se incorporó en el nombre de cada columna y se documenta su justificación a continuación.*

| Etapa | WIP limit | Justificación |
|---|---|---|
| Backlog | — | Reservorio de tareas, sin restricción |
| Revisión de Requisitos | 3 | Solo el PM/analista revisa requisitos; más de 3 atrasa el resto del flujo |
| Desarrollo | 4 | Cantidad de desarrolladores disponibles trabajando en paralelo |
| Testing | 2 | Un único recurso de QA; más de 2 tareas generan cuello de botella |
| Demo Cliente | 2 | El cliente tiene disponibilidad limitada para reuniones de validación |
| Hecho | — | Reservorio de tareas cerradas, sin restricción |

<img width="1468" height="797" alt="Screenshot 2026-07-14 at 10 31 56 AM" src="https://github.com/user-attachments/assets/37d519ad-9447-445a-8421-6149e5ffcad1" />
<img width="712" height="288" alt="Screenshot 2026-07-14 at 10 32 30 AM" src="https://github.com/user-attachments/assets/0080382a-a3ed-40ba-88e9-336dd5291ef6" />


## Parte 3: Priorización y Visualización

### Etiquetas creadas
`feature` · `bug` · `improvement` · `prevención de errores`

### Backlog cargado

| Tarea | Etiqueta | Prioridad |
|---|---|---|
| Detectar origen del retrabajo | bug | Urgente |
| Agregar validación temprana de requisitos al flujo | improvement | Alta |
| Redefinir WIP limit en Testing | improvement | Urgente |
| Crear política "no nuevas tareas si Testing está lleno" | improvement | Media |
| Documentar impacto esperado del cambio en Testing | improvement | Media |
| Implementar revisiones entre pares (code review) | prevención de errores | Alta |
| Crear tests automatizados básicos | prevención de errores | Alta |
| Identificar funcionalidades no usadas por el cliente | bug | Media |
| Planificar entregas incrementales | improvement | Media |
| Crear tarea "Demo con cliente" antes de cerrar features | feature | Media |
| Balancear asignación de tareas seniors/juniors | improvement | Alta |
| Crear sesiones de mentoría rápida | improvement | Media |

**Captura — Backlog con etiquetas y prioridades visibles:**

<img width="1469" height="800" alt="Screenshot 2026-07-14 at 10 48 55 AM" src="https://github.com/user-attachments/assets/95ed6066-9fe2-4eac-bda8-b96edd809c59" />

<img width="1470" height="798" alt="Screenshot 2026-07-14 at 10 58 09 AM" src="https://github.com/user-attachments/assets/11974ffc-fb36-40cb-9ab8-1e51fc58f7bc" />
<img width="1470" height="798" alt="Screenshot 2026-07-14 at 11 24 28 AM" src="https://github.com/user-attachments/assets/99419e71-391a-4d4d-82b5-336d4552c71e" />
<img width="1470" height="798" alt="Screenshot 2026-07-14 at 11 00 35 AM" src="https://github.com/user-attachments/assets/b01ba2e1-3de0-481d-9653-979c0333d5bf" />

## Parte 4: Mejora Continua

### Cuello de botella identificado
Crear los tests automatizados es el cuello de botella:
* WIP limit más bajo del tablero (2).
* La Tarea 3 ("Crear tests automatizados básicos") quedó trabada ahí esperando validación del cliente.
* Es el Caso 2 del enunciado (sobrecarga de testing).

<img width="1470" height="801" alt="Screenshot 2026-07-14 at 11 08 04 AM" src="https://github.com/user-attachments/assets/4f4714d2-8ab6-4ef3-adc2-a44b8708799b" />

Descripcion completa de la tarea:
PDCA - Cuello de botella en Testing

PLAN:
Se detecta que Testing es el cuello de botella del flujo: WIP limit más bajo 
(2), un solo recurso de QA, y tareas que quedan trabadas esperando validación 
(ver Tarea "Crear tests automatizados básicos"). 
Propuesta: reducir la carga que llega a Testing incorporando revisión entre 
pares antes de que la tarea entre a esa etapa, y sumar tests automatizados 
básicos para los casos más repetitivos.

DO:
- Se agrega una checklist de "code review" obligatoria antes de mover una 
  tarea de Desarrollo a Testing.
- Se implementan tests automatizados para el módulo de agenda de turnos 
  (cubre los casos de uso más frecuentes).
- Se mantiene la política ya acordada: no ingresan nuevas tareas a Testing 
  si ya hay 2 en curso.

CHECK:
Se va a medir el tiempo promedio que una tarea permanece en la etapa Testing, 
comparando la semana previa a la mejora contra las 2 semanas posteriores. 
También se va a contar la cantidad de bugs detectados post-producción antes 
y después del cambio.

ACT:
Si el tiempo promedio en Testing baja y los bugs post-producción se reducen, 
la revisión entre pares y los tests automatizados se vuelven parte 
permanente del flujo estándar de LeanDev. Si no hay mejora significativa, 
se revisa si el problema es de proceso o de falta de recursos, y se evalúa 
sumar otro recurso de QA.

### Retrospectiva del Sprint

<img width="1467" height="800" alt="Screenshot 2026-07-14 at 11 09 17 AM" src="https://github.com/user-attachments/assets/25eb69ed-fe9f-4bd4-88fd-1d4e21cf9734" />

Descripcion de la tarea:
Retrospectiva - LeanDev

QUÉ FUNCIONÓ:
- Agregar la etapa "Revisión de Requisitos" evitó que se siga arrastrando 
  el problema de retrabajo por requisitos mal levantados.
- Documentar los bloqueos en el chatter de cada tarea permitió detectar 
  rápido que Testing era el cuello de botella real, no solo una percepción.
- Definir el WIP limit de Testing en el nombre de la etapa hizo visible 
  la restricción aunque Odoo no la bloquee automáticamente.

QUÉ NO FUNCIONÓ / A MEJORAR:
- El WIP limit no se aplica de forma automática en Odoo Project (no bloquea 
  el ingreso de nuevas tareas), depende de la disciplina del equipo respetar 
  la política acordada.
- Faltó anticipar el bloqueo de validación con el cliente antes de empezar 
  los tests automatizados; se podría agendar esa validación en paralelo al 
  desarrollo, no después.

PRÓXIMOS PASOS:
- Medir el impacto del PDCA aplicado a Testing durante las próximas 2 semanas.
- Evaluar si conviene sumar un segundo recurso de QA si el cuello de botella 
  persiste.

## Prácticas Lean aplicadas

Durante el desarrollo del proyecto se aplicaron las siguientes prácticas de Lean Development:

| Práctica Lean | Aplicación en el proyecto |
|---|---|
| Eliminación de desperdicios | Se identificaron esperas, sobreproducción, retrabajo, defectos y talento desaprovechado para proponer mejoras concretas. |
| Desarrollo basado en MVP | Se definió un Producto Mínimo Viable con las funcionalidades esenciales, evitando desarrollar características de bajo valor en una primera entrega. |
| Gestión visual (Kanban) | Se modeló el flujo de trabajo mediante un tablero Kanban con etapas claramente definidas para visualizar el estado de cada tarea. |
| Límites de trabajo en curso (WIP Limits) | Se establecieron límites por etapa para evitar la sobrecarga de trabajo y detectar cuellos de botella, especialmente en Testing. |
| Entregas incrementales | Se propuso validar funcionalidades mediante demos con el cliente antes de finalizar cada feature, reduciendo el riesgo de desarrollar funcionalidades innecesarias. |
| Validación temprana | Se incorporó la etapa "Revisión de Requisitos" para disminuir el retrabajo causado por requisitos incompletos o incorrectos. |
| Calidad incorporada | Se implementaron revisiones entre pares (Code Review) y tests automatizados básicos para prevenir defectos antes de producción. |
| Mejora continua (Kaizen) | Se aplicó el ciclo PDCA para analizar el cuello de botella en Testing, implementar mejoras y definir métricas para evaluar su impacto. |
| Comunicación continua | Se simularon reuniones diarias registrando avances y bloqueos en el chatter de Odoo para mantener la visibilidad del proyecto. |
| Optimización del flujo | Se estableció la política de no incorporar nuevas tareas a Testing cuando se alcanza el WIP definido, favoreciendo un flujo continuo de trabajo. |

### Conclusión

La aplicación de estas prácticas permitió reducir desperdicios, mejorar la visibilidad del proceso, priorizar el trabajo de mayor valor para el cliente y establecer una base para la mejora continua del proyecto mediante los principios de Lean Development.

## Resultados Observados (resumen general)

- La incorporación de la etapa "Revisión de Requisitos" atacó directamente el desperdicio de retrabajo (Caso 1).
- El WIP limit documentado en Testing, junto con la política de no ingreso de nuevas tareas, visibilizó el cuello de botella real del proceso (Caso 2).
- Las etiquetas y prioridades permitieron visualizar rápido qué tareas requerían atención inmediata (Urgente) frente a mejoras de proceso a mediano plazo (Media).
- El uso del chatter como bitácora de dailies dejó trazabilidad de los bloqueos, insumo clave para el PDCA y la retrospectiva.
- Quedan pendientes de medir los resultados concretos del PDCA en las próximas iteraciones del proyecto.

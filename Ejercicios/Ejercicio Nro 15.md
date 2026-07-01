# Ejercicio Nro: 15

## Enunciado
**Ejercicio 15: Generar un plan de trabajo basado en SCRUM para resolver la siguiente tarea.**

**Descripción del ejercicio:**
1. Formar equipos de trabajo (3 a 5 personas).
2. Temática: Construcción de galpones para sistema informático de presupuesto.
3. Generar al menos tres historias de usuario (título, descripción y criterios de aceptación).
4. Foco: Presupuestos detallados, seguimiento durante la construcción, inclusión de etapas, generación de informes.
5. Historias claras, concisas y comprensibles (Agile).
6. Presentar al resto de la clase.

## Resolución

Para resolver la creación del sistema de presupuesto de construcción de galpones, se establece el siguiente **Plan de Trabajo Scrum**:

### 1. Definición de Roles
*   **Product Owner (PO):** Responsable de priorizar el Backlog y asegurar que el sistema entregue valor al negocio de construcción.
*   **Scrum Master (SM):** Facilita las ceremonias, elimina impedimentos y actúa como coach de la metodología.
*   **Equipo de Desarrollo:** Equipo multifuncional (diseñadores, desarrolladores, QA) encargado de convertir los requisitos en incrementos de software funcional.

### 2. Product Backlog: Historias de Usuario
Siguiendo el formato *"Como [rol] quiero [acción] para [objetivo]"* y los criterios **INVEST** :

**Historia 1: Creación de Presupuesto Detallado**
*   **Descripción:** "Como Administrador de Obra, quiero ingresar los materiales y mano de obra necesarios para un galpón, para generar un presupuesto detallado al cliente".
*   **Criterios de Aceptación:** 
    *   El sistema debe permitir cargar ítems por categorías (Materiales, Mano de Obra, Maquinaria).
    *   El sistema debe calcular automáticamente el costo total más un margen de beneficio configurable.

**Historia 2: Seguimiento por Etapas de Obra**
*   **Descripción:** "Como Jefe de Proyecto, quiero asignar el presupuesto a diferentes etapas (Cimentación, Estructura, Techo), para realizar un seguimiento del gasto real frente al estimado".
*   **Criterios de Aceptación:**
    *   Cada etapa debe tener un presupuesto asignado.
    *   Se debe visualizar una barra de progreso que indique el porcentaje de consumo del presupuesto por etapa.

**Historia 3: Generación de Informe de Desvíos**
*   **Descripción:** "Como Gerente, quiero exportar un informe de gastos, para identificar desvíos financieros durante la construcción del galpón".
*   **Criterios de Aceptación:**
    *   El informe debe generarse en formato PDF o Excel.
    *   Debe resaltar en rojo los ítems que superen el presupuesto original en más de un 10%.

### 3. Planificación de Ciclos (Sprints)
*   **Duración:** Sprints de 2 semanas para permitir una entrega rápida de valor.
*   **Sprint Planning:** El equipo selecciona las historias de mayor prioridad del Backlog y las descompone en tareas técnicas (ej. "Diseñar base de datos de materiales").
*   **Definition of Done (DoD):** Para que una historia se considere terminada, debe estar codificada, probada sin errores y validada por el PO .

### 4. Eventos y Seguimiento
*   **Daily Scrum:** Reunión diaria de 15 minutos para inspeccionar el progreso hacia el Sprint Goal y detectar obstáculos.
*   **Sprint Review:** Al finalizar el Sprint, se realiza una demo del sistema de presupuesto a los Stakeholders para recibir feedback.
*   **Sprint Retrospective:** El equipo analiza qué funcionó bien y qué mejorar en el proceso de trabajo para el siguiente Sprint.
*   **Burndown Chart:** Se utiliza este gráfico visible para todo el equipo para rastrear el trabajo pendiente diariamente.

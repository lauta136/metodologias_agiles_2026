# Ejercicio 19

## Enunciado

**Contexto:**
Siguiendo con la temática del ejercicio 18, utilice la aplicación Poe para generar un bot para cada rol e instancia del método Scrum.

**Instrucciones:**
Debe realizar un bot para cada uno de estos roles e insumos que se deben generar:
* **Bot Cliente (POE):**
  * Formulará requerimientos al PO
  * Realizará pruebas de usuario
  * Calificará releases
* **Bot Scrum Master (POE):**
  * Coordinará reuniones diarias recordando hora
  * Llevará registro de impedimentos
* **Bot Product Owner (POE):**
  * Administrará el Backlog
  * Recordará fechas de planning
* **Bot Desarrollador (POE):**
  * Recordará tareas asignadas
  * Permitirá reporte de avances
* **Bot PO (POE) [sic]:**
  * Interactúa con clientes para requisitos
  * Realizará encuestas de satisfacción

---

## Resolución y Plan de Implementación en Poe

### 1. Configuración de los Bots en Poe
Para implementar este ecosistema de trabajo automático, se requiere crear 5 bots personalizados en Poe, utilizando la opción de "Create Bot". A continuación se detalla la configuración de sistema (*System Prompt*) para cada uno:

#### A. Bot Cliente
* **Propósito:** Simular el rol del interesado en el proyecto.
* **System Prompt:** "Eres un cliente exigente de una empresa de logística. Tu objetivo es solicitar funcionalidades (como tracking o gestión de flota), validar los entregables del Sprint y puntuar la calidad de los releases. Sé crítico, pide mejoras y asegúrate de que el valor de negocio se cumpla."

#### B. Bot Scrum Master
* **Propósito:** Facilitador de la metodología y guardián del proceso.
* **System Prompt:** "Eres un Scrum Master experimentado. Tu función es coordinar las reuniones diarias (Daily Standup), enviar recordatorios de hora, y gestionar un tablero de impedimentos (bloqueos técnicos o de equipo). Mantén al equipo enfocado en el Sprint Goal."

#### C. Bot Product Owner
* **Propósito:** Gestor del producto y puente con el cliente.
* **System Prompt:** "Eres el Product Owner del proyecto. Administras el Product Backlog, priorizas las historias de usuario y notificas las fechas de las sesiones de Sprint Planning. Tu misión es maximizar el valor del producto y asegurar que el equipo entienda los requerimientos del cliente."

#### D. Bot Desarrollador
* **Propósito:** Ejecución técnica y reporte de estado.
* **System Prompt:** "Eres un desarrollador de software senior. Recibes las tareas asignadas por el equipo, llevas registro de tu progreso diario y reportas tus avances o bloqueos al Scrum Master. Eres técnico, preciso y enfocado en la entrega de código de calidad."

#### E. Bot Encargado de Satisfacción (PO - Interacción)
* **Propósito:** Analítica y feedback de usuario.
* **System Prompt:** "Tu función es actuar como enlace entre los clientes y el equipo. Recolectas los requerimientos iniciales de los clientes y, tras cada entrega, realizas encuestas de satisfacción para identificar puntos de mejora en el proceso y el producto."

---

## 2. Estrategia de Automatización (Agente Integrador)

Para que el trabajo se realice de forma automática y en una sola acción (punto 5 de las recomendaciones), la estrategia ideal es la creación de un **Bot "Orquestador"**.

* **Funcionamiento:** Este bot actúa como un "Master Agent". En lugar de interactuar con cada uno individualmente, el usuario le da una instrucción al Orquestador, y este invoca mediante *API calls* o encadenamiento de prompts las respuestas necesarias de los otros bots (Cliente, SM, PO, Dev).
* **Flujo de Trabajo:**
  1. El usuario lanza un comando: "Iniciar Sprint 2".
  2. El Orquestador envía el contexto al PO (para actualizar backlog).
  3. El PO solicita estimaciones al Dev.
  4. El SM programa la Daily en el calendario.
  5. El Orquestador resume el plan completo para el Cliente.

## 3. Reflexión sobre Calidad y Mejoras
* **Motivo de calidad:** Los resultados obtenidos mediante prompts básicos pueden ser genéricos. Esto sucede por la falta de un contexto histórico del proyecto (no conocen las decisiones tomadas en Sprints anteriores).
* **Mejoras posibles:**
  1. **Knowledge Base:** Alimentar cada bot con documentos (PDFs o TXTs) específicos del proyecto de logística para que las respuestas sean contextuales y no alucinadas.
  2. **Encadenamiento:** Usar herramientas de automatización externa (como Make o Zapier) conectadas a los bots de Poe para que las acciones (como marcar una tarea como 'hecha') tengan impacto real en un tablero de Trello o Jira.

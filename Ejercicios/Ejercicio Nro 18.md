# Ejercicio 18

## Enunciado

**Contexto:**
Una empresa de desarrollo de software ha decidido adoptar la metodología Scrum para mejorar la eficiencia y velocidad en sus proyectos. Tu equipo ha sido seleccionado para liderar la implementación de Scrum en un nuevo proyecto de desarrollo de una aplicación web para una empresa de logística.

**Instrucciones:**
1. Construye una serie de prompts que simulen las diferentes etapas y actividades de Scrum en este proyecto.
2. Cada prompt debe tener una entrada que corresponda a la salida de otro prompt, formando una secuencia lógica de ejecución.

**Cada prompt debe:**
* Describir claramente la actividad Scrum a simular.
* Explicar la entrada y salida requeridas.
* Solicitar a los alumnos que generen o completen la información de cada etapa.

**Formato de entrega:**
* Crear un documento `.md` donde se describa:
  1. Cada uno de los 5 prompts desarrollados.
  2. Resultados de la aplicación de cada prompt.
  3. Técnicas utilizadas en cada prompt.
* Subir la resolución haciendo Pull Request al repositorio: `https://github.com/cursos-uai/metodologias_agiles_2026`

---

## Resolución

### 1. Product Backlog (Definición de Épicas e Historias de Usuario)

**Prompt Desarrollado:**
> "Actúa como un Product Owner experto en metodologías ágiles. Nuestra empresa está desarrollando una nueva aplicación web para una compañía de logística. La entrada inicial son los siguientes requerimientos del cliente: 'Necesitamos rastrear paquetes en tiempo real, gestionar la flota de vehículos y tener un portal de clientes'. 
> Genera como salida el Product Backlog definiendo 2 Épicas principales y 2 Historias de Usuario por cada épica utilizando el formato estándar ('Como [rol], quiero [acción] para [beneficio]')."

**Técnicas Utilizadas:**
* **Role Prompting:** Se le asigna a la IA el rol de "Product Owner experto".
* **Zero-Shot Prompting:** Se le pide generar el resultado sin ejemplos previos, basándose en su conocimiento de la estructura de un Product Backlog.

**Resultados de la Aplicación:**
* **Épica 1: Gestión de Envíos y Rastreo**
  * *Historia de Usuario 1.1:* Como cliente, quiero ver la ubicación de mi paquete en tiempo real en un mapa para saber exactamente cuándo llegará.
  * *Historia de Usuario 1.2:* Como despachador, quiero actualizar el estado del paquete escaneando un código de barras para mantener el sistema sincronizado.
* **Épica 2: Portal de Clientes y Flota**
  * *Historia de Usuario 2.1:* Como cliente, quiero iniciar sesión en mi portal privado para ver el historial de todos mis envíos.
  * *Historia de Usuario 2.2:* Como administrador de flota, quiero ver la disponibilidad de los vehículos para asignar rutas de manera eficiente.

### 2. Sprint Planning

**Prompt Desarrollado:**
> "Actúa como Scrum Master y equipo de desarrollo. Toma como **entrada** el siguiente Product Backlog generado en la etapa anterior:
> [Insertar Resultados del Prompt 1]
> 
> Tu tarea es simular la reunión de Sprint Planning y generar como **salida** un Sprint Backlog para un Sprint de 2 semanas. Selecciona solo las Historias 1.1 y 2.1. Estima el esfuerzo de cada una utilizando Story Points (sucesión de Fibonacci) y divide cada historia en al menos 2 tareas técnicas concretas."

**Técnicas Utilizadas:**
* **Chain of Thought / Context Feeding:** Se encadena la salida del Prompt 1 como entrada para el Prompt 2.
* **Constraints (Restricciones):** Se le limita a seleccionar historias específicas y a usar una escala de estimación concreta (Fibonacci).

**Resultados de la Aplicación:**
* **Sprint Goal:** Proveer a los clientes visibilidad básica de sus envíos y acceso al portal privado.
* **Sprint Backlog:**
  * **HU 1.1: Mapa en tiempo real (8 Story Points)**
    * Tarea 1: Integrar API de Google Maps en el frontend.
    * Tarea 2: Crear endpoint en el backend para emitir coordenadas del paquete.
  * **HU 2.1: Portal Privado (5 Story Points)**
    * Tarea 1: Diseñar pantalla de login y registro.
    * Tarea 2: Implementar autenticación JWT en la base de datos.

### 3. Daily Standup Meeting

**Prompt Desarrollado:**
> "Actúa como dos desarrolladores (Dev A y Dev B). La **entrada** es el Sprint Backlog actual (en el día 3 del Sprint):
> [Insertar Resultados del Prompt 2]
> 
> Genera como **salida** la simulación de una Daily Standup. Cada desarrollador debe responder a las 3 preguntas clásicas de Scrum: ¿Qué hice ayer?, ¿Qué haré hoy? y ¿Hay algún impedimento?. Dev A está trabajando en el Mapa y Dev B en el Portal Privado. Incluye un impedimento técnico para Dev A."

**Técnicas Utilizadas:**
* **Multi-Persona Prompting:** Se le pide a la IA que asuma dos voces y perspectivas distintas en la misma respuesta.
* **Instruction Prompting:** Instrucciones claras sobre la estructura de salida (las 3 preguntas de Scrum) y condiciones forzadas (crear un impedimento).

**Resultados de la Aplicación:**
* **Dev A (Frontend/Mapa):**
  * *Ayer:* Configuré la base del proyecto frontend y comencé a integrar la API de Google Maps.
  * *Hoy:* Seguiré con la renderización de los marcadores dinámicos de los vehículos.
  * *Impedimentos:* Sí, tengo un problema de cuota excedida con la key de desarrollo de la API de Maps, necesito que el Scrum Master me habilite la cuenta de producción.
* **Dev B (Backend/Portal):**
  * *Ayer:* Diseñé los esquemas de base de datos para los usuarios y la pantalla de login.
  * *Hoy:* Implementaré la lógica de validación del token JWT.
  * *Impedimentos:* Ninguno por ahora, avanzo a buen ritmo.

### 4. Sprint Review

**Prompt Desarrollado:**
> "Actúa como un cliente de la empresa de logística y el Product Owner. La **entrada** es el incremento de producto generado en este Sprint: 
> 'Se finalizó el Portal Privado y la visualización del mapa, pero el mapa tiene un delay de 5 minutos en la actualización'.
> 
> Genera como **salida** el diálogo de la Sprint Review. El PO debe presentar el incremento y el Cliente debe dar su feedback, aprobando el login pero solicitando una mejora urgente para el delay del mapa en el próximo Sprint."

**Técnicas Utilizadas:**
* **Scenario Simulation / Roleplay:** Se crea una situación ficticia donde los actores deben interactuar en base al contexto dado.
* **Context Setting:** Se establece un resultado de Sprint mixto (un éxito y un defecto parcial) para generar una interacción más realista.

**Resultados de la Aplicación:**
* **Product Owner:** "Bienvenidos a la Sprint Review. En estas dos semanas logramos habilitar el portal de clientes con autenticación segura y despleamo el mapa de seguimiento. Sin embargo, notarán que la actualización de ubicación actual tiene un retraso de 5 minutos debido a limitaciones del proveedor del GPS satelital. Les mostramos la demo..."
* **Cliente:** "El portal de inicio de sesión funciona perfecto, es muy rápido y claro. Lo apruebo. Respecto al mapa, entiendo la limitación, pero 5 minutos es mucho tiempo en logística urbana. Necesitamos que para el próximo mes ese delay baje a máximo 30 segundos. Por favor, agreguen esa mejora al tope del Backlog."

### 5. Sprint Retrospective

**Prompt Desarrollado:**
> "Actúa como el Scrum Master facilitando la reunión retrospectiva. La **entrada** es el desarrollo del Sprint 1 completo (impedimento de API de Maps resuelto tarde, buen ritmo en backend, feedback de cliente sobre el delay).
> 
> Genera como **salida** un documento de Retrospectiva en formato de viñetas respondiendo a: 1. ¿Qué hicimos bien?, 2. ¿Qué hicimos mal/qué podemos mejorar?, y 3. Un plan de acción con 1 tarea concreta para el siguiente Sprint."

**Técnicas Utilizadas:**
* **Summarization y Reflection:** Se fuerza a la IA a sintetizar eventos previos (de los prompts 3 y 4) para sacar conclusiones.
* **Structured Output:** Petición de un formato de salida restrictivo (viñetas con 3 categorías específicas).

**Resultados de la Aplicación:**
* **¿Qué hicimos bien?**
  * Cumplimos con el objetivo del Sprint entregando el incremento esperado.
  * La comunicación técnica en el backend permitió finalizar las tareas del portal antes de tiempo.
* **¿Qué podemos mejorar?**
  * La gestión de accesos y credenciales de terceros (el bloqueo de la API de Maps demoró a Dev A).
  * Debimos identificar antes las limitaciones técnicas del GPS para no sorprender al cliente en la Review.
* **Plan de Acción (Próximo Sprint):**
  * **Acción:** El Scrum Master se encargará de validar todas las licencias y accesos a APIs externas durante el Sprint Planning, antes de que los desarrolladores comiencen sus tareas.

## Enunciado
1. ¿Qué es Extreme Programming (XP) y cuál es su objetivo principal dentro de las metodologías ágiles?
2. ¿Cuáles son los cinco valores principales de XP? Explicá brevemente cada uno.
3. ¿Por qué XP considera que las pruebas son un elemento fundamental del desarrollo de software?
4. ¿Qué es Test Driven Development (TDD) y cómo se relaciona con XP?
5. ¿En qué consiste la práctica de Pair Programming? Mencioná dos ventajas y una posible dificultad.
6. ¿Qué son las historias de usuario en XP y por qué se prefieren frente a una especificación extensa de requisitos?
7. ¿Qué significa Continuous Integration en XP y qué beneficios aporta al equipo de desarrollo?
8. ¿Cómo se aplica el concepto de Weekly Cycle en un proyecto desarrollado con XP?
9. En XP se plantea que se fija el tiempo, el costo y la calidad, y se negocia el alcance. ¿Qué significa esta idea? Explicalo con un ejemplo.
10. Elegí tres prácticas de XP y explicá cómo podrían aplicarse en un proyecto real de desarrollo de software.

## Resolución

### 1. Definición y Objetivo de XP
Extreme Programming (XP) es una metodología ágil que se originó a finales de los 80 y se popularizó con el "libro blanco" de Kent Beck. Se define como un proceso **adaptativo y orientado a las personas**. Sus objetivos principales son **reducir el riesgo** del proyecto, mejorar la respuesta ante los cambios del negocio, aumentar la productividad a lo largo de la vida del software y hacer que el trabajo sea más disfrutable para el equipo.

### 2. Los 5 Valores de XP
Los valores que guían la metodología son:
*   **Comunicación:** Fomentar el diálogo fluido dentro del equipo y con el cliente.
*   **Simplicidad:** Buscar la solución más sencilla que funcione hoy, evitando sobre-ingeniería.
*   **Retroalimentación:** Obtener información constante sobre el estado del producto y el proceso.
*   **Valentía:** Tomar decisiones difíciles, como refactorizar código complejo o aceptar errores.
*   **Respeto:** Valorar las contribuciones de cada miembro y el bienestar del equipo.

### 3. La importancia de las pruebas
En XP, las pruebas son el **elemento fundamental** porque permiten integrar el desarrollo en un proceso de construcción continua, creando una plataforma estable para el crecimiento futuro del sistema. Todos los desarrolladores deben escribirlas mientras crean el código de producción, asegurando que la calidad sea intrínseca y no un paso final.

### 4. Test Driven Development (TDD)
TDD (Desarrollo Dirigido por las Pruebas) es una práctica central de XP donde se escriben las **pruebas antes que cualquier código**. Se basa en un ciclo de "test, code, refactor" (rojo, verde, refactorizar), lo que ayuda a aclarar el alcance del código, mejora la cohesión y construye confianza entre compañeros.

### 5. Pair Programming
Consiste en que **todo el código** que va a producción sea escrito por dos personas sentadas frente a la misma máquina.
*   **Ventajas:** Ayuda a mantener a los desarrolladores centrados, clarifica ideas y permite cumplir mejor los estándares del equipo.
*   **Dificultad:** Puede ser difícil no invadir el espacio personal del otro o gestionar correctamente la rotación de las parejas para evitar el agotamiento.

### 6. Historias de Usuario
Son descripciones breves escritas en tarjetas que incluyen un nombre, descripción y estimación de tiempo. Se prefieren frente a los requisitos tradicionales porque las historias abrazan la **posibilidad de cambio**, mientras que la palabra "requisito" connota inmutabilidad, lo cual no es compatible con la agilidad.

### 7. Integración Continua (Continuous Integration)
Significa no dejar pasar más de dos horas sin integrar los cambios programados al sistema principal. Aporta beneficios como evitar pasos de integración impredecibles y costosos al final del proyecto, manteniendo el sistema siempre listo para ser lanzado (o desplegado en *staging*).

### 8. Ciclo Semanal (Weekly Cycle)
Se aplica mediante una reunión al inicio de cada semana donde se revisa el progreso, el cliente elige historias que sumen una semana de trabajo, y el equipo las fracciona en tareas para estimarlas. Durante la semana, se escriben pruebas automáticas y se implementan las historias para que al final del ciclo estén disponibles para ser desplegadas.

### 9. Triángulo de Hierro y Negociación de Alcance
Esta idea significa que para mantener una **calidad alta** sin generar deuda técnica, no se debe sacrificar el tiempo o el costo, sino **negociar qué funcionalidades se entregan** (alcance).
*   **Ejemplo:** Si un cliente necesita un sistema de ventas en dos meses con un presupuesto fijo, el equipo garantiza que el software será excelente y estará a tiempo, pero si el desarrollo se retrasa, se acuerda con el cliente entregar primero el "carrito de compras" y dejar el "módulo de estadísticas" para la siguiente entrega, en lugar de entregar ambos a medias o sin probar.

### 10. Aplicación de 3 Prácticas en un Proyecto Real
1.  **Sit Together (Sentarse Juntos):** En una oficina de desarrollo, esto se traduce en eliminar cubículos para crear un espacio abierto que promueva la comunicación cara a cara y reuniones espontáneas más productivas.
2.  **Informative Workspace (Espacio de Trabajo Informativo):** Colocar tableros físicos con tarjetas de historias y gráficos de evolución (burndown charts) en las paredes para que cualquier miembro del equipo vea el estado del proyecto de un vistazo.
3.  **Energized Work (Trabajo Energizado):** Implementar una política de no realizar horas extras sistemáticas y usar técnicas como Pomodoro para asegurar que el equipo trabaje a pleno rendimiento solo las horas en que puede ser productivo de forma sostenida.

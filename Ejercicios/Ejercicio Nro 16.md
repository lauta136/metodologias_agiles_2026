# Ejercicio Nro: 16

## Enunciado

**Objetivo:**

Utilizar el método Delphi para llegar a un consenso sobre la tecnología y la arquitectura más adecuadas para el desarrollo de una billetera virtual segura, escalable y confiable.

**Descripción:**

El método Delphi es una técnica de consulta estructurada que permite obtener el conocimiento y la experiencia de un grupo de especialistas mediante varias rondas de consulta anónimas. Su objetivo es alcanzar un consenso sobre problemas complejos, evitando que la opinión de una persona influya directamente sobre las demás. En este caso, el método se empleará para determinar cuál es la mejor combinación de tecnologías y arquitectura para desarrollar una billetera virtual.

---

# Resolución

## 1. Definición del problema

El objetivo principal consiste en determinar qué tecnologías y qué arquitectura de software permiten construir una billetera virtual que satisfaga los requisitos funcionales y no funcionales del proyecto. La aplicación deberá permitir realizar transferencias de dinero, consultar saldos, efectuar pagos electrónicos y administrar información sensible de los usuarios de manera eficiente y segura.

Para definir correctamente el problema se identifican los factores críticos que influirán en la decisión:

- **Seguridad:** protección de los datos personales y financieros mediante mecanismos de cifrado, autenticación multifactor, autorización basada en roles y monitoreo de accesos.
- **Escalabilidad:** capacidad del sistema para soportar un incremento progresivo de usuarios y transacciones sin afectar el rendimiento.
- **Confiabilidad:** garantizar la disponibilidad del servicio incluso ante fallas de hardware o software, reduciendo al mínimo los tiempos de inactividad.
- **Rendimiento:** lograr tiempos de respuesta bajos para consultas y operaciones financieras.
- **Mantenibilidad:** facilitar futuras modificaciones, incorporación de nuevas funcionalidades y corrección de errores sin afectar el resto del sistema.
- **Costo:** evaluar el impacto económico de la infraestructura, licencias, herramientas de desarrollo y mantenimiento operativo.

Estos criterios servirán como base para comparar las distintas alternativas tecnológicas durante el proceso Delphi.

---

## 2. Selección del panel de expertos

El panel estará conformado por profesionales con experiencia comprobable en distintas disciplinas relacionadas con el proyecto, buscando obtener una visión integral del problema.

Se propone seleccionar especialistas pertenecientes a los siguientes perfiles:

- Arquitectos de software especializados en sistemas distribuidos.
- Ingenieros en ciberseguridad con experiencia en aplicaciones financieras.
- Desarrolladores senior de plataformas FinTech.
- Especialistas en tecnologías Blockchain y registros distribuidos.
- Ingenieros DevOps con experiencia en infraestructura cloud y alta disponibilidad.
- Analistas funcionales con conocimiento de procesos financieros y medios de pago.

Cada experto participará de manera independiente y anónima para evitar sesgos o influencias personales. Además, se verificará que ninguno mantenga conflictos de interés con proveedores de tecnologías que puedan ser evaluadas durante el estudio.

La diversidad del panel permitirá analizar el problema desde distintos enfoques técnicos y funcionales, enriqueciendo la calidad del consenso obtenido.

---

## 3. Elaboración del cuestionario

Se desarrollará un cuestionario estructurado que permita comparar distintas tecnologías y estilos arquitectónicos considerando los criterios definidos anteriormente.

Entre las alternativas que podrían analizarse se encuentran:

### Tecnologías para almacenamiento de información

- Bases de datos relacionales (PostgreSQL, SQL Server).
- Bases de datos NoSQL (MongoDB).
- Sistemas de registro inmutable para auditoría.
- Soluciones basadas en Blockchain privada.

### Arquitecturas de software

- Arquitectura monolítica.
- Arquitectura por capas.
- Arquitectura basada en microservicios.
- Arquitectura orientada a eventos.

Cada alternativa será evaluada mediante preguntas de valoración utilizando una escala del 1 al 5 sobre aspectos como:

- Nivel de seguridad.
- Facilidad de escalabilidad.
- Costos de implementación.
- Rendimiento esperado.
- Facilidad de mantenimiento.
- Complejidad de desarrollo.
- Integración con servicios externos.

Además de las preguntas cerradas, el cuestionario incluirá preguntas abiertas para que los especialistas puedan fundamentar sus respuestas, proponer mejoras o mencionar riesgos asociados a cada alternativa tecnológica.

---

## 4. Aplicación del método Delphi

El método Delphi se desarrollará mediante varias rondas sucesivas de consulta.

### Primera ronda

Cada experto recibirá el cuestionario de forma individual y responderá según su experiencia profesional. Todas las respuestas serán anónimas y administradas por un coordinador del proceso.

Durante esta etapa se obtendrán opiniones iniciales sobre las distintas tecnologías, identificando fortalezas, debilidades y posibles riesgos de cada alternativa.

### Procesamiento de resultados

Una vez recopiladas las respuestas, el coordinador realizará un análisis estadístico calculando indicadores como promedio, mediana y dispersión para cada criterio evaluado.

También elaborará un informe resumiendo los argumentos técnicos más relevantes aportados por los especialistas, eliminando cualquier referencia que permita identificar a los autores de cada opinión.

### Segunda ronda

Los expertos recibirán el informe generado durante la primera etapa junto con el cuestionario original.

Con esta nueva información podrán:

- Mantener su evaluación inicial.
- Modificar sus respuestas.
- Justificar técnicamente cualquier opinión que continúe alejándose del consenso del grupo.

Este procedimiento favorece que las diferencias disminuyan progresivamente y que las decisiones se fundamenten en argumentos técnicos compartidos.

### Rondas adicionales

Si aún existen diferencias significativas entre las opiniones del panel, podrán realizarse nuevas rondas hasta alcanzar un nivel aceptable de consenso respecto de las tecnologías y arquitecturas evaluadas.

---

## 5. Selección de la tecnología y la arquitectura

Luego de finalizar el proceso Delphi, se analizarán los resultados obtenidos para seleccionar la alternativa con mejor desempeño global.

Como resultado del consenso, podría elegirse una arquitectura de **microservicios**, ya que permite dividir el sistema en componentes independientes que facilitan la escalabilidad, el mantenimiento y la disponibilidad del servicio.

Para la persistencia de la información se podría optar por una **base de datos relacional** para las operaciones transaccionales, complementada con un sistema de auditoría inmutable destinado a registrar todas las operaciones financieras importantes.

Asimismo, los expertos podrían recomendar la utilización de:

- Contenedores Docker para facilitar el despliegue.
- Orquestación mediante Kubernetes para mejorar la disponibilidad.
- APIs REST para la comunicación entre servicios.
- Autenticación multifactor y cifrado de extremo a extremo para reforzar la seguridad.
- Infraestructura en la nube con balanceadores de carga y mecanismos de recuperación ante fallos.

La elección final se justificará mediante los resultados estadísticos obtenidos durante las distintas rondas del método Delphi, demostrando que la solución seleccionada representa el mejor equilibrio entre seguridad, escalabilidad, rendimiento, confiabilidad y costos.

---

## 6. Documentación y comunicación

Finalizado el proceso de selección, se elaborará un documento técnico donde se registrará todo el trabajo realizado durante la aplicación del método Delphi.

La documentación incluirá:

- Objetivos del estudio.
- Integrantes y perfiles del panel de expertos.
- Criterios utilizados para evaluar las tecnologías.
- Cuestionarios empleados en cada ronda.
- Resultados estadísticos obtenidos.
- Principales argumentos técnicos considerados durante el proceso.
- Tecnologías evaluadas y motivos por los cuales algunas fueron descartadas.
- Justificación completa de la arquitectura finalmente seleccionada.

Finalmente, el informe será presentado a todas las partes interesadas del proyecto.

Al equipo de desarrollo se le entregará la especificación técnica para comenzar la implementación del sistema. A los responsables del proyecto y a los inversores se les presentará un informe ejecutivo explicando las ventajas de la solución elegida y los beneficios esperados en términos de seguridad, rendimiento y escalabilidad. De esta forma se garantiza la transparencia del proceso de decisión y se proporciona una base sólida para el desarrollo futuro de la billetera virtual.

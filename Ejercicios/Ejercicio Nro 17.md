# Ejercicio Nro 17

## Enunciado
Objetivo: Desarrollar una aplicación web que permita a los usuarios gestionar sus finanzas personales de manera eficiente y segura. La aplicación debe cumplir con los siguientes requisitos funcionales:
1. Gestión de cuentas bancarias:
Permitir la creación y edición de cuentas bancarias.
Visualizar el saldo actual y el historial de movimientos de cada cuenta.
Realizar transferencias entre cuentas propias.
Descargar el historial de movimientos en formato CSV o PDF.
2. Gestión de ingresos y gastos:
Permitir la creación y edición de ingresos y gastos.
Categorizar los ingresos y gastos por tipo (salario, alquiler, alimentación, etc.).
Visualizar gráficos y reportes sobre los ingresos y gastos por categoría y período de tiempo.
Establecer presupuestos para diferentes categorías de gastos.
3. Gestión de deudas:
Permitir la creación y edición de deudas.
Indicar el monto total de la deuda, la tasa de interés, el plazo de pago y el monto de las cuotas.
Visualizar un calendario de pagos y realizar simulaciones de diferentes escenarios de pago.
Generar informes sobre el progreso en el pago de las deudas.
## 1. Mapeo y Medición del Tamaño Funcional (COSMIC)

Para calcular el tamaño funcional del proyecto, se identifican los procesos funcionales y se desglosan sus respectivos movimientos de datos (*Entry*, *Exit*, *Read*, *Write*), asignando 1 Punto de Función COSMIC (PFC) a cada uno.

## Resolución 

### 1. Mapeo y Medición del Tamaño Funcional (COSMIC)

Para calcular el tamaño funcional del proyecto, se identifican los procesos funcionales y se desglosan sus respectivos movimientos de datos (*Entry*, *Exit*, *Read*, *Write*), asignando 1 Punto de Función COSMIC (PFC) a cada uno.

#### Módulo 1: Gestión de cuentas bancarias
* **Proceso: Crear cuenta bancaria**
  * *Entrada (Entry):* Ingresar datos de la nueva cuenta (nombre, tipo, banco).
  * *Escritura (Write):* Registrar la cuenta en la base de datos.
  * *Salida (Exit):* Mostrar mensaje de confirmación de creación.
* **Proceso: Editar cuenta bancaria**
  * *Entrada (Entry):* Seleccionar cuenta e ingresar modificaciones.
  * *Lectura (Read):* Cargar los datos actuales de la cuenta para su edición.
  * *Escritura (Write):* Actualizar los datos modificados en la base de datos.
  * *Salida (Exit):* Mostrar mensaje de confirmación de edición.
* **Proceso: Visualizar saldo e historial**
  * *Entrada (Entry):* Seleccionar la cuenta bancaria a consultar.
  * *Lectura (Read):* Leer el saldo actual de la cuenta.
  * *Lectura (Read):* Leer el historial de movimientos asociados.
  * *Salida (Exit):* Mostrar en pantalla el saldo y la lista de movimientos.
* **Proceso: Realizar transferencias entre cuentas propias**
  * *Entrada (Entry):* Ingresar cuenta origen, cuenta destino y monto a transferir.
  * *Lectura (Read):* Validar saldos y existencia de las cuentas.
  * *Escritura (Write):* Actualizar (restar) saldo de la cuenta origen.
  * *Escritura (Write):* Actualizar (sumar) saldo de la cuenta destino.
  * *Escritura (Write):* Registrar el nuevo movimiento de transferencia.
  * *Salida (Exit):* Mostrar comprobante de transferencia exitosa.
* **Proceso: Descargar historial de movimientos**
  * *Entrada (Entry):* Solicitar la descarga seleccionando el formato.
  * *Lectura (Read):* Obtener el historial de movimientos de la base de datos.
  * *Salida (Exit):* Exportar y descargar archivo en formato CSV.
  * *Salida (Exit):* Exportar y descargar archivo en formato PDF.

> **Subtotal Módulo 1:** 5 Entries + 4 Reads + 5 Writes + 6 Exits = **20 PFC**

---

#### Módulo 2: Gestión de ingresos y gastos
* **Proceso: Crear ingreso/gasto (con su respectiva categoría)**
  * *Entrada (Entry):* Ingresar datos del movimiento (monto, tipo, fecha, categoría).
  * *Escritura (Write):* Registrar el movimiento en la base de datos.
  * *Salida (Exit):* Mostrar confirmación de registro.
* **Proceso: Editar ingreso/gasto**
  * *Entrada (Entry):* Seleccionar movimiento e ingresar cambios.
  * *Lectura (Read):* Leer datos del movimiento a modificar.
  * *Escritura (Write):* Actualizar el registro en la base de datos.
  * *Salida (Exit):* Mostrar confirmación de actualización.
* **Proceso: Visualizar gráficos y reportes**
  * *Entrada (Entry):* Seleccionar filtros de reporte (categoría, período de tiempo).
  * *Lectura (Read):* Leer históricos de ingresos y gastos de la base de datos.
  * *Salida (Exit):* Renderizar y mostrar gráficos/reportes en pantalla.
* **Proceso: Establecer presupuestos**
  * *Entrada (Entry):* Ingresar límites de presupuesto por categoría.
  * *Escritura (Write):* Guardar o actualizar la meta de presupuesto en la base de datos.
  * *Salida (Exit):* Mostrar confirmación de presupuesto establecido.

> **Subtotal Módulo 2:** 4 Entries + 2 Reads + 3 Writes + 4 Exits = **13 PFC**

---

#### Módulo 3: Gestión de deudas
* **Proceso: Crear deuda**
  * *Entrada (Entry):* Ingresar datos (monto total, tasa de interés, plazo, cuotas).
  * *Escritura (Write):* Registrar la deuda en la base de datos.
  * *Salida (Exit):* Mostrar confirmación de registro.
* **Proceso: Editar deuda**
  * *Entrada (Entry):* Seleccionar la deuda e ingresar modificaciones.
  * *Lectura (Read):* Leer datos de la deuda a modificar.
  * *Escritura (Write):* Actualizar la deuda en la base de datos.
  * *Salida (Exit):* Mostrar confirmación de cambios.
* **Proceso: Visualizar calendario de pagos**
  * *Entrada (Entry):* Seleccionar opción de ver calendario de vencimientos.
  * *Lectura (Read):* Leer las cuotas y cronogramas de deudas de la base de datos.
  * *Salida (Exit):* Mostrar el calendario interactivo en pantalla.
* **Proceso: Realizar simulaciones de escenarios de pago**
  * *Entrada (Entry):* Ingresar variables temporales de simulación (ej. pagos anticipados).
  * *Salida (Exit):* Mostrar proyecciones calculadas en pantalla (no requiere persistencia).
* **Proceso: Generar informes sobre el progreso de deudas**
  * *Entrada (Entry):* Solicitar informe de progreso de deudas.
  * *Lectura (Read):* Leer deudas vigentes y pagos realizados.
  * *Salida (Exit):* Mostrar informe de progreso en pantalla.

> **Subtotal Módulo 3:** 5 Entries + 3 Reads + 2 Writes + 5 Exits = **15 PFC**

---

### 2. Respuestas al Formulario de Resolución (Ajuste Regional)

De acuerdo a una investigación del mercado tecnológico en Argentina, un desarrollador semi-senior percibe en promedio alrededor de 2.500 USD mensuales. Proyectando un equipo estándar de desarrollo (ej. 4 a 5 personas incluyendo QA y Project Manager) más costos operativos, se estima un **costo mensual de equipo de 12.500 USD**. Se mantiene la productividad histórica provista en las diapositivas de **23 PFC/mes**.

* **Estimación del tamaño del proyecto:**
  Utilizando el método COSMIC, se estima que el tamaño funcional total del proyecto es de **48 Puntos de Función COSMIC (PFC)**.
  *(Suma de los módulos: 20 + 13 + 15 = 48)*

* **Cálculo del costo por punto de función (CPFC):**
  Ajustado al mercado laboral de Argentina, el costo por punto de función se estima en **543,48 USD**.
  *(Fórmula: 12.500 USD mensuales / 23 PFC)*

* **Cantidad de puntos de función que se pueden hacer en un mes:**
  Se estima que un equipo de desarrollo de software estándar puede desarrollar **23 Puntos de Función COSMIC (PFC)** por mes.

* **Duración del proyecto:**
  La duración del proyecto se estima en **2,09 meses**.
  *(Fórmula: 48 PFC / 23 PFC/mes)*

* **Costo del proyecto:**
  El costo total del proyecto ajustado a la región se estima en **26.087,04 USD**.
  *(Fórmula: 48 PFC × 543,48 USD)*

# Práctica 1

## Ejercicios sobre Metodologías de Desarrollo en Cascada

### 1. Análisis de Requerimientos:
* **Ejercicio 1:** Un cliente te solicita una aplicación web para gestionar su inventario. Define los requisitos funcionales y no funcionales del sistema.
* **Ejercicio 2:** Redacta un caso de uso para la funcionalidad de "Agregar un nuevo producto" en la aplicación web del ejercicio 1.

### 2. Diseño del Sistema:
* **Ejercicio 3:** Elabora un diagrama de flujo de datos para la aplicación web del ejercicio 1.
* **Ejercicio 4:** Diseña la interfaz de usuario para la pantalla de "Inicio" de la aplicación web del ejercicio 1.

### 3. Diseño del Programa:
* **Ejercicio 5:** Elige una arquitectura adecuada para la aplicación web del ejercicio 1 y justifica tu elección.
* **Ejercicio 6:** Diseña la base de datos para la aplicación web del ejercicio 1.

### 4. Diseño:
Utilizando los siguientes diagramas resuelva los casos de usos de los ejercicios 7 y 8: 

* **Diagrama de Dominio:** Identifica las entidades, atributos y relaciones del sistema.
* **Diagrama de Robustez:** Analiza cómo el sistema responde a diferentes escenarios de uso.
* **Prototipo:** Crea una versión simplificada del sistema para probar la usabilidad y funcionalidad.
* **Diagrama de Secuencia:** Describe la interacción entre los diferentes objetos del sistema.
* **Diagrama de Clases:** Define las clases, sus atributos, métodos y relaciones.

* **Ejercicio 7:** Implementa la funcionalidad de "Agregar un nuevo producto" en la aplicación web del ejercicio 1 utilizando el lenguaje de programación de tu preferencia.
* **Ejercicio 8:** Implementa la lógica de negocio para la funcionalidad de "Agregar un nuevo producto" en la aplicación web del ejercicio 1.

### 5. Pruebas:
* **Ejercicio 9:** Define un conjunto de pruebas unitarias para la funcionalidad de "Agregar un nuevo producto" en la aplicación web del ejercicio 1.
* **Ejercicio 10:** Ejecuta pruebas de integración para la funcionalidad de "Agregar un nuevo producto" en la aplicación web del ejercicio 1.

### 6. Despliegue del Programa:
* **Ejercicio 11:** Definir un plan de despliegue para la aplicación web del ejercicio 1.
* **Ejercicio 12:** Despliega la aplicación web del ejercicio 1 en un servidor de producción.

### 7. Mantenimiento:
* **Ejercicio 13:** Definir un plan de mantenimiento para la aplicación web del ejercicio 1.
* **Ejercicio 14:** Implementa una corrección de errores para un problema detectado en la aplicación web del ejercicio 1.

### 8. Nos preparamos para nuevos retos:
* **Ejercicio 15:** Arme un equipo de trabajo y defina los roles para realizar los ejercicios anteriores para un futuro dominio de aplicación relacionado con inteligencia artificial generativa.
---

## 1. Análisis de Requerimientos

### Ejercicio 1: Requisitos Funcionales y No Funcionales

**Requisitos Funcionales (RF)**

| ID | Descripción |
|----|-------------|
| RF01 | El sistema debe permitir registrar, editar y eliminar productos (nombre, descripción, precio, categoría, stock). |
| RF02 | El sistema debe permitir consultar el listado de productos con filtros por categoría, nombre y stock disponible. |
| RF03 | El sistema debe permitir registrar entradas y salidas de stock (movimientos de inventario). |
| RF04 | El sistema debe generar alertas cuando el stock de un producto sea menor a un mínimo configurado. |
| RF05 | El sistema debe permitir la gestión de usuarios con distintos roles (administrador, operador). |
| RF06 | El sistema debe permitir generar reportes de inventario (stock actual, movimientos por período). |
| RF07 | El sistema debe registrar auditoría de cambios (quién, qué y cuándo se modificó). |
| RF08 | El sistema debe permitir la autenticación y autorización de usuarios. |

**Requisitos No Funcionales (RNF)**

| ID | Descripción |
|----|-------------|
| RNF01 | La aplicación debe responder a las consultas en menos de 2 segundos bajo carga normal. |
| RNF02 | El sistema debe estar disponible al menos el 99% del tiempo (SLA). |
| RNF03 | Debe ser compatible con navegadores modernos (Chrome, Edge, Firefox). |
| RNF04 | Los datos sensibles (contraseñas) deben almacenarse cifrados (hashing, ej. bcrypt). |
| RNF05 | El sistema debe ser escalable horizontalmente para soportar crecimiento de usuarios. |
| RNF06 | El código debe seguir principios de arquitectura en capas para facilitar mantenimiento. |
| RNF07 | El sistema debe contar con logs de errores centralizados. |

---

### Ejercicio 2: Caso de Uso — "Agregar un nuevo producto"

**Nombre del caso de uso:** Agregar nuevo producto
**Actor principal:** Operador / Administrador
**Precondición:** El usuario ha iniciado sesión con permisos suficientes.
**Postcondición:** El producto queda registrado en el sistema con stock inicial.

**Flujo Principal:**
1. El usuario accede a la sección "Productos".
2. El usuario selecciona la opción "Nuevo Producto".
3. El sistema muestra un formulario con los campos: nombre, descripción, categoría, precio, stock inicial, stock mínimo.
4. El usuario completa los datos y confirma.
5. El sistema valida los datos ingresados.
6. El sistema guarda el producto en la base de datos.
7. El sistema muestra un mensaje de confirmación y redirige al listado de productos.

**Flujos Alternativos:**
- **5a.** Si algún campo obligatorio falta o es inválido, el sistema muestra un mensaje de error y no permite continuar.
- **6a.** Si el producto ya existe (mismo SKU/código), el sistema rechaza la operación e informa al usuario.

---

## 2. Diseño del Sistema

### Ejercicio 3: Diagrama de Flujo de Datos

<img width="660" height="116" alt="Screenshot 2026-07-05 at 2 24 32 PM" src="https://github.com/user-attachments/assets/4a87e5a3-8874-4b6e-9e38-3ce8dcb0954e" />

**Entidades externas:** Usuario (Operador/Administrador)
**Procesos:** Gestionar Producto, Gestionar Movimientos, Generar Alertas, Generar Reportes
**Almacenes de datos:** Productos, Movimientos, Usuarios, Auditoría

---

### Ejercicio 4: Diseño de Interfaz — Pantalla de "Inicio"

   <img width="1192" height="751" alt="Screenshot 2026-07-05 at 2 33 04 PM" src="https://github.com/user-attachments/assets/1076006a-9d27-41a9-ae51-bee42732ff3e" />
---

## 3. Diseño del Programa

### Ejercicio 5: Arquitectura elegida y justificación

**Arquitectura propuesta:** Arquitectura en capas (N-Layer) con patrón **Repository + Service Layer**, expuesta como **Web API (.NET 9)** consumida por un frontend (o Razor Pages/React).

    Presentación (Controllers / Razor Pages)
            ↓
    Servicios (Lógica de negocio - Services)
            ↓
    Repositorios (Acceso a datos - Repository Pattern)
            ↓
    Persistencia (EF Core → SQL Server / PostgreSQL)

**Justificación:**
- **Separación de responsabilidades:** facilita el mantenimiento y las pruebas unitarias (se puede mockear el repositorio para testear el servicio).
- **Escalabilidad:** al exponer una Web API, se puede reutilizar la lógica de negocio para múltiples clientes (web, mobile, integraciones).
- **Familiaridad y madurez:** es un patrón ampliamente probado en el ecosistema .NET, con soporte nativo de EF Core para el patrón repositorio.
- **Mantenibilidad:** el uso de DTOs entre capas evita el acoplamiento directo con las entidades de dominio.

---

### Ejercicio 6: Diseño de la Base de Datos

**Modelo relacional (simplificado):**

    Usuarios
    - Id (PK)
    - Nombre
    - Email
    - PasswordHash
    - Rol

    Categorias
    - Id (PK)
    - Nombre

    Productos
    - Id (PK)
    - Nombre
    - Descripcion
    - Precio
    - Stock
    - StockMinimo
    - CategoriaId (FK -> Categorias.Id)

    Movimientos
    - Id (PK)
    - ProductoId (FK -> Productos.Id)
    - Tipo (Entrada/Salida)
    - Cantidad
    - Fecha
    - UsuarioId (FK -> Usuarios.Id)

    Auditoria
    - Id (PK)
    - Entidad
    - Accion
    - UsuarioId (FK -> Usuarios.Id)
    - Fecha
    - Detalle

**Relaciones:**
- Una `Categoria` tiene muchos `Productos` (1:N)
- Un `Producto` tiene muchos `Movimientos` (1:N)
- Un `Usuario` genera muchos `Movimientos` y registros de `Auditoria` (1:N)

---

## 4. Diseño detallado (Ejercicios 7 y 8)

### Diagrama de Dominio

<img width="395" height="540" alt="Screenshot 2026-07-05 at 3 05 54 PM" src="https://github.com/user-attachments/assets/1442a4a4-6845-4a77-896d-4fe949fa5e4b" />


### Diagrama de Robustez (conceptual)

<img width="1184" height="146" alt="Screenshot 2026-07-05 at 2 41 22 PM" src="https://github.com/user-attachments/assets/e2ad56a4-9bea-44d0-9a00-8e6a8cc90933" />


- **Boundary:** Formulario de alta de producto (UI)
- **Control:** ProductoController (recibe la petición), ProductoService (valida y aplica reglas de negocio)
- **Entity:** Producto (objeto de dominio persistido)

### Prototipo (versión simplificada)

<img width="931" height="578" alt="Screenshot 2026-07-05 at 3 11 34 PM" src="https://github.com/user-attachments/assets/bfc89755-bfd1-468c-a463-840b3cb07b62" />
<img width="685" height="619" alt="Screenshot 2026-07-05 at 3 11 57 PM" src="https://github.com/user-attachments/assets/6d6d678f-3ac3-4d9d-ae69-f50213166a33" />


### Diagrama de Secuencia

<img width="1169" height="596" alt="Screenshot 2026-07-05 at 2 49 47 PM" src="https://github.com/user-attachments/assets/0a6e1553-868b-4b14-809b-20e07c893c6b" />


### Diagrama de Clases

<img width="1315" height="605" alt="Screenshot 2026-07-05 at 3 01 24 PM" src="https://github.com/user-attachments/assets/8736ce53-9ff0-4e51-9eff-3eedac55a71f" />

---

### Ejercicio 7: Implementación — "Agregar un nuevo producto" (C# / .NET 9 Web API)

    // DTO
    public record ProductoDto(string Nombre, string Descripcion, decimal Precio, int Stock, int StockMinimo, int CategoriaId);

    // Entidad
    public class Producto
    {
        public int Id { get; set; }
        public string Nombre { get; set; } = string.Empty;
        public string Descripcion { get; set; } = string.Empty;
        public decimal Precio { get; set; }
        public int Stock { get; set; }
        public int StockMinimo { get; set; }
        public int CategoriaId { get; set; }
    }

    // Controller
    [ApiController]
    [Route("api/[controller]")]
    public class ProductosController : ControllerBase
    {
        private readonly IProductoService _service;

        public ProductosController(IProductoService service)
        {
            _service = service;
        }

        [HttpPost]
        public async Task<IActionResult> Post([FromBody] ProductoDto dto)
        {
            if (!ModelState.IsValid)
                return BadRequest(ModelState);

            var producto = await _service.CrearProductoAsync(dto);
            return CreatedAtAction(nameof(Post), new { id = producto.Id }, producto);
        }
    }

---

### Ejercicio 8: Lógica de negocio

    public interface IProductoService
    {
        Task<Producto> CrearProductoAsync(ProductoDto dto);
    }

    public class ProductoService : IProductoService
    {
        private readonly IProductoRepository _repository;

        public ProductoService(IProductoRepository repository)
        {
            _repository = repository;
        }

        public async Task<Producto> CrearProductoAsync(ProductoDto dto)
        {
            if (string.IsNullOrWhiteSpace(dto.Nombre))
                throw new ArgumentException("El nombre del producto es obligatorio.");

            if (dto.Precio <= 0)
                throw new ArgumentException("El precio debe ser mayor a cero.");

            var existe = await _repository.ExisteProductoAsync(dto.Nombre);
            if (existe)
                throw new InvalidOperationException("Ya existe un producto con ese nombre.");

            var producto = new Producto
            {
                Nombre = dto.Nombre,
                Descripcion = dto.Descripcion,
                Precio = dto.Precio,
                Stock = dto.Stock,
                StockMinimo = dto.StockMinimo,
                CategoriaId = dto.CategoriaId
            };

            await _repository.AgregarAsync(producto);
            return producto;
        }
    }

---

## 5. Pruebas

### Ejercicio 9: Pruebas Unitarias (xUnit)

    public class ProductoServiceTests
    {
        [Fact]
        public async Task CrearProducto_ConDatosValidos_DeberiaCrearProducto()
        {
            var repoMock = new Mock<IProductoRepository>();
            repoMock.Setup(r => r.ExisteProductoAsync(It.IsAny<string>())).ReturnsAsync(false);

            var service = new ProductoService(repoMock.Object);
            var dto = new ProductoDto("Mouse", "Mouse óptico", 1500, 10, 2, 1);

            var resultado = await service.CrearProductoAsync(dto);

            Assert.Equal("Mouse", resultado.Nombre);
            repoMock.Verify(r => r.AgregarAsync(It.IsAny<Producto>()), Times.Once);
        }

        [Fact]
        public async Task CrearProducto_ConNombreVacio_DeberiaLanzarExcepcion()
        {
            var repoMock = new Mock<IProductoRepository>();
            var service = new ProductoService(repoMock.Object);
            var dto = new ProductoDto("", "desc", 100, 5, 1, 1);

            await Assert.ThrowsAsync<ArgumentException>(() => service.CrearProductoAsync(dto));
        }

        [Fact]
        public async Task CrearProducto_ConNombreDuplicado_DeberiaLanzarExcepcion()
        {
            var repoMock = new Mock<IProductoRepository>();
            repoMock.Setup(r => r.ExisteProductoAsync("Mouse")).ReturnsAsync(true);
            var service = new ProductoService(repoMock.Object);
            var dto = new ProductoDto("Mouse", "desc", 100, 5, 1, 1);

            await Assert.ThrowsAsync<InvalidOperationException>(() => service.CrearProductoAsync(dto));
        }

        [Fact]
        public async Task CrearProducto_ConPrecioNegativo_DeberiaLanzarExcepcion()
        {
            var repoMock = new Mock<IProductoRepository>();
            var service = new ProductoService(repoMock.Object);
            var dto = new ProductoDto("Teclado", "desc", -10, 5, 1, 1);

            await Assert.ThrowsAsync<ArgumentException>(() => service.CrearProductoAsync(dto));
        }
    }

### Ejercicio 10: Pruebas de Integración

    public class ProductosControllerIntegrationTests : IClassFixture<WebApplicationFactory<Program>>
    {
        private readonly HttpClient _client;

        public ProductosControllerIntegrationTests(WebApplicationFactory<Program> factory)
        {
            _client = factory.CreateClient();
        }

        [Fact]
        public async Task Post_CrearProducto_DeberiaRetornar201()
        {
            var dto = new ProductoDto("Monitor", "Monitor 24 pulgadas", 45000, 5, 1, 1);
            var response = await _client.PostAsJsonAsync("/api/productos", dto);

            response.EnsureSuccessStatusCode();
            Assert.Equal(System.Net.HttpStatusCode.Created, response.StatusCode);
        }

        [Fact]
        public async Task Post_ProductoDuplicado_DeberiaRetornarError()
        {
            var dto = new ProductoDto("Monitor", "Monitor 24 pulgadas", 45000, 5, 1, 1);
            await _client.PostAsJsonAsync("/api/productos", dto); // primera vez
            var response = await _client.PostAsJsonAsync("/api/productos", dto); // duplicado

            Assert.False(response.IsSuccessStatusCode);
        }
    }

Estas pruebas usan una base de datos en memoria (`Microsoft.EntityFrameworkCore.InMemory`) o un contenedor de SQL Server en Docker para validar el flujo completo (Controller → Service → Repository → BD).

---

## 6. Despliegue del Programa

### Ejercicio 11: Plan de Despliegue

1. **Preparación del entorno:** provisionar servidor (IIS, Azure App Service o contenedor Docker) y base de datos de producción (SQL Server).
2. **Configuración de variables de entorno:** connection strings, claves JWT, niveles de log.
3. **Build y publicación:** `dotnet publish -c Release -o ./publish`.
4. **Migraciones de base de datos:** ejecutar `dotnet ef database update` contra la BD de producción.
5. **Despliegue:** subir artefactos al servidor / pipeline de CI-CD (GitHub Actions, Azure DevOps).
6. **Pruebas de humo (smoke tests):** verificar endpoints críticos tras el despliegue.
7. **Monitoreo post-despliegue:** revisar logs y métricas durante las primeras horas.
8. **Plan de rollback:** mantener el build anterior disponible para revertir en caso de fallo crítico.

### Ejercicio 12: Despliegue en servidor de producción (ejemplo con GitHub Actions + Azure)

    name: Deploy Inventario API

    on:
      push:
        branches: [main]

    jobs:
      build-and-deploy:
        runs-on: ubuntu-latest
        steps:
          - uses: actions/checkout@v4
          - name: Setup .NET
            uses: actions/setup-dotnet@v4
            with:
              dotnet-version: '9.0.x'
          - name: Restore
            run: dotnet restore
          - name: Build
            run: dotnet build --configuration Release --no-restore
          - name: Publish
            run: dotnet publish -c Release -o ./publish
          - name: Deploy to Azure Web App
            uses: azure/webapps-deploy@v3
            with:
              app-name: 'inventario-api'
              publish-profile: ${{ secrets.AZURE_PUBLISH_PROFILE }}
              package: ./publish

---

## 7. Mantenimiento

### Ejercicio 13: Plan de Mantenimiento

| Tipo | Descripción | Frecuencia |
|------|-------------|------------|
| Correctivo | Corrección de bugs reportados por usuarios | Según prioridad (crítico: inmediato) |
| Preventivo | Revisión de logs, performance y actualización de dependencias | Mensual |
| Adaptativo | Adaptación a cambios de infraestructura (ej. nuevas versiones de .NET) | Semestral |
| Perfectivo | Mejoras de UX o nuevas funcionalidades solicitadas | Por sprint/versión |
| Backups | Verificación de copias de seguridad de la base de datos | Diario (automatizado) |

### Ejercicio 14: Corrección de errores (ejemplo)

**Problema detectado:** el sistema permite ingresar stock inicial negativo, generando inconsistencias en los reportes.

    // Antes
    public async Task<Producto> CrearProductoAsync(ProductoDto dto)
    {
        // no validaba stock negativo
        ...
    }

    // Corrección aplicada
    public async Task<Producto> CrearProductoAsync(ProductoDto dto)
    {
        if (dto.Stock < 0)
            throw new ArgumentException("El stock inicial no puede ser negativo.");

        if (dto.StockMinimo < 0)
            throw new ArgumentException("El stock mínimo no puede ser negativo.");

        // resto de la lógica...
    }

Se agrega además una prueba unitaria de regresión:

    [Fact]
    public async Task CrearProducto_ConStockNegativo_DeberiaLanzarExcepcion()
    {
        var repoMock = new Mock<IProductoRepository>();
        var service = new ProductoService(repoMock.Object);
        var dto = new ProductoDto("Webcam", "desc", 5000, -3, 1, 1);

        await Assert.ThrowsAsync<ArgumentException>(() => service.CrearProductoAsync(dto));
    }

---

## 8. Nos preparamos para nuevos retos

### Ejercicio 15: Equipo de trabajo para un dominio de IA Generativa

**Dominio propuesto:** Plataforma de generación asistida de contenido (texto/imágenes) para pymes.

| Rol | Responsabilidad |
|-----|------------------|
| **Product Owner** | Define la visión del producto, prioriza el backlog, valida requisitos con el cliente. |
| **Analista Funcional** | Releva requisitos, redacta casos de uso e historias de usuario relacionados con prompts, modelos y flujos de generación. |
| **Arquitecto de Software** | Diseña la arquitectura (integración con APIs de modelos de IA, manejo de costos, colas de procesamiento asíncrono). |
| **Desarrollador Backend** | Implementa la lógica de negocio, integración con proveedores de IA, persistencia de resultados. |
| **Desarrollador Frontend** | Construye la interfaz para que el usuario ingrese prompts y visualice resultados. |
| **Ingeniero de Datos / MLOps** | Gestiona el versionado de modelos, monitoreo de calidad de las respuestas generadas, costos de inferencia. |
| **QA / Tester** | Diseña pruebas funcionales y de regresión, incluyendo evaluación de calidad de las salidas generadas. |
| **DevOps / SRE** | Gestiona el despliegue, escalabilidad y monitoreo en producción. |
| **Especialista en Ética/Seguridad de IA** | Revisa riesgos de sesgo, contenido inapropiado, cumplimiento normativo. |

**Notas sobre el ciclo de vida en este nuevo dominio:**
- El **análisis de requerimientos** debe incluir criterios de calidad de las respuestas generadas, no solo funcionalidad.
- El **diseño** debe considerar la latencia y el costo variable de las llamadas a modelos de IA.
- Las **pruebas** deben incorporar evaluación cualitativa (revisión humana o métricas automáticas) además de pruebas unitarias tradicionales.
- El **mantenimiento** debe contemplar el reentrenamiento o actualización de modelos y el monitoreo continuo de deriva (drift) en la calidad de las respuestas.

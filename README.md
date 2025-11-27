# Guía Paso a Paso: GA-1.6 Entrega Proyecto Fase 1 en GitHub

## Índice

1. [Introducción](#introducción)
2. [Paso 1: Configuración Inicial del Repositorio](#paso-1-configuración-inicial-del-repositorio)
3. [Paso 2: Configurar GitHub Issues y Labels](#paso-2-configurar-github-issues-y-labels)
4. [Paso 3: Crear GitHub Projects](#paso-3-crear-github-projects)
5. [Paso 4: Preparar Documentación](#paso-4-preparar-documentación)
6. [Paso 5: Trabajo Colaborativo con Git](#paso-5-trabajo-colaborativo-con-git-continuo)
7. [Paso 6: Mantener Coherencia](#paso-6-mantener-coherencia-durante-todo-el-sprint)
8. [Paso 7: Preparación Final para Entrega](#paso-7-preparación-final-para-entrega)
9. [Paso 8: Entrega](#paso-8-entrega)
10. [Errores Comunes a Evitar](#errores-comunes-a-evitar)
11. [Troubleshooting](#troubleshooting)
12. [Comandos Git Rápidos](#comandos-git-rápidos)
13. [Recursos Adicionales](#recursos-adicionales)

---

## Introducción

Esta guía te llevará paso a paso para completar la entrega de la Fase 1 del proyecto de Ingeniería de Software usando GitHub de manera profesional.

**Proyecto:** Marketplaces Agrícola - Sistema de gestión para distribución de productos agrícolas

**Equipo:** Dario Valarezo, Charlie Cárdenas Toledo, Lorena Conde, Milton Palacios

**Tiempo estimado:** 3-4 horas de trabajo colaborativo

**IMPORTANTE:** Para el día de hoy se debe realizar al menos un commit con 3 Historias de Usuario creadas en GitHub Issues.

---

## Paso 1: Configuración Inicial del Repositorio

### 1.1 Crear el Repositorio

1. Ve a [GitHub](https://github.com)
2. Click en el botón verde "New" o "+" → "New repository"
3. Configura:
   - **Repository name:** `marketplaces-agricola`
   - **Description:** Sistema de gestión para distribución de productos agrícolas
   - **Visibility:** Public
   - **Initialize:** Add a README file
   - **Add .gitignore:** Node (selecciona según tu tecnología)

### 1.2 Agregar Colaboradores

Si el repositorio es privado:
1. Ve a Settings → Collaborators
2. Click "Add people"
3. Buscar y agregar: **CharlieCardenasToledo**
4. Agregar a todos los miembros del equipo

### 1.3 Crear Estructura de Carpetas

```bash
git clone [URL-de-tu-repositorio]
cd [nombre-repositorio]

# Crear estructura
mkdir docs src tests

# Agregar archivos .gitkeep para que Git reconozca las carpetas vacías
touch docs/.gitkeep src/.gitkeep tests/.gitkeep

# Commit inicial de estructura
git add .
git commit -m "chore: setup initial project structure"
git push origin main
```

**Notas importantes:**
- **`.gitkeep`**: Git no rastrea carpetas vacías. Este archivo placeholder permite versionar la estructura de carpetas sin contenido.
- **`chore:`**: Prefijo para commits de mantenimiento, configuración y cambios que no modifican el código de producción (ejemplos: configuración de herramientas, estructura de carpetas, dependencias, scripts de build)

### 1.4 Crear Ramas Principales

```bash
# Crear rama develop
git checkout -b develop
git push -u origin develop

# Volver a main
git checkout main
```

---

## Paso 2: Configurar GitHub Issues y Labels

### 2.1 Crear Labels Personalizados

1. Ve a tu repositorio → **Issues** → **Labels**
2. Click "New label" y crea los siguientes:

**Tipo:**
- `feature` - Color: #0052CC
- `user-story` - Color: #5319E7
- `bug` - Color: #D73A4A
- `documentation` - Color: #0075CA

**Prioridad:**
- `priority:must-have` - Color: #B60205
- `priority:should-have` - Color: #D93F0B
- `priority:could-have` - Color: #FBCA04
- `priority:wont-have` - Color: #FFFFFF

**Story Points:**
- `sp:1` - Color: #C2E0C6
- `sp:2` - Color: #BFDADC
- `sp:3` - Color: #BFD4F2
- `sp:5` - Color: #C5DEF5
- `sp:8` - Color: #D4C5F9

**Nota sobre Story Points (SP):**
- Los Story Points son una unidad de medida relativa para estimar el esfuerzo, complejidad y tiempo necesario para completar una Historia de Usuario
- Se usa la secuencia de Fibonacci (1, 2, 3, 5, 8) donde números mayores indican mayor complejidad
- Ejemplos:
  - SP:1 - Tarea muy simple (ej: cambiar un texto, agregar un campo simple)
  - SP:2 - Tarea simple (ej: crear un componente básico de UI)
  - SP:3 - Tarea moderada (ej: crear un formulario con validaciones)
  - SP:5 - Tarea compleja (ej: implementar autenticación completa)
  - SP:8 - Tarea muy compleja (ej: integración con API externa y manejo de errores)

### 2.2 Crear Milestones (Épicas)

1. Ve a **Issues** → **Milestones** → "New milestone"
2. Crea Milestones para tus Épicas principales

**Ejemplo para Marketplaces Agrícola:**

**Milestone 1:**
- **Título:** Gestión de Usuarios y Autenticación
- **Description:** Funcionalidades de registro, login y gestión de perfiles de agricultores, distribuidores y clientes
- **Due date:** (opcional)

**Milestone 2:**
- **Título:** Catálogo de Productos Agrícolas
- **Description:** Gestión de inventario, categorías y búsqueda de productos agrícolas

**Milestone 3:**
- **Título:** Sistema de Pedidos y Entregas
- **Description:** Carrito de compras, procesamiento de pedidos y seguimiento de entregas

**Milestone 4:**
- **Título:** Panel de Administración
- **Description:** Dashboard, reportes y gestión de operaciones

### 2.3 Crear Issues (Historias de Usuario)

**Formato de Historias de Usuario:**
```
Como [tipo de usuario], quiero [acción], para [beneficio]
```

**Formato Gherkin para Criterios de Aceptación:**

Gherkin es un lenguaje estructurado para definir comportamientos esperados usando tres palabras clave:
- **Dado que** (Given): Contexto inicial o precondición
- **Cuando** (When): Acción que se ejecuta
- **Entonces** (Then): Resultado esperado

Este formato asegura que todos entiendan exactamente qué debe hacer el sistema.

---

1. Ve a **Issues** → "New issue"
2. Usa el formato:

**Ejemplo 1 - HU-001: Registro de Agricultor**

**Título:** HU-001: Registro de agricultor en la plataforma

**Descripción:**
```markdown
## Historia de Usuario
Como agricultor, quiero registrarme en la plataforma con mis datos de finca y productos, para poder vender mis cosechas directamente a distribuidores.

## Criterios de Aceptación

- **Dado que** un agricultor accede a la página de registro
- **Cuando** completa el formulario con nombre, cédula, ubicación de finca, productos que cultiva y certificaciones
- **Entonces** debe recibir un correo de verificación y su cuenta queda en estado "pendiente de aprobación"

- **Dado que** el agricultor no completa campos obligatorios
- **Cuando** intenta enviar el formulario
- **Entonces** debe ver mensajes de validación indicando los campos faltantes

- **Dado que** el agricultor ya está registrado
- **Cuando** intenta registrarse nuevamente con la misma cédula
- **Entonces** debe ver mensaje "Esta cédula ya está registrada"

## Notas Técnicas
- Validar cédula ecuatoriana (10 dígitos)
- Geocodificar ubicación de finca
- Almacenar certificaciones orgánicas/agrícolas
```

**Ejemplo 2 - HU-002: Catálogo de productos agrícolas**

**Título:** HU-002: Ver catálogo de productos agrícolas disponibles

**Descripción:**
```markdown
## Historia de Usuario
Como distribuidor, quiero ver el catálogo de productos agrícolas disponibles con precios y cantidades, para seleccionar los productos que necesito comprar.

## Criterios de Aceptación

- **Dado que** un distribuidor accede al catálogo
- **Cuando** visualiza la lista de productos
- **Entonces** debe ver nombre del producto, categoría, precio por unidad, cantidad disponible, ubicación del agricultor y foto

- **Dado que** el distribuidor busca un producto específico
- **Cuando** usa el filtro de búsqueda por nombre o categoría
- **Entonces** debe ver solo los productos que coinciden con el criterio

- **Dado que** el distribuidor selecciona un producto
- **Cuando** hace click en el detalle
- **Entonces** debe ver información completa: descripción, agricultor productor, certificaciones, fecha de cosecha estimada

## Notas Técnicas
- Categorías: Frutas, Verduras, Granos, Tubérculos, Lácteos
- Ordenar por: precio, distancia, disponibilidad
- Imágenes optimizadas (max 500KB)
```

**Ejemplo 3 - HU-003: Realizar pedido de productos**

**Título:** HU-003: Realizar pedido de productos agrícolas

**Descripción:**
```markdown
## Historia de Usuario
Como distribuidor, quiero agregar productos al carrito y realizar un pedido, para coordinar la compra y entrega de productos agrícolas.

## Criterios de Aceptación

- **Dado que** el distribuidor selecciona productos
- **Cuando** los agrega al carrito especificando cantidades
- **Entonces** debe ver el resumen con subtotal, IVA y total a pagar

- **Dado que** el distribuidor completa el carrito
- **Cuando** procede al checkout
- **Entonces** debe poder seleccionar método de pago (transferencia, efectivo en entrega) y dirección de entrega

- **Dado que** el distribuidor confirma el pedido
- **Cuando** hace click en "Confirmar pedido"
- **Entonces** debe recibir número de orden, los agricultores deben ser notificados, y el pedido aparece en "Mis pedidos"

## Notas Técnicas
- Validar stock disponible antes de confirmar
- Generar número único de orden
- Enviar notificación email/SMS a agricultores
- Calcular ruta óptima de entrega
```

3. Asignar:
   - **Labels:** `user-story`, `priority:must-have`, `sp:3`
   - **Milestone:** Gestión de Usuarios y Autenticación (para HU-001) o el correspondiente
   - **Assignees:** Miembro(s) responsable(s)

4. Crear más Historias de Usuario (mínimo 10-12 HU):
   - HU-004: Login de usuario (agricultor/distribuidor/admin)
   - HU-005: Gestión de perfil de agricultor
   - HU-006: Publicar nueva cosecha disponible
   - HU-007: Seguimiento de estado de pedido
   - HU-008: Dashboard de administrador con estadísticas
   - HU-009: Reportes de ventas por agricultor
   - HU-010: Sistema de calificaciones y reseñas
   - HU-011: Notificaciones de nuevos productos
   - HU-012: Gestión de métodos de pago

---

## Paso 3: Crear GitHub Projects

### 3.1 Crear Project "Product Backlog"

1. Ve a tu repositorio → **Projects** → "New project"
2. Selecciona plantilla "Table"
3. Nombre: **Product Backlog**
4. Configura campos personalizados:
   - Click en "+" junto a los encabezados
   - Agregar campo "Priority" (Single select: Must, Should, Could, Won't)
   - Agregar campo "Story Points" (Number)
   - Agregar campo "Status" (Single select: Backlog, Ready, In Progress, Done)

5. Agregar todos los Issues:
   - Click "+ Add item"
   - Buscar y agregar cada issue creado

6. Ordenar por prioridad (Must-have primero)

### 3.2 Crear Project "Sprint 1"

1. Crear nuevo proyecto → plantilla "Board"
2. Nombre: **Sprint 1**
3. Configurar columnas:
   - Renombrar columnas: `To Do`, `In Progress`, `In Review`, `Done`

4. Agregar Issues seleccionados para Sprint 1:
   - Selecciona 3-5 HU según capacidad del equipo
   - Click "+ Add items" → seleccionar los issues
   - Distribuir en la columna "To Do"

5. Agregar descripción al proyecto:
   - Click en los "..." del proyecto → "Settings"
   - En README/Description documentar:
     ```markdown
     ## Sprint 1 - Marketplaces Agrícola (Semana 1-2)

     ### Objetivo
     Implementar funcionalidades básicas de registro, autenticación y visualización de catálogo de productos agrícolas

     ### Historias Seleccionadas
     - HU-001: Registro de agricultor en la plataforma (SP: 5)
     - HU-002: Ver catálogo de productos agrícolas (SP: 3)
     - HU-004: Login de usuario (agricultor/distribuidor) (SP: 3)
     - HU-006: Publicar nueva cosecha disponible (SP: 3)

     ### Capacidad del Equipo
     - 4 integrantes (Dario Valarezo, Charlie Cárdenas Toledo, Lorena Conde, Milton Palacios)
     - Disponibilidad: 12 horas por persona
     - Velocidad estimada: 3.5 SP por persona
     - Total Sprint: 14 SP

     ### Justificación
     Se seleccionaron estas HU porque:
     - Son la base fundamental del sistema (autenticación y catálogo)
     - Tienen prioridad "must-have"
     - Permiten validar la propuesta de valor del producto
     - Representan el flujo principal: agricultor publica → distribuidor ve productos
     ```

### 3.3 Agregar Task Lists a Issues del Sprint

1. Editar cada Issue del Sprint 1
2. Agregar sección de tareas:

**Ejemplo para HU-001: Registro de agricultor**

```markdown
## Tareas

### Análisis y Diseño
- [ ] Revisar RF-001 a RF-005 del SRS sobre registro de usuarios
- [ ] Diseñar mockup de formulario de registro en Figma
- [ ] Definir modelo de datos: tabla Agricultores (id, nombre, cedula, email, telefono, ubicacion_finca, productos[], certificaciones[], estado)
- [ ] Diseñar flujo de verificación de correo

### Implementación Backend
- [ ] Crear modelo Agricultor en Mongoose/Sequelize
- [ ] Implementar endpoint POST /api/auth/register-agricultor
- [ ] Validar formato de cédula ecuatoriana (10 dígitos)
- [ ] Integrar servicio de geocodificación para ubicación de finca
- [ ] Configurar envío de email de verificación con token
- [ ] Implementar endpoint GET /api/auth/verify-email/:token

### Implementación Frontend
- [ ] Crear componente RegistroAgricultorForm.jsx
- [ ] Implementar validación de formulario con Formik/React Hook Form
- [ ] Agregar selector de productos (checkboxes: Tomate, Brócoli, Papa, etc.)
- [ ] Implementar upload de certificaciones (PDF, max 2MB)
- [ ] Integrar mapa para seleccionar ubicación de finca
- [ ] Mostrar mensaje de éxito y redirección a verificación de email

### Documentación
- [ ] Actualizar README con proceso de registro
- [ ] Documentar endpoint en Swagger: POST /api/auth/register-agricultor
- [ ] Agregar ejemplos de request/response en documentación API

### Testing
- [ ] Test unitario: validación de cédula ecuatoriana
- [ ] Test unitario: creación de agricultor en BD
- [ ] Test integración: flujo completo de registro
- [ ] Test E2E: registro desde interfaz y verificación de email
- [ ] Pruebas manuales con datos reales

### Gestión
- [ ] Daily stand-up: reportar avance diario
- [ ] Actualizar estado en GitHub Projects (mover a In Progress/Done)
- [ ] Code review por otro miembro del equipo
```

**Ejemplo para HU-002: Ver catálogo de productos**

```markdown
## Tareas

### Análisis y Diseño
- [ ] Revisar RF-008 a RF-012 del SRS sobre catálogo
- [ ] Diseñar mockup de vista de catálogo (grid/lista)
- [ ] Definir modelo Producto (id, nombre, categoria, precio, cantidad_disponible, unidad, agricultor_id, foto_url, fecha_cosecha)
- [ ] Diseñar sistema de filtros y búsqueda

### Implementación Backend
- [ ] Crear modelo Producto
- [ ] Implementar endpoint GET /api/productos (con paginación, filtros, ordenamiento)
- [ ] Implementar endpoint GET /api/productos/:id (detalle)
- [ ] Agregar filtros: categoria, precio_min, precio_max, distancia
- [ ] Implementar búsqueda por nombre
- [ ] Configurar upload de imágenes a S3/Cloudinary

### Implementación Frontend
- [ ] Crear componente CatalogoProductos.jsx
- [ ] Crear componente ProductoCard.jsx
- [ ] Implementar grid responsivo (4 cols desktop, 2 cols tablet, 1 col mobile)
- [ ] Agregar barra de filtros (categoría, rango de precio)
- [ ] Implementar búsqueda en tiempo real
- [ ] Crear componente DetalleProducto.jsx (modal o página)
- [ ] Agregar indicador de distancia desde ubicación del distribuidor

### Documentación
- [ ] Documentar endpoints GET /api/productos y GET /api/productos/:id
- [ ] Agregar ejemplos de filtros en documentación

### Testing
- [ ] Test unitario: filtrado por categoría
- [ ] Test unitario: búsqueda por nombre
- [ ] Test integración: paginación del catálogo
- [ ] Test E2E: flujo completo de visualización y filtrado

### Gestión
- [ ] Daily stand-up diario
- [ ] Actualizar GitHub Projects
```

---

## Paso 4: Preparar Documentación

### 4.1 Actualizar README.md

Edita el archivo README.md en la raíz:

```markdown
# Marketplaces Agrícola

Sistema de gestión y distribución de productos agrícolas que conecta agricultores locales directamente con distribuidores mayoristas, eliminando intermediarios y garantizando precios justos y productos frescos.

## Integrantes

- **Dario Valarezo** - Full Stack Developer - @dariovalarezo
- **Charlie Cárdenas Toledo** - Full Stack Developer - @CharlieCardenasToledo
- **Lorena Conde** - Full Stack Developer - @lorenaconde
- **Milton Palacios** - Full Stack Developer - @miltonpalacios

## Enlaces a GitHub Projects

- [Product Backlog](https://github.com/CharlieCardenasToledo/evaluaciones-is/projects/1)
- [Sprint 1](https://github.com/CharlieCardenasToledo/evaluaciones-is/projects/2)

## Definition of Ready (DoR)

Una Historia de Usuario está lista para ser trabajada cuando:
- Tiene criterios de aceptación claros en formato Gherkin
- Está estimada con story points
- Tiene prioridad asignada (must/should/could/wont-have)
- No tiene dependencias bloqueantes con otras HU
- Los diseños/mockups están disponibles (si aplica)
- El equipo entiende completamente lo que se debe hacer

## Definition of Done (DoD)

Una Historia de Usuario está completa cuando:
- El código está implementado y funciona correctamente
- Los tests unitarios y de integración pasan exitosamente (coverage > 80%)
- La documentación técnica está actualizada (README, API docs)
- La HU cumple todos los criterios de aceptación en formato Gherkin
- No hay bugs críticos o bloqueantes
- Los commits están vinculados al issue (#número)
- El estado del issue está actualizado en GitHub Projects

## Capacidad del Equipo

- **Integrantes:** 4 personas
- **Disponibilidad:** 12 horas por persona por sprint (2 semanas)
- **Velocidad estimada:** 3.5 SP por persona = 14 SP total por sprint
- **Sprint duration:** 2 semanas

## Convenciones

Ver [Paso 1](#paso-1-configuración-inicial-del-repositorio) para convenciones de ramas y commits, y [Paso 2](#paso-2-configurar-github-issues-y-labels) para labels.

## Instalación

```bash
# Clonar repositorio
git clone [URL]
cd [nombre-repo]

# Instalar dependencias
npm install  # o el comando según tu tecnología

# Configurar variables de entorno
cp .env.example .env

# Ejecutar
npm start
```

## Estructura del Proyecto

```
├── docs/           # Documentación del proyecto
│   └── SRS.pdf     # Especificación de Requerimientos
├── src/            # Código fuente
├── tests/          # Tests unitarios e integración
├── .gitignore      # Archivos ignorados por git
└── README.md       # Este archivo
```

## Tecnologías

- **Frontend:** React 18, Tailwind CSS, React Router, Axios
- **Backend:** Node.js, Express.js, MongoDB, Mongoose
- **Autenticación:** JWT, bcrypt
- **Storage:** Cloudinary (imágenes de productos)
- **Maps:** Google Maps API (geocodificación de fincas)
- **Testing:** Jest, React Testing Library, Supertest
- **DevOps:** Docker, GitHub Actions (CI/CD)

## Funcionalidades Principales

- Registro y gestión de perfiles (agricultores, distribuidores, administradores)
- Catálogo de productos agrícolas con filtros avanzados
- Sistema de pedidos y seguimiento de entregas
- Notificaciones en tiempo real
- Dashboard administrativo con reportes y estadísticas
- Sistema de calificaciones y reseñas
- Gestión de inventario y cosechas
```

### 4.2 Subir Documento SRS

```bash
# Copiar tu SRS actualizado a la carpeta docs
cp ruta/al/SRS_NombreProyecto.pdf docs/

# O crear versión markdown
# Editar docs/SRS.md con tu contenido

# Commit
git add docs/
git commit -m "docs: add updated SRS document"
git push origin main
```

---

## Paso 5: Trabajo Colaborativo con Git (Continuo)

### 5.1 Flujo de Trabajo para Cada Tarea

**Ejemplo: Dario trabajando en HU-001 (Registro de agricultor)**

```bash
# 1. Actualizar repositorio
git checkout develop
git pull origin develop

# 2. Crear rama para la funcionalidad
git checkout -b feature/registro-agricultor

# 3. Trabajar en el código
# ... crear modelo Agricultor, endpoints, validaciones ...

# 4. Hacer commits frecuentes y descriptivos
git add backend/models/Agricultor.js
git commit -m "feat: add Agricultor model with validations #1"

git add backend/routes/auth.js backend/controllers/authController.js
git commit -m "feat: implement register-agricultor endpoint #1"

git add backend/utils/validacionCedula.js
git commit -m "feat: add ecuadorian ID validation utility #1"

git add backend/services/emailService.js
git commit -m "feat: implement email verification service #1"

git add backend/tests/auth.test.js
git commit -m "test: add unit tests for agricultor registration #1"

# 5. Subir cambios
git push -u origin feature/registro-agricultor

# 6. Actualizar Issue en GitHub Projects
# - Ir al Project "Sprint 1"
# - Arrastrar HU-001 de "To Do" a "In Progress"
# - Editar el issue y marcar tareas completadas:
#   [x] Crear modelo Agricultor
#   [x] Implementar endpoint POST /api/auth/register-agricultor
#   [x] Validar cédula ecuatoriana
```

**Ejemplo: Charlie trabajando en HU-002 (Catálogo de productos)**

```bash
git checkout develop
git pull origin develop
git checkout -b feature/catalogo-productos

# Trabajo en frontend y backend
git add frontend/src/components/CatalogoProductos.jsx
git commit -m "feat: create product catalog component with filters #2"

git add backend/routes/productos.js
git commit -m "feat: add productos endpoints with pagination #2"

git add frontend/src/components/ProductoCard.jsx
git commit -m "feat: create product card component #2"

git push -u origin feature/catalogo-productos
```

### 5.2 Integrar Cambios a Develop

```bash
# Opción 1: Merge directo (simple)
git checkout develop
git merge feature/registro-agricultor
git push origin develop

# Opción 2: Pull Request (recomendado pero opcional)
# - Crear PR en GitHub desde feature/registro-agricultor hacia develop
# - Pedir code review a un compañero (otro miembro del equipo)
# - Hacer merge cuando esté aprobado
```

### 5.3 Actualizar Estado en GitHub Projects

1. Ve al Project "Sprint 1"
2. Arrastra el Issue a la columna correspondiente:
   - "In Progress" cuando empiezas a trabajar
   - "In Review" cuando pides revisión
   - "Done" cuando está completado según DoD

3. En el Issue, marca las tareas completadas:
   - Editar el issue
   - Cambiar `- [ ]` por `- [x]` en las tareas completadas

---

## Paso 6: Mantener Coherencia (Durante todo el Sprint)

### 6.1 Checklist Diario

Cada día, verifica:

- [ ] Todos los commits están vinculados a issues (#número)
- [ ] Los commits usan la convención correcta (feat:, fix:, etc.)
- [ ] El estado en GitHub Projects refleja el trabajo real
- [ ] Todos los integrantes tienen commits recientes
- [ ] Las task lists están actualizadas

### 6.2 Sincronización del Equipo

Daily stand-up (5-10 minutos):
1. ¿Qué hice ayer?
2. ¿Qué haré hoy?
3. ¿Tengo algún bloqueante?

Actualizar en GitHub:
- Comentar en los Issues si hay bloqueantes
- Actualizar task lists
- Mover cards en el Project Board

---

## Paso 7: Preparación Final para Entrega

### 7.1 Verificación de Completitud

Revisa que tengas:

**Repositorio:**
- [x] Repositorio público o CharlieCardenasToledo agregado
- [x] README.md completo con toda la información
- [x] Estructura /docs, /src, /tests
- [x] .gitignore configurado
- [x] SRS actualizado en /docs

**GitHub Issues:**
- [x] Milestones creados
- [x] Mínimo 8-10 Issues (Historias de Usuario)
- [x] Formato correcto: "Como [rol], quiero [acción], para [beneficio]"
- [x] Criterios de aceptación Gherkin en cada HU
- [x] Labels asignados (tipo, prioridad, SP)

**GitHub Projects:**
- [x] Project "Product Backlog" con todos los issues
- [x] Project "Sprint 1" con tablero Kanban
- [x] Issues del Sprint con task lists completas
- [x] Justificación de selección en descripción del proyecto

**Flujo Git:**
- [x] Ramas main, develop, feature/* creadas
- [x] Commits con convención feat/fix/docs/etc.
- [x] Commits vinculados a issues (#número)
- [x] Todos los integrantes con contribuciones visibles
- [x] Commits distribuidos en el tiempo (no todo el último día)

**Coherencia:**
- [x] El SRS coincide con los Issues
- [x] Los Issues están en GitHub Projects
- [x] Los commits referencian los Issues
- [x] El README tiene enlaces funcionales a Projects

### 7.2 Revisión en Equipo

1. Cada miembro revisa una sección diferente
2. Compartir pantalla y revisar juntos:
   - Insights > Contributors (verificar que todos aparezcan)
   - Insights > Network (verificar flujo de ramas)
   - Projects (verificar organización)
   - Issues (verificar formato y criterios)

3. Corregir errores encontrados

---

## Paso 8: Entrega

### 8.1 Obtener URL del Repositorio

```
https://github.com/[usuario]/[nombre-repositorio]
```

### 8.2 Entregar en la Plataforma

1. Copiar la URL del repositorio
2. Ir a la plataforma de la universidad
3. Pegar URL en el campo de entrega
4. Verificar que la URL funcione (click en ella para probar)

### 8.3 Verificación Post-Entrega

1. Abre el repositorio en modo incógnito (para ver como lo ve el docente)
2. Verifica que:
   - El repositorio sea accesible
   - Los enlaces a Projects funcionen
   - Los documentos se vean correctamente

---

## Errores Comunes a Evitar

NO HACER:
- Crear todo el contenido el último día
- Hacer un solo commit masivo
- Olvidar vincular commits con issues (#número)
- Dejar integrantes sin contribuciones
- Issues sin criterios de aceptación
- Repositorio inaccesible para el docente
- README vacío o sin enlaces
- Task lists vacías en los Issues del Sprint

SI HACER:
- Trabajar de forma incremental
- Commits pequeños y frecuentes
- Todos los integrantes participando
- Issues completos con criterios Gherkin
- Mantener Projects actualizados
- Coherencia entre SRS, Issues y código

---

## Troubleshooting

### Problemas Comunes con Git

**Error: "Permission denied (publickey)"**
```bash
# Verificar que tienes configurada tu clave SSH
ssh -T git@github.com

# Si no tienes clave SSH, generarla:
ssh-keygen -t ed25519 -C "tu-email@ejemplo.com"
# Luego agregar la clave a GitHub: Settings → SSH and GPG keys
```

**Error: "Your branch is behind 'origin/main'"**
```bash
# Sincronizar tu rama local con la remota
git pull origin main
```

**Error: "Merge conflict"**
```bash
# 1. Identificar archivos en conflicto
git status

# 2. Abrir archivos y resolver conflictos manualmente
# Buscar marcadores: <<<<<<< HEAD, =======, >>>>>>>

# 3. Después de resolver
git add archivo-resuelto.js
git commit -m "fix: resolve merge conflict"
```

**Error: "fatal: not a git repository"**
```bash
# Estás en el directorio equivocado. Navega al repositorio:
cd ruta/al/repositorio
# O inicializa uno nuevo:
git init
```

**Deshacer el último commit (sin perder cambios)**
```bash
git reset --soft HEAD~1
```

**Ver historial de commits**
```bash
git log --oneline --graph --all
```

### Problemas con GitHub

**No veo mi proyecto en GitHub Projects**
- Verifica que agregaste los Issues al proyecto usando "+ Add item"
- Refresca la página (F5)

**Los colaboradores no pueden acceder al repositorio**
- Verifica en Settings → Collaborators que estén agregados
- Si es privado, asegúrate de que aceptaron la invitación

**Las imágenes no se ven en el README**
- Usa rutas relativas: `![imagen](./docs/imagen.png)`
- O URLs absolutas de GitHub: `![imagen](https://github.com/usuario/repo/blob/main/imagen.png)`

---

## Comandos Git Rápidos

```bash
# Ver estado actual
git status

# Ver cambios no guardados
git diff

# Agregar todos los cambios
git add .

# Commit rápido
git commit -m "mensaje"

# Ver ramas
git branch -a

# Cambiar de rama
git checkout nombre-rama

# Crear y cambiar a nueva rama
git checkout -b nueva-rama

# Actualizar desde remoto
git pull origin main

# Subir cambios
git push origin nombre-rama

# Ver historial
git log --oneline

# Descartar cambios locales de un archivo
git checkout -- archivo.js

# Ver quién modificó cada línea de un archivo
git blame archivo.js
```

---

## Recursos Adicionales

- [Documentación GitHub Projects](https://docs.github.com/en/issues/planning-and-tracking-with-projects)
- [Documentación GitHub Issues](https://docs.github.com/en/issues)
- [Guía de Markdown](https://guides.github.com/features/mastering-markdown/)
- [Conventional Commits](https://www.conventionalcommits.org/)

---

## Soporte

Si tienes dudas:
1. Revisa esta guía completa
2. Consulta la documentación oficial de GitHub
3. Pregunta en clase o al docente
4. Discute con tu equipo en el repositorio (usando Issues o Discussions)

---

**¡Éxito en tu entrega!**

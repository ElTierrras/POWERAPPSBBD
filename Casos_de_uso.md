# 🎭 Diagrama de Casos de Uso – Power Apps Sistema de Control Contractual y Presupuestal

## 1. Actores
- **Administrador:** Cesar Romero, Jhojan Cubillos  
- **Usuario Lectura:** Natalia Gonzales Foglia, Luisa Pedraza Duque  
- **Usuario Especial (Lectura y Edición):** Giovanna Rojas (Jefa)  

---

## 2. Tabla de Casos de Uso

| Caso de Uso | Actor(es) | Descripción | Requerimientos Funcionales Asociados | Flujo Básico |
|-------------|-----------|-------------|--------------------------------------|--------------|
| Registrar Contratos | Administrador | Permite ingresar un nuevo contrato con todos sus datos (vigencia, anexos, obligaciones). | RF1 – Gestión de Contratos | 1. Admin accede al módulo → 2. Ingresa datos → 3. Guarda contrato → 4. Sistema confirma registro |
| Consultar Contratos | Lectura, Admin, Jefa | Permite buscar contratos por NIT o razón social y visualizar su estado. | RF1 – Gestión de Contratos | 1. Usuario accede al módulo → 2. Ingresa criterio de búsqueda → 3. Sistema muestra resultados |
| Registrar Proveedores | Administrador | Permite ingresar datos generales y documentos legales de proveedores. | RF2 – Gestión de Proveedores | 1. Admin accede al módulo → 2. Ingresa datos → 3. Guarda proveedor → 4. Sistema confirma |
| Consultar Proveedores | Lectura, Admin, Jefa | Permite visualizar información de proveedores y su relación con contratos. | RF2 – Gestión de Proveedores | 1. Usuario accede → 2. Selecciona proveedor → 3. Sistema muestra información |
| Visualizar Presupuesto | Lectura, Admin, Jefa | Permite consultar asignaciones, compromisos y saldos desde Power BI filtrado por NIT. | RF3 – Gestión Presupuestal | 1. Usuario accede → 2. Ingresa NIT → 3. Sistema muestra datos desde Power BI |
| Configurar Alertas | Administrador | Permite definir alertas de vencimiento (<3 meses) y ejecución ≥70%. | RF4 – Alertas y Notificaciones | 1. Admin accede → 2. Configura parámetros → 3. Sistema activa alertas |
| Generar Memorandos | Admin, Jefa | Permite crear memorandos semiautomáticos con campos comunes y pantalla editable. | RF4 – Alertas y Notificaciones | 1. Usuario accede → 2. Sistema reúne campos → 3. Usuario completa → 4. Memorando generado |
| Editar Contratos/Proveedores | Jefa (usuario especial) | Permite modificar información de contratos y proveedores. | RF1, RF2 | 1. Jefa accede → 2. Selecciona registro → 3. Edita → 4. Guarda cambios |
| Auditoría de Modificaciones | Administrador | Registra cambios realizados en contratos/proveedores. (Opcional) | RF5 – Seguridad y Acceso | 1. Admin accede → 2. Sistema registra cambios → 3. Reporte disponible |

---

## 3. Diagrama de Casos de Uso (Mermaid)

```mermaid
flowchart LR
    actorAdmin[Administrador]
    actorLectura[Usuario Lectura]
    actorJefa[Usuario Especial - Jefa]

    actorAdmin --> UC1[Registrar Contratos]
    actorAdmin --> UC2[Registrar Proveedores]
    actorAdmin --> UC3[Configurar Alertas]
    actorAdmin --> UC4[Generar Memorandos]
    actorAdmin --> UC5[Acceso Presupuesto]

    actorLectura --> UC6[Consultar Contratos]
    actorLectura --> UC7[Consultar Proveedores]
    actorLectura --> UC8[Visualizar Presupuesto]

    actorJefa --> UC9[Editar Contratos]
    actorJefa --> UC10[Editar Proveedores]
    actorJefa --> UC11[Generar Memorandos]

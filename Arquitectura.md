# Diagrama de Arquitectura – Power Apps Sistema de Control Contractual y Presupuestal

## 1. Descripción General
El sistema se construye sobre **Power Apps** como interfaz principal, con integración a **Power BI**, **correo corporativo**, y futura conexión con **SAP Sourcing**. La arquitectura contempla módulos de contratos, proveedores, presupuesto, alertas, memorandos y seguridad, cada uno con flujos específicos.

---

## 2. Componentes Principales
- **Frontend (Power Apps):**
  - Formularios de registro y consulta.
  - Pantallas de edición y generación de memorandos.
  - Interfaz de alertas y notificaciones.
- **Backend (Lógica de Negocio):**
  - Validación de datos.
  - Reglas de seguridad y permisos.
  - Procesamiento de alertas y auditoría.
- **Base de Datos:**
  - Tablas de contratos, proveedores, presupuesto, auditoría.
  - Relación entre entidades por NIT.
- **Integraciones:**
  - **Power BI:** visualización de presupuesto.
  - **Correo corporativo:** envío de alertas.
  - **SAP Sourcing:** integración futura con gestión de compras.

---

## 3. Flujo de Procesos

### 3.1 Contratos
1. Administrador de Contratos accede al módulo.  
2. Ingresa datos (NIT, razón social, fechas, valor).  
3. Adjunta documentos.  
4. Sistema valida y guarda en BD.  
5. Contrato queda disponible para consulta.  

### 3.2 Proveedores
1. Administrador de Contratos registra proveedor.  
2. Ingresa NIT, nombre, documentos legales.  
3. Sistema valida y guarda en BD.  
4. Proveedor queda vinculado a contratos.  

### 3.3 Presupuesto
1. Administrador de Presupuesto accede al módulo.  
2. Ingresa NIT.  
3. Sistema consulta Power BI.  
4. Devuelve asignaciones, compromisos y saldos.  
5. Usuario visualiza ejecución.  

### 3.4 Alertas
1. Administrador de Presupuesto configura parámetros (ejecución ≥70%).  
2. Administrador de Contratos configura alertas de vencimiento (<3 meses).  
3. Sistema valida condiciones.  
4. Envía correo a responsables.  
5. Registra alerta en BD.  

### 3.5 Memorandos
1. Administrador de Contratos o Permiso Especial accede al módulo.  
2. Sistema reúne campos comunes del contrato.  
3. Usuario completa información faltante.  
4. Sistema genera documento final.  

### 3.6 Auditoría
1. Cualquier acción de registro/edición dispara evento.  
2. Sistema guarda log en tabla de auditoría.  
3. Administrador puede consultar historial.  

---

## 4. Roles y Permisos
- **Administrador de Contratos:** acceso exclusivo a contratos, proveedores, memorandos, auditoría.  
- **Administrador de Presupuesto:** acceso exclusivo a presupuesto, alertas, auditoría.  
- **Usuario Lectura:** acceso solo a consultas (contratos, proveedores, presupuesto).  
- **Permiso Especial:** acceso a edición de contratos/proveedores y generación de memorandos.  

---

## 5. Requerimientos No Funcionales
- **Seguridad:** control de acceso por roles, confidencialidad, auditoría.  
- **Disponibilidad:** alta disponibilidad y respaldo.  
- **Usabilidad:** interfaz intuitiva y clara.  
- **Rendimiento:** consultas y registros en <2 segundos.  
- **Mantenibilidad:** código modular y documentado.  
- **Integración:** Power BI y futura conexión con SAP Sourcing.  

---

## 6. Diagrama de Arquitectura (Mermaid)

```mermaid
flowchart TB
    %% Actores
    AdminContratos([Administrador de Contratos])
    AdminPresupuesto([Administrador de Presupuesto])
    Lectura([Usuario Lectura])
    Especial([Permiso Especial])

    %% Frontend
    subgraph Frontend[Power Apps - Interfaz]
        UI[Interfaz de Usuario]
    end

    %% Backend
    subgraph Backend[Lógica de Negocio]
        Validacion[Validación de Datos]
        Reglas[Reglas de Seguridad]
        Procesos[Procesamiento de Alertas y Auditoría]
    end

    %% Base de Datos
    subgraph BD[Base de Datos]
        Contratos[(Tabla Contratos)]
        Proveedores[(Tabla Proveedores)]
        Presupuesto[(Tabla Presupuesto)]
        Auditoria[(Tabla Auditoría)]
    end

    %% Integraciones
    BI[Power BI]
    Mail[Correo Corporativo]
    SAP[SAP Sourcing]

    %% Conexiones de actores
    AdminContratos --> UI
    AdminPresupuesto --> UI
    Lectura --> UI
    Especial --> UI

    %% Conexiones internas
    UI --> Backend
    Backend --> BD
    Backend --> BI
    Backend --> Mail
    Backend --> SAP

# Diagrama de Componentes – Power Apps

## 1. Descripción General
El sistema se compone de **Frontend (Power Apps), Backend (lógica de negocio), Base de Datos y servicios de integración externos**. Cada componente cumple un rol específico en la gestión de contratos, proveedores, presupuesto, alertas, memorandos y auditoría.

---

## 2. Componentes Principales

- **Frontend (Power Apps):**
  - Interfaz de usuario para registro, consulta, edición y generación de memorandos.
  - Pantallas de configuración de alertas y visualización de presupuesto.
  - Validaciones iniciales de formularios.

- **Backend (Lógica de Negocio):**
  - Procesa reglas de seguridad y permisos por rol.
  - Evalúa condiciones de alertas (ejecución ≥70%, vencimiento <3 meses).
  - Orquesta la generación de memorandos.
  - Registra acciones en auditoría.

- **Base de Datos:**
  - Tablas de contratos, proveedores, presupuesto, alertas, memorandos y auditoría.
  - Garantiza integridad referencial y trazabilidad.
  - Optimizada con índices en NIT y fechas.

- **Integraciones:**
  - **Power BI:** provee datos de ejecución presupuestal.
  - **Correo Corporativo:** envía notificaciones de alertas.
  - **SAP Sourcing (futuro):** integración con gestión de compras.

---

## 3. Flujo de Procesos por Componentes

1. **Usuario → Frontend:**  
   Accede a módulos de contratos, proveedores, presupuesto o alertas.  

2. **Frontend → Backend:**  
   Envía datos ingresados y solicitudes de consulta.  

3. **Backend → Base de Datos:**  
   Valida existencia de registros, guarda contratos/proveedores, registra auditoría.  

4. **Backend → Power BI:**  
   Solicita ejecución y saldos filtrados por NIT.  

5. **Backend → Correo Corporativo:**  
   Envía alertas automáticas a responsables.  

6. **Backend → SAP Sourcing (futuro):**  
   Integra datos de compras y proveedores externos.  

---

## 4. Diagrama de Componentes

```mermaid
flowchart TB
    %% Frontend
    subgraph Frontend[Frontend - Power Apps]
        UI[Interfaz de Usuario]
    end

    %% Backend
    subgraph Backend[Backend - Lógica de Negocio]
        Logic[Reglas de Negocio]
        Validacion[Validación de Datos]
        AuditoriaProc[Procesamiento de Auditoría]
        AlertasProc[Procesamiento de Alertas]
        MemorandosProc[Generación de Memorandos]
    end

    %% Base de Datos
    subgraph BD[Base de Datos]
        Contratos[(Tabla Contratos)]
        Proveedores[(Tabla Proveedores)]
        Presupuesto[(Tabla Presupuesto)]
        Alertas[(Tabla Alertas)]
        Memorandos[(Tabla Memorandos)]
        Auditoria[(Tabla Auditoría)]
    end

    %% Integraciones
    subgraph Integraciones[Servicios Externos]
        BI[Power BI]
        Mail[Correo Corporativo]
        SAP[SAP Sourcing]
    end

    %% Conexiones
    UI --> Logic
    Logic --> Validacion
    Logic --> AuditoriaProc
    Logic --> AlertasProc
    Logic --> MemorandosProc

    Logic --> Contratos
    Logic --> Proveedores
    Logic --> Presupuesto
    Logic --> Alertas
    Logic --> Memorandos
    Logic --> Auditoria

    Logic --> BI
    Logic --> Mail
    Logic --> SAP

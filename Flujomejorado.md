# 📊 Diagrama de Flujo – Power Apps Sistema de Control Contractual y Presupuestal

```mermaid
flowchart TD

    %% Inicio y Seguridad
    A[Inicio de Sesión] --> B{Validación Grupo Seguridad}
    B -->|No autorizado| Z[Acceso Denegado]
    B -->|Autorizado| C[Menú Principal]

    %% Menú Principal
    C --> D[Gestión de Contratos]
    C --> E[Gestión de Proveedores]
    C --> F[Gestión Presupuestal]
    C --> G[Alertas y Notificaciones]
    C --> H[Generación de Memorandos]
    C --> I[Seguridad y Auditoría]
    C --> J[Integración con otras Apps]
    C --> K[Cierre de Sesión]

    %% Contratos
    D --> D1[Registro completo de contratos]
    D1 --> D2[Búsqueda avanzada por NIT o razón social]
    D2 --> D3[Visualización integral: estado, valor, vigencia]
    D3 --> D4{¿Contrato vence en menos de 3 meses?}
    D4 -->|Sí| G
    D4 -->|No| C

    %% Proveedores
    E --> E1[Registro de datos generales y documentos legales]
    E1 --> E2[Relación proveedor–contrato]
    E2 --> E3[Evaluación de participación en proyectos]

    %% Presupuesto
    F --> F1[Conexión con Power BI]
    F1 --> F2[Identificación por NIT]
    F2 --> F3[Registro de asignaciones, compromisos y pagos]
    F3 --> F4[Consulta de saldos disponibles]
    F4 --> F5{¿Ejecución ≥ 70%?}
    F5 -->|Sí| G
    F5 -->|No| C

    %% Alertas
    G --> G1[Generar alerta automática]
    G1 --> G2[Enviar correo a responsables]
    G2 --> G3[Registrar alerta en sistema]

    %% Memorandos
    H --> H1[Reunir campos comunes del contrato]
    H1 --> H2[Pantalla editable para completar información]
    H2 --> H3[Generar documento final]

    %% Seguridad y Auditoría
    I --> I1[Control de acceso por roles y permisos]
    I1 --> I2[Confidencialidad garantizada]
    I2 --> I3[Registro de auditoría de modificaciones opcional]

    %% Integración
    J --> J1[Conexión con Power BI]
    J --> J2[Integración futura con SAP Sourcing]
    J --> J3[Conexión con otras Apps VP]

    %% Cierre
    K --> L[Registro de actividad]
    L --> M[Fin del Flujo]

    %% Roles
    subgraph Roles
        RA[Administrador: Cesar Romero, Jhojan Cubillos]
        RL[Lectura: Natalia Gonzales Foglia, Luisa Pedraza Duque]
        RE[Lectura y Edición: Giovanna Rojas]
    end

    %% Relación de roles con seguridad
    RA --> B
    RL --> B
    RE --> B

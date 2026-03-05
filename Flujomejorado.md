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
    C --> G[Alertas Automáticas]
    C --> H[Generación de Memorandos]
    C --> I[Auditoría Opcional]
    C --> J[Integración con otras Apps]
    C --> K[Cierre de Sesión]

    %% Contratos
    D --> D1[Registro/Consulta de Contratos]
    D1 --> D2{¿Contrato vence en < 3 meses?}
    D2 -->|Sí| G
    D2 -->|No| C

    %% Proveedores
    E --> E1[Registro de Proveedores]
    E1 --> E2[Relación Proveedor-Contrato]
    E2 --> E3[Consulta Historial]

    %% Presupuesto
    F --> F1[Conexión con Power BI]
    F1 --> F2[Identificación por NIT]
    F2 --> F3{¿Ejecución ≥ 70%?}
    F3 -->|Sí| G
    F3 -->|No| C

    %% Alertas
    G --> G1[Generar Alerta]
    G1 --> G2[Enviar Correo a Responsables]
    G2 --> G3[Registrar Alerta en Sistema]

    %% Memorandos
    H --> H1[Reunir Campos Comunes]
    H1 --> H2[Pantalla Editable para Usuario]
    H2 --> H3[Generar Documento Final]

    %% Auditoría Opcional
    I --> I1[Registro de Modificaciones]
    I1 --> C

    %% Integración
    J --> J1[Conexión con Apps VP]
    J1 --> C

    %% Cierre
    K --> L[Registro de Actividad]
    L --> M[Fin del Flujo]

    %% Roles
    subgraph Roles
        RA[Administrador: Cesar Romero, Jhojan Cubillos]
        RL[Lectura: Natalia Gonzales Foglia, Luisa Pedraza Duque]
        RE[Lectura y Edición: Giovanna Rojas (Jefa)]
    end

    %% Relación de roles con seguridad
    RA --> B
    RL --> B
    RE --> B

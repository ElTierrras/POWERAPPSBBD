```mermaid
flowchart TB
    %% Definición del sistema
    subgraph Sistema[Power Apps]
        UC1[Registrar Contratos]
        UC2[Consultar Contratos]
        UC3[Registrar Proveedores]
        UC4[Consultar Proveedores]
        UC5[Visualizar Presupuesto]
        UC6[Configurar Alertas]
        UC7[Generar Memorandos]
        UC8[Editar Contratos/Proveedores]
        UC9[Auditoría de Modificaciones]
    end

    %% Actores a la izquierda
    AdminContratos([Administrador de Contratos]) --- UC1
    AdminContratos --- UC2
    AdminContratos --- UC3
    AdminContratos --- UC4
    AdminContratos --- UC7
    AdminContratos --- UC8
    AdminContratos --- UC9

    AdminPresupuesto([Administrador de Presupuesto]) --- UC5
    AdminPresupuesto --- UC6
    AdminPresupuesto --- UC9

    %% Actores a la derecha
    Lectura([Usuario Lectura]) --- UC2
    Lectura --- UC4
    Lectura --- UC5

    Especial([Permiso Especial]) --- UC2
    Especial --- UC4
    Especial --- UC5
    Especial --- UC7
    Especial --- UC8

# Diagrama de Casos de Uso

```mermaid
flowchart LR
    subgraph Sistema[Power Apps Sistema]
        UC1[Registrar Contratos]
        UC2[Consultar Contratos]
        UC3[Registrar Proveedores]
        UC4[Consultar Proveedores]
        UC5[Visualizar Presupuesto]
        UC6[Configurar Alertas]
        UC7[Generar Memorandos]
        UC8[Editar Contratos]
        UC9[Editar Proveedores]
        UC10[Auditoría de Modificaciones]
    end

    Admin([Administrador]) --> UC1
    Admin --> UC2
    Admin --> UC3
    Admin --> UC4
    Admin --> UC5
    Admin --> UC6
    Admin --> UC7
    Admin --> UC10

    Lectura([Usuario Lectura]) --> UC2
    Lectura --> UC4
    Lectura --> UC5

    Jefa([Usuario Especial - Giovanna Rojas]) --> UC2
    Jefa --> UC4
    Jefa --> UC5
    Jefa --> UC7
    Jefa --> UC8
    Jefa --> UC9

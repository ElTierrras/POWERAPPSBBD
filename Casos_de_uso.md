# 🎭 Diagrama de Casos de Uso – Power Apps

```mermaid
usecaseDiagram
    actor Admin as "Administrador"
    actor Lectura as "Usuario Lectura"
    actor Editor as "Usuario Especial (Jefa)"

    Admin --> (Registrar Contratos)
    Admin --> (Registrar Proveedores)
    Admin --> (Configurar Alertas)
    Admin --> (Generar Memorandos)
    Admin --> (Acceso Presupuesto Power BI)

    Lectura --> (Consultar Contratos)
    Lectura --> (Consultar Proveedores)
    Lectura --> (Visualizar Presupuesto)

    Editor --> (Editar Contratos)
    Editor --> (Editar Proveedores)
    Editor --> (Generar Memorandos)

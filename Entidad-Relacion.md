# Diagrama Entidad-Relación – Base de Datos

## 1. Descripción General
El modelo de datos soporta los módulos de **Contratos, Proveedores, Presupuesto, Alertas, Memorandos y Auditoría**. Cada entidad está diseñada para garantizar trazabilidad, seguridad y consultas eficientes.

---

## 2. Entidades y Atributos

```mermaid
erDiagram
    CONTRATO {
        int id PK
        string nit
        string razon_social
        date fecha_inicio
        date fecha_fin
        float valor
        string estado
        string anexos
    }

    PROVEEDOR {
        int id PK
        string nit
        string nombre
        string documentos
        string tipo
    }

    PRESUPUESTO {
        int id PK
        string nit
        float asignacion
        float compromiso
        float pago
        float saldo
    }

    ALERTA {
        int id PK
        string tipo
        string descripcion
        date fecha_generacion
        string estado
    }

    MEMORANDO {
        int id PK
        int contrato_id FK
        string asunto
        string contenido
        date fecha_emision
    }

    AUDITORIA {
        int id PK
        string entidad
        string accion
        string usuario
        date fecha
        string detalle
    }

    USUARIO {
        int id PK
        string nombre
        string rol
        string correo
    }

    ROL {
        int id PK
        string nombre
        string descripcion
    }

    PERMISO {
        int id PK
        string modulo
        string accion
    }

    USUARIO ||--o{ ROL : "tiene"
    ROL ||--o{ PERMISO : "define"

    CONTRATO ||--o{ PROVEEDOR : "asociado a"
    CONTRATO ||--o{ PRESUPUESTO : "relacionado con"
    CONTRATO ||--o{ MEMORANDO : "genera"

    ALERTA ||--o{ CONTRATO : "aplica a"
    ALERTA ||--o{ PRESUPUESTO : "aplica a"

    AUDITORIA ||--o{ USUARIO : "registrada por"
    AUDITORIA ||--o{ CONTRATO : "sobre"
    AUDITORIA ||--o{ PROVEEDOR : "sobre"
    AUDITORIA ||--o{ PRESUPUESTO : "sobre"

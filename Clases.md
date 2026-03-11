# Diagrama de Clases – Power Apps Sistema Contractual y Presupuestal

## 1. Descripción General
El modelo de clases representa la estructura lógica del sistema, incluyendo las entidades principales (Contratos, Proveedores, Presupuesto, Alertas, Memorandos, Auditoría y Usuarios), sus atributos y métodos, y las relaciones entre ellas.

---

## 2. Detalles de Clases

- **Contrato:** gestiona registro, consulta, edición y eliminación de contratos.  
- **Proveedor:** almacena datos de proveedores y permite edición.  
- **Presupuesto:** maneja asignaciones, compromisos, pagos y saldos; vinculado a alertas.  
- **Alerta:** evalúa condiciones y envía notificaciones.  
- **Memorando:** genera documentos vinculados a contratos.  
- **Auditoría:** registra todas las acciones realizadas en el sistema.  
- **Usuario:** representa a los actores del sistema, autenticación y consultas.  
- **Rol y Permiso:** definen el modelo de seguridad y control de accesos.  

---

## 3. Consideraciones Técnicas
- **Encapsulación:** cada clase maneja sus propios métodos y atributos.  
- **Herencia futura:** posible extensión de `Usuario` para roles específicos.  
- **Integridad:** todas las acciones se registran en `Auditoría`.  
- **Seguridad:** control de acceso mediante `Rol` y `Permiso`.  

---


## 4. Diagrama de Clases (Mermaid)

```mermaid
classDiagram
    class Contrato {
        +int id
        +string nit
        +string razonSocial
        +date fechaInicio
        +date fechaFin
        +float valor
        +string estado
        +string anexos
        +registrar()
        +consultar()
        +editar()
        +eliminar()
    }

    class Proveedor {
        +int id
        +string nit
        +string nombre
        +string documentos
        +string tipo
        +registrar()
        +consultar()
        +editar()
    }

    class Presupuesto {
        +int id
        +string nit
        +float asignacion
        +float compromiso
        +float pago
        +float saldo
        +visualizar()
        +configurarAlertas()
    }

    class Alerta {
        +int id
        +string tipo
        +string descripcion
        +date fechaGeneracion
        +string estado
        +evaluarCondiciones()
        +enviarCorreo()
    }

    class Memorando {
        +int id
        +int contratoId
        +string asunto
        +string contenido
        +date fechaEmision
        +generar()
        +editar()
    }

    class Auditoria {
        +int id
        +string entidad
        +string accion
        +string usuario
        +date fecha
        +string detalle
        +registrarEvento()
        +consultarLog()
    }

    class Usuario {
        +int id
        +string nombre
        +string correo
        +string rol
        +autenticar()
        +consultar()
    }

    class Rol {
        +int id
        +string nombre
        +string descripcion
        +asignarPermisos()
    }

    class Permiso {
        +int id
        +string modulo
        +string accion
    }

    %% Relaciones
    Contrato --> Proveedor : "asociado a"
    Contrato --> Presupuesto : "impacta"
    Contrato --> Memorando : "genera"
    Contrato --> Auditoria : "registrado en"

    Proveedor --> Auditoria : "registrado en"
    Presupuesto --> Alerta : "dispara"
    Presupuesto --> Auditoria : "registrado en"

    Memorando --> Auditoria : "registrado en"
    Alerta --> Auditoria : "registrado en"

    Usuario --> Rol : "tiene"
    Rol --> Permiso : "define"
    Usuario --> Auditoria : "ejecuta acción"

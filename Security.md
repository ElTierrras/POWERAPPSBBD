# Diagrama de Seguridad y Roles

## 1. Descripción General
El sistema implementa un modelo de seguridad basado en **roles y permisos**, garantizando que cada usuario tenga acceso únicamente a los módulos que le corresponden. La trazabilidad se asegura mediante auditoría y control de accesos.

---

## 2. Roles y Usuarios

- **Administrador (Grupo Seguridad):**
  - Cesar Romero  
  - Jhojan Cubillos  
  - Acceso completo a configuración de seguridad y administración de usuarios.  

- **Lectura:**
  - Natalia Gonzales Foglia  
  - Luisa Pedraza Duque  
  - Acceso únicamente a consultas de contratos, proveedores y presupuesto.  

- **Permiso Especial:**
  - Giovanna Rojas
  - Acceso a edición de contratos/proveedores y generación de memorandos.  

---

## 3. Módulos Protegidos
- **Contratos:** registro, consulta, edición.  
- **Proveedores:** registro, consulta, edición.  
- **Presupuesto:** visualización y alertas.  
- **Alertas:** configuración y notificaciones.  
- **Memorandos:** generación y edición.  

---

# Mapa de Permisos – Power Apps

## Descripción General
El sistema define permisos específicos por rol, garantizando que cada usuario solo pueda realizar las operaciones que le corresponden en cada módulo. Se utiliza el modelo **CRUD (Crear, Leer, Actualizar, Eliminar)** para detallar los accesos.

---

## Tabla de Permisos por Rol

| Módulo        | Administrador (Cesar Romero, Jhojan Cubillos) | Lectura (Natalia Gonzales, Luisa Pedraza) | Permiso Especial (Giovanna Rojas) |
|---------------|-----------------------------------------------|-------------------------------------------|-----------------------------------|
| **Contratos** | C, R, U, D                                   | R                                         | R, U                              |
| **Proveedores** | C, R, U, D                                 | R                                         | R, U                              |
| **Presupuesto** | R, U (configuración alertas)                | R                                         | R                                 |
| **Alertas**   | C, R, U, D                                   | –                                         | –                                 |
| **Memorandos** | C, R, U, D                                  | –                                         | C, R, U                           |
| **Auditoría** | R                                             | –                                         | –                                 |

---

## Detalles Específicos

- **Administrador:**  
  - Control total sobre contratos, proveedores, alertas y memorandos.  
  - Puede crear, consultar, actualizar y eliminar registros.  
  - Acceso de solo lectura a auditoría.  

- **Lectura:**  
  - Acceso únicamente a consultas de contratos, proveedores y presupuesto.  
  - No puede crear, editar ni eliminar.  

- **Permiso Especial (Jefa):**  
  - Puede consultar y editar contratos y proveedores.  
  - Puede generar y editar memorandos.  
  - Acceso de solo lectura a presupuesto.  
  - No tiene acceso a alertas ni auditoría.  

---

## Consideraciones Técnicas

- **Seguridad:** cada acción se valida en el backend antes de ejecutarse.  
- **Auditoría:** todas las operaciones CRUD quedan registradas con usuario, fecha y acción.  
- **Escalabilidad:** se pueden agregar nuevos roles y permisos sin modificar la estructura actual.  
- **Trazabilidad:** el mapa de permisos se integra con el diagrama de seguridad y roles.  

---

## 4. Diagrama de Seguridad y Roles (Mermaid)

```mermaid
flowchart LR
    %% Roles
    RA[Administrador: Cesar Romero, Jhojan Cubillos]
    RL[Lectura: Natalia Gonzales Foglia, Luisa Pedraza Duque]
    RE[Permiso Especial: Giovanna Rojas]

    %% Grupo de Seguridad
    Access[Grupo Seguridad]

    %% Sistema
    subgraph PowerApp[Power Apps]
        Contratos[Contratos]
        Proveedores[Proveedores]
        Presupuesto[Presupuesto]
        Alertas[Alertas]
        Memorandos[Memorandos]
    end

    %% Conexiones
    RA --> Access
    RL --> Access
    RE --> Access

    Access --> Contratos
    Access --> Proveedores
    Access --> Presupuesto
    Access --> Alertas
    Access --> Memorandos

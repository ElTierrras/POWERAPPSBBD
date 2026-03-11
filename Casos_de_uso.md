# 🎭 Diagrama de Casos de Uso – Power Apps Sistema de Control Contractual y Presupuestal

## 1. Actores
- **Administrador:** Cesar Romero, Jhojan Cubillos  
- **Usuario Lectura:** Natalia Gonzales Foglia, Luisa Pedraza Duque  
- **Usuario Especial (Lectura y Edición):** Giovanna Rojas (Jefa)  

---

## 2. Tabla de Casos de Uso

### Caso de Uso: Registrar Contratos
- **Actor(es):** Administrador  
- **Descripción:** Permite ingresar un nuevo contrato con todos sus datos (vigencia, anexos, obligaciones, modificaciones).  
- **Flujo Principal:**  
  1. Admin accede al módulo de contratos.  
  2. Ingresa datos obligatorios (NIT, razón social, fechas, valor).  
  3. Adjunta documentos.  
  4. Guarda contrato.  
  5. Sistema confirma registro.  
- **Camino Alternativo:** Si faltan datos obligatorios, el sistema muestra mensaje de error y no guarda.  
- **Excepciones:** Error de conexión con base de datos.  
- **Dependencias:** Requiere que el proveedor esté registrado previamente.  
- **Visualización del Módulo:** Formulario con campos estructurados, botones de guardar y cancelar, lista de contratos registrados.  

---

### Caso de Uso: Consultar Contratos
- **Actor(es):** Administrador, Lectura, Jefa  
- **Descripción:** Permite buscar contratos por NIT o razón social y visualizar su estado.  
- **Flujo Principal:**  
  1. Usuario accede al módulo.  
  2. Ingresa criterio de búsqueda.  
  3. Sistema muestra resultados con estado, valor y vigencia.  
- **Camino Alternativo:** Si no hay resultados, se muestra mensaje “No se encontraron contratos”.  
- **Excepciones:** Error de conexión con base de datos.  
- **Dependencias:** Requiere contratos previamente registrados.  
- **Visualización del Módulo:** Pantalla con barra de búsqueda, filtros y tabla de resultados.  

---

### Caso de Uso: Generar Memorandos
- **Actor(es):** Administrador, Jefa  
- **Descripción:** Permite crear memorandos semiautomáticos con campos comunes y pantalla editable.  
- **Flujo Principal:**  
  1. Usuario accede al módulo de memorandos.  
  2. Sistema reúne campos comunes del contrato.  
  3. Usuario completa información faltante en pantalla editable.  
  4. Memorando se genera en formato documento.  
- **Camino Alternativo:** Usuario cancela antes de guardar.  
- **Excepciones:** Error en la generación del documento.  
- **Dependencias:** Requiere contrato previamente registrado.  
- **Visualización del Módulo:** Pantalla editable con campos prellenados y botón “Generar Memorando”.  

---

*(Se repite la misma estructura para cada caso de uso: Proveedores, Presupuesto, Alertas, Seguridad, etc.)*

---

## 3. Diagrama de Casos de Uso

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

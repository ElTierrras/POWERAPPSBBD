# Diagrama de Secuencia – Alertas y Memorandos

## 1. Descripción General
Este diagrama muestra el flujo de interacción entre los actores (usuarios), el sistema Power Apps, y los servicios externos (Power BI, correo corporativo, generador de documentos). Se incluyen todos los pasos desde la consulta inicial hasta la generación de alertas y memorandos.

---

## 2. Diagrama de Secuencia

```mermaid
sequenceDiagram
    participant U as Usuario (Admin Contratos/Presupuesto, Lectura, Permiso Especial)
    participant App as Power Apps
    participant BI as Power BI
    participant Mail as Correo Corporativo
    participant Doc as Generador de Memorandos
    participant DB as Base de Datos

    %% Consulta de contratos/presupuesto
    U->>App: Solicita consulta de contrato/presupuesto
    App->>DB: Verifica existencia de contrato/proveedor
    DB-->>App: Devuelve datos básicos
    App->>BI: Solicita datos filtrados por NIT
    BI-->>App: Devuelve ejecución, asignaciones y saldos

    %% Evaluación de condiciones para alertas
    App->>App: Evalúa condiciones (vencimiento <3 meses o ejecución ≥70%)
    alt Condiciones cumplidas
        App->>Mail: Envía correo de alerta a responsables
        Mail-->>U: Notificación recibida
        App->>DB: Registra alerta en tabla de auditoría
    else Condiciones no cumplidas
        App-->>U: Muestra mensaje “Sin alertas activas”
    end

    %% Generación de memorandos
    U->>App: Solicita generar memorando
    App->>DB: Reúne campos comunes del contrato
    DB-->>App: Devuelve datos contractuales
    App->>Doc: Envía datos prellenados
    Doc-->>U: Muestra pantalla editable
    U->>Doc: Ingresa datos faltantes
    Doc->>DB: Guarda borrador de memorando
    U->>Doc: Confirma generación
    Doc-->>U: Memorando final generado
    Doc->>DB: Registra memorando vinculado al contrato
    DB-->>App: Actualiza estado del contrato

# ESPECIFICACIÓN DE CASOS DE USO

## Encabezado
- **ID:** UC-01  
- **Nombre:** Registrar Contratos  
- **Tipo:** Obligatorio  
- **Prioridad:** Alta  
- **Actores involucrados:** Administrador  

---

## Descripción del Caso de Uso
Permite al Administrador registrar un nuevo contrato en el sistema, incluyendo vigencia, anexos, obligaciones y modificaciones, garantizando trazabilidad contractual.

---

## Entradas y Salidas
| Entradas | Salidas |
|----------|---------|
| NIT, razón social, fechas, valor, anexos | Contrato registrado, mensaje de confirmación |

---

## Precondiciones y Postcondiciones
| Precondiciones | Postcondiciones |
|----------------|-----------------|
| Usuario autenticado como Administrador | Contrato disponible para consulta |

---

## Dependencias y Extensiones
| Dependencias | Extensiones |
|--------------|-------------|
| UC‑03 Registrar Proveedores | Carga masiva de contratos |

---

## Flujo Normal de Eventos
| No. | Acción del actor | Respuesta del sistema |
|-----|-----------------|-----------------------|
| 1 | Admin accede al módulo | Formulario de registro |
| 2 | Ingresa datos obligatorios | Validación de campos |
| 3 | Adjunta documentos | Guarda anexos |
| 4 | Confirma registro | Guarda contrato y confirma |

---

## Caminos Alternativos
| Flujo normal | Alternativa | Acción | Respuesta |
|--------------|-------------|--------|-----------|
| Paso 2 | Datos incompletos | Intento de guardar | Error de validación |

---

## Caminos de Excepción
- Error de conexión BD  
- NIT inexistente  

---

## Puntos de Extensión
No aplica.  

---

## Criterios de Aceptación
- Registro exitoso con campos obligatorios.  
- Contrato disponible inmediatamente.  

---

## Requerimientos No Funcionales
- Usabilidad: formulario claro.  
- Rendimiento: <2 segundos.  
- Seguridad: solo Administradores.  

---

## Borrador de Interfaz
Formulario con campos NIT, razón social, fechas, valor, anexos. Botones Guardar/Cancelar.  

---

## Seguimiento
| Fecha | Descripción | Gestor |
|-------|-------------|--------|
| 11/03/2026 | Se completa especificación | Líder de Planeación |

---

## Control de Cambios
| Fecha | Descripción | Autor |
|-------|-------------|-------|
|       |             |       |

---

## Encabezado
- **ID:** UC-02  
- **Nombre:** Consultar Contratos  
- **Tipo:** Obligatorio  
- **Prioridad:** Alta  
- **Actores involucrados:** Administrador, Lectura, Permiso Especial  

---

## Descripción
Permite buscar contratos por NIT o razón social y visualizar estado, valor y vigencia.

---

## Entradas y Salidas
| Entradas | Salidas |
|----------|---------|
| Criterio de búsqueda | Lista de contratos filtrados |

---

## Precondiciones y Postcondiciones
| Precondiciones | Postcondiciones |
|----------------|-----------------|
| Usuario autenticado | Contratos visibles |

---

## Dependencias y Extensiones
| Dependencias | Extensiones |
|--------------|-------------|
| UC‑01 Registrar Contratos | Filtros avanzados |

---

## Flujo Normal
| No. | Acción | Respuesta |
|-----|--------|-----------|
| 1 | Usuario accede al módulo | Sistema muestra buscador |
| 2 | Ingresa criterio | Sistema filtra |
| 3 | Selecciona contrato | Sistema muestra detalles |

---

## Caminos Alternativos
| Flujo | Alternativa | Acción | Respuesta |
|-------|-------------|--------|-----------|
| Paso 2 | Sin resultados | Usuario busca | Mensaje “No se encontraron contratos” |

---

## Excepciones
- Error BD  
- Contrato inexistente  

---

## Puntos de Extensión
No aplica.  

---

## Criterios de Aceptación
- Búsqueda por NIT/razón social.  
- Visualización integral.  

---

## RNF
- Usabilidad: filtros claros.  
- Rendimiento: <1 segundo.  

---

## Borrador Interfaz
Pantalla con barra de búsqueda, filtros y tabla de resultados.  

---

## Seguimiento
| Fecha | Descripción | Gestor |
|-------|-------------|--------|
| 11/03/2026 | Especificación completa | Líder Planeación |

---

## Control de Cambios
| Fecha | Descripción | Autor |
|-------|-------------|-------|


---

## Encabezado
- **ID:** UC-03  
- **Nombre:** Registrar Proveedores  
- **Tipo:** Obligatorio  
- **Prioridad:** Alta  
- **Actores involucrados:** Administrador  

---

## Descripción
Permite al Administrador registrar datos generales y documentos legales de un proveedor, vinculándolo con contratos futuros.

---

## Entradas y Salidas
| Entradas | Salidas |
|----------|---------|
| NIT, nombre, documentos legales | Proveedor registrado, mensaje de confirmación |

---

## Precondiciones y Postcondiciones
| Precondiciones | Postcondiciones |
|----------------|-----------------|
| Usuario autenticado como Administrador | Proveedor disponible para relación con contratos |

---

## Dependencias y Extensiones
| Dependencias | Extensiones |
|--------------|-------------|
| Ninguna | Carga masiva de proveedores |

---

## Flujo Normal
| No. | Acción | Respuesta |
|-----|--------|-----------|
| 1 | Admin accede al módulo | Formulario de registro |
| 2 | Ingresa datos obligatorios | Validación |
| 3 | Adjunta documentos | Guarda anexos |
| 4 | Confirma registro | Proveedor guardado |

---

## Caminos Alternativos
| Flujo | Alternativa | Acción | Respuesta |
|-------|-------------|--------|-----------|
| Paso 2 | Datos incompletos | Intento de guardar | Error de validación |

---

## Excepciones
- Error BD  
- NIT duplicado  

---

## Puntos de Extensión
No aplica.  

---

## Criterios de Aceptación
- Registro exitoso con datos obligatorios.  
- Proveedor disponible para contratos.  

---

## RNF
- Usabilidad: formulario claro.  
- Rendimiento: <2 segundos.  
- Seguridad: solo Administradores.  

---

## Borrador Interfaz
Formulario con campos NIT, nombre, documentos. Botones Guardar/Cancelar.  

---

## Seguimiento
| Fecha | Descripción | Gestor |
|-------|-------------|--------|
| 11/03/2026 | Especificación completa | Líder Planeación |

---

## Control de Cambios
| Fecha | Descripción | Autor |
|-------|-------------|-------|


---

## Encabezado
- **ID:** UC-04  
- **Nombre:** Consultar Proveedores  
- **Tipo:** Obligatorio  
- **Prioridad:** Alta  
- **Actores involucrados:** Administrador, Lectura, Permiso Especial  

---

## Descripción
Permite consultar información de proveedores registrados y su relación con contratos.

---

## Entradas y Salidas
| Entradas | Salidas |
|----------|---------|
| Criterio de búsqueda | Información del proveedor |

---

## Precondiciones y Postcondiciones
| Precondiciones | Postcondiciones |
|----------------|-----------------|
| Usuario autenticado | Información visible |

---

## Dependencias y Extensiones
| Dependencias | Extensiones |
|--------------|-------------|
| UC‑03 Registrar Proveedores | Filtros avanzados |

---

## Flujo Normal
| No. | Acción | Respuesta |
|-----|--------|-----------|
| 1 | Usuario accede al módulo | Sistema muestra buscador |
| 2 | Ingresa criterio | Sistema filtra |
| 3 | Selecciona proveedor | Sistema muestra detalles |

---

## Caminos Alternativos
| Flujo | Alternativa | Acción | Respuesta |
|-------|-------------|--------|-----------|
| Paso 2 | Sin resultados | Usuario busca | Mensaje “No se encontraron proveedores” |

---

## Excepciones
- Error BD  
- Proveedor inexistente  

---

## Puntos de Extensión
No aplica.  

---

## Criterios de Aceptación
- Búsqueda por NIT/nombre.  
- Visualización integral.  

---

## RNF
- Usabilidad: filtros claros.  
- Rendimiento: <1 segundo.  

---

## Borrador Interfaz
Pantalla con barra de búsqueda, filtros y tabla de resultados.  

---

## Seguimiento
| Fecha | Descripción | Gestor |
|-------|-------------|--------|
| 11/03/2026 | Especificación completa | Líder Planeación |

---

## Control de Cambios
| Fecha | Descripción | Autor |
|-------|-------------|-------|

---

## Encabezado
- **ID:** UC-05  
- **Nombre:** Visualizar Presupuesto  
- **Tipo:** Obligatorio  
- **Prioridad:** Alta  
- **Actores involucrados:** Administrador, Lectura, Permiso Especial  

---

## Descripción
Permite consultar asignaciones, compromisos y saldos desde Power BI filtrado por NIT.

---

## Entradas y Salidas
| Entradas | Salidas |
|----------|---------|
| NIT | Datos de presupuesto desde Power BI |

---

## Precondiciones y Postcondiciones
| Precondiciones | Postcondiciones |
|----------------|-----------------|
| Usuario autenticado | Datos visibles |

---

## Dependencias y Extensiones
| Dependencias | Extensiones |
|--------------|-------------|
| Integración con Power BI | Integración futura con SAP |

---

## Flujo Normal
| No. | Acción | Respuesta |
|-----|--------|-----------|
| 1 | Usuario accede al módulo | Sistema muestra buscador |
| 2 | Ingresa NIT | Sistema consulta Power BI |
| 3 | Sistema muestra datos | Usuario visualiza |

---

## Caminos Alternativos
| Flujo | Alternativa | Acción | Respuesta |
|-------|-------------|--------|-----------|
| Paso 2 | NIT inválido | Usuario ingresa | Mensaje de error |

---

## Excepciones
- Error conexión Power BI  

---

## Puntos de Extensión
No aplica.  

---

## Criterios de Aceptación
- Consulta por NIT.  
- Visualización integral.  

---

## RNF
- Usabilidad: interfaz clara.  
- Rendimiento: <2 segundos.  

---

## Borrador Interfaz
Pantalla con campo NIT y tabla de resultados.  

---

## Seguimiento
| Fecha | Descripción | Gestor |
|-------|-------------|--------|
| 11/03/2026 | Especificación completa | Líder Planeación |

---

## Control de Cambios
| Fecha | Descripción | Autor |
|-------|-------------|-------|


---

## Encabezado
- **ID:** UC-06  
- **Nombre:** Configurar Alertas  
- **Tipo:** Obligatorio  
- **Prioridad:** Alta  
- **Actores involucrados:** Administrador  

---

## Descripción
Permite configurar alertas automáticas de vencimiento (<3 meses) y ejecución ≥70%.

---

## Entradas y Salidas
| Entradas | Salidas |
|----------|---------|
| Parámetros de alerta | Alerta activa |

---

## Precondiciones y Postcondiciones
| Precondiciones | Postcondiciones |
|----------------|-----------------|
| Usuario autenticado | Alerta configurada |

---

## Dependencias y Extensiones
| Dependencias | Extensiones |
|--------------|-------------|
| UC‑01, UC‑05 | Integración con correo |

---

## Flujo Normal
| No. | Acción | Respuesta |
|-----|--------|-----------|
| 1 | Admin accede al módulo | Sistema muestra formulario |
| 2 | Ingresa parámetros | Sistema valida |
| 3 | Confirma | Sistema guarda configuración |

---

## Caminos Alternativos
| Flujo | Alternativa | Acción | Respuesta |
|-------|-------------|--------|-----------|
| Paso 2 | Datos inválidos | Admin guarda | Error |

---

## Excepciones
- Error BD  

---

## Puntos de Extensión
No aplica.  

---

## Criterios de Aceptación
- Configuración exitosa.  
- Alertas activas.  

---

## RNF
- Usabilidad: interfaz clara.  
- Rendimiento: <1 segundo.  

---

## Borrador Interfaz
Formulario con parámetros de alerta.  

---

## Seguimiento
| Fecha | Descripción | Gestor |
|-------|-------------|--------|
| 11/03/2026 | Especificación completa | Líder Planeación |

---

## Control de Cambios
| Fecha | Descripción | Autor |
|-------|-------------|-------|

---

## Encabezado
- **ID:** UC-07  
- **Nombre:** Generar Memorandos  
- **Tipo:** Obligatorio  
- **Prioridad:** Alta  
- **Actores involucrados:** Administrador, Permiso Especial  

---

## Descripción
Permite crear memorandos semiautomáticos a partir de campos comunes de contratos, con pantalla editable para completar información faltante y generar un documento final.

---

## Entradas y Salidas
| Entradas | Salidas |
|----------|---------|
| Campos comunes del contrato, datos adicionales | Documento de memorando generado |

---

## Precondiciones y Postcondiciones
| Precondiciones | Postcondiciones |
|----------------|-----------------|
| Usuario autenticado | Memorando disponible para descarga o envío |

---

## Dependencias y Extensiones
| Dependencias | Extensiones |
|--------------|-------------|
| UC‑01 Registrar Contratos | Integración con correo electrónico |

---

## Flujo Normal
| No. | Acción | Respuesta |
|-----|--------|-----------|
| 1 | Usuario accede al módulo | Sistema reúne campos comunes |
| 2 | Usuario completa información | Sistema valida |
| 3 | Usuario confirma | Sistema genera documento |

---

## Caminos Alternativos
| Flujo | Alternativa | Acción | Respuesta |
|-------|-------------|--------|-----------|
| Paso 2 | Usuario cancela | Cancela edición | Memorando no generado |

---

## Excepciones
- Error en generación del documento.  

---

## Puntos de Extensión
No aplica.  

---

## Criterios de Aceptación
- Memorando generado con campos obligatorios.  
- Documento editable antes de confirmación.  

---

## RNF
- Usabilidad: interfaz editable clara.  
- Rendimiento: generación <2 segundos.  

---

## Borrador Interfaz
Pantalla editable con campos prellenados y botón “Generar Memorando”.  

---

## Seguimiento
| Fecha | Descripción | Gestor |
|-------|-------------|--------|
| 11/03/2026 | Especificación completa | Líder Planeación |

---

## Control de Cambios
| Fecha | Descripción | Autor |
|-------|-------------|-------|

---

## Encabezado
- **ID:** UC-09  
- **Nombre:** Auditoría de Modificaciones  
- **Tipo:** Opcional  
- **Prioridad:** Media  
- **Actores involucrados:** Administrador  

---

## Descripción
Permite registrar cambios realizados en contratos y proveedores para fines de trazabilidad y control interno.

---

## Entradas y Salidas
| Entradas | Salidas |
|----------|---------|
| Acción realizada, usuario, fecha | Registro en log de auditoría |

---

## Precondiciones y Postcondiciones
| Precondiciones | Postcondiciones |
|----------------|-----------------|
| Usuario autenticado | Registro disponible en log |

---

## Dependencias y Extensiones
| Dependencias | Extensiones |
|--------------|-------------|
| UC‑01, UC‑03, UC‑08 | Reportes de auditoría |

---

## Flujo Normal
| No. | Acción | Respuesta |
|-----|--------|-----------|
| 1 | Usuario realiza acción | Sistema captura evento |
| 2 | Sistema guarda en log | Registro disponible |

---

## Caminos Alternativos
No aplica.  

---

## Excepciones
- Error BD  
- Fallo en escritura de log  

---

## Puntos de Extensión
No aplica.  

---

## Criterios de Aceptación
- Registro automático de cambios.  
- Log disponible para consulta.  

---

## RNF
- Seguridad: acceso restringido.  
- Rendimiento: registro inmediato.  

---

## Borrador Interfaz
Pantalla de consulta de auditoría con filtros por fecha y usuario.  

---

## Seguimiento
| Fecha | Descripción | Gestor |
|-------|-------------|--------|
| 11/03/2026 | Especificación completa | Líder Planeación |

---

## Control de Cambios
| Fecha | Descripción | Autor |
|-------|-------------|-------|

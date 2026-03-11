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

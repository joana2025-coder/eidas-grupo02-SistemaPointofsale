# Casos de uso

## Diagrama general

El diagrama representa los principales casos de uso del Sistema POS del Bar Carrefour.

Los actores identificados son:

- **Encargada:** registra pedidos, gestiona el stock y realiza operaciones sobre las mesas.
- **Dueño:** consulta el historial de ventas y los reportes.
- **Proveedor de Pago:** interviene en el procesamiento de pagos electrónicos.

Las relaciones principales son:

- **Registrar pedido** incluye obligatoriamente la autenticación del usuario y la consulta de disponibilidad de stock.
- **Consultar historial de ventas** incluye la autenticación del usuario.
- **Procesar pago**, **Reponer stock a demanda** y **Emitir ticket** extienden otros casos de uso de manera condicional.

El código PlantUML se encuentra en `diagramas/casos-de-uso.puml`.

---

## CU-01 — Registrar pedido

| **Campo** | **Detalle** |
|---|---|
| **Identificador** | CU-01 |
| **Nombre** | Registrar pedido |
| **Descripción** | Permite cargar los productos consumidos por una mesa. |
| **Actores** | Principal: Encargada / Secundario: No aplica |
| **Precondiciones** | La encargada debe haber iniciado sesión. La mesa debe encontrarse ocupada. El sistema debe estar disponible. |
| **Postcondiciones** | Éxito: El pedido queda registrado, los productos quedan asociados a la mesa, el subtotal se actualiza automáticamente y se descuenta el stock. / Fallo: La operación se cancela o se impide agregar productos según la excepción. |

### Secuencia normal

| **#** | **Acción (actor)** | **Reacción (sistema)** |
|---|---|---|
| 1 | La encargada selecciona una mesa ocupada. | El sistema muestra la información de la mesa y el pedido actual. |
| 2 | La encargada selecciona “Agregar pedido”. | El sistema muestra el listado de productos disponibles con su stock. |
| 3 | La encargada selecciona los productos consumidos. | El sistema agrega los productos al pedido. |
| 4 | La encargada confirma el pedido. | El sistema calcula automáticamente el subtotal y descuenta el stock. |
| 5 | La encargada guarda el pedido. | El sistema registra el pedido y actualiza el consumo de la mesa. |

### Excepciones

| **#** | **Situación** | **Respuesta del sistema** |
|---|---|---|
| E1 | Se intenta registrar un pedido sin productos. | El sistema solicita seleccionar al menos un producto. |
| E2 | Se pierde la conexión. | El sistema notifica el error y cancela la operación. |
| E3 | Un producto no tiene stock suficiente. | El sistema impide agregarlo y sugiere un reemplazo. |

| **Campo** | **Detalle** |
|---|---|
| **Rendimiento** | Respuesta inmediata al agregar productos y actualizar el subtotal. |
| **Frecuencia** | Alta: se utiliza cada vez que se registra un pedido. |
| **Importancia** | Alta: es una función principal del sistema. |
| **Urgencia** | Alta: se necesita para registrar los pedidos durante la atención. |

---

## CU-02 — Registrar pago

| **Campo** | **Detalle** |
|---|---|
| **Identificador** | CU-02 |
| **Nombre** | Registrar pago |
| **Descripción** | Permite registrar el pago correspondiente al consumo de una mesa. |
| **Actores** | Principal: Encargada / Secundario: Proveedor de Pago |
| **Precondiciones** | Debe existir una mesa con un consumo registrado y un total a pagar. |
| **Postcondiciones** | Éxito: El sistema registra el pago, libera la mesa y emite el ticket. / Fallo: El pago no se registra y la mesa permanece ocupada hasta completar correctamente la operación. |

### Secuencia normal

| **#** | **Acción (actor)** | **Reacción (sistema)** |
|---|---|---|
| 1 | La encargada selecciona la mesa. | El sistema muestra el total a pagar. |
| 2 | La encargada selecciona el método de pago: efectivo, tarjeta o QR. | El sistema procesa el método seleccionado. |
| 3 | La encargada utiliza tarjeta o QR. | El sistema se comunica con el proveedor de pago electrónico para confirmar la transacción. |
| 4 | — | El sistema registra el pago, libera la mesa y emite el ticket. |

### Excepciones

| **#** | **Situación** | **Respuesta del sistema** |
|---|---|---|
| E1 | El pago electrónico es rechazado. | El sistema informa el rechazo y no registra el pago. |
| E2 | El proveedor de pago no responde. | El sistema informa el error y permite reintentar la operación. |
| E3 | No se selecciona un método de pago. | El sistema solicita seleccionar un método de pago. |

| **Campo** | **Detalle** |
|---|---|
| **Rendimiento** | Respuesta inmediata al registrar el pago. |
| **Frecuencia** | Alta: se utiliza al finalizar cada consumo. |
| **Importancia** | Alta: permite completar la venta. |
| **Urgencia** | Alta: se necesita para finalizar la atención y liberar la mesa. |

---

## CU-03 — Gestionar stock de productos

| **Campo** | **Detalle** |
|---|---|
| **Identificador** | CU-03 |
| **Nombre** | Gestionar stock de productos |
| **Descripción** | Permite dar de alta, modificar productos y reponer stock cuando el sistema emite una alerta de stock bajo. En este caso de uso se desarrolla principalmente la reposición de stock. |
| **Actores** | Principal: Encargada / Secundario: No aplica |
| **Precondiciones** | Debe existir un producto registrado en el sistema y el sistema debe estar disponible. |
| **Postcondiciones** | Éxito: El stock disponible queda actualizado y el producto vuelve a estar habilitado para la venta si estaba deshabilitado por falta de stock. / Fallo: El stock no se actualiza y el producto mantiene su estado anterior. |

### Secuencia normal

| **#** | **Acción (actor)** | **Reacción (sistema)** |
|---|---|---|
| 1 | — | El sistema detecta que un producto llegó al stock mínimo y notifica a la encargada. |
| 2 | La encargada repone el producto y actualiza el stock disponible. | El sistema registra la actualización del stock. |
| 3 | — | El sistema habilita nuevamente el producto para su venta si estaba deshabilitado por falta de stock. |

### Excepciones

| **#** | **Situación** | **Respuesta del sistema** |
|---|---|---|
| E1 | La cantidad ingresada para la reposición no es válida. | El sistema informa el error y solicita ingresar una cantidad válida. |
| E2 | No se puede actualizar el stock. | El sistema informa el error y mantiene el stock anterior. |

| **Campo** | **Detalle** |
|---|---|
| **Rendimiento** | Respuesta inmediata al actualizar el stock. |
| **Frecuencia** | Media: se utiliza cuando se repone mercadería o se modifica un producto. |
| **Importancia** | Alta: permite mantener actualizada la disponibilidad de productos. |
| **Urgencia** | Media: se realiza cuando se detecta la necesidad de reposición. |

---

## CU-04 — Generar cierre de turno

| **Campo** | **Detalle** |
|---|---|
| **Identificador** | CU-04 |
| **Nombre** | Generar cierre de turno |
| **Descripción** | Permite generar un reporte con las ventas realizadas durante el turno, discriminadas por método de pago, y dejarlo disponible para consulta del dueño. |
| **Actores** | Principal: Encargada / Secundario: Dueño |
| **Precondiciones** | Debe haber ventas registradas durante el turno. |
| **Postcondiciones** | Éxito: El sistema totaliza las ventas del turno discriminadas por método de pago y genera el reporte. / Fallo: El cierre no se genera y las ventas del turno permanecen disponibles para una nueva consulta. |

### Secuencia normal

| **#** | **Acción (actor)** | **Reacción (sistema)** |
|---|---|---|
| 1 | Al finalizar el turno, la encargada solicita el cierre de turno. | El sistema inicia el proceso de cierre. |
| 2 | — | El sistema totaliza las ventas del turno discriminadas por método de pago. |
| 3 | — | El sistema genera el reporte y lo deja disponible para consulta del dueño. |

### Excepciones

| **#** | **Situación** | **Respuesta del sistema** |
|---|---|---|
| E1 | No existen ventas registradas durante el turno. | El sistema informa que no hay ventas para incluir en el cierre. |
| E2 | Se produce un error al generar el reporte. | El sistema informa el error y permite volver a intentar. |

| **Campo** | **Detalle** |
|---|---|
| **Rendimiento** | Generación del reporte en pocos segundos. |
| **Frecuencia** | Alta: se utiliza al finalizar cada turno. |
| **Importancia** | Alta: permite controlar las ventas realizadas durante el turno. |
| **Urgencia** | Media: se realiza al finalizar el turno. |
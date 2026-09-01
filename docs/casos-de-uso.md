# Casos de uso

## Diagrama general

El diagrama representa los principales casos de uso del Sistema POS del Bar Carrefour.

Los actores identificados son:

* **Encargada:** registra pedidos, gestiona el stock y realiza operaciones sobre las mesas.
* **Dueño:** consulta el historial de ventas y los reportes.
* **Proveedor de Pago:** interviene en el procesamiento de pagos electrónicos.

Las relaciones principales son:

* **Registrar pedido** incluye obligatoriamente la autenticación del usuario y la consulta de disponibilidad de stock.
* **Consultar historial de ventas** incluye la autenticación del usuario.
* **Procesar pago**, **Reponer stock a demanda** y **Emitir ticket** extienden otros casos de uso de manera condicional.

El código PlantUML se encuentra en `diagramas/casos-de-uso.puml`.

---

## CU-01 — Registrar pedido

| Campo           | Detalle                                                                                                                                                                                                                           |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Identificador   | CU-01                                                                                                                                                                                                                             |
| Nombre          | Registrar pedido                                                                                                                                                                                                                  |
| Descripción     | Permite cargar los productos consumidos por una mesa.                                                                                                                                                                             |
| Actores         | Principal: Encargada / Secundario: No especificado                                                                                                                                                                                |
| Precondiciones  | La encargada debe haber iniciado sesión. La mesa debe encontrarse ocupada. El sistema debe estar disponible.                                                                                                                      |
| Postcondiciones | Éxito: El pedido queda registrado, los productos quedan asociados a la mesa, el subtotal se actualiza automáticamente y se descuenta el stock. / Fallo: La operación se cancela o se impide agregar productos según la excepción. |

### Secuencia normal

| # | Acción (actor)                                    | Reacción (sistema)                                                   |
| - | ------------------------------------------------- | -------------------------------------------------------------------- |
| 1 | La encargada selecciona una mesa ocupada.         | El sistema muestra la información de la mesa y el pedido actual.     |
| 2 | La encargada selecciona “Agregar pedido”.         | El sistema muestra el listado de productos disponibles con su stock. |
| 3 | La encargada selecciona los productos consumidos. | El sistema agrega los productos al pedido.                           |
| 4 | La encargada confirma el pedido.                  | El sistema calcula automáticamente el subtotal y descuenta el stock. |
| 5 | La encargada guarda el pedido.                    | El sistema registra el pedido y actualiza el consumo de la mesa.     |

### Excepciones

| #  | Situación                                     | Respuesta del sistema                                 |
| -- | --------------------------------------------- | ----------------------------------------------------- |
| E1 | Se intenta registrar un pedido sin productos. | El sistema solicita seleccionar al menos un producto. |
| E2 | Se pierde la conexión.                        | El sistema notifica el error y cancela la operación.  |
| E3 | Un producto no tiene stock suficiente.        | El sistema impide agregarlo y sugiere un reemplazo.   |

| Campo       | Detalle         |
| ----------- | --------------- |
| Rendimiento | No especificado |
| Frecuencia  | No especificado |
| Importancia | No especificado |
| Urgencia    | No especificado |

---

## CU-02 — Registrar pago

| Campo           | Detalle                                                                                        |
| --------------- | ---------------------------------------------------------------------------------------------- |
| Identificador   | CU-02                                                                                          |
| Nombre          | Registrar pago                                                                                 |
| Descripción     | Permite registrar el pago correspondiente al consumo de una mesa.                              |
| Actores         | Principal: Encargada / Secundario: Proveedor de Pago                                           |
| Precondiciones  | Debe existir una mesa con un consumo registrado y un total a pagar.                            |
| Postcondiciones | Éxito: El sistema registra el pago, libera la mesa y emite el ticket. / Fallo: No especificado |

### Secuencia normal

| # | Acción (actor)                                                     | Reacción (sistema)                                                                         |
| - | ------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| 1 | La encargada selecciona la mesa.                                   | El sistema muestra el total a pagar.                                                       |
| 2 | La encargada selecciona el método de pago: efectivo, tarjeta o QR. | El sistema procesa el método seleccionado.                                                 |
| 3 | La encargada utiliza tarjeta o QR.                                 | El sistema se comunica con el proveedor de pago electrónico para confirmar la transacción. |
| 4 | —                                                                  | El sistema registra el pago, libera la mesa y emite el ticket.                             |

### Excepciones

| #  | Situación                        | Respuesta del sistema |
| -- | -------------------------------- | --------------------- |
| E1 | No especificada en el documento. | No especificada.      |

| Campo       | Detalle         |
| ----------- | --------------- |
| Rendimiento | No especificado |
| Frecuencia  | No especificado |
| Importancia | No especificado |
| Urgencia    | No especificado |

---

## CU-03 — Gestionar stock de productos

| Campo           | Detalle                                                                                                                                                                 |
| --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Identificador   | CU-03                                                                                                                                                                   |
| Nombre          | Gestionar stock de productos                                                                                                                                            |
| Descripción     | Permite dar de alta, modificar productos y reponer stock cuando el sistema emite una alerta de stock bajo.                                                              |
| Actores         | Principal: Encargada / Secundario: No especificado                                                                                                                      |
| Precondiciones  | Debe existir un producto registrado en el sistema.                                                                                                                      |
| Postcondiciones | Éxito: El stock disponible queda actualizado y el producto vuelve a estar habilitado para la venta si estaba deshabilitado por falta de stock. / Fallo: No especificado |

### Secuencia normal

| # | Acción (actor)                                                   | Reacción (sistema)                                                                                   |
| - | ---------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| 1 | —                                                                | El sistema detecta que un producto llegó al stock mínimo y notifica a la encargada.                  |
| 2 | La encargada repone el producto y actualiza el stock disponible. | El sistema registra la actualización del stock.                                                      |
| 3 | —                                                                | El sistema habilita nuevamente el producto para su venta si estaba deshabilitado por falta de stock. |

### Excepciones

| #  | Situación                        | Respuesta del sistema |
| -- | -------------------------------- | --------------------- |
| E1 | No especificada en el documento. | No especificada.      |

| Campo       | Detalle         |
| ----------- | --------------- |
| Rendimiento | No especificado |
| Frecuencia  | No especificado |
| Importancia | No especificado |
| Urgencia    | No especificado |

---

## CU-04 — Generar cierre de turno

| Campo           | Detalle                                                                                                                        |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Identificador   | CU-04                                                                                                                          |
| Nombre          | Generar cierre de turno                                                                                                        |
| Descripción     | Permite generar un reporte con las ventas realizadas durante el turno.                                                         |
| Actores         | Principal: Encargada / Secundario: Dueño                                                                                       |
| Precondiciones  | Debe haber ventas registradas durante el turno.                                                                                |
| Postcondiciones | Éxito: El sistema totaliza las ventas del turno discriminadas por método de pago y genera el reporte. / Fallo: No especificado |

### Secuencia normal

| # | Acción (actor)                                                   | Reacción (sistema)                                                         |
| - | ---------------------------------------------------------------- | -------------------------------------------------------------------------- |
| 1 | Al finalizar el turno, la encargada solicita el cierre de turno. | El sistema inicia el proceso de cierre.                                    |
| 2 | —                                                                | El sistema totaliza las ventas del turno discriminadas por método de pago. |
| 3 | —                                                                | El sistema genera el reporte y lo deja disponible para consulta del dueño. |

### Excepciones

| #  | Situación                        | Respuesta del sistema |
| -- | -------------------------------- | --------------------- |
| E1 | No especificada en el documento. | No especificada.      |

| Campo       | Detalle         |
| ----------- | --------------- |
| Rendimiento | No especificado |
| Frecuencia  | No especificado |
| Importancia | No especificado |
| Urgencia    | No especificado |
|             |                 |

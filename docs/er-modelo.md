# Modelo Entidad-Relación

## Diagrama



**Diagrama ER:** [Ver diagrama ER](https://www.plantuml.com/plantuml/svg/bPDHRXCn48RVVGe_8-q5ggfgI8E88B1A5rwZwNeQhDgUQ3pxWB8S2d64Nep6Yv6pn4ZDI-J_dvt_yzY-ZG8iWtTAYHM7UaC67UbL46l0D5jqqDldNq4t-jv6GG-w_NoltmBh9J3Z8msi50Qnybr_YGEm9NrK-kNtHbkp6_v8LthzgTFNr-s7cvlaDatw2-GV65_ihuljylrYcyJyqRdQKn26YCy_OUOmkKBvyPTdWn5A68yHwYI3HwQY9gaO1GnTxDwYiORA_eUaL1CUiVzswdstw5RTUhDAOXmUX0JSILyjrvl5noJFQT_bNiLCIw_WkaC1vt3tBv-Pd2fW3zEn5_kluiqtMm8UcCpGIvMmpNuvkwozwgOS67jBCxWer3zDVSfGs9y7mhuUvb78KAuf4sVJg1niTKG5K6Vx9vGIIPBo__kpGs-ZfJ2FAtTKXkKtEOvDGqVTPYJ6lOt2eD8ZcRjYCQ2QbiaSZ_DxTPKUPAhBvvdRNAXandYWOCwRZhgTcFSOa46TLjdfyZ3GMq6bRZ6OmRlV)


## Entidades

| Entidad | Descripción | Relaciones clave |
|----------|-------------|------------------|
| Usuario | Representa a los usuarios que utilizan el sistema y registra los pedidos realizados. | 1:N con Pedido |
| Mesa | Representa las mesas disponibles del bar y permite conocer su estado. | 1:N con Pedido |
| Pedido | Representa la orden realizada por un cliente y registra sus datos principales. | N:1 con Usuario y Mesa; 1:N con Detalle_Pedido; 1:1 con Pago |
| Detalle_Pedido | Representa cada producto incluido dentro de un pedido, junto con su cantidad y subtotal. | N:1 con Pedido y Producto |
| Producto | Representa los productos ofrecidos por el bar, incluyendo precio y stock disponible. | 1:N con Detalle_Pedido |
| Pago | Representa el pago asociado a un pedido y registra el método, total y fecha. | 1:1 con Pedido; 1:1 con Ticket |
| Ticket | Representa el comprobante emitido como resultado del pago de un pedido. | 1:1 con Pago |
## Descripción de atributos principales

_Para cada entidad, describir brevemente los atributos más relevantes y su propósito._

### Usuario

- `id_usuario` (PK): Identifica de manera única a cada usuario del sistema.
- `nombre`: Nombre del usuario.
- `usuario`: Nombre de usuario utilizado para iniciar sesión.
- `contraseña`: Credencial utilizada para la autenticación.
- `rol`: Indica el tipo de usuario y sus permisos dentro del sistema.

### Mesa

- `id_mesa` (PK): Identifica de manera única a cada mesa.
- `numero_mesa`: Número que identifica la mesa dentro del bar.
- `estado`: Indica si la mesa se encuentra libre u ocupada.

### Pedido

- `id_pedido` (PK): Identifica de manera única a cada pedido.
- `fecha`: Registra la fecha y hora en que se realiza el pedido.
- `subtotal`: Representa el importe subtotal del pedido.
- `id_mesa` (FK): Identifica la mesa asociada al pedido.
- `id_usuario` (FK): Identifica al usuario que registra el pedido.

### Detalle_Pedido

- `id_detalle` (PK): Identifica de manera única cada detalle del pedido.
- `cantidad`: Indica la cantidad de unidades del producto solicitado.
- `subtotal`: Representa el importe correspondiente a ese detalle.
- `id_pedido` (FK): Identifica el pedido al que pertenece el detalle.
- `id_producto` (FK): Identifica el producto incluido en el detalle.

### Producto

- `id_producto` (PK): Identifica de manera única cada producto.
- `nombre`: Nombre del producto ofrecido por el bar.
- `precio`: Precio del producto.
- `stock`: Cantidad disponible del producto.

### Pago

- `id_pago` (PK): Identifica de manera única cada pago.
- `metodo_pago`: Indica el medio utilizado para realizar el pago.
- `total`: Importe total abonado.
- `fecha`: Registra la fecha y hora del pago.
- `id_pedido` (FK): Identifica el pedido al que corresponde el pago.

### Ticket

- `id_ticket` (PK): Identifica de manera única cada ticket.
- `fecha_emision`: Registra la fecha y hora en que se emite el ticket.
- `id_pago` (FK): Identifica el pago asociado al ticket.
## Decisiones de diseño

_Justificar al menos dos decisiones de diseño relevantes: por qué se modeló de esa manera,
qué alternativas se consideraron y por qué se descartaron._

### Decisión 1 — Separación entre Pedido y Detalle_Pedido

Se decidió modelar `Pedido` y `Detalle_Pedido` como entidades separadas porque un mismo pedido puede contener varios productos. `Pedido` almacena la información general de la orden, mientras que `Detalle_Pedido` permite registrar cada producto, su cantidad y su subtotal.

Como alternativa, se podría haber almacenado directamente la información de los productos dentro de `Pedido`, pero esta opción dificultaría registrar varios productos y sus cantidades dentro de una misma orden. Por este motivo, se descartó y se optó por una relación 1:N entre `Pedido` y `Detalle_Pedido`.

### Decisión 2 — Separación entre Pago y Ticket

Se decidió separar las entidades `Pago` y `Ticket` para diferenciar la información correspondiente a la operación de pago de la información del comprobante emitido. `Pago` registra el método de pago, el total y la fecha, mientras que `Ticket` registra la fecha de emisión y el pago asociado.

Como alternativa, se podría haber incluido la información del ticket directamente dentro de `Pago`, pero mantenerlas separadas permite diferenciar claramente ambas responsabilidades y facilita futuras modificaciones. Por este motivo, se optó por una relación 1:1 entre `Pago` y `Ticket`.

### Decisión 3 — Uso de Detalle_Pedido para relacionar Pedido y Producto

Se decidió utilizar `Detalle_Pedido` como entidad intermedia entre `Pedido` y `Producto`, ya que permite registrar información propia de cada producto dentro de una orden, principalmente la cantidad y el subtotal.

La alternativa habría sido relacionar directamente `Pedido` con `Producto`, pero esa opción no permitiría representar adecuadamente los datos específicos de cada producto incluido en un pedido. Por este motivo, se utiliza `Detalle_Pedido` como entidad intermedia.
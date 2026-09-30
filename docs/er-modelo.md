# Modelo Entidad-Relación

## Diagrama



**Diagrama ER:** [Ver diagrama ER](https://www.plantuml.com/plantuml/svg/ZLJDRjim3BxhANGUu1S8Yg9Pac71bYr8lLq3Hc9ReROPKFHXZVTGmnwXBpPPZXV5jOVvOkWZnU_ZZtZd1LZgib1Ad1IeDsIn8Bsgn5cmsGuBCExrTwKpVU-yO0bw-_LUlmVM2s361wfPAGpkyaD_ypMm8trIEdpljBFx-WpDzFfBhczkjfzkRwCro-AlelB06CpVvxl5n_akWfTBAMge4WQFhxzWO64g4kJdNpqRz92AATlpf9AwHAR49w8O2cHfDFeMhRDNoHuxP8hX0SrJ6tivprVvUhEAeAyFGW9j0ilLOhsPVuxmKEs7FjP8JQFjeck98Lo1-xVwR6UP56YWQtkI_xIyGRAfm2EJhOrCAjpszhHsmpl_DIb7HXChaOhpGkRvd4D22e_NXErvYgn48KkzJyeuLetHnevsy28dT-OP9HKa7VBFwTbZwRoZQeJiAfyX6SCB75mHcvjIflWKCHZJCQPbwDGy4O_bFJMW_NvecYoZK_-0PfhnCUmM1XKVxD0g3YjKvsDhR4x36P_5vT3vzNDq3ZFY6TQMFr9bCU5hklbejHXt267QKoHh-bRDT2Y-u32B_Bg6Z52u5r3g3YiR5kiV)


## Entidades

| Entidad | Descripción | Relaciones clave |
|----------|-------------|------------------|
| Usuario | Representa a los usuarios que utilizan el sistema y registra los pedidos realizados. | 1\:N con Pedido; 1\:N con Trazabilidad |
| Mesa | Representa las mesas disponibles del bar y permite conocer su estado. | 1\:N con Pedido; 1:0..1 con Pago |
| Pedido | Representa la orden realizada por un cliente y registra sus datos principales. | N:1 con Usuario y Mesa; 1\:N con Detalle_Pedido |
| Detalle_Pedido | Representa cada producto incluido dentro de un pedido, junto con su cantidad y subtotal. | N:1 con Pedido y Producto |
| Producto | Representa los productos ofrecidos por el bar, incluyendo precio y stock disponible. | 1:N con Detalle_Pedido |
| Pago | Representa el pago asociado al consumo de una mesa y registra el método, total y fecha. | 1:0..1 con Mesa; 1:1 con Ticket |
| Ticket | Representa el comprobante emitido como resultado del pago. | 1:1 con Pago |
| Trazabilidad | Registra las operaciones realizadas en el sistema, identificando al usuario, la fecha y la hora. | N:1 con Usuario |
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
- `id_mesa` (FK): Identifica la mesa cuyo consumo corresponde al pago.

### Ticket

- `id_ticket` (PK): Identifica de manera única cada ticket.
- `fecha_emision`: Registra la fecha y hora en que se emite el ticket.
- `id_pago` (FK): Identifica el pago asociado al ticket.
### Trazabilidad

- `id_trazabilidad` (PK): Identifica de manera única cada registro de trazabilidad.
- `accion`: Describe la operación realizada en el sistema.
- `fecha_hora`: Registra la fecha y hora en que se realizó la operación.
- `id_usuario` (FK): Identifica al usuario que realizó la operación.
## Decisiones de diseño

_Justificar al menos dos decisiones de diseño relevantes: por qué se modeló de esa manera,
qué alternativas se consideraron y por qué se descartaron._

### Decisión 1 — Separación entre Pedido y Detalle_Pedido

Se decidió modelar `Pedido` y `Detalle_Pedido` como entidades separadas porque un mismo pedido puede contener varios productos. `Pedido` almacena la información general de la orden, mientras que `Detalle_Pedido` permite registrar cada producto, su cantidad y su subtotal.

Como alternativa, se podría haber almacenado directamente la información de los productos dentro de `Pedido`, pero esta opción dificultaría registrar varios productos y sus cantidades dentro de una misma orden. Por este motivo, se descartó y se optó por una relación 1:N entre `Pedido` y `Detalle_Pedido`.

### Decisión 2 — Separación entre Pago y Ticket

Se decidió separar las entidades `Pago` y `Ticket` para diferenciar la información correspondiente a la operación de pago de la información del comprobante emitido. `Pago` registra el método de pago, el total y la fecha, mientras que `Ticket` registra la fecha de emisión y el pago asociado.

Como alternativa, se podría haber incluido la información del ticket directamente dentro de `Pago`, pero mantenerlas separadas permite diferenciar claramente ambas responsabilidades y facilita futuras modificaciones. Por este motivo, se optó por una relación 1:1 entre `Pago` y `Ticket`.

### Decisión 3 — Asociación del Pago con la Mesa

Se decidió asociar `Pago` con `Mesa` porque en el sistema el pago corresponde al consumo de una mesa y se registra antes de cerrar y liberar la mesa. De esta manera, una mesa puede tener un pago registrado al finalizar su consumo.

Como alternativa, se podría haber asociado `Pago` directamente con `Pedido`, pero esto no representa correctamente el funcionamiento definido en los casos de uso, donde la encargada selecciona una mesa para registrar el pago correspondiente a su consumo. Por este motivo, se optó por relacionar `Pago` con `Mesa`. 
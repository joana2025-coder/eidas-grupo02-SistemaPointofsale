# Modelo Entidad-Relación

## Diagrama

## Diagrama

[![Ver diagrama ER](https://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.githubusercontent.com/joana2025-coder/eidas-grupo02-SistemaPointofsale/main/diagramas/er.puml)](https://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.githubusercontent.com/joana2025-coder/eidas-grupo02-SistemaPointofsale/main/diagramas/er.puml)

## Entidades

| Entidad | Descripción | Relaciones clave |
|---|---|---|
| Usuario | Representa a los usuarios que utilizan el sistema y registran los pedidos. El atributo `activo` permite desactivar usuarios sin eliminar sus registros históricos. | 1:N con Pedido; 1:N con Trazabilidad |
| Mesa | Representa las mesas disponibles del bar y permite conocer su estado. | 1:N con Cuenta; 1:N con Trazabilidad |
| Cuenta | Representa cada ocupación o consumo de una mesa, desde su apertura hasta su cierre. | N:1 con Mesa; 1:N con Pedido; 1:0..1 con Pago |
| Pedido | Representa la orden realizada durante una ocupación de mesa y registra sus datos principales. | N:1 con Usuario y Cuenta; 1:N con Detalle_Pedido |
| Detalle_Pedido | Representa cada producto incluido en un pedido, junto con su cantidad, precio unitario y subtotal. | N:1 con Pedido y Producto |
| Producto | Representa los productos ofrecidos por el bar, incluyendo su precio, categoría y estado de disponibilidad. | 1:N con Detalle_Pedido |
| Pago | Representa el pago correspondiente a una cuenta y registra el método, total y fecha. | N:1 con Cuenta; 1:1 con Ticket |
| Ticket | Representa el comprobante emitido como resultado del pago. | 1:1 con Pago |
| Trazabilidad | Registra las operaciones realizadas en el sistema, identificando al usuario, la fecha, la hora y el registro afectado. | N:1 con Usuario; asociación opcional con Mesa |

## Descripción de atributos principales

### Usuario

- `id_usuario` (PK): identifica de manera única a cada usuario.
- `nombre`: nombre del usuario.
- `usuario`: nombre utilizado para iniciar sesión.
- `contraseña`: credencial utilizada para la autenticación.
- `rol`: indica el tipo de usuario y sus permisos dentro del sistema.
- `activo`: indica si el usuario está habilitado para utilizar el sistema.

### Mesa

- `id_mesa` (PK): identifica de manera única a cada mesa.
- `numero_mesa`: número que identifica la mesa dentro del bar.
- `estado`: indica el estado de la mesa, por ejemplo, disponible, ocupada o pendiente de cierre.

### Cuenta

- `id_cuenta` (PK): identifica de manera única cada ocupación de una mesa.
- `fecha_apertura`: registra cuándo comienza la ocupación.
- `fecha_cierre`: registra cuándo finaliza la ocupación; puede quedar sin valor mientras la cuenta esté abierta.
- `estado`: indica la situación de la cuenta.
- `id_mesa` (FK): identifica la mesa a la que corresponde la cuenta.

### Pedido

- `id_pedido` (PK): identifica de manera única a cada pedido.
- `fecha`: registra la fecha y hora en que se realiza el pedido.
- `subtotal`: representa el importe subtotal del pedido.
- `id_cuenta` (FK): identifica la cuenta a la que pertenece el pedido.
- `id_usuario` (FK): identifica al usuario que registra el pedido.

### Detalle_Pedido

- `id_detalle` (PK): identifica de manera única cada detalle del pedido.
- `cantidad`: indica la cantidad de unidades del producto solicitado.
- `precio_unitario`: conserva el precio del producto al momento de registrar el pedido.
- `subtotal`: representa el importe correspondiente a ese detalle.
- `id_pedido` (FK): identifica el pedido al que pertenece el detalle.
- `id_producto` (FK): identifica el producto incluido en el detalle.

### Producto

- `id_producto` (PK): identifica de manera única cada producto.
- `nombre`: nombre del producto ofrecido por el bar.
- `precio`: precio vigente del producto.
- `categoria`: categoría a la que pertenece el producto.
- `activo`: indica si el producto está habilitado para su uso en el sistema.

### Pago

- `id_pago` (PK): identifica de manera única cada pago.
- `metodo_pago`: indica el medio utilizado para realizar el pago.
- `total`: importe total abonado.
- `fecha`: registra la fecha y hora del pago.
- `id_cuenta` (FK): identifica la cuenta cuyo consumo corresponde al pago.

### Ticket

- `id_ticket` (PK): identifica de manera única cada ticket.
- `fecha_emision`: registra la fecha y hora en que se emite el ticket.
- `id_pago` (FK, UNIQUE): identifica el pago asociado al ticket y evita asociar varios tickets a un mismo pago.

### Trazabilidad

- `id_trazabilidad` (PK): identifica de manera única cada registro de trazabilidad.
- `accion`: describe la operación realizada en el sistema.
- `fecha_hora`: registra la fecha y hora de la operación.
- `id_usuario` (FK): identifica al usuario que realizó la operación.
- `id_mesa` (FK, opcional): identifica la mesa relacionada con la operación, cuando corresponda.
- `entidad_afectada`: indica el tipo de entidad sobre la que se realizó la operación.
- `id_registro_afectado`: identifica el registro afectado por la operación.

## Decisiones de diseño

### Decisión 1 — Separación entre Pedido y Detalle_Pedido

Se decidió modelar `Pedido` y `Detalle_Pedido` como entidades separadas porque un mismo pedido puede contener varios productos. `Pedido` almacena la información general de la orden, mientras que `Detalle_Pedido` permite registrar cada producto, su cantidad, el precio unitario y el subtotal.

Como alternativa, se podría haber almacenado directamente la información de los productos dentro de `Pedido`, pero esto dificultaría registrar varios productos y sus cantidades dentro de una misma orden. Por este motivo, se optó por una relación 1:N entre `Pedido` y `Detalle_Pedido`.

### Decisión 2 — Separación entre Pago y Ticket

Se decidió separar las entidades `Pago` y `Ticket` para diferenciar la información correspondiente a la operación de pago de la información del comprobante emitido. `Pago` registra el método de pago, el total y la fecha, mientras que `Ticket` registra la fecha de emisión y el pago asociado.

Como alternativa, se podría haber incluido la información del ticket directamente dentro de `Pago`. Sin embargo, mantenerlas separadas permite diferenciar ambas responsabilidades. Se establece una relación 1:1 entre `Pago` y `Ticket`.

### Decisión 3 — Incorporación de Cuenta entre Mesa, Pedido y Pago

Se decidió incorporar la entidad `Cuenta` para representar cada ocupación o consumo de una mesa. Una misma mesa puede utilizarse muchas veces, por lo que relacionar directamente `Mesa` con `Pago` limitaría incorrectamente el registro de pagos a lo largo del tiempo.

La entidad `Cuenta` permite asociar los pedidos y el pago correspondiente a una ocupación específica. De esta manera, se conserva el historial de consumos de cada mesa y se evita confundir pagos de distintas ocupaciones.

Como alternativa, se podría haber relacionado `Pago` directamente con `Mesa` o con un único `Pedido`, pero estas opciones no representan adecuadamente una cuenta que agrupa varios pedidos. Por ese motivo, se optó por relacionar `Mesa` con `Cuenta`, y `Cuenta` con `Pedido` y `Pago`.

### Decisión 4 — Conservación del historial y trazabilidad

Se incorporó el atributo `activo` en `Usuario` y `Producto` para permitir su desactivación sin eliminar los registros históricos relacionados. Además, se agregó `precio_unitario` en `Detalle_Pedido` para conservar el precio aplicado al momento de registrar cada pedido, aunque el precio vigente del producto cambie posteriormente.

Por otra parte, `Trazabilidad` incluye la entidad y el registro afectados, además de la mesa cuando corresponde. Esto permite identificar con mayor precisión qué operación se realizó y sobre qué registro.
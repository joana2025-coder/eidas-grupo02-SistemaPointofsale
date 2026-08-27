# Historias de usuario

_Presentar al menos una historia de usuario representativa por módulo._
_Cada historia debe incluir formato clásico, criterios de aceptación y validación INVEST._

---

## HU-01 — Registrar Pedidos

| Campo | Detalle |
|-------|---------|
| Historia | Como encargada, quiero registrar pedidos asociados a una mesa para mantener organizado el consumo de cada cliente. |
| Módulo | Gestión en pedidos |
| Requisitos relacionados | RF-04, RF-05, RF-06 |

### Criterios de aceptación

1. La encargada debe poder seleccionar una mesa y registrar uno o varios productos.
2. El sistema debe guardar el pedido asociado a la mesa seleccionada.
3. El sistema debe permitir modificar o eliminar productos del pedido antes de confirmarlo.

### Validación INVEST

| Criterio | ¿Se cumple? | Observación |
|----------|-------------|-------------|
| Independiente | Si | Puede desarrollarse de manera independiente|
| Negociable | Si | Los detalles del registro pueden acordarse|
| Valiosa | Si | Permite organizar el consumo de cada mesa|
| Estimable |Si | Se puede estimar el tiempo de desarrollo|
| Pequeña | Si | Tiene un alcance concreto y reducido|
| Verificable | Si | Se puede verificar que el pedido quede asociado a la mesa correcta|

---

## HU-02 — Registrar Pagos

| Campo | Detalle |
|-------|---------|
| Historia | Como encargada, quiero registrar pagos en efectivo, tarjeta o QR para facilitar el cobro a los clientes.  |
| Módulo |Gestión de pagos |
| Requisitos relacionados | RF-07, RF-08 |

### Criterios de aceptación

1. El sistema debe permitir seleccionar el pedido o consumo que se desea cobrar.
2. La encargada debe poder seleccionar el medio de pago: efectivo, tarjeta o QR.
3. Al confirmar el pago, el sistema debe registrar el pago y actualizar el estado del consumo como pagado.

### Validación INVEST

| Criterio | ¿Se cumple? | Observación |
|----------|-------------|-------------|
| Independiente | Si | Puede desarrollarse de manera independiente|
| Negociable | Si | Los medios y detalle del pago pueden acordarse|
| Valiosa | Si | Facilita el cobro y registros de los pagos|
| Estimable | Si | Se puede estimar el tiempo y esfuerzo necesario|                                                                                                                                        
| Pequeña | Si | Tiene un alcance concreto y reducido|
| Verificable | Si | Se puede fijar pago de registro correctamente|

---

## HU-03 — Acciones del pedido de la moza

| Campo | Detalle |
|-------|---------|
| Historia | Como moza, quiero visualizar las mesas y su estado actual para organizar mejor la atención de los clientes.  |
| Módulo | Gestión de mesas|
| Requisitos relacionados | RF-02, RF-03 |

### Criterios de aceptación

1. La moza debe poder visualizar todas las mesas disponibles.
2. El sistema debe mostrar el estado actual de cada mesa, por ejemplo: libre, ocupada o reservada.
3. El estado de una mesa debe actualizarse cuando se registra o finaliza un pedido.

### Validación INVEST

| Criterio | ¿Se cumple? | Observación |
|----------|-------------|-------------|
| Independiente | Si | Puede desarrollarse de manera independiente|
| Negociable | Si | Los estados de las mesas pueden definirse y acordarse|
| Valiosa | Si | Ayuda a organizar la atención de los clientes|
| Estimable | Si | Se puede estimar el tiempo y esfuerzo necesario|
| Pequeña | Si | Tiene un alcance concreto y reducido|
| Verificable | Si | Se puede verificar que los estados se muestren y actualicen correctamente|

---

## HU-04 — Control de historial

| Campo | Detalle |
|-------|---------|
| Historia | Como dueño, quiero consultar el historial de ventas y consumos para controlar la recaudación diaria del negocio. |
| Módulo | Reportes e historial |
| Requisitos relacionados | RF-10, RF-11 |

### Criterios de aceptación

1. El dueño debe poder consultar las ventas y consumos registrados.
2. El sistema debe permitir consultar la información por fecha.
3. El historial debe mostrar datos como mesa, importe, medio de pago y fecha de la venta.

### Validación INVEST

| Criterio | ¿Se cumple? | Observación |
|----------|-------------|-------------|
| Independiente | Si | Puede desarrollarse de manera independiente|
| Negociable | Si | Los datos y filtros del historial pueden acordarse|
| Valiosa | Si | Permiten controlar las ventas y la recaudación|
| Estimable | Si | Se puede estimar el tiempo y esfuerzo necesario|
| Pequeña | Si | Tiene un alcance concreto y reducido|
| Verificable | Si | Se puede verificar que el historial muestre los datos correctamente|

| Pequeña | | |
| Verificable | | |

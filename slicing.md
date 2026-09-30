# Ejercicio: partir una épica en slices verticales

## La épica

> Como moza, quiero gestionar una mesa desde su apertura hasta su cierre, para registrar el consumo del cliente, cobrarlo correctamente y dejar la mesa disponible para una nueva atención. 

---

## Parte A — Historias verticales


### Historia 1 — [Visualizar y dar apertura a una mesa disponible]

|Como moza, quiero visualizar las mesas y abrir una mesa disponible, para comenzar la atención. | 

| Requisitos relacionados: * RF-03, RF-04, RF-05, RF-06, RF-21, RF-23, RF-24 y RF-25.  
* RNF-01, RNF-02, RNF-03, RNF-04, RNF-08, RNF-10, RNF-16 y RNF-18. |

**Criterios de aceptación**
1- El sistema muestra las 24 mesas y su estado actual.
2- La moza puede abrir únicamente una mesa Disponible, previa confirmación.
3- Al confirmar la apertura, la mesa pasa a estado Ocupada.
3- El sistema registra el usuario, la fecha y la hora de la apertura.
4- La visualización de las mesas se actualiza mostrando el nuevo estado.

---

### Historia 2 — [Registrar y modificar un pedido]

| Como encargada, quiero asociar un pedido a una mesa y agregar, modificar o eliminar sus productos, para registrar correctamente el consumo solicitado por los clientes. | 

| Requisitos relacionados: * RF-06, RF-07, RF-08, RF-09, RF-10, RF-21, RF-24, RF-25 y RF-26. 
 * RNF-01, RNF-02, RNF-03, RNF-08, RNF-10, RNF-13, RNF-16 y RNF-18. | 

**Criterios de aceptación**
1- La encargada puede asociar un pedido a una mesa abierta.
2- La encargada puede agregar productos disponibles al pedido indicando una cantidad válida.
3- La encargada puede modificar la cantidad de los productos del pedido.
4- La encargada puede eliminar un producto del pedido previa confirmación.
5- El sistema actualiza automáticamente el detalle y el total después de agregar, modificar o eliminar productos.
6- El sistema registra las modificaciones realizadas sobre el pedido.

---

### Historia 3 — [Consultar el consumo y el importe]

| Como moza, quiero consultar el detalle y el total actualizado del consumo de una mesa, para informar al cliente el importe que debe abonar. | 

| Requisitos relacionados: * RF-10, RF-11 y RF-14. 
 * RNF-01, RNF-03, RNF-08, RNF-12, RNF-16 y RNF-18. | 

**Criterios de aceptación**
1- El sistema muestra el detalle del consumo: productos, cantidades, precios unitarios y subtotales.
2- El sistema muestra el importe total actualizado del consumo.
3- El total coincide con la suma de los subtotales.
4- La consulta está disponible para mesas con pedido activo.
5- La consulta no modifica la información registrada.

---

### Historia 4 — [Registrar el pago y generar la venta]

| Como encargada, quiero registrar el pago de una mesa, para confirmar el cobro y generar la venta correspondiente. | 

| Requisitos relacionados: * RF-12, RF-13, RF-14, RF-15, RF-21 y RF-24. 
* RNF-03, RNF-08, RNF-10, RNF-13, RNF-16, RNF-18 y RNF-22. | 

**Criterios de aceptación**
1- Solo se puede registrar un pago para una mesa que tenga un consumo registrado.
2- El sistema muestra el importe final a pagar.
3- El sistema permite seleccionar efectivo, tarjeta o QR como medio de pago.
4- El sistema solicita la confirmación antes de registrar el pago.
5- Al confirmar un pago válido, el sistema registra el pago y confirma la venta.
6- La mesa pasa a estado Pendiente de cierre una vez confirmada la venta.

---

### Historia 5 — [Emitir el comprobante]

| Como encargada, quiero emitir el comprobante de una venta confirmada, para entregar al cliente una constancia del pago realizado. | 

| Requisitos relacionados: * RF-27. 
* RNF-01, RNF-03, RNF-12 y RNF-18. | 

**Criterios de aceptación**
1- El sistema permite emitir comprobantes únicamente para ventas confirmadas.
2- El comprobante contiene los datos principales de la venta y del pago.
3- El comprobante identifica a la mesa y al usuario responsable de la operación. 
4- El comprobante puede visualizarse e imprimirse.

---

### Historia 6 — [Cerrar una mesa pagada]

| Como encargada, quiero cerrar una mesa con pago confirmado, para dejarla disponible para una nueva atención. | 

| Requisitos relacionados: * RF-16, RF-17, RF-21, RF-24 y RF-25. 
* RNF-03, RNF-08, RNF-10, RNF-13, RNF-16 y RNF-18. | 

**Criterios de aceptación**
1- Solo se puede cerrar una mesa en estado Pendiente de cierre.
2- El sistema solicita confirmación antes de cerrar la mesa.
3- Al confirmar el cierre, la mesa pasa a Disponible.
4- El sistema registra el usuario, fecha y hora de la operación.
5- La información de la venta y el comprobante permanece almacenada.

---

## Parte B — Los caminos que no salen bien

**Historia elegida:** [Historia 4 — Registrar el pago y generar la venta]

| Pregunta | Qué hace el sistema | Quién decide (analista / negocio / técnica) |
|----------|----------------------|-----------------------------------------------|
| ¿Qué pasa si el saldo es insuficiente? | Rechaza el cobro, muestra la alerta "Monto o saldo insuficiente" y mantiene la mesa en estado Ocupada con el pedido activo.| Dueño / Responsable del bar y Encargada. Definen la política comercial (ej. si se rechaza el pago o si se permite pago parcial/dividido). |
| ¿Qué pasa si el destinatario no existe o está dado de baja? | Si la mesa o el pedido no existe, está cerrado o no está activo, el sistema no permite registrar el pago. Informa que la operación no es válida, cancela la operación y emite un mensaje de error.| Analista Funcional, identifica y documenta la regla. El dueño del bar define qué estados habilitan el cobro. |
| ¿Qué pasa si el sistema descuenta el saldo y falla antes de acreditarlo del otro lado? | El pago, el registro de la venta y el cambio de estado de la mesa deben confirmarse como una sola operación. Si falla una parte, el sistema no debe dejar pagos, ventas ni estados de mesa inconsistentes. | La encargada del bar o el dueño, establece la regla de que no puede haber una venta sin pago ni un pago sin venta. Los desarrolladores definen cómo lograrlo en el sistema mediante transacciones y recuperación ante errores. |
| ¿Qué pasa si el usuario aprieta "Enviar" dos veces? | Si la moza presiona dos veces Confirmar pago, el sistema procesa un único pago y una única venta. Debe impedir comprobantes duplicados y mostrar que la operación se está procesando.| Los desarrolladores toman decisión de usabilidad y arquitectura para evitar que la Moza / Encargada cobre dos veces por accidente. |
| ¿Qué pasa si se cae la conexión justo después de confirmar? | El sistema consulta si el pago ya fue registrado antes de permitir reintentar. Si la venta existe, informa que fue confirmada; si no existe, permite realizar nuevamente el cobro. No debe generar ventas duplicadas.| La encargada del bar válida. Los desarrolladores definen el mecanismo de recuperación, consulta y reintento seguro. |

---

## Parte C — Defensa

_Se hace oral, en el plenario. No se documenta en este archivo._

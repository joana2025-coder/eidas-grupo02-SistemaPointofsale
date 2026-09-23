# Casos de uso

---

## CU-01 — Iniciar sesión

**Actor:** Usuario

**Objetivo:** Permitir que un usuario registrado acceda al sistema mediante sus credenciales y que el sistema identifique su rol.

### Precondiciones

* El usuario debe estar registrado y activo.
* El sistema debe estar disponible.

### Postcondiciones

* El usuario accede al sistema.
* El sistema identifica su rol y habilita las funcionalidades correspondientes a sus permisos.

### Flujo principal

1. El usuario accede a la pantalla de inicio de sesión.
2. El sistema solicita nombre de usuario y contraseña.
3. El usuario ingresa sus credenciales.
4. El sistema valida las credenciales.
5. El sistema verifica que el usuario se encuentre activo.
6. El sistema identifica el rol del usuario.
7. El sistema permite el acceso a las funcionalidades correspondientes.

### Flujos alternativos

* **4a. Credenciales incorrectas:** el sistema informa que los datos ingresados no son válidos y solicita intentar nuevamente.
* **5a. Usuario inactivo:** el sistema rechaza el acceso e informa que el usuario no se encuentra habilitado.
* **3a. Cancelación:** el usuario puede cancelar el inicio de sesión.
* **Inactividad:** luego del período establecido de inactividad, la sesión se cierra automáticamente.

**Requisitos funcionales relacionados:** RF-01, RF-22.

**Requisitos no funcionales relacionados:** RNF-05, RNF-06, RNF-07, RNF-19 y RNF-23.

---

## CU-02 — Gestionar usuarios y roles

**Actor:** Encargada

**Objetivo:** Permitir a la encargada gestionar los usuarios del sistema y asignar o modificar sus roles según corresponda.

### Precondiciones

* La encargada debe haber iniciado sesión.
* Debe contar con los permisos necesarios para gestionar usuarios y roles.
* El sistema debe estar disponible.

### Postcondiciones

* El usuario registrado, modificado o desactivado queda actualizado en el sistema.
* El rol asignado o modificado queda registrado.
* La información necesaria para el acceso y los permisos queda actualizada.

### Flujo principal

1. La encargada accede a la gestión de usuarios.
2. El sistema muestra los usuarios registrados.
3. La encargada selecciona la operación que desea realizar: registrar, modificar o desactivar un usuario.
4. Para registrar un usuario, la encargada ingresa los datos solicitados.
5. El sistema valida la información ingresada.
6. La encargada asigna el rol correspondiente al usuario.
7. El sistema registra el usuario y el rol asignado.
8. Para modificar un usuario o su rol, la encargada realiza los cambios correspondientes.
9. El sistema valida y guarda los cambios.
10. Para desactivar un usuario, la encargada selecciona la opción correspondiente y confirma la operación.
11. El sistema actualiza el estado del usuario.

### Flujos alternativos

* **5a. Nombre de usuario ya existente:** el sistema informa que el nombre de usuario no puede repetirse y solicita ingresar otro.
* **10a. Cancelación de desactivación:** si la encargada cancela la operación, el usuario no se desactiva.
* **9a. Datos inválidos:** el sistema informa el error y solicita corregir la información.
* **3a. Cancelación:** la encargada puede cancelar la operación antes de confirmarla.

**Requisitos funcionales relacionados:** RF-02, RF-22.

**Requisitos no funcionales relacionados:** RNF-06, RNF-08, RNF-10.

---

## CU-03 — Visualizar y abrir mesa

**Actores:** Moza o Encargada

**Objetivo:** Permitir visualizar el estado de las 24 mesas y abrir una mesa disponible para iniciar la atención.

### Precondiciones

* El usuario debe haber iniciado sesión.
* Debe contar con los permisos correspondientes.
* El sistema debe estar disponible.

### Postcondiciones

* La mesa seleccionada queda en estado **Ocupada**.
* La mesa queda asociada a un pedido activo.
* La operación queda registrada con usuario, fecha y hora.

### Flujo principal

1. El usuario accede a la visualización de mesas.
2. El sistema muestra las 24 mesas y su estado actual.
3. El usuario selecciona una mesa en estado **Disponible**.
4. El sistema solicita confirmación para abrir la mesa.
5. El usuario confirma la operación.
6. El sistema cambia el estado de la mesa a **Ocupada**.
7. El sistema genera o habilita el pedido activo asociado a la mesa.
8. El sistema registra el usuario, la fecha y la hora de la operación.
9. El sistema actualiza la visualización del estado de la mesa.

### Flujos alternativos

* **3a. Mesa no disponible:** el sistema informa que no es posible abrir la mesa.
* **4a. Cancelación:** si el usuario cancela la confirmación, la mesa mantiene su estado actual.
* **6a. Error durante la operación:** si no es posible completar la apertura, la mesa mantiene su estado anterior y no se genera una operación incompleta.

**Requisitos funcionales relacionados:** RF-03, RF-04, RF-05, RF-23, RF-24 y RF-25.

**Requisitos no funcionales relacionados:** RNF-01, RNF-03, RNF-08, RNF-10, RNF-13, RNF-16 y RNF-18.

---

## CU-04 — Registrar y gestionar pedido

**Actor:** Encargada

**Objetivo:** Permitir a la encargada registrar un pedido asociado a una mesa y gestionar los productos del pedido, actualizando su detalle y total.

### Precondiciones

* La encargada debe haber iniciado sesión.
* La mesa debe encontrarse abierta para realizar un pedido.
* La encargada debe contar con los permisos correspondientes.
* El sistema debe estar disponible.

### Postcondiciones

* El pedido queda asociado a la mesa correspondiente.
* Los productos y sus cantidades quedan registrados.
* El detalle y el total del pedido quedan actualizados.
* Las modificaciones realizadas quedan registradas.

### Flujo principal

1. La encargada selecciona una mesa abierta.
2. El sistema muestra el pedido activo asociado a la mesa.
3. La encargada selecciona la opción para agregar productos.
4. El sistema muestra los productos disponibles.
5. La encargada selecciona un producto e indica la cantidad.
6. El sistema registra el producto en el pedido.
7. El sistema actualiza el detalle y el total del pedido.
8. La encargada puede modificar la cantidad de un producto del pedido.
9. El sistema actualiza el detalle y el total.
10. La encargada puede seleccionar un producto para eliminarlo del pedido.
11. El sistema solicita confirmación para eliminarlo.
12. La encargada confirma la eliminación.
13. El sistema elimina el producto y actualiza el detalle y el total.
14. El pedido queda registrado con la información actualizada.

### Flujos alternativos

* **1a. Mesa no disponible:** el sistema informa que no es posible registrar el pedido para esa mesa.
* **5a. Cantidad inválida:** el sistema informa el error y solicita ingresar una cantidad válida.
* **11a. Cancelación de eliminación:** si la encargada cancela la operación, el producto permanece en el pedido.
* **14a. Error durante la operación:** si no es posible completar la operación, el sistema evita guardar información parcial o duplicada.

**Requisitos funcionales relacionados:** RF-06, RF-07, RF-08, RF-09, RF-10, RF-25 y RF-26.

**Requisitos no funcionales relacionados:** RNF-01, RNF-02, RNF-03, RNF-08, RNF-10, RNF-13, RNF-16 y RNF-18.

---

## CU-05 — Consultar consumo

**Actor:** Moza

**Objetivo:** Permitir a la moza consultar el detalle del consumo de una mesa y visualizar su total actualizado.

### Precondiciones

* La moza debe haber iniciado sesión.
* Debe contar con los permisos correspondientes.
* El sistema debe estar disponible.

### Postcondiciones

* El detalle del consumo de la mesa seleccionada queda visualizado.
* El total correspondiente al consumo queda mostrado.
* La consulta no modifica la información registrada.

### Flujo principal

1. La moza accede a la consulta de consumo.
2. El sistema muestra las mesas que pueden ser consultadas.
3. La moza selecciona una mesa.
4. El sistema obtiene el consumo asociado a la mesa.
5. El sistema muestra los productos, cantidades y valores correspondientes.
6. El sistema calcula y muestra el total del consumo.
7. El sistema mantiene la información actualizada si el consumo de la mesa cambia.

### Flujos alternativos

* **4a. No existe consumo registrado:** el sistema informa que no hay consumo para la mesa seleccionada.
* **3a. Mesa no disponible para consulta:** el sistema informa que no es posible realizar la consulta.
* **6a. Error al obtener la información:** el sistema informa que no fue posible consultar el consumo.

**Requisitos funcionales relacionados:** RF-10, RF-11, RF-14 y RF-26.

**Requisitos no funcionales relacionados:** RNF-01, RNF-03, RNF-08, RNF-12 y RNF-20.

---

## CU-06 — Registrar pago

**Actor:** Encargada

**Objetivo:** Permitir a la encargada registrar el pago correspondiente al consumo de una mesa mediante efectivo, tarjeta o QR.

### Precondiciones

* La encargada debe haber iniciado sesión.
* La mesa debe tener un consumo registrado.
* El importe final debe estar calculado.
* La encargada debe contar con los permisos correspondientes.
* El sistema debe estar disponible.

### Postcondiciones

* El pago queda registrado y asociado a la mesa y al consumo correspondiente.
* El medio de pago seleccionado queda registrado.
* La venta queda confirmada cuando el pago es válido.
* La operación queda registrada con la información correspondiente.

### Flujo principal

1. La encargada selecciona la mesa cuyo consumo desea cobrar.
2. El sistema muestra el importe final a pagar.
3. La encargada selecciona el medio de pago.
4. El sistema permite seleccionar entre **efectivo, tarjeta o QR**.
5. La encargada confirma el pago.
6. El sistema valida el pago.
7. El sistema registra el pago asociado al consumo.
8. El sistema confirma la venta.
9. El sistema registra la operación correspondiente.

### Flujos alternativos

* **2a. No existe consumo:** el sistema informa que no hay un consumo disponible para cobrar.
* **3a. Cancelación:** la encargada puede cancelar la operación antes de confirmar el pago.
* **6a. Pago no válido:** el sistema informa que el pago no puede ser confirmado y no registra la venta.
* **7a. Pago ya registrado:** el sistema evita registrar nuevamente el mismo pago.
* **7b. Error durante el registro:** el sistema evita guardar una operación incompleta o duplicada.

**Requisitos funcionales relacionados:** RF-12, RF-13, RF-14, RF-15 y RF-24.

**Requisitos no funcionales relacionados:** RNF-03, RNF-08, RNF-10, RNF-13, RNF-16 y RNF-18.

---

## CU-07 — Emitir comprobante

**Actor:** Encargada

**Objetivo:** Permitir a la encargada generar y consultar el comprobante correspondiente a una venta confirmada.

### Precondiciones

* La encargada debe haber iniciado sesión.
* El pago debe haber sido registrado y confirmado.
* La venta debe encontrarse confirmada.
* El sistema debe estar disponible.

### Postcondiciones

* El comprobante queda generado y asociado a la venta.
* La encargada puede visualizar el comprobante.
* El comprobante queda disponible junto con la información de la operación.

### Flujo principal

1. La encargada accede a la operación correspondiente.
2. El sistema verifica que el pago se encuentre registrado y la venta confirmada.
3. El sistema genera el comprobante.
4. El comprobante muestra la información correspondiente a la operación, incluyendo la mesa, el importe y el medio de pago.
5. El sistema muestra el comprobante.
6. La encargada puede visualizarlo y, si corresponde, imprimirlo.

### Flujos alternativos

* **2a. Pago no confirmado:** el sistema informa que no es posible generar el comprobante.
* **2b. Venta no confirmada:** el sistema informa que la operación todavía no puede generar un comprobante.
* **6a. Cancelación de impresión:** si la encargada decide no imprimirlo, el comprobante permanece generado y disponible para su consulta.

**Requisitos funcionales relacionados:** RF-15, RF-18 y RF-27.

**Requisitos no funcionales relacionados:** RNF-03, RNF-08, RNF-12 y RNF-18.

---

## CU-08 — Cerrar y liberar mesa

**Actor:** Encargada

**Objetivo:** Permitir a la encargada cerrar una mesa luego de que el pago haya sido confirmado y dejarla disponible para una nueva atención.

### Precondiciones

* La encargada debe haber iniciado sesión.
* La mesa debe tener un pago confirmado.
* La encargada debe contar con los permisos correspondientes.
* El sistema debe estar disponible.

### Postcondiciones

* La mesa queda en estado **Disponible**.
* La venta y el comprobante permanecen almacenados.
* La operación de cierre queda registrada con usuario, fecha y hora.

### Flujo principal

1. La encargada selecciona la mesa que desea cerrar.
2. El sistema verifica que el pago se encuentre confirmado.
3. El sistema muestra la información correspondiente a la operación.
4. El sistema solicita confirmación para cerrar la mesa.
5. La encargada confirma el cierre.
6. El sistema cierra la mesa.
7. El sistema cambia el estado de la mesa a **Disponible**.
8. El sistema conserva la información de la venta y el comprobante.
9. El sistema registra el usuario, la fecha y la hora de la operación.
10. El sistema actualiza el estado de la mesa.

### Flujos alternativos

* **2a. Pago no confirmado:** el sistema informa que la mesa no puede cerrarse.
* **4a. Cancelación:** si la encargada cancela la operación, la mesa mantiene su estado actual.
* **6a. Error durante el cierre:** si no es posible completar la operación, la mesa no pasa a Disponible y se evita dejar la operación en un estado incompleto.

**Requisitos funcionales relacionados:** RF-16, RF-17, RF-21, RF-24 y RF-25.

**Requisitos no funcionales relacionados:** RNF-08, RNF-10, RNF-13, RNF-16 y RNF-18.

---

## CU-09 — Consultar historial y ventas

**Actores:** Encargada o Dueño

**Objetivo:** Permitir consultar información histórica de las ventas y obtener información resumida de las ventas y consumos registrados.

### Precondiciones

* El usuario debe haber iniciado sesión.
* Debe contar con los permisos correspondientes.
* El sistema debe estar disponible.

### Postcondiciones

* La información solicitada queda visualizada.
* Los datos históricos permanecen sin modificaciones.

### Flujo principal

1. El usuario accede a la consulta de historial y ventas.
2. El sistema verifica los permisos del usuario.
3. El usuario selecciona los criterios de consulta correspondientes.
4. El sistema busca las ventas y consumos almacenados que coincidan con los criterios.
5. El sistema muestra la información disponible.
6. El usuario puede consultar el detalle de las ventas y consumos.
7. El sistema puede mostrar la información resumida correspondiente.

### Flujos alternativos

* **2a. Usuario sin permisos:** el sistema rechaza el acceso a la consulta.
* **4a. No existen resultados:** el sistema informa que no se encontraron ventas o consumos para los criterios seleccionados.
* **3a. Criterios inválidos:** el sistema solicita corregir los datos ingresados.
* **6a. Error en la consulta:** el sistema informa que no fue posible obtener la información solicitada.

**Requisitos funcionales relacionados:** RF-18, RF-19, RF-20, RF-28 y RF-29.

**Requisitos no funcionales relacionados:** RNF-01, RNF-03, RNF-08 y RNF-12.

---

## CU-10 — Consultar trazabilidad

**Actor:** Administrador del sistema

**Objetivo:** Permitir al administrador consultar los registros de las operaciones realizadas en el sistema, identificando el usuario, la fecha y la hora correspondientes.

### Precondiciones

* El administrador debe haber iniciado sesión.
* Debe contar con los permisos correspondientes.
* El sistema debe estar disponible.

### Postcondiciones

* Los registros de trazabilidad solicitados quedan visualizados.
* Los registros de trazabilidad no son modificados ni eliminados mediante esta consulta.

### Flujo principal

1. El administrador accede a la consulta de trazabilidad.
2. El sistema verifica que el usuario tenga los permisos correspondientes.
3. El sistema obtiene los registros de las operaciones almacenadas.
4. El sistema muestra la información de trazabilidad disponible.
5. El administrador consulta los registros, identificando el usuario, la fecha y la hora de las operaciones.

### Flujos alternativos

* **2a. Usuario sin permisos:** el sistema rechaza el acceso a la consulta.
* **3a. No existen registros:** el sistema informa que no hay registros disponibles para consultar.
* **5a. Intento de modificación o eliminación:** el sistema no permite modificar ni eliminar los registros de trazabilidad.

**Requisitos funcionales relacionados:** RF-21 y RF-24.

**Requisitos no funcionales relacionados:** RNF-06, RNF-08, RNF-10 y RNF-22.

---

## CU-11 — Gestionar productos

**Actor:** Encargada

**Objetivo:** Permitir a la encargada registrar, modificar y desactivar productos que pueden utilizarse en los pedidos.

### Precondiciones

* La encargada debe haber iniciado sesión.
* Debe contar con los permisos correspondientes.
* El sistema debe estar disponible.

### Postcondiciones

* El producto queda registrado, modificado o desactivado según la operación realizada.
* Los productos desactivados no pueden ser incorporados a nuevos pedidos.
* La información histórica relacionada con productos utilizados en ventas se conserva.

### Flujo principal

1. La encargada accede a la gestión de productos.
2. El sistema muestra los productos registrados.
3. La encargada selecciona la operación que desea realizar: registrar, modificar o desactivar un producto.
4. Para registrar un producto, la encargada ingresa la información solicitada.
5. El sistema valida la información ingresada.
6. La encargada confirma el registro.
7. El sistema guarda el nuevo producto.
8. Para modificar un producto, la encargada selecciona el producto y realiza los cambios correspondientes.
9. El sistema valida y guarda los cambios.
10. Para desactivar un producto, la encargada selecciona el producto correspondiente.
11. El sistema solicita confirmación.
12. La encargada confirma la desactivación.
13. El sistema desactiva el producto e impide que sea incorporado a nuevos pedidos.

### Flujos alternativos

* **5a. Datos inválidos:** el sistema informa el error y solicita corregir la información.
* **6a. Cancelación del registro:** si la encargada cancela la operación, el producto no se registra.
* **9a. Cancelación de modificación:** si la encargada cancela la operación, los datos anteriores se mantienen.
* **11a. Cancelación de desactivación:** si la encargada cancela la operación, el producto permanece activo.
* **13a. Producto desactivado:** el sistema no permite incorporar el producto desactivado a un nuevo pedido.

**Requisitos funcionales relacionados:** RF-30.

**Requisitos no funcionales relacionados:** RNF-06, RNF-08 y RNF-15.

---

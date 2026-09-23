# Historias de usuario
---
# H-U 1 — Inicio de sesión

**Como** usuario del sistema,  
**quiero** iniciar sesión mediante usuario y contraseña,  
**para** acceder de forma segura a las funcionalidades habilitadas según mi rol.

**Módulo:** Inicio de Sesión

**Requisitos relacionados:** RF-01 y RF 22

**Requisitos no funcionales:** RNF-05; RNF 06, RNF-07 y RNF-19

### Criterios de aceptación

1- El sistema permite ingresar nombre de usuario y contraseña.
2- Si las credenciales son correctas y el usuario está activo, el sistema permite iniciar sesión.
3- Si las credenciales son incorrectas, el sistema rechaza el acceso e informa un mensaje de error.
4- El sistema identifica el rol del usuario al iniciar sesión.
5- Al cerrar sesión, el usuario no puede continuar utilizando funciones restringidas.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Se puede desarrollar y probar verificando el ingreso con credenciales válidas e inválidas, sin necesidad de completar las demás funcionalidades del sistema.  |
| **Negociable** | Sí | La forma de ingresar los datos y la presentación de la pantalla puede modificarse, mediante usuario y contraseña. |
| **Valiosa** | Sí | Permite que los usuarios autorizados accedan al sistema y evita el acceso de personas no habilitadas. |
| **Estimable** | Sí | Sabemos qué debe hacer: pedir usuario y contraseña y validar los datos. |
| **Pequeña** | Sí | Se limita a validar credenciales, iniciar sesión e identificar el rol. |
| **Verificable** | Sí | Puede probarse con credenciales válidas, inválidas, usuarios inactivos y cierre de sesión. |

---

# H-U 2 — Gestión de usuarios

**Como** encargada,  
**quiero** registrar, modificar y desactivar usuarios,  
**para** mantener actualizada la información de las personas autorizadas a utilizar el sistema.

**Módulo:** Gestión de usuarios

**Requisitos relacionados:** RF-02; RF-21 y RF-24

**Requisitos no funcionales:** RNF-06; RNF-08 y RNF-10

### Criterios de aceptación

1- La encargada puede registrar un usuario con nombre de usuario y rol. 
2- El sistema no permite registrar dos usuarios con el mismo nombre de usuario.
3- La encargada puede modificar los datos de un usuario existente.
4- La encargada puede desactivar un usuario sin eliminar su historial de operaciones.
5- El sistema solicita confirmación antes de desactivar un usuario.
6- Un usuario desactivado no puede iniciar sesión.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede probarse utilizando usuarios de prueba sin necesidad de completar el resto de las funcionalidades. |
| **Negociable** | Sí | La forma de registrar, modificar o desactivar usuarios puede cambiar, siempre que se mantengan esas funciones.  |
| **Valiosa** | Sí | Permite mantener controlados y actualizados los usuarios que tienen acceso al sistema.  |
| **Estimable** | Sí | Los criterios definen las acciones principales: registrar, modificar y desactivar usuarios. |
| **Pequeña** | Sí | Se limita a administrar usuarios, sin incluir otras funciones. |
| **Verificable** | Sí | Se puede probar creando, modificando y desactivando usuarios. |

---

# H-U 3 — Gestionar roles y permisos

**Como** encargada,  
**quiero** asignar un rol a cada usuario,  
**para** controlar qué funcionalidades puede utilizar cada usuario.

**Módulo:** Gestionar roles y permisos

**Requisitos relacionados:** RF-02 y RF-22

**Requisitos no funcionales:** RNF-05 y RNF-06

### Criterios de aceptación

1- La encargada puede asignar o modificar el rol de un usuario activo.
2- El sistema aplica los permisos correspondientes al rol. 
3- Un usuario no puede acceder a una funcionalidad que no	tiene habilitada.
4- Ante un intento de acceso no autorizado, el sistema informa que el usuario no posee permisos suficientes.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede probarse asignando distintos roles a usuarios de prueba y verificando sus accesos.  |
| **Negociable** | Sí | Se puede cambiar la forma de mostrar los roles y permisos. |
| **Valiosa** | Sí | Evita que una persona acceda a funciones que no le corresponden. |
| **Estimable** | Sí | Los roles y permisos que debe tener cada usuario están definidos. |
| **Pequeña** | Sí | Solo se ocupa de asignar roles y controlar los permisos.  |
| **Verificable** | Sí | Se puede probar entrando con diferentes roles y comprobando sus permisos. |

---

# H-U 4 — Visualizar y abrir una mesa disponible

**Como** moza o encargada,  
**quiero** visualizar las 24 mesas y abrir una mesa disponible,
**para** comenzar la atención y asociar pedidos.

**Módulo:** Visualizar y abrir una mesa disponible

**Requisitos relacionados:** RF-03; RF-04; RF-05; RF-06; RF-21; RF-23; RF-24 y RF-25

**Requisitos no funcionales:** RNF-01; RNF-03; RNF-04; RNF-08; RNF-10; RNF-16 y RNF-18

### Criterios de aceptación

1- El sistema muestra las 24 mesas numeradas del 1 al 24 y su estado actual.
2- El sistema permite abrir una mesa únicamente cuando está Disponible. 
3- Antes de abrir la mesa, solicita confirmación.
4- Al confirmar, la mesa pasa a Ocupada y se genera un pedido activo asociado.
5- El sistema registra el usuario, la fecha y la hora de la apertura.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede probarse sin realizar una venta. |
| **Negociable** | Sí | La forma visual de representar las mesas, puede modificarse, siempre que la información sea clara y se mantenga la regla de que solo pueden abrirse mesas disponibles.  |
| **Valiosa** | Sí | Permite conocer rápidamente e identificar una mesa disponible para iniciar correctamente la atención y cargar un pedido. |
| **Estimable** | Sí | Sabemos que deben mostrarse 24 mesas y verificar la disponibilidad, confirmar la apertura y asociar la mesa a un pedido.  |
| **Pequeña** | Sí | Se concentra en consultar el estado de las mesas y abrir una mesa disponible. |
| **Verificable** | Sí | Puede probarse abriendo mesas disponibles y rechazando mesas ocupadas. |

---

# H-U 5 — Asociar pedidos a una mesa

**Como** encargada,  
**quiero** asociar pedidos a una mesa abierta,
**para** registrar correctamente el consumo del cliente. 

**Módulo:** Asociar pedidos a una mesa

**Requisitos relacionados:** RF-06 y RF-21 

**Requisitos no funcionales:** RNF-08; RNF-10; RNF-16 y RNF-18

### Criterios de aceptación

1- La encargada puede seleccionar una mesa abierta y visualizar el pedido activo asociado.
2- El sistema permite crear o visualizar el pedido activo asociado a esa mesa.
3- El pedido queda vinculado a la mesa seleccionada.
4- El sistema no permite asociar un pedido a una mesa cerrada, inexistente o sin autorización.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Requiere una mesa abierta con un pedido activo.  |
| **Negociable** | Sí | Puede modificarse la forma de seleccionar la mesa o confirmar la asociación. |
| **Valiosa** | Sí | Permite registrar el consumo de los clientes. |
| **Estimable** | Sí | Se limita a seleccionar la mesa, agregar productos y actualizar el total.  |
| **Pequeña** | Sí | No incluye cerrar la mesa, cobrar ni emitir comprobantes.  |
| **Verificable** | Sí | Puede probarse con mesas válidas, cerradas e inexistentes. |

---

# H-U 6 — Agregar productos al pedido

**Como** encargada,  
**quiero** agregar productos al pedido de una mesa, 
**para** registrar los productos solicitados por el cliente.

**Módulo:** Agregar productos al pedido

**Requisitos relacionados:** RF-07 y RF-26

**Requisitos no funcionales:** RNF-01; RNF-03; RNF-08; RNF-16 y RNF-18

### Criterios de aceptación

1. La encargada puede seleccionar un producto disponible e indicar cantidad.
2. El producto seleccionado se incorpora al pedido de la mesa. 
3. El sistema actualiza el detalle y el total del pedido.
4. El sistema no permite agregar productos a un pedido inexistente o cerrado.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Requiere una mesa con un pedido activo, que puede prepararse para la prueba.  |
| **Negociable** | Sí | Puede modificarse la forma de seleccionar productos y cantidades.  |
| **Valiosa** | Sí | Permite registrar el consumo real del cliente.  |
| **Estimable** | Sí | Los criterios indican que se selecciona un producto y se incorpora al pedido con su cantidad.  |
| **Pequeña** | Sí | Se limita a agregar productos y no incluye su modificación o eliminación. |
| **Verificable** | Sí | Se puede comprobar que el producto seleccionado aparezca en el pedido con la cantidad correspondiente.  |

---

# H-U 7 — Modificación de pedidos

**Como** encargada,  
**quiero** modificar la cantidad de un producto incluido en un pedido activo,  
**para** corregir cambios solicitados por los clientes antes del pago.

**Módulo:** Modificación de pedidos

**Requisitos relacionados:** RF-08 y RF-26

**Requisitos no funcionales:** RNF-03; RNF-08; RNF-10; RNF-16 y RNF-18

### Criterios de aceptación

1- La encargada puede modificar la cantidad de un producto del pedido activo
2- El sistema valida que la cantidad ingresada sea válida.
3- El sistema actualiza el detalle y el total del pedido.
4- La modificación queda asociada al pedido correspondiente.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede probarse sobre un pedido existente. |
| **Negociable** | Sí | Puede variar la forma de aumentar o disminuir cantidades. |
| **Valiosa** | Sí | Permite corregir el consumo registrado. |
| **Estimable** | Sí | La modificación y el recálculo están definidos.  |
| **Pequeña** | Sí | Solo modifica la cantidad de productos existentes.  |
| **Verificable** | Sí | Se puede probar aumentando, disminuyendo o ingresando cantidades. |

---

# H-U 8 — Eliminación de productos

**Como** encargada,  
**quiero** eliminar un producto de un pedido activo,   
**para** corregir el consumo cuando un producto ya no corresponde. 

**Módulo:** Eliminación de productos

**Requisitos relacionados:** RF-09; RF-21; RF-24; RF-25 y RF-26 

**Requisitos no funcionales:** RNF-03; RNF-08; RNF-10; RNF-16 y RNF-18

### Criterios de aceptación

1. La encargada puede seleccionar un producto del pedido para eliminarlo.
2- El sistema solicita confirmación antes de eliminar el producto.
3- Si confirma la eliminación, el producto se elimina del pedido.
4- Si cancela, el pedido permanece sin modificaciones.
5- El sistema registra el usuario, la fecha y la hora de la operación.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede probarse con un pedido que tenga productos cargados. |
| **Negociable** | Sí | La forma de solicitar la eliminación puede cambiar, pero debe mantenerse la confirmación antes de eliminar.  |
| **Valiosa** | Sí | Permite corregir errores en el pedido y mantener actualizado el consumo.  |
| **Estimable** | Sí | La selección, confirmación, eliminación y recálculo están definidos.  |
| **Pequeña** | Sí | Se limita a eliminar un producto de un pedido activo. |
| **Verificable** | Sí | Se puede probar confirmando y cancelando la eliminación.  |

---

# H-U 9 — Consulta de consumo

**Como** moza,  
**quiero** consultar el detalle del consumo de una mesa y obtener el importe actualizado, 
**para**  conocer cuánto debe abonar el cliente.

**Módulo:** Consulta de consumo

**Requisitos relacionados:** RF-10; RF-11; RF-14 y RF-26

**Requisitos no funcionales:** RNF-01; RNF-03; RNF-08; RNF-12 y RNF-20

### Criterios de aceptación

1. El sistema muestra los productos asociados a la mesa. 
2- El sistema muestra las cantidades y valores correspondientes. 
3- El sistema calcula automáticamente el importe del consumo.
4- Al modificarse el consumo, el importe se actualiza. 
5- El importe mostrado coincide con la suma de los productos registrados 

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede probarse con una mesa que tenga productos cargados y un consumo registrado. |
| **Negociable** | Sí | La forma de presentar el detalle y el importe puede cambiar, pero debe mostrarse la información necesaria. |
| **Valiosa** | Sí | Permite conocer el consumo y el importe que debe pagar el cliente. |
| **Estimable** | Sí | Se conocen los datos que deben mostrarse y calcularse. |
| **Pequeña** | Sí | Se concentra en consultar y calcular el consumo, sin incluir el registro del pago.  |
| **Verificable** | Sí | Se puede comparar el total mostrado con la suma de los productos.  |

---

# H-U 10 — Registro de pago

**Como** encargada,  
**quiero** registrar el pago de una mesa y seleccionar el medio utilizado,  
**para** registrar correctamente la venta. 

**Módulo:** Registro de pago

**Requisitos relacionados:** RF-12; RF-13; RF-14; RF-15; RF-21 y RF-24

**Requisitos no funcionales:** RNF-03; RNF-08; RNF-10; RNF-13; RNF-16 y RNF-18 

### Criterios de aceptación

1- La encargada puede seleccionar una mesa con consumo pendiente.
2- El sistema muestra el importe final y los medios de pago habilitados.
3- El pago queda registrado asociado a la mesa y al pedido correspondiente.
4- La venta se confirma únicamente cuando el pago es válido.
5- El sistema evita registrar pagos o ventas duplicadas ante una única confirmación.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede probarse en una mesa con consumo y un importe previamente calculado.  |
| **Negociable** | Sí | La forma de seleccionar el medio de pago puede modificarse, manteniendo las opciones habilitadas.   |
| **Valiosa** | Sí | Permite registrar el pago y completar la operación de venta.  |
| **Estimable** | Sí | Los criterios establecen la selección del medio de pago, el importe y el registro de la venta. |
| **Pequeña** | Sí | Se limita en registrar un pago y generar la venta.  |
| **Verificable** | Sí | Se puede probar pagando con efectivo, tarjeta o QR. |

---

# H-U 11 — Emisión de comprobante

**Como** encargada,  
**quiero** generar un comprobante después de registrar el pago, 
**para** entregar al cliente una constancia de la operación realizada. 

**Módulo:** Emisión de comprobante

**Requisitos relacionados:** RF-15 y RF-18 y RF-27

**Requisitos no funcionales:** RNF-03; RNF-08; RNF-12 y RNF-18

### Criterios de aceptación

1- El sistema permite generar el comprobante de una venta registrada. 
2. El comprobante contiene el importe y los datos de la operación requeridos. 
3. El comprobante identifica la mesa, el importe y el medio de pago.
4- El comprobante puede visualizarse y, si corresponde, imprimirse.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede probarse utilizando una venta previamente registrada.  |
| **Negociable** | Sí | El formato y la presentación del comprobante pueden modificarse, siempre que contenga la información requerida.  |
| **Valiosa** | Sí | Permite entregar  una constancia de pago por la venta realizada. |
| **Estimable** | Sí | Sabemos qué datos debe tener el comprobante. |
| **Pequeña** | Sí | Solo genera, muestra o imprime el comprobante.  |
| **Verificable** | Sí | Se puede comprobar que tenga los datos correctos de la venta.  |

---

# H-U 12 — Cerrar y liberar una mesa

**Como** encargada,  
**quiero** cerrar una mesa con el pago confirmado, 
**para** dejarla disponible para nuevos clientes.  

**Módulo:** Cerrar y liberar una mesa

**Requisitos relacionados:** RF-16; RF-17; RF-21; RF-24 y RF-25

**Requisitos no funcionales:** RNF-08; RNF-10; RNF-13; RNF-16 y RNF-18

### Criterios de aceptación

1. El sistema permite cerrar una mesa cuando el pago está confirmado.
2- El sistema solicita confirmación antes del cierre. 
3. Al cerrar la mesa, el estado cambia automáticamente a Disponible. 
4- La venta y el comprobante permanecen almacenados.
5- El sistema registra el usuario, la fecha y la hora del cierre.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede probarse con una mesa que haya completado correctamente el proceso de pago.  |
| **Negociable** | Sí | Puede cambiar la forma de confirmar el cierre.  |
| **Valiosa** | Sí | Permite liberar correctamente la mesa para que pueda utilizarse nuevamente. |
| **Estimable** | Sí | Los criterios establecen las condiciones de cierre y el cambio posterior del estado.  |
| **Pequeña** | Sí | Se limita al cierre y liberar una mesa. |
| **Verificable** | Sí | Puede probarse con una mesa pagada. |

---

# H-U 13 — Consulta historial de ventas

**Como** encargada,  
**quiero** consultar el historial de ventas registradas,  
**para** obtener información de operaciones realizadas anteriormente.

**Módulo:** Consulta historial de ventas

**Requisitos relacionados:** RF-18; RF-19; RF-28 y RF-29

**Requisitos no funcionales:** RNF-01; RNF-03; RNF-08 y RNF-12

### Criterios de aceptación

1. La encargada puede consultar ventas registradas. 
2. El sistema muestra la información disponible de cada venta. 
3. El historial permite identificar la operación consultada. 
4. La consulta no modifica los datos históricos 

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede probarse utilizando ventas previamente registradas.  |
| **Negociable** | Sí | La forma de mostrar o filtrar el historial puede modificarse sin cambiar el objetivo.  |
| **Valiosa** | Sí | Permite consultar operaciones anteriores y realizar un seguimiento de las ventas.  |
| **Estimable** | Sí | Se conocen los filtros y datos que deben mostrarse.  |
| **Pequeña** | Sí | Solo consulta el historial general de ventas. |
| **Verificable** | Sí | Puede probarse con ventas de distintas fechas. |

---

# H-U 14 — Consultar resumen de ventas

**Como** dueño o encargada,,  
**quiero** consultar un resumen de ventas y consumos, 
**para** obtener una visión general de la actividad del bar.

**Módulo:** Consultar resumen de ventas

**Requisitos relacionados:** RF-19 y RF-20

**Requisitos no funcionales:** RNF-01; RNF-03; RNF-08 y  RNF-12

### Criterios de aceptación

1. El sistema muestra un resumen basado en las ventas y consumos registrados. 
2. La información corresponde a los datos almacenados. 
3- La información mostrada coincide con las ventas almacenadas.
4- Si no existen ventas para el período seleccionado, el sistema informa que no hay resultados.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede probarse utilizando información histórica de ventas y consumos.  |
| **Negociable** | Sí | La forma de presentar el resumen puede modificarse, siempre que muestre la información requerida.   |
| **Valiosa** | Sí | Facilita el control y permite obtener una visión general de la actividad. |
| **Estimable** | Sí | El período y los datos del resumen están definidos. |
| **Pequeña** | Sí | Se limita a mostrar un resumen y no informes complejos. |
| **Verificable** | Sí | Se pueden comparar los resultados con las ventas registradas.  |

---

# H-U 15 — Consulta de trazabilidad de operaciones

**Como** administrador del sistema,   
**quiero**  consultar la trazabilidad de las operaciones realizadas, 
**para** saber qué usuario realizó una operación y cuándo fue realizada.

**Módulo:** Consulta de trazabilidad de operaciones

**Requisitos relacionados:** RF-21 y RF-24

**Requisitos no funcionales:** RNF-06; RNF-08; RNF-10 y RNF-22

### Criterios de aceptación

1 - El sistema registra el usuario, la fecha y la hora de las operaciones relevantes.
2- El administrador puede consultar los registros de trazabilidad.
3 -La información permite identificar la operación realizada.
4- Los usuarios sin permisos no pueden modificar ni eliminar los registros de auditoría.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede probarse utilizando operaciones previamente registradas en el sistema.  |
| **Negociable** | Sí | La forma de consultar la información puede modificarse, pero deben mantenerse el usuario, la fecha y la hora.  |
| **Valiosa** | Sí | Permite controlar quién realizó una operación y cuándo, mejorando el seguimiento de las actividades.  |
| **Estimable** | Sí | Los criterios establecen claramente los datos que deben registrarse y consultarse.  |
| **Pequeña** | Sí | Solo registra y consulta las operaciones realizadas.  |
| **Verificable** | Sí | Puede comprobarse el registro de usuario, fecha y hora. |

---

# H-U 16 — Gestión de productos

**Como** encargada,  
**quiero** registrar, modificar y desactivar productos ofrecidos por el bar,  
**para** mantener actualizada la información utilizada al registrar pedidos. 
**Módulo:** Gestión de productos

**Requisitos relacionados:** RF-07 y RF-30

**Requisitos no funcionales:** RNF-06; RNF-08; RNF-15

### Criterios de aceptación

1- La encargada puede registrar un producto con sus datos obligatorios.
2- La encargada puede modificar los datos de un producto existente.
3- La encargada puede desactivar un producto sin eliminar su historial.
4- Un producto desactivado no puede agregarse a nuevos pedidos.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede probarse consultando el listado de productos sin necesidad de completar una venta.   |
| **Negociable** | Sí | Puede cambiar la forma de registrar y editar productos.  |
| **Valiosa** | Sí | Mantiene actualizado el catálogo del bar.  |
| **Estimable** | Sí | Los criterios indican que deben mostrarse los productos disponibles y que los productos no disponibles no puedan seleccionarse.  |
| **Pequeña** | Sí | Se concentra en la consulta y disponibilidad de productos. |
| **Verificable** | Sí | Se puede probar creando, modificando y desactivando productos.  |




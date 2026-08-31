# Historias de usuario
---
# H-U 1 — Inicio de sesión

**Como** usuario del sistema,  
**quiero** iniciar sesión mediante usuario y contraseña,  
**para** acceder de forma segura a las funcionalidades habilitadas según mi rol.

**Módulo:** Inicio de Sesión

**Requisitos relacionados:** RF-01

**Requisitos no funcionales:** RNF-05, RNF-07 y RNF-19

### Criterios de aceptación

1. El sistema permite ingresar nombre de usuario y contraseña.
2. Si las credenciales son correctas y el usuario se encuentra activo, el sistema permite iniciar sesión.
3. Si las credenciales son incorrectas, el sistema rechaza el acceso e informa un mensaje de error.
4. Al iniciar sesión, el sistema identifica el rol del usuario.
5. Al cerrar sesión, el usuario no puede continuar utilizando funciones restringidas.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede desarrollarse y probarse de forma separada, utilizando usuarios de prueba definidos. |
| **Negociable** | Sí | El diseño visual, mensajes de error y duración de sesión pueden ajustarse sin modificar el objetivo. |
| **Valiosa** | Sí | Permite el acceso seguro de los usuarios al sistema según su rol. |
| **Estimable** | Sí | Tiene criterios claros y una estimación de 3 puntos. |
| **Pequeña** | Sí | Se limita a validar credenciales, iniciar sesión e identificar el rol. |
| **Verificable** | Sí | Puede probarse con credenciales válidas, inválidas, usuarios inactivos y cierre de sesión. |

---

# H-U 2 — Gestión de usuarios

**Como** encargada,  
**quiero** registrar, modificar y desactivar usuarios,  
**para** mantener actualizada la información de las personas autorizadas a utilizar el sistema.

**Módulo:** Gestión de usuarios

**Requisitos relacionados:** RF-02

**Requisitos no funcionales:** RNF-05, RNF-07, RNF-08 y RNF-22

### Criterios de aceptación

1. La encargada puede registrar un usuario con nombre de usuario, rol y estado.
2. El sistema no permite registrar dos usuarios con el mismo nombre de usuario.
3. La encargada puede modificar los datos de un usuario existente.
4. La administradora puede desactivar un usuario sin eliminar su historial de operaciones.
5. El sistema solicita confirmación antes de desactivar un usuario.
6. Un usuario desactivado no puede iniciar sesión.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede trabajarse como un módulo específico de administración de usuarios. |
| **Negociable** | Sí | La interfaz y forma de carga de datos pueden definirse durante el desarrollo. |
| **Valiosa** | Sí | Permite mantener actualizadas las personas autorizadas a utilizar el sistema. |
| **Estimable** | Sí | Los datos obligatorios, validaciones y acciones permitidas están definidos. |
| **Pequeña** | Sí | Se limita a registrar, modificar y desactivar usuarios; no incluye permisos individuales. |
| **Verificable** | Sí | Puede comprobarse mediante altas, modificaciones, intentos de usuario duplicado y desactivaciones. |

---

# H-U 3 — Asignación de roles

**Como** encargada,  
**quiero** asignar un rol a cada usuario,  
**para** controlar las funciones a las que puede acceder dentro del sistema.

**Módulo:** Asignación de roles y permisos

**Requisitos relacionados:** RF-02 y RF-22

**Requisitos no funcionales:** RNF-05, RNF-06, RNF-19 y RNF-22

### Criterios de aceptación

1. El sistema muestra los roles disponibles: Moza, Encargada y Administradora del sistema.
2. La encargada puede asignar o modificar el rol de un usuario activo.
3. El sistema no permite asignar un rol inexistente.
4. Un usuario no puede acceder a una funcionalidad que no esté autorizada para su rol.
5. Ante un intento de acceso no autorizado, el sistema informa que el usuario no posee permisos suficientes.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | La asignación de roles constituye una funcionalidad administrativa diferenciada. |
| **Negociable** | Sí | Puede negociarse cómo se visualizan los roles y permisos sin modificar la matriz definida. |
| **Valiosa** | Sí | Evita que usuarios no autorizados accedan a funciones restringidas. |
| **Estimable** | Sí | Los roles, permisos y comportamiento ante accesos no autorizados están definidos. |
| **Pequeña** | Sí | Se limita a asignar roles y aplicar la matriz de permisos predefinida. |
| **Verificable** | Sí | Puede probarse iniciando sesión con usuarios de cada rol e intentando acceder a distintas funciones. |

---

# H-U 4 — Visualización de mesas

**Como** moza,  
**quiero** visualizar las 24 mesas y su estado actual,  
**para** conocer rápidamente la disponibilidad del salón.

**Módulo:** Visualización de mesas

**Requisitos relacionados:** RF-03, RF-04 y RF-23

**Requisitos no funcionales:** RNF-01, RNF-03, RNF-04, RNF-12, RNF-16 y RNF-20

### Criterios de aceptación

1. El sistema muestra las 24 mesas numeradas del 1 al 24.
2. Cada mesa muestra uno de los estados definidos: Disponible, Ocupada o Pendiente de cierre.
3. Las mesas disponibles se diferencian visualmente de las ocupadas y pendientes de cierre.
4. El estado visualizado se actualiza cuando se abre, paga o cierra una mesa.
5. La pantalla puede utilizarse correctamente desde una computadora o tablet.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | La visualización del salón puede desarrollarse como una pantalla específica. |
| **Negociable** | Sí | Puede modificarse el diseño de las mesas, colores e íconos sin cambiar el objetivo. |
| **Valiosa** | Sí | Permite conocer rápidamente la disponibilidad del salón. |
| **Estimable** | Sí | Se conocen la cantidad de mesas, los estados y el comportamiento esperado. |
| **Pequeña** | Sí | Solo contempla mostrar las 24 mesas y sus estados. |
| **Verificable** | Sí | Puede comprobarse que se visualicen las 24 mesas y que sus estados se actualicen correctamente. |

---

# H-U 5 — Apertura de mesa

**Como** moza,  
**quiero** abrir una mesa disponible,  
**para** comenzar a registrar el consumo de los clientes.

**Módulo:** Apertura de mesas

**Requisitos relacionados:** RF-05, RF-06, RF-21 y RF-24

**Requisitos no funcionales:** RNF-01, RNF-02, RNF-08, RNF-10, RNF-16 y RNF-18

### Criterios de aceptación

1. La moza puede seleccionar únicamente mesas con estado Disponible.
2. El sistema solicita confirmación antes de abrir la mesa.
3. Al confirmar la apertura, la mesa cambia automáticamente al estado Ocupada.
4. Al abrir una mesa, el sistema crea un pedido activo asociado a esa mesa.
5. El sistema registra el usuario, fecha y hora de apertura.
6. El sistema no permite abrir una mesa que ya esté Ocupada o Pendiente de cierre.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Aunque utiliza la pantalla de mesas, la apertura es una operación puntual y diferenciada. |
| **Negociable** | Sí | Puede definirse si se abre con botón, doble clic o ventana de confirmación. |
| **Valiosa** | Sí | Permite comenzar una atención y habilitar el registro de consumo. |
| **Estimable** | Sí | Están definidas la condición inicial, el cambio de estado y la creación del pedido. |
| **Pequeña** | Sí | Solo abre una mesa y crea su pedido activo asociado. |
| **Verificable** | Sí | Puede probarse con una mesa disponible, una mesa ocupada y una mesa pendiente de cierre. |

---

# H-U 6 — Agregar productos al pedido

**Como** moza,  
**quiero** agregar productos al pedido de una mesa ocupada,  
**para** registrar el consumo solicitado por los clientes.

**Módulo:** Agregar productos al pedido

**Requisitos relacionados:** RF-07 y RF-26

**Requisitos no funcionales:** RNF-01, RNF-02, RNF-03, RNF-08, RNF-16 y RNF-18

### Criterios de aceptación

1. La moza puede seleccionar una mesa con pedido activo.
2. El sistema muestra únicamente productos con estado Disponible.
3. La moza puede agregar uno o más productos indicando una cantidad mayor a cero.
4. Cada producto agregado queda asociado al pedido de la mesa seleccionada.
5. El sistema registra el precio vigente del producto al momento de agregarlo.
6. Al agregar un producto, el sistema actualiza automáticamente el total del pedido.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede desarrollarse como una función específica utilizando una mesa y productos de prueba. |
| **Negociable** | Sí | La forma de buscar y seleccionar productos puede modificarse sin afectar la necesidad. |
| **Valiosa** | Sí | Permite registrar el consumo solicitado por los clientes. |
| **Estimable** | Sí | Están definidos productos disponibles, cantidad válida, precio vigente y actualización de total. |
| **Pequeña** | Sí | Se limita a incorporar productos a un pedido activo. |
| **Verificable** | Sí | Puede comprobarse que se agreguen productos, se almacene el precio y se actualice el total. |

---

# H-U 7 — Modificación de pedidos

**Como** moza,  
**quiero** modificar la cantidad de un producto incluido en un pedido activo,  
**para** corregir cambios solicitados por los clientes antes del pago.

**Módulo:** Modificación de pedidos

**Requisitos relacionados:** RF-08, RF-21, RF-24 y RF-26

**Requisitos no funcionales:** RNF-03, RNF-08, RNF-10, RNF-16 y RNF-18

### Criterios de aceptación

1. La moza puede modificar la cantidad de un producto únicamente si la mesa está en estado Ocupada.
2. El sistema no permite cantidades iguales a cero o negativas.
3. Al modificar una cantidad, el sistema actualiza el subtotal del producto y el total del pedido.
4. El sistema no permite modificar productos de una mesa que tenga el pago confirmado.
5. El sistema registra el usuario, fecha y hora de la modificación.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede probarse sobre un pedido existente sin incluir otras operaciones del flujo. |
| **Negociable** | Sí | Puede negociarse la interfaz para aumentar o disminuir cantidades. |
| **Valiosa** | Sí | Permite corregir cambios solicitados por el cliente antes del pago. |
| **Estimable** | Sí | Las reglas de cantidades permitidas, actualización de total y estado de mesa están definidas. |
| **Pequeña** | Sí | Solo contempla la modificación de cantidades de productos ya cargados. |
| **Verificable** | Sí | Puede probarse con cantidades válidas, cero, negativas y pedidos ya pagados. |

---

# H-U 8 — Eliminación de productos

**Como** moza,  
**quiero** eliminar un producto de un pedido activo,  
**para** corregir productos cargados por error antes de confirmar el pago.

**Módulo:** Eliminación de productos

**Requisitos relacionados:** RF-09, RF-25 y RF-26

**Requisitos no funcionales:** RNF-01, RNF-08, RNF-10, RNF-13, RNF-16 y RNF-18

### Criterios de aceptación

1. La moza puede seleccionar un producto perteneciente a un pedido activo.
2. El sistema solicita confirmación antes de eliminar el producto.
3. Si la moza confirma la eliminación, el producto se elimina del pedido.
4. Si la moza cancela la operación, el pedido no presenta modificaciones.
5. Luego de eliminar un producto, el sistema actualiza el total del pedido.
6. El sistema registra el usuario, fecha y hora de la eliminación.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | La eliminación es una acción puntual dentro de un pedido activo. |
| **Negociable** | Sí | Puede variar el diseño del mensaje de confirmación sin modificar la regla de negocio. |
| **Valiosa** | Sí | Permite corregir productos cargados erróneamente antes del cobro. |
| **Estimable** | Sí | Las condiciones de eliminación, confirmación, cancelación y actualización del total están definidas. |
| **Pequeña** | Sí | Se limita a eliminar un producto de un pedido activo. |
| **Verificable** | Sí | Puede probarse confirmando y cancelando la eliminación, y comprobando el nuevo total. |

---

# H-U 9 — Consulta de consumo

**Como** moza,  
**quiero** consultar el detalle del consumo de una mesa y su importe total actualizado,  
**para** informar correctamente al cliente cuánto debe abonar.

**Módulo:** Consulta de consumo

**Requisitos relacionados:** RF-10, RF-11 y RF-14

**Requisitos no funcionales:** RNF-01, RNF-03, RNF-08, RNF-12, RNF-16 y RNF-18

### Criterios de aceptación

1. La moza puede seleccionar una mesa con estado Ocupada.
2. El sistema muestra los productos asociados al pedido de la mesa.
3. Para cada producto, el sistema muestra cantidad, precio unitario y subtotal.
4. El sistema calcula y muestra el importe total del consumo.
5. El total mostrado coincide con la suma de los subtotales de los productos.
6. El importe se actualiza automáticamente cuando se agregan, modifican o eliminan productos.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede desarrollarse como una consulta sobre pedidos de prueba ya cargados. |
| **Negociable** | Sí | La disposición visual de productos, subtotales y total puede ajustarse. |
| **Valiosa** | Sí | Permite informar correctamente al cliente los productos consumidos y el importe a pagar. |
| **Estimable** | Sí | Se define qué información debe visualizarse y cómo se calcula el total. |
| **Pequeña** | Sí | Se limita a consultar el consumo y su importe actualizado. |
| **Verificable** | Sí | Puede probarse comparando productos, cantidades, subtotales y total esperado. |

---

# H-U 10 — Registro de pago

**Como** moza,  
**quiero** registrar el pago de una mesa y seleccionar el medio utilizado,  
**para** confirmar el cobro y generar el registro de la venta.

**Módulo:** Registro de pago

**Requisitos relacionados:** RF-12, RF-13 y RF-15

**Requisitos no funcionales:** RNF-03, RNF-08, RNF-10, RNF-16, RNF-18 y RNF-22

### Criterios de aceptación

1. La moza puede registrar un pago únicamente para una mesa Ocupada con al menos un producto cargado.
2. El sistema muestra el importe total antes de confirmar el pago.
3. La moza puede seleccionar efectivo, tarjeta o código QR como medio de pago.
4. El sistema no permite confirmar un pago si no se seleccionó un medio de pago.
5. Al confirmar el pago, el sistema genera automáticamente la venta.
6. La venta almacena detalle de productos, total, medio de pago, usuario, fecha y hora.
7. Después de confirmar el pago, la mesa cambia al estado Pendiente de cierre.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede probarse con una mesa de prueba que tenga un pedido activo y total calculado. |
| **Negociable** | Sí | La interfaz de selección del medio de pago puede ajustarse sin modificar las reglas definidas. |
| **Valiosa** | Sí | Permite confirmar el cobro, registrar la venta y avanzar al cierre de mesa. |
| **Estimable** | Sí | Los medios de pago, pago único, vuelto, validaciones y resultado esperado están definidos. |
| **Pequeña** | Sí | Se limita a registrar un pago único y generar automáticamente la venta asociada. |
| **Verificable** | Sí | Puede probarse con efectivo, tarjeta, QR, falta de medio de pago e importe insuficiente. |

---

# H-U 11 — Emisión de comprobante

**Como** moza,  
**quiero** emitir o visualizar el comprobante de una venta confirmada,  
**para** entregar al cliente una constancia del pago realizado.

**Módulo:** Emisión de comprobante

**Requisitos relacionados:** RF-27

**Requisitos no funcionales:** RNF-01, RNF-03, RNF-12 y RNF-18

### Criterios de aceptación

1. El sistema permite emitir un comprobante únicamente para ventas confirmadas.
2. El comprobante incluye número de venta, fecha, hora, número de mesa, detalle de productos, total abonado y medio de pago.
3. El comprobante identifica al usuario que registró el pago, con un número único asociado.
4. El comprobante puede visualizarse en pantalla e imprimirse.
5. El sistema no permite emitir un comprobante para una venta inexistente o no confirmada.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede desarrollarse y verificarse sobre una venta confirmada de prueba. |
| **Negociable** | Sí | El diseño, tamaño y formato visual del comprobante pueden ajustarse. |
| **Valiosa** | Sí | Brinda al cliente una constancia de la venta y del pago realizado. |
| **Estimable** | Sí | Se especificaron los datos mínimos y los medios de visualización e impresión. |
| **Pequeña** | Sí | Solo contempla generar, visualizar e imprimir el comprobante. |
| **Verificable** | Sí | Puede comprobarse que el comprobante tenga número único y datos coincidentes con la venta. |

---

# H-U 12 — Cierre de mesa

**Como** moza,  
**quiero** cerrar una mesa después de confirmar el pago,  
**para** dejarla disponible para nuevos clientes.

**Módulo:** Cierre de mesa

**Requisitos relacionados:** RF-16 y RF-17

**Requisitos no funcionales:** RNF-03, RNF-08, RNF-10, RNF-13, RNF-16 y RNF-18

### Criterios de aceptación

1. La moza puede cerrar únicamente una mesa que se encuentre en estado Pendiente de cierre.
2. El sistema solicita confirmación antes de cerrar la mesa.
3. Si la moza confirma el cierre, la mesa cambia al estado Disponible.
4. Si la moza cancela el cierre, la mesa permanece Pendiente de cierre.
5. El sistema registra el usuario, fecha y hora del cierre.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede desarrollarse como una operación puntual sobre mesas con pago confirmado. |
| **Negociable** | Sí | La forma de confirmar el cierre puede ajustarse sin cambiar el resultado esperado. |
| **Valiosa** | Sí | Libera la mesa para atender nuevos clientes. |
| **Estimable** | Sí | Están definidos el estado previo, la confirmación, el cambio de estado y la trazabilidad. |
| **Pequeña** | Sí | Se limita a cerrar una mesa ya pagada. |
| **Verificable** | Sí | Puede probarse cerrando mesas pendientes de cierre y verificando que pasen a Disponible. |

---

# H-U 13 — Historial de ventas

**Como** encargada,  
**quiero** consultar el historial de ventas registradas,  
**para** revisar las operaciones realizadas por el bar.

**Módulo:** Consulta e historial de ventas

**Requisitos relacionados:** RF-18, RF-19 y RF-28

**Requisitos no funcionales:** RNF-01, RNF-03, RNF-10, RNF-12 y RNF-22

### Criterios de aceptación

1. La encargada puede consultar todas las ventas confirmadas.
2. El sistema permite filtrar ventas por fecha desde y fecha hasta.
3. Cada venta muestra número de venta, fecha, hora, mesa, total, medio de pago y usuario responsable, desde la más reciente hasta la más antigua.
4. Si no existen ventas para el período consultado, el sistema informa que no se encontraron registros.
5. El historial es de solo lectura y no permite modificar ventas registradas.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Es una consulta administrativa diferenciada de la operación diaria de mesas y pedidos. |
| **Negociable** | Sí | La forma visual de presentar ventas y filtros puede adaptarse. |
| **Valiosa** | Sí | Permite controlar y revisar las operaciones realizadas por el bar. |
| **Estimable** | Sí | Los campos mostrados, filtros, ordenamiento y comportamiento sin resultados están definidos. |
| **Pequeña** | Sí | Se limita al historial general; no incluye consulta por mesa ni resumen. |
| **Verificable** | Sí | Puede probarse con ventas de distintos días y verificar el filtrado y ordenamiento. |

---

# H-U 14 — Resumen de ventas

**Como** encargada,  
**quiero** obtener información resumida de las ventas realizadas,  
**para** controlar la actividad comercial del bar durante un período determinado.

**Módulo:** Consulta de ventas

**Requisitos relacionados:** RF-20

**Requisitos no funcionales:** RNF-01, RNF-03, RNF-08, RNF-12 y RNF-22

### Criterios de aceptación

1. La encargada puede seleccionar un período de fechas para consultar el resumen.
2. El sistema muestra el importe total vendido durante el período seleccionado.
3. El sistema muestra la cantidad de ventas realizadas.
4. El sistema muestra el total cobrado por efectivo, tarjeta y código QR.
5. El sistema muestra el producto más vendido del período.
6. Los importes del resumen coinciden con las ventas almacenadas en el historial.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | El resumen es una funcionalidad de consulta separada del historial detallado. |
| **Negociable** | Sí | El diseño de los indicadores, tarjetas o gráficos puede modificarse. |
| **Valiosa** | Sí | Permite a la encargada controlar la actividad comercial durante un período. |
| **Estimable** | Sí | Se definieron los indicadores: total vendido, cantidad de ventas, medios de pago y producto más vendido. |
| **Pequeña** | Sí | Se limita a un resumen del período elegido y no incorpora reportes complejos. |
| **Verificable** | Sí | Puede contrastarse cada indicador con las ventas existentes en el historial. |

---

# H-U 15 — Consulta de trazabilidad

**Como** encargada,  
**quiero** consultar qué usuario realizó una operación relevante y cuándo la realizó,  
**para** mantener la trazabilidad y facilitar el control de las operaciones.

**Módulo:** Consulta de trazabilidad

**Requisitos relacionados:** RF-21 y RF-24

**Requisitos no funcionales:** RNF-08, RNF-10 y RNF-22

### Criterios de aceptación

1. El sistema registra trazabilidad para altas, modificaciones y desactivaciones de usuarios.
2. El sistema registra la apertura y cierre de mesas.
3. El sistema registra la incorporación, modificación y eliminación de productos en pedidos.
4. El sistema registra pagos confirmados y ventas generadas.
5. Cada registro de trazabilidad incluye tipo de operación, elemento afectado, usuario, fecha y hora.
6. La encargada puede consultar la trazabilidad por fecha, usuario y tipo de operación.
7. Los registros de trazabilidad no pueden ser modificados ni eliminados.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Aunque recibe información de varios módulos, se desarrolla como una consulta específica de auditoría. |
| **Negociable** | Sí | La forma de mostrar filtros, fechas y registros puede ajustarse. |
| **Valiosa** | Sí | Permite identificar qué usuario realizó una operación y cuándo la realizó. |
| **Estimable** | Sí | Están definidos los eventos auditados, los datos guardados y los filtros disponibles. |
| **Pequeña** | Sí | Se limita a registrar y consultar trazabilidad; no modifica las operaciones originales. |
| **Verificable** | Sí | Puede probarse realizando operaciones y verificando que queden registradas con usuario, fecha y hora. |

---

# H-U 16 — Gestión de productos

**Como** encargada,  
**quiero** registrar, modificar y desactivar productos ofrecidos por el bar,  
**para** mantener actualizada la información utilizada al registrar pedidos.

**Módulo:** Gestión de productos

**Requisitos relacionados:** RF-30

**Requisitos no funcionales:** RNF-06, RNF-08, RNF-12, RNF-17 y RNF-18

### Criterios de aceptación

1. La encargada puede registrar un producto con código, nombre, categoría, precio y estado.
2. El sistema no permite registrar productos con código repetido.
3. El sistema no permite registrar productos sin nombre, sin categoría o con precio igual a cero o negativo.
4. La encargada puede modificar el nombre, categoría, precio y disponibilidad de un producto existente.
5. La encargada puede desactivar un producto para impedir que sea agregado a nuevos pedidos.
6. El sistema solicita confirmación antes de desactivar un producto.
7. Los productos desactivados siguen figurando en ventas históricas, pero no aparecen como disponibles para pedidos nuevos.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Es un módulo administrativo propio, aunque luego sea utilizado para la gestión de pedidos. |
| **Negociable** | Sí | La interfaz de carga, categorías y visualización de productos puede ajustarse. |
| **Valiosa** | Sí | Mantiene actualizado el catálogo de productos disponibles para la atención. |
| **Estimable** | Sí | Los campos, validaciones, modificación de precios, disponibilidad y desactivación están definidos. |
| **Pequeña** | Sí | Se limita al mantenimiento del catálogo de productos, sin incluir control de stock o proveedores. |
| **Verificable** | Sí | Puede probarse con altas, códigos duplicados, precios inválidos, modificaciones y desactivaciones. |


## Fin de las Historias de Usuario

**Sistema:** Point of Sale (POS) — Bar Carrefour  
**Cantidad de Historias de Usuario:** 16

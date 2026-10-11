# Historias de usuario
---
# HU - 1 — Iniciar sesión

**Como** empleado del bar (moza, encargada o administrador),   
**quiero** iniciar sesión mediante mi usuario y contraseña, 
**para** acceder de forma segura a las funcionalidades que me corresponden según mi rol. 

**Módulo:** Iniciar sesión

**Requisitos relacionados:** RF-01 y RF 22

**Requisitos no funcionales:** RNF-05; RNF-07; RNF-19 y RNF-23

### Criterios de aceptación

1- El sistema permite ingresar con usuario y contraseña.
2- Si las credenciales son correctas y el usuario está activo, se habilita el acceso a la interfaz autorizada. 
3- Si los datos son incorrectos, se rechaza el ingreso con un mensaje seguro: "Usuario o contraseña incorrectos".
4- No se permite acceder a ninguna función operativa sin previa autenticación.
5- La sesión se cierra tras 10 minutos de inactividad, exigiendo re-autenticarse para continuar.
6- Las credenciales se transmiten por https con TLS.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede probarse con usuarios de prueba sin necesitar mesas, pedidos o ventas.  |
| **Negociable** | Sí | Se puede definir la presentación y el flujo de ingreso, manteniendo la autenticación requerida. |
| **Valiosa** | Sí | Protege el acceso y permite que cada usuario utilice las funciones que corresponden a su rol. |
| **Estimable** | Sí | El alcance está limitado al ingreso, validación, rol y sesión. |
| **Pequeña** | Sí | Se limita a validar credenciales, iniciar sesión e identificar el rol. |
| **Verificable** | Sí | Puede probarse con credenciales válidas, inválidas, usuarios inactivos y cierre de sesión. |

---

# HU - 2 — Gestionar usuarios y roles

**Como** administrador del sistema,  
**quiero** registrar, asignar roles, modificar y dar de baja a usuarios,  
**para** asegurar que cada trabajador acceda solo a las funciones que le corresponden.

**Módulo:** Gestionar usuarios y roles

**Requisitos relacionados:** RF-02; RF-22 y RF-25

**Requisitos no funcionales:** RNF-06 y RNF-07

### Criterios de aceptación

1- El administrador puede crear nuevos usuarios indicando nombre, usuario, contraseña inicial y rol asignado.
2- Permite modificar datos personales y reasignar roles de usuarios ya registrados.
3- Permite desactivar (baja lógica) cuentas de usuario previa confirmación.
4- El usuario inactivo no puede iniciar sesión, preservándose su historial operativo.
5- Solo el rol Administrador tiene acceso a este módulo; otros perfiles son rechazados. 
6- La contraseña inicial se almacena con hash seguro.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede probarse con usuarios de prueba sin completar las demás funcionalidades.  |
| **Negociable** | Sí | Puede cambiar la forma de administrar usuarios, manteniendo las reglas de acceso.  |
| **Valiosa** | Sí | Evita accesos indebidos y permite administrar quién puede utilizar cada función. |
| **Estimable** | Sí | Las acciones principales son claras: alta, modificación, baja y asignación de rol. |
| **Pequeña** | Sí | Se limita a usuarios y roles. |
| **Verificable** | Sí | Se crea un usuario moza, se valida su rol y se confirma que no pueda abrir una función no permitida. |

---

# HU - 3 — Gestionar mesas

**Como** moza o encargada,  
**quiero** ver el tablero con las 24 mesas y su estado (Disponible, Ocupada o Pendiente de cierre), 
**para** saber dónde ubicar a los clientes sin preguntar. 

**Módulo:** Gestionar mesas

**Requisitos relacionados:** RF-03; RF-04 y RF-23

**Requisitos no funcionales:** RNF-03; RNF-04; RNF-11 y  RNF-20

### Criterios de aceptación

1- El tablero presenta las 24 mesas numeradas del 1 al 24, adaptable a tablet y PC.
2- Cada mesa muestra de forma diferenciada su estado: "Disponible", "Ocupada" o "Pendiente de cierre".
3- Los cambios de estado se actualizan en todos los dispositivos conectados en menos de 3 segundos sin recarga manual.  
4- Soporta la consulta concurrente de al menos 2 operadores simultáneos sin inconsistencias.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede probarse utilizando mesas de prueba en diferentes estados, sin necesitar completar el proceso de venta.  |
| **Negociable** | Sí | La disposición estética, íconos y paleta de colores son consensuables, siempre que los estados sean claros.  |
| **Valiosa** | Sí | Permite conocer rápidamente la situación de las mesas y coordinar la atención. |
| **Estimable** | Sí | Sabemos que deben mostrarse 24 mesas y mostrar el estado actual. |
| **Pequeña** | Sí | Se concentra únicamente en visualizar las mesas y sus estados.  |
| **Verificable** | Sí | Con dos pantallas abiertas, se comprueba un cambio desde otro dispositivo en menos de 3 segundos.  |

---

# HU - 4 — Abrir una mesa disponible

**Como** encargada,  
**quiero** registrar la apertura de una mesa que esté disponible,
**para** iniciar la atención de los clientes.

**Módulo:** Abrir una mesa disponible

**Requisitos relacionados:** RF-05 y RF-25

**Requisitos no funcionales:** RNF-01 y RNF-03

### Criterios de aceptación

1- Muestra las 24 mesas numeradas del 1 al 24  y su estado actual.
2- Solo se puede abrir una mesa cuando está Disponible. 
3- Antes de abrir la mesa, el sistema solicita confirmación. 
4- Al confirmar, la mesa pasa a Ocupada y se refleja en el tablero.
5- La apertura de una mesa debe poder realizarse en un máximo de 3 pantallas. 

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Solo requiere una mesa en estado disponible para ser ejecutada. |
| **Negociable** | Sí | Puede cambiar la forma de seleccionar y confirmar la mesa. |
| **Valiosa** | Sí | Permite iniciar correctamente la atención y evita asignar mesas que no están disponibles.  |
| **Estimable** | Sí | Incluye selección, validación, confirmación y cambio de estado.  |
| **Pequeña** | Sí | Se limita exclusivamente a la apertura de una mesa. |
| **Verificable** | Sí | Se abre una mesa disponible (pasa a Ocupada) y si se intenta abrir una ocupada (el sistema lo impide). |

---

# HU - 5 — Cargar pedidos a una mesa

**Como** encargada,  
**quiero** asociar pedidos a una mesa abierta,
**para** registrar correctamente el consumo del cliente. 

**Módulo:** Cargar pedidos a una mesa

**Requisitos relacionados:** RF-06 y RF-24

**Requisitos no funcionales:** RNF-01 y RNF-08

### Criterios de aceptación

1- El sistema vincula un nuevo pedido únicamente a mesas abiertas en estado "Ocupada".
2- El pedido queda vinculado a la mesa seleccionada.
3- El sistema impide asociar pedidos a mesas que se encuentren "Disponibles", "Pendientes de cierre”.
4- El pedido registra el usuario que realizó la asociación. 
5- Si ocurre un error, no queda un pedido parcial.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede probarse con una mesa de prueba en estado “Ocupada”, sin necesidad de completar el cobro ni el cierre de la mesa.  |
| **Negociable** | Sí | Puede modificarse la forma de seleccionar la mesa, manteniendo la regla de vincular el pedido a una mesa ocupada.  |
| **Valiosa** | Sí | Permite relacionar el pedido con la mesa correcta y mantener el consumo identificado.  |
| **Estimable** | Sí | Están definidas la mesa, el pedido y las validaciones necesarias para realizar la asociación.   |
| **Pequeña** | Sí | No incluye modificación, cobro, comprobante ni cierre. |
| **Verificable** | Sí | Se puede asociar un pedido a una mesa ocupada y comprobar que quede correctamente vinculado; también se puede intentar asociarlo a una mesa no válida.  |

---

# HU - 6 — Agregar productos al pedido

**Como** encargada,  
**quiero** agregar, modificar y eliminar productos del pedido de una mesa,
**para** mantener actualizado el consumo solicitado por el cliente. 

**Módulo:** Agregar productos al pedido

**Requisitos relacionados:** RF-07; RF-08; RF-09; RF-25 y RF-26

**Requisitos no funcionales:** RNF-01; RNF- 02 y RNF-03

### Criterios de aceptación

1- Permite seleccionar productos del catálogo vigente e indicar la cantidad para incorporarlos al pedido.
2- Un pedido de hasta 5 productos se carga en 5 pasos de interacción como máximo.
3- Permite modificar las cantidades y/o eliminar un producto antes de su confirmación o cierre. 
4- El importe total del pedido se recalcula automáticamente ante cualquier cambio.
5- No se permite editar pedidos de mesas que no estén abiertas o con el cobro cerrado. 

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Se prueba con un pedido de una mesa de prueba y un catálogo cargado.  |
| **Negociable** | Sí | La disposición del catálogo y buscador son adaptables con los usuarios.  |
| **Valiosa** | Sí | Mantiene el consumo real actualizado y reduce errores de registración y cobro.  |
| **Estimable** | Sí | Las operaciones y sus restricciones están claramente delimitadas.  |
| **Pequeña** | Sí | Se limita a agregar productos y modificar cantidades.  |
| **Verificable** | Sí | Se agrega, modifica y elimina un producto y se comprueba que el pedido y total se actualicen.  |

---

# HU - 7 — Consultar consumo y total

**Como** moza o encargada,
**quiero** consultar el detalle del consumo de una mesa y el total calculado,  
**para** comunicar el importe al cliente y comprobar que la cuenta sea exacta antes de cobrar. 

**Módulo:** Consultar consumo y total

**Requisitos relacionados:** RF-10; RF-11 y RF-26

**Requisitos no funcionales:** RNF-01; RNF-03 y RNF-12 

### Criterios de aceptación

1- Muestra una pantalla con la lista de productos: nombre, cantidad, precio unitario y subtotal.
2- Muestra el importe total calculado de forma automática (suma de cantidades × precio unitario)    
3- Cuando cambia el consumo, el total se actualiza automáticamente. 
4- El total mostrado coincide con los productos registrados. 
5- La información se muestra clara y legible en PC y tablet.
6- Se accede dentro del máximo de 3 pantallas y responde en menos de 3 segundos.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Solo necesita una mesa de prueba con productos cargados.  |
| **Negociable** | Sí | El formato de presentación (pantalla de detalle) es negociable.  |
| **Valiosa** | Sí | Permite conocer el consumo y el importe que debe pagar el cliente.  |
| **Estimable** | Sí | Se conocen los datos a mostrar y la operación de cálculo.  |
| **Pequeña** | Sí | Una pantalla de detalle.   |
| **Verificable** | Sí | Se comparan los productos registrados con el total mostrado.  |

---

# HU - 8 — Registrar pagos

**Como** encargada,  
**quiero** registrar el pago seleccionando efectivo, tarjeta o código QR,   
**para** confirmar el cobro del consumo y dejar registrada la venta. 

**Módulo:** Registrar pagos

**Requisitos relacionados:** RF-12; RF-13; RF-14; RF-15 y RF-21  

**Requisitos no funcionales:** RNF-08; RNF-16 y RNF-18 

### Criterios de aceptación

1- La encargada selecciona la mesa con consumo y visualiza el monto final exacto a cobrar.
2- El sistema ofrece los medios habilitados: Efectivo, Tarjeta o Código QR.
3- Al confirmar el pago, el sistema registra la venta asociada a la mesa, fecha, hora y usuario.
4- El sistema cuenta con validación de concurrencia para evitar cobros dobles ante clics múltiples.
5- La mesa queda en estado "Pendiente de cierre" quedando disponible para realizar el cierre de la mesa. 

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede probarse con una mesa que tenga un consumo pendiente de cobro.  |
| **Negociable** | Sí | Puede cambiar la forma de seleccionar el medio de pago, manteniendo las opciones habilitadas. |
| **Valiosa** | Sí | Permite registrar correctamente el cobro y confirmar la venta.  |
| **Estimable** | Sí | Están definidos los medios de pago, validaciones necesarias.  |
| **Pequeña** | Sí | Se enfoca exclusivamente en la transacción de cobro.  |
| **Verificable** | Sí | Se puede probar comprobando que el cobro coincide con lo consumido.  |

---

# HU - 9 — Emitir comprobantes

**Como** encargada, 
**quiero** generar y visualizar el comprobante de pago de una venta confirmada, 
**para** entregar al cliente una constancia del pago realizado. 

**Módulo:** Emitir comprobantes

**Requisitos relacionados:** RF-15 y RF-27

**Requisitos no funcionales:** RNF-03 y RNF-08

### Criterios de aceptación

1- El comprobante se emite una vez confirmada la venta.
2- El ticket detalla: número de mesa, fecha, hora, ítems consumidos, total y medio de pago. 
3- Permite visualizar el comprobante en pantalla y enviarlo a la impresora habilitada.
4- El comprobante generado queda guardado para consultas posteriores.
5- Se genera en menos de 3 segundos.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede probarse utilizando una venta confirmada. |
| **Negociable** | Sí | El diseño gráfico del ticket es configurable, mientras contenga los datos requeridos.  |
| **Valiosa** | Sí | Entrega al cliente una constancia del pago realizado.  |
| **Estimable** | Sí | Generación de plantilla de comprobante estándar. |
| **Pequeña** | Sí | Solo genera, muestra e imprime el ticket.  |
| **Verificable** | Sí | Muestra que los ítems del ticket coinciden exactamente con la venta cobrada.  |

---

# HU - 10 — Cerrar y liberar una mesa

**Como** encargada,  
**quiero** cerrar una mesa una vez confirmado el pago, 
**para** que vuelva a figurar como Disponible y quede lista para recibir a otros clientes.   

**Módulo:** Cerrar y liberar una mesa

**Requisitos relacionados:** RF-16; RF-17; RF-21; RF-24 y RF-25

**Requisitos no funcionales:** RNF-08; RNF-10 y RNF-16 

### Criterios de aceptación

1- Solo se puede cerrar una mesa cuando el pago está confirmado. 
2- El sistema solicita confirmación antes del cierre. 
3- Al confirmar el cierre, la mesa pasa de Pendiente de cierre a Disponible. 
4- Se registra el usuario que realizó el cierre, junto con la fecha y hora. 
5- La venta y el comprobante permanecen almacenados.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede probarse con una mesa que haya completado correctamente el proceso de pago.  |
| **Negociable** | Sí | Puede cambiar la forma de confirmar el cierre manteniendo sus condiciones.  |
| **Valiosa** | Sí | Completa el ciclo de atención y libera la mesa para un nuevo cliente.  |
| **Estimable** | Sí | Están definidos el requisito de pago, la confirmación y el cambio de estado. |
| **Pequeña** | Sí | Se concentra únicamente en cerrar y liberar la mesa.  |
| **Verificable** | Sí | Intentar cerrar sin pagar (bloquea) y cerrar una mesa pagada (queda Disponible).  |

---

# HU - 11 — Consultar historial de ventas

**Como** dueño, encargada o contable,
**quiero** consultar las ventas confirmadas por período o por mesa, 
**para** revisar operaciones pasadas y controlar la actividad.  

**Módulo:** Consultar historial de ventas

**Requisitos relacionados:** RF-18; RF-19; RF-28 y RF-29

**Requisitos no funcionales:** RNF-03 y RNF-08 

### Criterios de aceptación

1- Lista únicamente operaciones de ventas efectivamente confirmadas y concluidas.  
2- Cada fila muestra: fecha, hora, mesa (1 a 24), monto total cobrado y medio de pago utilizado.
3- Permite filtrar por rango de fechas (desde/hasta) y por número de mesas.
4- Si no existen operaciones para el filtro seleccionado, informa "No se encontraron operaciones registradas".
5- La consulta no modifica los datos históricos 
6- La consulta responde en menos de 3 segundos.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede probarse con ventas históricas de prueba.   |
| **Negociable** | Sí | Puede cambiar la forma de presentar y filtrar los datos.  |
| **Valiosa** | Sí | Asegura el control administrativo y permite aclarar diferencias en una cuenta. |
| **Estimable** | Sí | Se conocen los filtros y datos que deben mostrarse.  |
| **Pequeña** | Sí | Se limita a la consulta del historial, sin incluir reportes complejos.  |
| **Verificable** | Sí | Se consultan distintos períodos y mesas, y se comparan los resultados con las ventas almacenadas.  |

---

# HU - 12 — Consultar resumen de ventas

**Como** dueño o contable,  
**quiero** consultar el resumen de las ventas por período con totales por medio de pago,   
**para** conocer el rendimiento comercial sin revisar cada venta individual. 

**Módulo:** Consultar resumen de ventas

**Requisitos relacionados:** RF-19 y RF-20

**Requisitos no funcionales:** RNF-03; RNF-08 y RNF-12

### Criterios de aceptación

1. Permite seleccionar por período (rango personalizado).
2. Presenta indicadores consolidados: total general recaudado y cantidad de ventas cerradas.
3- Muestra el total según el medio de pago. 
4- La información coincide con las ventas almacenadas. 
5- Si no hubo ventas en el rango, se reflejan valores en $0 e indica "Sin movimientos registrados".
6- La información se muestra clara y legible en (PC/ tablet) y responde en menos de 3 segundos.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede probarse utilizando información histórica de ventas y consumos.  |
| **Negociable** | Sí | Puede modificarse la forma de presentar el resumen.   |
| **Valiosa** | Sí | Es la herramienta con la que el dueño conoce el desempeño del negocio con información resumida.   |
| **Estimable** | Sí | El período y los datos del resumen están definidos.  |
| **Pequeña** | Sí | Se limita al resumen de ventas, sin incluir informes adicionales. |
| **Verificable** | Sí | Se comparan los totales del resumen con las ventas registradas. |

---

# HU - 13 — Auditoría y Trazabilidad

**Como** dueño o administrador del sistema,  
**quiero** que las operaciones relevantes registren quién las realizó, la fecha y la hora, 
**para** auditar la operativa del bar y detectar errores o diferencias. 

**Módulo:** Auditoría y Trazabilidad

**Requisitos relacionados:** RF-21 y RF-24

**Requisitos no funcionales:** RNF-10 y RNF-22

### Criterios de aceptación

1- El sistema registra automáticamente las operaciones relevantes, como aperturas, cierres, cobros y modificaciones de pedidos. 
2- El dueño o administrador puede consultar los registros de trazabilidad.
3- Cada entrada documenta: fecha, hora exacta, usuario responsable, acción realizada y mesa asociada.
4 -Los datos de trazabilidad no pueden modificarse desde la interfaz.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede probarse realizando operaciones de prueba y consultando sus registros.  |
| **Negociable** | Sí | Puede cambiar la forma de consultar la trazabilidad, manteniendo los datos obligatorios.  |
| **Valiosa** | Sí | Permite identificar al responsable de cada operación y cuándo ocurrió, y delimita la responsabilidad entre turnos.   |
| **Estimable** | Sí | Los datos obligatorios y las operaciones a registrar están definidos.  |
| **Pequeña** | Sí | Se limita al registro y consulta de trazabilidad.  |
| **Verificable** | Sí | Se realiza una operación y se comprueba que usuario, fecha y hora queden registrados. |

---

# HU - 14 — Gestionar productos

**Como** encargada,  
**quiero**  administrar el catálogo de productos (altas, modificaciones de precio y desactivación), 
**para** asegurar que la oferta del bar esté actualizada y los consumos se cobren a valores vigentes. 

**Módulo:** Gestionar productos

**Requisitos relacionados:** RF-30

**Requisitos no funcionales:** RNF-06 y RNF-08

### Criterios de aceptación

 1- Permite registrar nuevos productos ingresando nombre, categoría y precio unitario de venta.
 2- Permite actualizar el precio de un producto; el nuevo valor aplica únicamente a futuras comandas, sin alterar ventas históricas.
 3- Permite desactivar productos que ya no se ofrecen, para que no figuren al tomar pedidos.  
 4- La baja de un producto no elimina su información histórica. 
 5- La edición de precios requiere perfil con permisos autorizados 

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Se gestiona sin necesidad de mesas ni pedidos.   |
| **Negociable** | Sí | Puede cambiar la forma de alta, modificación o baja, manteniendo las reglas de negocio.   |
| **Valiosa** | Sí | Permite adaptar los precios y actualizar la carta.  |
| **Estimable** | Sí | Las operaciones sobre productos y sus restricciones están definidas. |
| **Pequeña** | Sí | Se concentra en administrar el catálogo y sus precios. |
| **Verificable** | Sí | Cambiar un precio y comprobar que las ventas anteriores conservan el precio cobrado.  |

---

# HU - 15 — Respaldo y Recuperación de datos 

**Como** administrador del sistema, 
**quiero** contar con copias de seguridad automáticas diarias y un procedimiento de restauración, 
**para** garantizar la continuidad operativa y salvaguardar los datos ante fallas o actualizaciones. 

**Módulo:** Respaldo y Recuperación de datos 

**Requisitos no funcionales:** RNF-09; RNF-14; RNF-15 y RNF-21

### Criterios de aceptación

1- El sistema ejecuta al menos un respaldo completo automatizado de la base de datos por cada jornada operativa.
2- El administrador puede verificar fecha, tamaño y estado del último respaldo exitoso generado.
3- El procedimiento de restauración permite recuperar el estado de los datos al último backup sin afectar mesas, pedidos ni cobros.
4- El mantenimiento se programa fuera del horario operativo, de modo que el sistema esté disponible el 100 % de ese horario.
5- Las actualizaciones del sistema preservan los datos transaccionales históricos.

### INVEST

| Criterio | ¿Se cumple? | Observación |
|---|---|---|
| **Independiente** | Sí | Puede verificarse mediante un respaldo y una restauración de prueba, sin necesidad de ejecutar las operaciones de atención, cobro o cierre de mesas.  |
| **Negociable** | Sí | El horario de ejecución y backup son configurables.   |
| **Valiosa** | Sí | Evita perder las ventas del día ante una falla y asegura la continuidad del servicio.   |
| **Estimable** | Sí | El respaldo, restauración y prueba de actualización son tareas de infraestructura conocidas.  |
| **Pequeña** | Sí | Entra en una iteración, aunque reúne respaldo, restauración y mantenimiento. |
| **Verificable** | Sí | Se realiza un respaldo, se restaura en un entorno de prueba y se comparan los datos y totales de ventas antes y después.  |




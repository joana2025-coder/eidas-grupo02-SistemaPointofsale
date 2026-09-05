# Requisitos del sistema

## Descripción del sistema

El Sistema POS (Point of Sale) es una solución informática destinada a gestionar de manera integral las operaciones del bar ubicado dentro del supermercado Carrefour, que cuenta con 24 mesas para la atención de clientes.

Su objetivo principal es digitalizar y centralizar el proceso de atención y venta, permitiendo al personal gestionar en un único sistema el estado de las mesas, los pedidos, los consumos, los pagos y las ventas realizadas.

El sistema permitirá visualizar en tiempo real las 24 mesas, identificando cuáles se encuentran libres u ocupadas. Al iniciar una atención, el personal podrá asociar una mesa con los pedidos realizados por los clientes, agregar o modificar productos y consultar el consumo acumulado.

El sistema calculará automáticamente el total de la cuenta, reduciendo errores y agilizando la atención. Una vez finalizado el consumo, se podrá registrar el medio de pago —efectivo, tarjeta o código QR—, emitir el comprobante correspondiente y cerrar la operación.

Luego del pago, la mesa volverá a estar disponible para una nueva atención.

El sistema también conservará un historial de las operaciones realizadas, permitiendo consultar ventas y consumos anteriores y facilitando el control administrativo del establecimiento.

El acceso estará protegido mediante autenticación y roles de usuario, de manera que cada integrante del personal pueda utilizar únicamente las funcionalidades correspondientes a sus permisos.

En síntesis, el POS permitirá transformar la gestión manual del bar en un proceso digital, centralizado, rápido y trazable, mejorando la organización del personal, reduciendo errores y optimizando la experiencia de atención al cliente.

### Flujo principal del sistema

**Mesa → Pedido → Consumo → Cálculo del total → Pago → Comprobante → Cierre → Mesa disponible**

## Descripción del sistema y contexto real

El establecimiento cuenta con 24 mesas destinadas a la atención de clientes y trabaja con dos turnos diarios:

- **Turno mañana:** 1 moza y 1 encargada.
- **Turno tarde:** 1 moza y 1 encargada.

La atención comienza cuando la moza recibe al cliente y toma su pedido. Luego, transmite la información a la encargada, quien se encarga de registrar el pedido en el sistema POS y asociarlo a la mesa correspondiente.

El sistema permite visualizar las mesas y conocer su estado, registrar los productos consumidos, calcular automáticamente el importe total, registrar diferentes medios de pago, emitir tickets y mantener un historial de las ventas realizadas.

El proceso finaliza cuando se registra el pago correspondiente al consumo y se libera la mesa, dejándola disponible para una nueva atención.

El sistema POS tiene como finalidad centralizar y organizar la información relacionada con mesas, pedidos, productos, consumos y pagos, reduciendo errores de registración, agilizando la atención y facilitando el control de las operaciones realizadas durante cada turno.

## Objetivos específicos

- Gestionar el estado de las 24 mesas del establecimiento.
- Registrar y consultar los pedidos asociados a cada mesa.
- Mantener actualizado el consumo de cada cliente.
- Calcular automáticamente los importes correspondientes.
- Registrar los pagos realizados mediante los medios habilitados.
- Emitir tickets correspondientes a las operaciones finalizadas.
- Mantener un historial de ventas y consumos.
- Facilitar la tarea de las encargadas durante la atención.
- Mejorar la organización de la información generada durante cada turno.
- Permitir al responsable del negocio consultar información relacionada con las ventas.
- Garantizar el acceso a las funcionalidades según el rol de cada usuario.


## Requisitos funcionales

Los requisitos funcionales indican qué debe hacer el sistema.

### Módulo 1. Autenticación y gestión de usuarios

**RF-01. Inicio de sesión:** El sistema deberá permitir a los usuarios iniciar sesión mediante usuario y contraseña.

**RF-02. Gestión de usuarios y roles:** El sistema deberá permitir gestionar los usuarios registrados y asignarles un rol de acceso.

**RF-22. Control de acceso:** El sistema deberá controlar el acceso a las funcionalidades de acuerdo con el rol del usuario.

**RF-24. Identificación del usuario:** El sistema deberá registrar qué usuario realizó las operaciones relevantes sobre pedidos, pagos, ventas y mesas.

### Módulo 2. Gestión de mesas

**RF-03. Visualización de mesas:** El sistema deberá mostrar un tablero con las 24 mesas del bar y permitir identificar visualmente cada una.

**RF-04. Estado de las mesas:** El sistema deberá mostrar el estado actual de cada mesa, utilizando como mínimo los estados "Disponible", "Ocupada" y "Pendiente de cierre".

**RF-05. Apertura de mesa:** El sistema deberá permitir abrir una mesa que se encuentre disponible.

**RF-16. Cierre de mesa:** El sistema deberá permitir cerrar una mesa una vez registrada la venta y confirmado el pago.

**RF-17. Actualización del estado de la mesa:** El sistema deberá cambiar automáticamente el estado de una mesa a "Disponible" luego de su cierre.

**RF-23. Actualización en tiempo real del estado:** El sistema deberá actualizar en tiempo real el estado de las 24 mesas cuando se produzca una apertura, cierre o cambio de estado.

### Módulo 3. Gestión de pedidos y consumo

**RF-06. Asociación de pedidos:** El sistema deberá permitir asociar un pedido a una mesa abierta.

**RF-07. Registro de productos:** El sistema deberá permitir agregar productos al pedido de una mesa.

**RF-08. Modificación de cantidades:** El sistema deberá permitir modificar la cantidad de productos solicitados antes del cierre de la mesa.

**RF-09. Eliminación de productos:** El sistema deberá permitir eliminar productos de un pedido antes de su confirmación o cierre.

**RF-10. Cálculo del consumo:** El sistema deberá calcular automáticamente el importe correspondiente a los productos consumidos.

**RF-11. Consulta de consumo:** El sistema deberá permitir consultar el detalle del consumo asociado a una mesa.

**RF-25. Confirmación de operaciones:** El sistema deberá solicitar confirmación antes de realizar operaciones que puedan modificar o eliminar información relevante.

**RF-26. Actualización de pedidos:** El sistema deberá actualizar automáticamente el total del pedido cuando se agreguen, modifiquen o eliminen productos.

### Módulo 4. Pagos y comprobantes

**RF-12. Registro del pago:** El sistema deberá permitir registrar el pago correspondiente al consumo de una mesa.

**RF-13. Selección del medio de pago:** El sistema deberá permitir seleccionar el medio de pago utilizado, como efectivo, tarjeta o código QR.

**RF-14. Cálculo del importe final:** El sistema deberá calcular y mostrar el importe final a pagar.

**RF-15. Confirmación de la venta:** El sistema deberá registrar y confirmar la venta una vez efectuado y validado el pago.

**RF-27. Emisión de comprobante:** El sistema deberá permitir emitir o visualizar un comprobante correspondiente a la venta realizada.

### Módulo 5. Ventas e historial

**RF-18. Historial de ventas:** El sistema deberá conservar las ventas confirmadas para permitir su consulta posterior.

**RF-19. Consulta de ventas:** El sistema deberá permitir consultar las ventas realizadas dentro de un período determinado.

**RF-20. Información resumida de ventas:** El sistema deberá permitir obtener información resumida de las ventas realizadas.

**RF-28. Consulta del historial:** El sistema deberá permitir consultar las ventas históricas almacenadas, incluyendo información como fecha, hora, mesa, importe y medio de pago.

**RF-29. Consulta por mesa:** El sistema deberá permitir consultar las ventas y consumos asociados a una mesa determinada.

### Módulo 6. Trazabilidad de operaciones

**RF-21. Registro de fecha y hora:** El sistema deberá registrar la fecha y hora de las operaciones relevantes realizadas en el sistema.

### Módulo 7. Gestión de productos

**RF-30. Gestión de productos:** El sistema deberá permitir administrar la información de los productos ofrecidos por el bar, según los permisos del usuario.

---

## Requisitos no funcionales

Los requisitos no funcionales establecen las características y condiciones de calidad que deberá cumplir el sistema.

### Usabilidad y eficiencia

**RNF-01. Usabilidad:** El sistema deberá permitir realizar las operaciones frecuentes de apertura de mesa, registro de pedido y consulta de consumo utilizando un máximo de **3 pantallas**, sin contar la pantalla de inicio de sesión.

**RNF-02. Eficiencia operativa:** El registro de un pedido de hasta **5 productos** deberá poder completarse en un máximo de **5 pasos de interacción**, sin considerar el ingreso de datos propios del pedido.

**RNF-03. Tiempo de respuesta:** El sistema deberá responder a las operaciones habituales en un tiempo máximo de **3 segundos** bajo condiciones normales de operación.

### Acceso y seguridad

**RNF-04. Acceso simultáneo:** El sistema deberá permitir el acceso simultáneo de al menos **2 usuarios autorizados del personal operativo**, manteniendo la consistencia de la información de mesas, pedidos, pagos y ventas.

**RNF-05. Autenticación:** El sistema deberá requerir autenticación mediante usuario y contraseña antes de permitir el acceso a las funcionalidades restringidas.

**RNF-06. Autorización:** El sistema deberá controlar los permisos de acuerdo con el rol asignado a cada usuario.

**RNF-07. Seguridad de contraseñas:** Las contraseñas de los usuarios deberán almacenarse mediante un mecanismo de hash seguro y no deberán conservarse en texto plano.

**RNF-08. Integridad de datos:** El sistema deberá garantizar la integridad de la información relacionada con pedidos, ventas, pagos, usuarios y mesas.

**RNF-09. Respaldo:** El sistema deberá realizar al menos **un respaldo de la información por cada jornada de trabajo**.

**RNF-10. Trazabilidad:** El sistema deberá mantener la trazabilidad de las operaciones relevantes realizadas por los usuarios, registrando como mínimo el usuario, la fecha y la hora de la operación.

### Compatibilidad y presentación

**RNF-11. Compatibilidad:** El sistema deberá ser compatible con los dispositivos utilizados por el personal del bar, incluyendo computadoras y tablets.

**RNF-12. Legibilidad:** La información deberá visualizarse de manera clara, ordenada y legible, sin pérdida de información en los dispositivos compatibles.

**RNF-20. Interfaz adaptable:** La interfaz deberá adaptarse correctamente a los diferentes tamaños de pantalla de computadoras y tablets, manteniendo visibles las funciones principales sin desplazamiento horizontal.

### Recuperación y disponibilidad

**RNF-13. Recuperación ante errores:** Ante un error durante una operación, el sistema no deberá confirmar ni registrar parcialmente una transacción, evitando la pérdida o duplicación de información.

**RNF-14. Disponibilidad:** El sistema deberá estar disponible durante el **100 % del horario operativo planificado**, exceptuando los períodos de mantenimiento previamente programados.

**RNF-15. Mantenimiento:** Las tareas de mantenimiento y actualización deberán poder realizarse sin modificar ni eliminar los datos históricos de pedidos, pagos y ventas.

**RNF-16. Consistencia:** Cuando se confirme el pago de una mesa, el sistema deberá actualizar de forma consistente el estado de la mesa, la venta y el registro del pago.

**RNF-17. Escalabilidad:** La estructura del sistema deberá permitir incorporar nuevas funcionalidades sin modificar los datos históricos existentes ni afectar las funcionalidades actuales.

**RNF-18. Confiabilidad:** Las operaciones de registro de pedidos, pagos y ventas deberán completarse correctamente, evitando la generación de registros duplicados ante una única confirmación de la operación.

### Gestión de sesiones y recuperación de información

**RNF-19. Control de sesiones:** El sistema deberá cerrar automáticamente la sesión de un usuario después de **15 minutos de inactividad**, requiriendo nuevamente la autenticación para acceder a las funcionalidades restringidas.

**RNF-21. Recuperación de información:** Ante un fallo del sistema, deberá ser posible recuperar la información almacenada a partir del respaldo correspondiente a la última jornada de trabajo.

**RNF-22. Auditabilidad:** Las operaciones críticas deberán poder ser identificadas mediante el usuario, la fecha y la hora en que fueron realizadas.

### Seguridad de la transmisión

**RNF-23. Transmisión segura:** El sistema deberá utilizar **HTTPS mediante TLS** para proteger la transmisión de credenciales, información de pedidos, ventas y pagos entre los dispositivos de los usuarios y el servidor.

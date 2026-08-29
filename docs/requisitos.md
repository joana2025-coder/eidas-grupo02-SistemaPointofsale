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

**RF-01. Inicio de sesión:** El sistema deberá permitir a los usuarios iniciar sesión mediante usuario y contraseña.

**RF-02. Gestión de usuarios y roles:** El sistema deberá permitir gestionar los usuarios registrados y asignarles un rol de acceso.

**RF-03. Visualización de mesas:** El sistema deberá mostrar las 24 mesas disponibles del bar.

**RF-04. Estado de las mesas:** El sistema deberá mostrar el estado actual de cada mesa, por ejemplo: disponible, ocupada o pendiente de cierre.

**RF-05. Apertura de mesa:** El sistema deberá permitir abrir una mesa que se encuentre disponible.

**RF-06. Asociación de pedidos:** El sistema deberá permitir asociar un pedido a una mesa abierta.

**RF-07. Registro de productos:** El sistema deberá permitir agregar productos al pedido de una mesa.

**RF-08. Modificación de cantidades:** El sistema deberá permitir modificar la cantidad de productos solicitados antes del cierre de la mesa.

**RF-09. Eliminación de productos:** El sistema deberá permitir eliminar productos de un pedido antes de su confirmación o cierre.

**RF-10. Cálculo del consumo:** El sistema deberá calcular automáticamente el importe correspondiente a los productos consumidos.

**RF-11. Consulta de consumo:** El sistema deberá permitir consultar el detalle del consumo asociado a una mesa.

**RF-12. Registro del pago:** El sistema deberá permitir registrar el pago correspondiente al consumo de una mesa.

**RF-13. Selección del medio de pago:** El sistema deberá permitir seleccionar el medio de pago utilizado, como efectivo, tarjeta o código QR.

**RF-14. Cálculo del importe final:** El sistema deberá calcular y mostrar el importe final a pagar.

**RF-15. Registro de venta:** El sistema deberá registrar la venta una vez efectuado y confirmado el pago.

**RF-16. Cierre de mesa:** El sistema deberá permitir cerrar una mesa una vez registrada la venta y confirmado el pago.

**RF-17. Actualización del estado de la mesa:** El sistema deberá cambiar automáticamente el estado de una mesa a "Disponible" luego de su cierre.

**RF-18. Registro de ventas:** El sistema deberá mantener un registro de las ventas realizadas.

**RF-19. Consulta de ventas:** El sistema deberá permitir consultar las ventas realizadas.

**RF-20. Información resumida de ventas:** El sistema deberá permitir obtener información resumida de las ventas realizadas.

**RF-21. Registro de fecha y hora:** El sistema deberá registrar la fecha y hora de las operaciones relevantes realizadas en el sistema.

**RF-22. Control de acceso:** El sistema deberá controlar el acceso a las funcionalidades de acuerdo con el rol del usuario.

**RF-23. Consulta del estado de las mesas:** El sistema deberá permitir consultar en tiempo real el estado de las 24 mesas.

**RF-24. Identificación del usuario:** El sistema deberá registrar qué usuario realizó las operaciones relevantes sobre pedidos, pagos, ventas y mesas.

**RF-25. Confirmación de operaciones:** El sistema deberá solicitar confirmación antes de realizar operaciones que puedan modificar o eliminar información relevante.

**RF-26. Actualización de pedidos:** El sistema deberá actualizar el total del pedido automáticamente cuando se agreguen, modifiquen o eliminen productos.

**RF-27. Emisión de comprobante:** El sistema deberá permitir emitir o visualizar un comprobante correspondiente a la venta realizada.

**RF-28. Consulta del historial:** El sistema deberá permitir consultar el historial de ventas registradas.

**RF-29. Consulta por mesa:** El sistema deberá permitir consultar las ventas y consumos asociados a una mesa determinada.

**RF-30. Gestión de productos:** El sistema deberá permitir administrar la información de los productos ofrecidos por el bar, según los permisos del usuario.

---

## Requisitos no funcionales

Los requisitos no funcionales establecen las características y condiciones de calidad que deberá cumplir el sistema.

**RNF-01. Usabilidad:** El sistema deberá presentar una interfaz clara, intuitiva y fácil de utilizar.

**RNF-02. Eficiencia operativa:** Las operaciones frecuentes deberán requerir la menor cantidad posible de pasos.

**RNF-03. Tiempo de respuesta:** El sistema deberá responder a las operaciones habituales en un tiempo máximo de 3 segundos bajo condiciones normales de operación.

**RNF-04. Acceso simultáneo:** El sistema deberá permitir el acceso simultáneo de los usuarios autorizados sin generar inconsistencias en la información.

**RNF-05. Autenticación:** El sistema deberá requerir autenticación para acceder a las funcionalidades restringidas.

**RNF-06. Autorización:** El sistema deberá controlar los permisos de acuerdo con el rol asignado a cada usuario.

**RNF-07. Seguridad de contraseñas:** Las contraseñas de los usuarios deberán almacenarse de forma segura y no deberán conservarse en texto plano.

**RNF-08. Integridad de datos:** El sistema deberá garantizar la integridad de la información relacionada con pedidos, ventas, pagos, usuarios y mesas.

**RNF-09. Respaldo:** El sistema deberá realizar respaldos periódicos de la información almacenada.

**RNF-10. Trazabilidad:** El sistema deberá mantener la trazabilidad de las operaciones relevantes realizadas por los usuarios.

**RNF-11. Compatibilidad:** El sistema deberá ser compatible con los dispositivos utilizados por el personal del bar, incluyendo computadoras y tablets.

**RNF-12. Legibilidad:** La información deberá visualizarse de manera clara, ordenada y legible.

**RNF-13. Recuperación ante errores:** El sistema deberá evitar la pérdida de información ante errores de operación o fallos durante una transacción.

**RNF-14. Disponibilidad:** El sistema deberá estar disponible durante el horario operativo del bar.

**RNF-15. Mantenimiento:** El sistema deberá permitir realizar tareas de mantenimiento y actualización sin afectar innecesariamente la información almacenada.

**RNF-16. Consistencia:** El sistema deberá mantener actualizada y consistente la información sobre el estado de las mesas, pedidos, pagos y ventas.

**RNF-17. Escalabilidad:** El sistema deberá permitir futuras ampliaciones de funcionalidades sin requerir modificaciones completas de la estructura existente.

**RNF-18. Confiabilidad:** El sistema deberá procesar correctamente las operaciones de pedidos, pagos y ventas, minimizando la posibilidad de errores.

**RNF-19. Control de sesiones:** El sistema deberá gestionar las sesiones de los usuarios de forma segura y evitar el acceso no autorizado a una sesión activa.

**RNF-20. Interfaz adaptable:** La interfaz deberá adaptarse correctamente a los diferentes tamaños de pantalla de los dispositivos compatibles.

**RNF-21. Recuperación de información:** Ante un fallo del sistema, deberá ser posible recuperar la información almacenada a partir de los respaldos disponibles.

**RNF-22. Auditabilidad:** Las operaciones críticas deberán poder ser identificadas mediante el usuario, fecha y hora en que fueron realizadas.

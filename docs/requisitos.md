# Requisitos del sistema

## Descripción del sistema

El sistema Point of Sale (POS) está destinado a gestionar las operaciones del bar ubicado dentro de Carrefour. Permite a las encargadas administrar las 24 mesas, registrar los pedidos asociados a cada mesa, gestionar los pagos y consultar el historial de ventas y consumos. El sistema busca agilizar la atención, facilitar la gestión de las mesas y reducir errores en el registro y cobro de los pedidos.

# Requisitos del sistema

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

# Definition of Ready (DoR)

_Antes de que una historia entre a desarrollo, tiene que pasar un filtro: el Definition of
Ready. Es un acuerdo del equipo sobre qué condiciones mínimas debe cumplir una historia para
considerarse "lista para trabajar". Si no las cumple, vuelve a refinamiento._

---

## Checklist del equipo

_Entre 6 y 10 ítems. Cada uno redactado como una condición verificable ("la historia tiene
criterios de aceptación escritos"), no como un deseo ("la historia está bien definida")._

| # | Ítem | Justificación (qué problema evita, máx. 3 renglones) |
|---|------|--------------------------------------------------------|
| 1 | La historia está redactada en formato "Como [rol], quiero [acción], para [objetivo]", con un único actor y un único objetivo | Evita historias que mezclan varios roles o varios objetivos, las cuales resultan difíciles de estimar, desarrollar y dar por terminadas |
| 2 | La historia tiene criterios de aceptación verificables que cubren el camino principal y al menos una excepción | Sin esto, el estado de "terminado" queda a criterio subjetivo de cada persona y el equipo de testing no tiene una base clara contra qué comparar |
| 3 | Las reglas de negocio con valores concretos (montos, estados válidos, tiempos, límites) están explicitadas y no se infieren| Evita interpretaciones divergentes y malentendidos sobre el comportamiento del sistema entre analistas, desarrolladores y testers |
| 4 | Las dependencias de la historia (otras historias, módulos o servicios externos) están identificadas y ya están disponibles o planificadas antes en el backlog | Evita que el equipo comience a trabajar en una historia que quedará bloqueada a mitad de camino por falta de componentes requeridos |
| 5 | La historia fue validada contra los criterios INVEST y no quedan observaciones "No" o "Parcial" sin resolver | Evita arrastrar historias que no son independientes o que son demasiado grandes, lo cual complica la estimación y planificación del sprint |
| 6 | El equipo tiene una estimación de esfuerzo (story points) consensuada, no propuesta por una sola persona | Evita comprometer historias en el sprint sin un acuerdo real y de mutua conformidad del equipo de desarrollo sobre el esfuerzo que implican |
| 7 | Se conoce qué rol puede ejecutar la acción y qué debe pasar si un usuario sin permiso la intenta | Evita descubrir en pleno desarrollo que falta definir la matriz de permisos y el comportamiento de seguridad de la interfaz |
| 8 | La historia no depende de una decisión de negocio todavía pendiente (un valor, un límite o una política que el dueño del producto no definió) | Evita que cualquier desarrollo realizado antes de que se formalice la política comercial se convierta en pérdida de tiempo y en costoso retrabajo |

---

## Aplicación a tres historias propias

_Elijan TRES historias de usuario de su propio trabajo del primer semestre y pásenlas por su
propia checklist. Es esperable —y deseable— que alguna no pase._

### Historia 1 — [  H-U 1 / Inicio de sesión ]

| Ítem (según checklist) | ¿Pasa? | Qué le falta (si no pasa) |
|-------------------------|--------|-----------------------------|
| 1 | SÍ | - |
| 2 | SÍ | Cuenta con 5 criterios que cubren el caso feliz, las credenciales inválidas y el cierre de sesión |
| 3 | NO | No define cuánto tiempo dura la sesión activa antes de expirar. El propio INVEST la clasifica como negociable, pero para programar el criterio 5 (cierre automático) hace falta un valor concreto (ej.: 30 minutos de inactividad) |
| 4 | SÍ | No posee dependencias de otras historias del backlog; representa la base de seguridad del sistema |
| 5 | SÍ | Todos los criterios de la validación INVEST están marcados de forma conforme con "Sí" |
| 6 | SÍ | Se encuentra estimada por el equipo técnico en un valor consensuado de 3 puntos de historia |
| 7 | SÍ | El criterio de aceptación 4 determina explícitamente que el sistema debe identificar el rol del usuario al ingresar |
| 8 | SÍ | No depende de ninguna decisión de negocio ni política comercial pendiente de aprobación |
---

### Historia 2 — [ H-U 6 / Agregar productos al pedido ]

| Ítem (según checklist) | ¿Pasa? | Qué le falta (si no pasa) |
|-------------------------|--------|-----------------------------|
| 1 | SÍ | - |
| 2 | SÍ | Cubre correctamente la selección de la mesa, el catálogo de productos disponibles, las cantidades, el precio vigente y el recálculo automático del total |
| 3 | SÍ | Los valores críticos están explícitos: la cantidad solicitada debe ser obligatoriamente mayor a cero y el precio aplicado debe ser el vigente al momento de la carga |
| 4 | NO | Depende directamente del módulo de Gestión de productos (H-U 16), el cual se ubica de forma posterior en el backlog. Sin ese módulo programado, no existe una base real de productos disponibles para cargar ni testear esta funcionalidad |
| 5 | SÍ | Validación INVEST completada y aprobada sin observaciones negativas |
| 6 | SÍ | Es estimable; la lógica de mapeo de productos y de actualización del acumulado es acotada y conocida por el equipo |
| 7 | SÍ | El rol ejecutor está explícitamente definido para las mozas en el salón |
| 8 | SÍ | No cuenta con decisiones comerciales de negocio pendientes de definición |
---

### Historia 3 — [ H-U 10 / Registro de pago ]

| Ítem (según checklist) | ¿Pasa? | Qué le falta (si no pasa) |
|-------------------------|--------|-----------------------------|
| 1 | SÍ | - |
| 2 | SÍ | Cubre de manera verificable la selección del medio de pago, la validación del medio obligatorio y la posterior generación de la venta histórica |
| 3 | NO | No define cómo se calcula ni se registra el vuelto cuando el cliente abona con un monto de efectivo superior al total acumulado de la comanda |
| 4 | SÍ | No depende de historias ajenas que no se encuentren resueltas (requiere de forma elemental que la mesa tenga consumos previos cargados, lo cual ya está contemplado en el sistema) |
| 5 | SÍ | Validación INVEST completada con éxito y sin observaciones negativas |
| 6 | SÍ | Al estar definidos los medios de pago principales y el comportamiento esperado del flujo, la historia es estimable técnicamente |
| 7 | SÍ | Rol ejecutor definido de forma correcta para el personal de servicio (mozas y encargadas) |
| 8 | NO | No está definida la política de pagos combinados. El dueño del bar aún no ha resuelto si el sistema debe permitir dividir la cuenta de una mesa (ej.: pagar una parte en efectivo y otra con QR) o si cada pedido debe cancelarse de forma estricta con un único medio de pago |

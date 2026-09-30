# Diseño UI

_Presentar al menos un wireframe por pantalla o módulo relevante._
_Los wireframes en imagen o PDF van en `diagramas/wireframes/`; acá se documenta la justificación de cada uno._

---

## Pantalla / Módulo 1 — [Login - Inicio de sesion]

**Wireframe:** `diagramas/wireframes/[01-login (1).svg]`

**Patrones de diseño utilizados:** _( Formulario simple centrado en una sola columna, mensaje de error en línea (online validation), foco automático en el primer campo )_

**Justificación:** _¿ Es la puerta de entrada de RF 01 y RNF 05. Como la sesion se cierra tras 10 minutos de inactividad (RNF 19), el personal va a haber esta pantalla varias veces por turno, así que debe ser mínima: dos campos por turno, un botón y nada más. El foco automático y el envío con Enter reducen el tiempo de reingreso. El mesaje de error es genérico ( "Usuario o contraseñas incorrectos"), para no relevar cual de los dos datos falló Tras el login el sistema identifica el rol (RF-22) y muestra solo las opciones que corresponden a la moza, la encargada o el dueño._

**Formulario (si aplica):**
- Cantidad de campos: 2 (Usuario y contraseña).
- Flujo (todo en una pantalla / por pasos): Todo en una pantalla.
- Validaciones relevantes: ambos campos obligatorios; credenciales inválidas muestran error sin indicar cuál dato es incorrecto; la contraseña se oculta con opción de mostrarla (útil en tablet); al expirar la sesión por inactividad se vuelve a esta pantalla con aviso "Tu sesión se cerró por inactividad"

---

## Pantalla / Módulo 2 — [Tableros de mesas]

**Wireframe:** `diagramas/wireframes/[02-tableros-de-mesa.svg]`

**Patrones de diseño utilizados:**  Grilla de cards (una por mesa), código de estado con color + texto + ícono, leyenda fija, modal de confirmación, actualización en vivo del tablero.

**Justificación:** RF-03 pide ver las 24 mesas y RF-04 sus estados. La grilla de 6 x 4 entra completa en una tablet sin scroll, y respeta el plano mental del salón. Cada card muestra el número grande y el estado, de modo que la moza sabe de un vistazo qué mesa está libre para sentar a un cliente. Un clic en una mesa Disponible abre el modal de confirmación (RF-25) antes de cambiar el estado, para evitar aperturas accidentales con toques involuntarios en tablet. Un clic en una mesa Ocupada o Pendiente de cierre lleva directo al pedido o al cobro. Como hay dos personas usando el sistema a la vez (RNF-04), el tablero se actualiza en tiempo real (RF-23) para que ambas vean el mismo estado. Cada mesa lleva usuario, fecha y hora de la apertura (RF-21, RF-24, RNF-10).

**Formulario (si aplica):**
- Cantidad de campos: (Solo confirmación mediante modal).
- Flujo (todo en una pantalla / por pasos): Todo en una pantalla.
- Validaciones relevantes: Solo se puede abrir una mesa en estado Disponible; las mesas Ocupadas y Pendiente de cierre no ofrecen la acción "Abrir"; si otra persona cambió el estado mientras el modal estaba abierto, el sistema avisa y actualiza el tablero.

---

## Pantalla / Módulo 3 — [Pedido y consumo de la mesa]

**Wireframe:** `diagramas/wireframes/[03-pedido-mesas.svg]`

**Patrones de diseño utilizados:** Vista dividida maestro-detalle (catálogo a la izquierda, pedido a la derecha), pestañas de categorías, cards de producto de un solo toque, stepper de cantidad (-/+), total fijo siempre visible, modal de confirmación para eliminar.

**Justificación:** Esta pantalla concentra tres historias: registrar y modificar el pedido, y consultar el consumo. Al tener catálogo y pedido lado a lado, la encargada nunca cambia de pantalla para ver cómo va la cuenta, lo que cumple RNF-01 (máximo 3 pantallas para apertura, pedido y consumo). Cada toque en una card agrega 1 unidad del producto, así un pedido de 5 productos se registra en 5 interacciones (RNF-02). El stepper permite corregir cantidades sin teclado (RF-08), y el total se recalcula solo (RF-10, RF-26), lo que reduce errores de suma manual. La eliminación pide confirmación (RF-09, RF-25) porque es una operación que borra información. Las pestañas por categoría acortan la búsqueda cuando el menú crece (RF-30). La misma pantalla, sin los controles de edición, sirve para que la moza consulte el detalle y el importe que informa al cliente (RF-11, RF-14) sin modificar nada.

**Formulario (si aplica):**
- Cantidad de campos: 1 por producto agregado (cantidad); la selección del producto es por toque, no por campo de texto
- Flujo (todo en una pantalla / por pasos): Todo en una pantalla, sin pasos
- Validaciones relevantes:  cantidad entera mayor a 0; no se pueden agregar productos no disponibles; solo se puede editar un pedido de una mesa abierta (Ocupada); el precio aplicado es el vigente al momento de la carga; cada modificación registra usuario, fecha y hora (RF-24, RNF-10).

  ---

## Pantalla / Módulo 4 — [Cobro y comprobante]

**Wireframe:** `diagramas/wireframes/[04-cobro comprobante.svg]`

**Patrones de diseño utilizados:** Selector de opciones exclusivas en formato botones grandes (radio cards), resumen de solo lectura, modal de confirmación, estado de carga con botón deshabilitado, pantalla de éxito con siguiente acción clara, vista de comprobante imprimible.

**Justificación:** El cobro es el momento de mayor riesgo del sistema, as´´í que el diseño apunta a evitar errores. Se muestra el importe final antes de elegir el medio (RF-14) y los tres medios de pago (RF-13) aparecen como opciones exclusivas y grandes, sin escritura. Al confirmar, el botón se deshabilita y muestra "procesando", lo que evita el doble click y la venta duplicada (RNF-18). Si falla la conexión, la pantalla consulta si el pago ya se registro antes de permitir reintentar. Al terminar, la pantalla de éxito ofrece dos acciones en el orden del flujo: ver o imprimit el comprobante (RF-27) y cerrar la mesa (RF-16, RF-17). El botón, "cerrar la mesa" pide confirmación y solo se habilita con la mesa en pendiente de cierre. El comprobante muestra mesa, usuarui responsable, fecha, hora, detalle, importe, y medio de pago.

**Formulario (si aplica):**
- Cantidad de campos: 1 (medio de pago); el importe es solo lectura.
- Flujo (todo en una pantalla / por pasos): Todo en una pantalla, con confirmación por modal al final.
- Validaciones relevantes: Hay que elegir un medio de pago para habilitar "confirmar pago"; Solo se  cobra una mesa con consumo registrado; un único pago y una única venta con confirmación; Si el pago falla, la mesa sigue Ocupada con su pedido; el cierre solo se permite en estado Eendiente de cierre.

---

## Pantalla / Módulo 5 — [Historial de ventas]

**Wireframe:** `diagramas/wireframes/[05-Historial-ventas.svg]`

**Patrones de diseño utilizados:** Filtros en la parte superior, tarjeta de resumen, tabla con paginación, vista de detalle de solo lectura.

**Justificación:** Cubre RF-18, RF-19, RF-20, RF-28 y RF-29, que necesitan el dueño y el área administrativa para controlar el negocio. A diferencia del salón, acá el usuario está sentado y busca información, por lo que una tabla con filtros por período y por mesa es el patrón más eficiente. La tarjeta de resumen responde primero lo que el dueño más consulta (cuánto se vendió) antes de bajar al detalle. La paginación evita cargar todo el historial y ayuda a cumplir los 3 segundos de RNF-03. Es de solo lectura, en línea con RNF-08 y RNF-15, y solo es visible para los roles autorizados (RF-22).

**Formulario (si aplica):**
- Cantidad de campos: 3 filtros (fecha desde, fecha hasta, mesa).
- Flujo (todo en una pantalla / por pasos): Todo en una pantalla.
- Validaciones relevantes:  "Desde" no puede ser posterior a "Hasta"; si no hay ventas en el período se muestra "No hay ventas en el período seleccionado"; solo accesible para dueño y encargada. 



## Consideraciones de accesibilidad

_Al menos una consideración concreta, relacionada con el sistema y sus usuarios reales
(no una mención genérica de "cumple con WCAG"). Ejemplos: contraste para usuarios con
baja visión, tamaño de tap targets para uso móvil, navegación por teclado, textos
alternativos en ícono-only buttons._

EL ESTADO DE LAS MESAS NO DEPENDE SOLO DEL COLOR:Cada card del tablero muestra el estado escrito ("Disponible", "Ocupada", "Pendiente de cierre") y un ícono distinto, además del color. Así una moza con daltonismo, o con el brillo de la tablet bajo por la luz del salón, distingue las mesas sin equivocarse.
TAP TARGETS DE AL MENOS 44 X 44 PX: En el tablero, en los botones -/+ del pedido y en los medios de pago. El personal usa tablets mientras camina y con las manos ocupadas, y un toque impreciso en "Quitar" o "Confirmar pago" tiene consecuencias. Los botones destructivos van separados de los frecuentes y siempre con confirmación.
CONTRASTE DE TEXTO Y FONDO DE AL MENOS 4.5:1: En importes, totales y estados. Los totales se muestran en tamaño grande, porque la moza los lee a la distancia de una mesa con un cliente esperando.
NAVEGACIÓN POR TECLADO EN LA COMPUTADORA DE LA ENCARGADA: Orden de tabulación lógico, Enter para confirmar y Esc para cancelar los modales, y foco inicial en el botón menos riesgoso (Cancelar) al abrir una confirmación.
BOTONES QUE SON SOLO ÍCONO: (volver, quitar, imprimir) llevan texto alternativo (`aria-label`) y una etiqueta visible en tablets, para que ningún usuario tenga que adivinar su función.
INTERFAZ ADAPTABLE SIN SCROLL HORIZONTAL: En computadoras y tablets (RNF-11, RNF-20), y el resultado de cada acción se informa con un mensaje visible, no solo con un cambio de color.

-

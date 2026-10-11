# Casos de uso

---

## CU-01 — Iniciar sesión

**Actor:** Usuario del sistema (moza, encargada, dueño o administrador)

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
8. El usuario comienza a utilizar el sistema.

### Flujos alternativos

* **1a. Cancelación:** el usuario puede cancelar el inicio de sesión.
* **3a. Credenciales incorrectas:** el sistema informa que los datos ingresados no son válidos y solicita intentar nuevamente.
* **5a. Usuario inactivo:** el sistema rechaza el acceso e informa que el usuario no se encuentra habilitado.
* **Inactividad:** luego del período establecido de inactividad, el sistema cierra automáticamente la sesión.

**Requisitos funcionales relacionados:** RF-01 y RF-22.

**Requisitos no funcionales relacionados:** RNF-05, RNF-07, RNF-19 y RNF-23.

---

## CU-02 — Gestionar usuarios y roles

**Actor:** Administrador del sistema

**Objetivo:** Permitir que el administrador registre, modifique y dé de baja usuarios, y les asigne el rol que determina las
funciones a las que pueden acceder.

### Precondiciones

* La encargada debe haber iniciado sesión.
* El sistema debe estar disponible.
* Debe contar con los permisos necesarios para gestionar usuarios y roles.

### Postcondiciones

* El usuario queda creado, modificado o dado de baja, según la operación realizada.
* La operación queda registrada con usuario, fecha y hora.
* Un usuario dado de baja no puede iniciar sesión y conserva su historial operativo.

### Flujo principal

1. El administrador accede a la gestión de usuarios.
2. El sistema muestra los usuarios registrados.
3. El administrador selecciona la opción de crear un nuevo usuario.
4. El sistema solicita nombre, usuario, contraseña inicial y rol.
5. El administrador ingresa los datos y confirma.
6. El sistema valida la información ingresada.
7. El sistema valida que los datos estén completos y que el usuario no exista.
7. El sistema guarda la contraseña de forma segura (hash) y crea el usuario activo con el rol asignado.
8. El sistema informa que el usuario fue creado.

### Flujos alternativos

* **2a. Nombre de usuario ya existente:** el sistema informa que el nombre de usuario no puede repetirse y solicita ingresar otro.
* **6a. Datos inválidos:** el sistema informa el error e indica qué corregir.
* **5a. Cancelación:** la encargada puede cancelar la operación antes de confirmarla.
* Cancelación de desactivación:** si el administrador cancela la operación y no se guardan los cambios.
* Acceso no autorizado:** si un usuario sin rol de administrador intenta acceder al módulo, el sistema rechaza el
acceso.

**Requisitos funcionales relacionados:** RF-02 y RF-22.

**Requisitos no funcionales relacionados:** RNF-06 y RNF-07.

---

## CU-03 — Gestionar mesas

**Actores:**  Moza o encargada

**Objetivo:** Permitir consultar el estado de las 24 mesas para saber cuáles están disponibles.

### Precondiciones

* El usuario debe haber iniciado sesión.
* El sistema debe estar disponible.
* Debe contar con los permisos correspondientes.

### Postcondiciones

* El usuario conoce el estado actual de cada mesa.
* La operación queda registrada con usuario, fecha y hora.

### Flujo principal

1. El usuario accede al tablero de las mesas.
2. El sistema muestra las 24 mesas numeradas del 1 al 24.
3. El sistema muestra el estado de cada mesa de forma diferenciada: Disponible, Ocupada o Pendiente de cierre.
4. Cuando una mesa cambia de estado desde otro dispositivo, el sistema actualiza el tablero automáticamente.
5. El usuario identifica la mesa que necesita.

### Flujos alternativos

* **2a. Falla de conexión:** si se pierde la conexión, el sistema informa que el tablero no se está actualizando.
* **3a. Consulta simultánea:** si dos usuarios consultan a la vez, ambos ven el mismo estado actualizado, sin
inconsistencias.

**Requisitos funcionales relacionados:** RF-03, RF-04 y RF-23.

**Requisitos no funcionales relacionados:** RNF-03, RNF-04, RNF-11 y RNF-20.

---

## CU-04 — Abrir una mesa

**Actor:** Encargada

**Objetivo:** Permitir registrar	la	apertura	de	una	mesa	disponible	para	iniciar	la	atención	de	los	clientes

### Precondiciones

* La encargada debe haber iniciado sesión.
* La	mesa	debe	estar	en	estado	Disponible
* El sistema debe estar disponible.

### Postcondiciones

* La	mesa	queda	en	estado	Ocupada	y	se	refleja	en	el	tablero
* La	apertura	queda	registrada	con	usuario,	fecha	y	hora.

### Flujo principal

1. La	encargada	accede	al	tablero	de	mesas.
2. La	encargada	selecciona	una	mesa	disponible.
3. La	encargada	elige	la	opción	de	abrir	la	mesa.
4. El	sistema	verifica	que	la	mesa	esté	Disponible.
5. El	sistema	solicita	confirmación.
6. La	encargada	confirma	la	apertura.
7. El	sistema	cambia	el	estado	de	la	mesa	a	Ocupada.
8. El	sistema	actualiza	el	tablero	y	registra	la	operación

### Flujos alternativos

* **4a. Mesa no disponible:** si	la	mesa	está	Ocupada	o	Pendiente	de	cierre,	el	sistema	impide	la	apertura	e	informa	el
motivo.
* **6a. Cancelación:**la	encargada	cancela	y	la	mesa	conserva	su	estado.
* **8a. Error durante la operación:** si no es posible completar la operación, el sistema evita guardar información parcial o duplicada.

**Requisitos funcionales relacionados:** RF-05 y RF-25.

**Requisitos no funcionales relacionados:** RNF-01	y	RNF-03.

---

## CU-05 — Asociar pedidos a una mesa

**Actor:** Encargada

**Objetivo:** Permitir	crear	un	pedido	y	vincularlo	a	una	mesa	abierta	para	registrar	el	consumo	del	cliente.

### Precondiciones

* La encargada debe haber iniciado sesión.
* El sistema debe estar disponible.
* La	mesa	debe	estar	en	estado	Ocupada.

### Postcondiciones

* El	pedido	queda	vinculado	a	la	mesa	seleccionada
* El	pedido	registra	el	usuario	que	lo	asoció.

### Flujo principal

1. La	encargada	accede	al	tablero	de	mesas.
2. La	encargada	selecciona	una	mesa	ocupada.
3. La	encargada	elige	la	opción	de	crear	un	nuevo	pedido.
4. El	sistema	verifica	que	la	mesa	esté	Ocupada.
5. El	sistema	crea	el	pedido	vinculado	a	la	mesa.
6. El	sistema	registra	el	usuario	que	realizó	la	asociación.
7. El	sistema	habilita	la	carga	de	productos.

### Flujos alternativos

* **4a. Mesa no disponible para consulta:** 	si	la	mesa	está	Disponible	o	Pendiente	de	cierre,	el	sistema	rechaza	la	asociación	e	informa
el	motivo.
* **5a. Error	al	guardar:** el	sistema	no	deja	un	pedido	parcial	e	informa	el	error.

**Requisitos funcionales relacionados:** RF-06 y RF-24.

**Requisitos no funcionales relacionados:** 	RNF-01 y RNF-08.

---

## CU-06 — Agregar,	modificar	y	eliminar	productos	del	pedido

**Actor:** Encargada

**Objetivo:** Permitir	mantener	actualizado	el	consumo	de	una	mesa	agregando,	modificando	o	eliminando	productos	del
pedido.

### Precondiciones
* La	encargada	debe	haber	iniciado	sesión.
* El	pedido	debe	estar	asociado	a	una	mesa	Ocupada,	con	el	cobro	aún	no	cerrado.
* Debe	existir	un	catálogo	de	productos	vigente.
  
### Postcondiciones

* El	pedido	refleja	los	productos	y	cantidades	vigentes.
* El	total	del	pedido	queda	recalculado.
* Los	cambios	quedan	registrados	con	usuario,	fecha	y	hora.

### Flujo principal

1. La	encargada	selecciona	el	pedido	de	la	mesa.
2. El	sistema	muestra	el	catálogo de productos	vigentes.
3. La	encargada	selecciona un producto.
4. La	encargada	indica la cantidad.
5. El	sistema	agrega el producto al pedido.
6. El	sistema	recalcula	el importe	total.
7. La	encargada	repite los pasos	3	a	6	hasta	completar	el	pedido

### Flujos alternativos

* **3a.	Modificar	cantidad:**	la	encargada	selecciona	un	producto	del	pedido	y	cambia	su	cantidad;	el	sistema
recalcula	el	total.
* **3b.	Eliminar producto:**	la	encargada	selecciona	un	producto	del	pedido	y	elige	eliminarlo;	el sistema solicita
confirmación	y,	al	confirmar,	lo	quita	y	recalcula	el	total.
* **1a.	Pedido no	editable:**	si	la	mesa	no	está	abierta	o	el cobro ya está	cerrado, el	sistema	no permite	editar	el
pedido.
* **3c.	Producto desactivado:** los	productos	desactivados no	figuran	en el	catálogo.

**Requisitos funcionales relacionados:** RF-07,	RF-08, RF-09, RF-25, RF-26.

**Requisitos no funcionales relacionados:** RNF-01,	RNF-02 y RNF-03.

---

## CU-07 — Consultar consumo y total

**Actor:** Moza	o	encargada

**Objetivo:** Permitir	consultar	el	detalle	del	consumo	de	una	mesa	y	su	total	para	comunicar	el	importe	al	cliente.

### Precondiciones

* El	usuario	debe	haber	iniciado	sesión	como	moza	o	encargada.
* La	mesa	debe	tener	un	pedido	registrado.
  
### Postcondiciones

* El	usuario	conoce	el	detalle	del	consumo	y	el	total.
* No	se	modifican	datos

### Flujo principal

1.	El	usuario	accede	al tablero	de	mesas.
2.	El	usuario	selecciona una	mesa	con	consumo.
3.	El	usuario	elige	la opción	de	ver	el	consumo.
4.	El	sistema	muestra	la lista	de	productos	con	nombre,	cantidad,	precio	unitario	y	subtotal.
5.	El	sistema	muestra	el importe	total	calculado.
6.	El	usuario	verifica	el	detalle	y	comunica	el	importe	al	cliente

### Flujos alternativos

* **4a.	Mesa	sin	consumo:** el	sistema	informa	que	la mesa	no tiene productos	cargados.
* **5a.	Consumo	modificado durante la	consulta:** el sistema	actualiza	el detalle y el	total	automáticamente

**Requisitos funcionales relacionados:** RF-10,	RF-11 y RF-26.

**Requisitos no funcionales relacionados:** RNF-01,	RNF-03 y RNF-12.

---

## CU-08 — Registrar pago

**Actor:** Encargada

**Objetivo:** Permitir	registrar	el	cobro	del	consumo	de	una	mesa	mediante	efectivo,	tarjeta	o	código	QR	y	confirmar	la
venta.

### Precondiciones

* La	encargada	debe	haber	iniciado	sesión.
* La	mesa	debe	tener	consumo	pendiente	de	cobro.

### Postcondiciones

* La	venta	queda	confirmada y registrada	con	mesa,	fecha,	hora	y	usuario.
* La	mesa	queda	en estado	Pendiente	de	cierre.
* Se	emite	el comprobante	de	pago.

### Flujo principal

1.  La	encargada	selecciona	la	mesa	con	consumo.
2.	El	sistema	muestra	el	monto	final	a	cobrar.
3.	El	sistema	ofrece	los	medios	de	pago	habilitados:	efectivo,	tarjeta	o	código	QR.
4.	La	encargada	selecciona	un	medio	de	pago.
5.	La	encargada	confirma	el	pago.
6.	El	sistema	valida	el	pago.
7.	El	sistema	confirma	la	venta	y	la	registra	con	mesa,	fecha,	hora	y	usuario.
8.	El	sistema	cambia	la	mesa	a	Pendiente	de	cierre.
9.	El	sistema	emite	el	comprobante.


### Flujos alternativos

* ** 4a. Sin	medio	de	pago:**	si	no	se	selecciona	un	medio	de	pago,	el	sistema	no	permite	continuar.
* **5a.	Clics	múltiples:** el	sistema	registra	una	sola	venta	y	evita	cobros	dobles.
* **6a.	Pago	inválido	o	rechazado:** el	sistema	no	confirma	la	venta,	informa	el	motivo	y	la	mesa	conserva	su	estado.
* **7a.	Error	al	registrar:** el	sistema	mantiene	consistentes	la	venta,	el	pago	y	el	estado	de	la	mesa,	sin	dejar
registros	parciales.

**Requisitos funcionales relacionados:** RF-12,	RF-13, RF-14,	RF-15 y RF-21.

**Requisitos no funcionales relacionados:** RNF-08,	RNF-16 y RNF-18.

---

## CU-09 — Emitir	comprobante

**Actores:** Encargada 

**Objetivo:** Permitir	generar	y	visualizar	el	comprobante	de	una	venta	confirmada	como	constancia	del	pago.

### Precondiciones

* La	venta	debe	estar	confirmada.
* El	sistema	debe	estar	disponible.

### Postcondiciones

* El	comprobante	queda	generado	y	guardado,	sin	posibilidad	de	alterarse.
* La	encargada	puede	entregarlo	al	cliente.

### Flujo principal

1.	El	sistema	genera	el	comprobante	de	la	venta	confirmada.
2.	El	comprobante	incluye	número	de	mesa,	fecha	y	hora,	ítems	consumidos,	total	y	medio	de	pago.
3.	El	sistema	muestra	el	comprobante	en	pantalla.
4.	La	encargada	envía	el	comprobante	a	la	impresora	habilitada.
5.	El	sistema	guarda	el	comprobante	para	consultas	posteriores.
6.	La	encargada	entrega	el	comprobante	al	cliente.

### Flujos alternativos

* **4a.	Impresora	no	disponible:**	el	sistema	mantiene	el	comprobante	en	pantalla	y	guardado,	y	permite	imprimirlo
luego.
* **4b.	Sin	impresión:** la	encargada	puede	optar	por	no	imprimir;	el	comprobante	queda	igualmente	guardado.
  
**Requisitos funcionales relacionados:** RF-15 y RF-27

**Requisitos no funcionales relacionados:** RNF-03 y RNF-08

---

## CU-10 — Cerrar	y	liberar	una	mesa

**Actor:** Encargada

**Objetivo:** Permitir	cerrar	una	mesa	una	vez	confirmado	el	pago	para	que	vuelva	a	estar	disponible.

### Precondiciones

* La	encargada	debe	haber	iniciado	sesión.
* La	mesa	debe	estar	en	estado	Pendiente	de	cierre,	con	el	pago	confirmado.

### Postcondiciones

* La	mesa	queda	en	estado	Disponible.
* El	cierre	queda	registrado	con	usuario,	fecha	y	hora.
* La	venta	y	el	comprobante	permanecen	almacenados.

### Flujo principal

1.	La	encargada	accede	al	tablero	de	mesas.
2.	La	encargada	selecciona	la	mesa	Pendiente	de	cierre.
3.	La	encargada	elige	la	opción	de	cerrar	la	mesa.
4.	El	sistema	verifica	que	el	pago	esté	confirmado.
5.	El	sistema	solicita	confirmación.
6.	La	encargada	confirma	el	cierre.
7.	El	sistema	cambia	la	mesa	a	Disponible.
8.	El	sistema	registra	usuario,	fecha	y	hora	del	cierre	y	actualiza	el	tablero

### Flujos alternativos

* **4a.	Pago	no	confirmado:**	el	sistema	bloquea	el	cierre	e	informa	el	motivo.
* **6a.	Cancelación:** la	encargada	cancela	y	la	mesa	queda	Pendiente	de	cierre.
* **7a.	Error	durante	el	cierre:**	el	sistema	no	deja	un	cierre	parcial	y	mantiene	consistentes	la	mesa,	la	venta	y	el
pago.

**Requisitos funcionales relacionados:** RF-16,	RF-17, RF-21, RF-24 y RF-25.

**Requisitos no funcionales relacionados:** RNF-08,	RNF-10  y RNF-16.

---

## CU-11 — 	Consultar	historial	de	ventas

**Actor:** Dueño,	encargada	o	contable

**Objetivo:** Permitir	consultar	las	ventas	confirmadas	por	período	o	por	mesa	para	revisar	operaciones	pasadas.

### Precondiciones

* El	usuario	debe	haber	iniciado	sesión	con	un	rol	autorizado.
* Deben	existir	ventas	registradas.
  
### Postcondiciones

* El	usuario	revisa	las	ventas	que	cumplen	el	filtro.
* No	se	modifican	datos	históricos.

### Flujo principal

1.	El	usuario	accede	al	historial	de	ventas.
2.	El	sistema	solicita	los	filtros	de	consulta.
3.	El	usuario	indica	un	rango	de	fechas	(desde/hasta)	y,	opcionalmente,	un	número	de	mesa.
4.	El	sistema	busca	las	ventas	confirmadas	que	cumplen	el	filtro.
5.	El	sistema	muestra	fecha,	hora,	mesa,	monto	total	y	medio	de	pago	de	cada	venta.
6.	El	usuario	revisa	los	resultados.

### Flujos alternativos

* **5a.	Sin	resultados:**	el	sistema	informa	«No	se	encontraron	operaciones	registradas».
* **Rol	contable:	el	contable	solo	puede	consultar;	no	puede	modificar	datos.

**Requisitos funcionales relacionados:** RF-18; RF-19; RF-28 y RF-29.

**Requisitos no funcionales relacionados:** RNF-03 y RNF-08.

---

## CU-12 — 	Consultar resumen de ventas

**Actor:** Dueño	o	contable

**Objetivo:** Permitir	consultar	el	resumen	consolidado	de	ventas	de	un	período,	con	totales	por	medio	de	pago.

### Precondiciones

* El	usuario	debe	haber	iniciado	sesión	como	dueño	o	contable.
* Deben	existir	ventas	registradas.
  
### Postcondiciones

* El	usuario	conoce	el	rendimiento	comercial	del	período.
* No	se	modifican	datos.

### Flujo principal

1.	El	usuario	accede	al	resumen	de	ventas.
2.	El	sistema	solicita	el	período	a	consultar.
3.	El	usuario	selecciona	un	rango	de	fechas.
4.	El	sistema	calcula	los	indicadores	del	período.
5.	El	sistema	muestra	el	total	vendido	y	la	cantidad	de	ventas.
6.	El	sistema	muestra	el	total	por	medio	de	pago.

### Flujos alternativos

* **4a.	Sin	ventas	en	el	período:** el	sistema	muestra	valores	en	$0	e	indica	«Sin	movimientos	registrados».
* **3a.	Rango	inválido:** si	la	fecha	de	inicio	es	posterior	a	la	de	fin,	el	sistema	solicita	corregir	el	rango

**Requisitos funcionales relacionados:** RF-19,	RF-20.

**Requisitos no funcionales relacionados:** 	RNF-03,	RNF-08	y	RNF-12.

---

## CU-13 — 	Auditoría y Trazabilidad

**Actor:** 	Dueño	o	administrador	del	sistema

**Objetivo:** Permitir	consultar	quién	realizó	cada	operación	relevante,	cuándo	y	sobre	qué	mesa,	para	auditar	la	operativa
del	bar.

### Precondiciones

* El	usuario	debe	haber	iniciado	sesión	como	dueño	o	administrador.
* Deben	existir	operaciones	registradas.
  
### Postcondiciones

* El	usuario	identifica	responsables	y	horarios	de	las	operaciones.
* Los	registros	de	trazabilidad	no	se	modifican.
* 
### Flujo principal

1.	El	usuario	accede	al	registro	de	trazabilidad.
2.	El	sistema	solicita	los	filtros	de	consulta.
3.	El	usuario	filtra	por	usuario,	fecha	y	hora.
4.	El	sistema	busca	las	operaciones	que	cumplen	el	filtro.
5.	El	sistema	muestra	fecha,	hora,	usuario	responsable,	acción	realizada	y	mesa	asociada.
6.	El	usuario	revisa	los	registros.
7.	
### Flujos alternativos

* **5a.	Sin	resultados:** el	sistema	informa	que	no	hay	operaciones	para	el	filtro.
* **6a.	Intento	de	modificación:** la	interfaz	no	permite	modificar	ni	eliminar	registros	de	trazabilidad

**Requisitos funcionales relacionados:** RF-21,	RF-24.

**Requisitos no funcionales relacionados:** RNF-10	y	RNF-22.

---

## CU-14 — 	Gestionar	productos

**Actor:** 	Encargada

**Objetivo:** Permitir	administrar	el	catálogo	de	productos	(altas,	cambios	de	precio	y	desactivación)	para	que	los	consumos
se	cobren	a	valores	vigentes.

### Precondiciones

* La	encargada	debe	haber	iniciado	sesión	con	permisos	autorizados.
* El	sistema	debe	estar	disponible.
  
### Postcondiciones

* El	catálogo	queda	actualizado.
* Los	cambios	de	precio	aplican	solo	a	futuros	pedidos;	las	ventas	históricas	no	se	alteran.
* Los	cambios	quedan	registrados	con	usuario,	fecha	y	hora.

### Flujo principal

1.	La	encargada	accede	al	catálogo	de	productos.
2.	El	sistema	muestra	los	productos	registrados.
3.	La	encargada	elige	la	opción	de	crear	un	producto.
4.	El	sistema	solicita	nombre,	categoría	y	precio	unitario.
5.	La	encargada	ingresa	los	datos	y	confirma.
6.	El	sistema	valida	los	datos	y	guarda	el	producto.
7.	El	sistema	informa	que	el	producto	fue	creado.

### Flujos alternativos

* **3a.	Modificar	precio:** la	encargada	selecciona	un	producto	y	actualiza	su	precio;	el	nuevo	valor	aplica	a	futuros
pedidos	y	no	altera	ventas	anteriores.
* **3b.	Desactivar	producto:** la	encargada	desactiva	un	producto;	deja	de	figurar	al	tomar	pedidos	y	conserva	su
información	histórica.
* **5a.	Cancelación:** la	encargada	cancela	y	no	se	guardan	cambios.
* **6a.	Datos	incompletos	o	inválidos:** el	sistema	informa	el	error	e	indica	qué	corregir

**Requisitos funcionales relacionados:** RF-30

**Requisitos no funcionales relacionados:** RNF-06 y RNF-08.

---

## CU-15 — 	Respaldo y Recuperación de datos 

**Actor:** 	Administrador	del	sistema	(el	respaldo	automático	lo	ejecuta	el	sistema)

**Objetivo:** Garantizar	copias	de	seguridad	diarias	y	permitir	restaurar	la	información	ante	fallas	o	actualizaciones.

### Precondiciones

* Para	consultar	o	restaurar,	el	administrador	debe	haber	iniciado	sesión.
* El	sistema	debe	contar	con	al	menos	un	respaldo	disponible	para	restaurar.
  
### Postcondiciones

* Existe	un	respaldo	completo	por	jornada	operativa.
* Tras	una	restauración,	los	datos	coinciden	con	el	último	respaldo,	sin	afectar	mesas,	pedidos	ni	cobros.

### Flujo principal

1.	El	sistema	ejecuta	automáticamente	un	respaldo	completo	de	la	base	de	datos	por	cada	jornada	operativa.
2.	El	sistema	guarda	el	respaldo	y	registra	fecha,	tamaño	y	estado.
3.	El	administrador	accede	al	módulo	de	respaldos.
4.	El	sistema	muestra	los	datos	del	último	respaldo	exitoso.
5.	Ante	una	falla,	el	administrador	selecciona	el	respaldo	a	restaurar.
6.	El	sistema	ejecuta	el	procedimiento	de	restauración.
7.	El	sistema	informa	que	la	información	fue	recuperada.
   
### Flujos alternativos

* **2a.	Respaldo	fallido:** el	sistema	marca	el	respaldo	con	error	para	que	el	administrador	lo	vea.
* **5a.	Sin	respaldo	disponible:**	el	sistema	informa	que	no	hay	respaldos	para	restaurar.
* **Mantenimiento	y	actualizaciones:	se	programan	fuera	del	horario	operativo	y	preservan	los	datos	históricos.
  
**Requisitos funcionales relacionados:** no	aplica;	este	caso	se	sustenta	en	requisitos	no	funcionales.

**Requisitos no funcionales relacionados:** RNF-09,	RNF-14,	RNF-15 y RNF-21.

---

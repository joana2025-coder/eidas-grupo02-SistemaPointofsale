# Requisitos del sistema

## Descripción del sistema

El sistema Point of Sale (POS) está destinado a gestionar las operaciones del bar ubicado dentro de Carrefour. Permite a las encargadas administrar las 24 mesas, registrar los pedidos asociados a cada mesa, gestionar los pagos y consultar el historial de ventas y consumos. El sistema busca agilizar la atención, facilitar la gestión de las mesas y reducir errores en el registro y cobro de los pedidos.

## Requisitos funcionales

### Módulo 1 — Acceso y gestión de mesas

| ID | Requisito |
|----|-----------|
| RF-01 | El sistema debe permitir iniciar sesión mediante usuario y contraseña. |
| RF-02 | El sistema debe mostrar las 24 mesas y su estado actual. |
| RF-03 | Las encargadas deben poder habilitar mesas ocupadas. |
| RF-04 | Las encargadas deben poder cerrar y liberar mesas. |

### Módulo 2 — Gestión de pedidos

| ID | Requisito |
|----|-----------|
| RF-05 | Las encargadas deben poder registrar pedidos asociados a una mesa. |
| RF-06 | El sistema debe permitir modificar pedidos agregando o eliminando productos. |
| RF-07 | El sistema debe calcular automáticamente el total consumido. |
| RF-08 | El sistema debe permitir consultar consumos por mesa. |

### Módulo 3 — Pagos y ventas

| ID | Requisito |
|----|-----------|
| RF-09 | El sistema debe permitir registrar pagos en efectivo, tarjeta o QR. |
| RF-10 | El sistema debe emitir tickets de compra. |
| RF-11 | El sistema debe almacenar historial de ventas y consumos. |

## Requisitos no funcionales

### Rendimiento y disponibilidad

| ID | Requisito |
|----|-----------|
| RNF-01 | El tiempo de respuesta debe ser menor a 3 segundos. |
| RNF-02 | El sistema debe mantenerse disponible durante todo el horario laboral. |
| RNF-03 | El sistema debe permitir copias de seguridad de la información. |

### Seguridad y usabilidad

| ID | Requisito |
|----|-----------|
| RNF-04 | La información debe almacenarse de forma segura. |
| RNF-05 | El sistema debe ser intuitivo y fácil de utilizar. |
| RNF-06 | El sistema debe ser compatible con computadoras y tablets. |
| RNF-07 | La interfaz debe mostrar claramente el estado de las mesas. |
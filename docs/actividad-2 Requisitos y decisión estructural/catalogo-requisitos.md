# Requisitos de MercuApp

Este catálogo traduce el problema identificado en la Actividad 1 a capacidades que podamos discutir y verificar. El alcance considerado va desde que MercuApp recibe un pedido hasta que se confirma la entrega o se registra una incidencia. Los pagos, mapas, notificaciones y ERP se tratan como sistemas externos con los que la plataforma debe integrarse.

## Requisitos funcionales

| ID | Requisito |
| :--- | :--- |
| RF-01 | MercuApp debe recibir pedidos de los canales habilitados, conservar el identificador de origen y evitar crear dos pedidos cuando el canal reintente el envío. |
| RF-02 | Antes de confirmar una compra, MercuApp debe comprobar la disponibilidad de los productos en la tienda correspondiente y reservar temporalmente las unidades durante el proceso de pago. Si el pago falla o la reserva vence, debe liberar esas unidades. |
| RF-03 | El personal autorizado debe poder asignar cada pedido listo para despacho a un repartidor disponible que opere en la zona de entrega. |
| RF-04 | El cliente debe poder consultar el estado más reciente de su pedido y, cuando exista información de ubicación, ver el avance de la entrega. |
| RF-05 | El equipo de soporte debe poder registrar incidencias, cancelaciones y cambios relevantes, asociados al pedido y con fecha. |

## Atributos de calidad

| ID | Atributo | Objetivo inicial |
| :--- | :--- | :--- |
| RNF-01 | Disponibilidad | Mantener una disponibilidad objetivo de 99,5 % durante el horario de operación. El equipo debe acordar el periodo de medición y cómo se contarán mantenimientos e interrupciones externas. |
| RNF-02 | Rendimiento | Responder las consultas de estado de pedido en menos de 2 segundos para el percentil 95, bajo una carga representativa que se definirá antes de las pruebas. |
| RNF-03 | Seguridad | Proteger la información sensible en tránsito y en reposo, y limitar el acceso a funciones y datos según el rol del usuario. |
| RNF-04 | Mantenibilidad | Organizar el sistema en módulos con responsabilidades claras para que las reglas de un dominio puedan cambiar sin alterar la lógica de los otros dominios. |
| RNF-05 | Integración y resiliencia | Registrar los reintentos y errores de comunicación con los canales y servicios externos, de manera que puedan diagnosticarse y procesarse sin duplicar pedidos. |

## Restricciones y aspectos por confirmar

- El proyecto académico define una plataforma logística central para una empresa de retail digital; no se especifica todavía una tecnología obligatoria.
- La disponibilidad de webhooks, APIs y datos de inventario depende de cada canal y sistema externo. Debe confirmarse con la empresa del caso.
- El periodo de retención de reservas, el volumen esperado de pedidos y la carga máxima no están definidos. Se dejan como decisiones pendientes para una etapa posterior.
- El seguimiento en vivo depende de que el repartidor y el servicio de ubicación puedan enviar datos. La aplicación debe indicar cuándo la ubicación no está disponible en vez de mostrar información antigua como si fuera actual.

# Escenarios de calidad

Estos escenarios convierten los objetivos de calidad en situaciones que el equipo puede revisar. Las cifras son objetivos iniciales del proyecto; antes de implementarlos, se debe acordar el entorno y la carga de prueba para que los resultados sean comparables.

## Consulta del estado de un pedido

- **Estímulo:** un cliente solicita el estado de un pedido activo.
- **Entorno:** operación normal y carga representativa de un periodo de alta demanda.
- **Respuesta esperada:** MercuApp devuelve el estado más reciente que conoce y la interfaz lo presenta al cliente.
- **Medida:** al menos el 95 % de las consultas termina en menos de 2 segundos, medidos desde que la API recibe la solicitud hasta que responde.

## Dos compras del último artículo

- **Estímulo:** dos clientes intentan comprar al mismo tiempo la última unidad disponible en una tienda.
- **Entorno:** ambas solicitudes llegan mientras la tienda reporta una unidad disponible.
- **Respuesta esperada:** solo una solicitud obtiene la reserva; la otra recibe un mensaje claro de falta de disponibilidad. Si el pago de la primera falla o la reserva vence, la unidad vuelve a quedar disponible.
- **Medida:** en las pruebas de concurrencia no se confirma más de una compra por la misma unidad.

## Reintento de un canal externo

- **Estímulo:** un canal vuelve a enviar un pedido porque no recibió respuesta a tiempo.
- **Entorno:** el primer envío pudo haber sido recibido por MercuApp, pero la respuesta no llegó al canal.
- **Respuesta esperada:** MercuApp reconoce la clave del pedido de origen y devuelve el resultado del pedido ya registrado, sin crear otro.
- **Medida:** cada identificador de origen produce como máximo un pedido en MercuApp, incluso si se reintenta la solicitud.

## Cambio en reglas de asignación

- **Estímulo:** el equipo cambia una regla de asignación de entregas, por ejemplo, el criterio para seleccionar repartidores disponibles.
- **Entorno:** desarrollo y revisión antes de publicar una nueva versión.
- **Respuesta esperada:** la regla puede modificarse y probarse dentro del módulo de logística sin cambiar las reglas de inventario o pagos. La aplicación sigue desplegándose como una unidad.
- **Medida:** las pruebas del módulo de logística verifican el cambio y las pruebas de regresión de inventario y pagos continúan pasando.

## Interrupción de un servicio externo

- **Estímulo:** el servicio de mapas o notificaciones no responde temporalmente.
- **Entorno:** un pedido está en preparación o en camino.
- **Respuesta esperada:** MercuApp conserva el pedido y su estado, registra el error y permite reintentar la integración. No presenta como actual una ubicación que no ha podido confirmar.
- **Medida:** la interrupción externa no elimina ni duplica el pedido, y el error queda asociado al pedido para su diagnóstico.

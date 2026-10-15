# Escenarios de Calidad

## Escenario 1: Rendimiento en Consulta de Pedidos
* **Estímulo:** El cliente final ingresa a la aplicación para verificar el estado de su orden activa.
* **Entorno:** Operación normal con picos de tráfico urbano vespertino.
* **Respuesta:** El sistema procesa la consulta y renderiza la interfaz con el estado actual.
* **Medida de Calidad:** La respuesta se completa en un tiempo inferior a 2 segundos (95 percentil).

## Escenario 2: Concurrencia de Inventario (Disponibilidad y Consistencia)
* **Estímulo:** Dos clientes intentan comprar el último artículo disponible de una tienda al mismo tiempo.
* **Entorno:** Alta concurrencia durante una campaña de descuentos masivos.
* **Respuesta:** El mecanismo transaccional bloquea el stock de forma atómica para el primer pago exitoso y rechaza limpiamente el segundo con un aviso de quiebre.
* **Medida de Calidad:** Cero sobreventas de inventario espejo registradas en la base de datos central.

## Escenario 3: Mantenibilidad (Facilidad de Cambio)
* **Estímulo:** El equipo de producto solicita modificar las reglas de cálculo de asignación de última milla.
* **Entorno:** Fase de evolución de software en entorno de desarrollo.
* **Respuesta:** El cambio se confina exclusivamente al módulo de logística sin requerir modificaciones ni recompilación en los módulos de pagos o inventario.

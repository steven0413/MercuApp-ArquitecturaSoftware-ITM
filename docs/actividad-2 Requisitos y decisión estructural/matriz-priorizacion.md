# Priorización de requisitos - MercuApp

## Cómo se priorizó

Priorizamos pensando en lo que puede afectar directamente una compra y una entrega. Primero van las capacidades que evitan pedidos duplicados, ventas de productos agotados y pérdida de seguimiento. Después quedan las funciones que ayudan a mejorar la operación cuando el flujo principal ya está bajo control.

Para comparar los requisitos usamos tres niveles: **alto, medio y bajo**. La complejidad es una estimación inicial del esfuerzo y del cuidado técnico que exige cada requisito; no representa una medición de horas.

| ID | Requisito | Prioridad | Impacto en el negocio | Impacto arquitectónico | Complejidad | Motivo |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| RF-01 | Recibir pedidos desde varios canales y evitar registros duplicados | Alta | Alto | Alto | Media | Sin un registro confiable, la operación pierde pedidos o procesa el mismo pedido más de una vez. |
| RF-02 | Consultar y reservar inventario por tienda durante la compra | Alta | Alto | Alto | Alta | Una reserva consistente reduce cancelaciones por productos que ya no están disponibles. Requiere resolver concurrencia y vencimiento de reservas. |
| RF-03 | Asignar pedidos a repartidores disponibles según zona | Alta | Alto | Medio | Media | La asignación influye en los tiempos de entrega y necesita datos de disponibilidad y ubicación. |
| RF-04 | Mostrar al cliente el estado del pedido y la ubicación disponible de la entrega | Alta | Alto | Medio | Media | La trazabilidad mejora la experiencia y reduce consultas a soporte. |
| RF-05 | Registrar incidencias, cancelaciones y cambios de entrega | Media | Medio | Medio | Baja | Da contexto a soporte y permite entender por qué una entrega no terminó como se esperaba. |
| RNF-01 | Mantener una disponibilidad objetivo del 99,5 % durante el horario operativo | Alta | Alto | Alto | Media | Una interrupción en horas de venta afecta pedidos, pagos y coordinación. El porcentaje debe revisarse con un periodo de medición acordado. |
| RNF-02 | Responder consultas de pedido en menos de 2 segundos en el percentil 95 | Alta | Alto | Medio | Media | Permite evaluar la experiencia de consulta en condiciones representativas de carga. |
| RNF-03 | Proteger datos sensibles en tránsito y en reposo | Alta | Alto | Alto | Media | Los datos de clientes y transacciones requieren controles de acceso y protección durante almacenamiento y comunicación. |
| RNF-04 | Permitir cambios de reglas de un dominio sin modificar los demás | Media | Medio | Alto | Media | Favorece la evolución del sistema; depende de mantener límites claros entre módulos. |

## Lectura de la matriz

Los requisitos RF-01 y RF-02 son los más sensibles para la arquitectura porque conectan los canales externos con órdenes e inventario y deben conservar coherencia ante reintentos o compras simultáneas. Por eso la decisión estructural debe facilitar transacciones locales y límites de dominio claros.

La trazabilidad y la asignación también son prioritarias para el negocio, aunque su primera versión puede apoyarse en servicios externos de mapas y notificaciones. La matriz se podrá ajustar cuando el equipo tenga datos reales sobre volumen, canales disponibles y operación de las tiendas.

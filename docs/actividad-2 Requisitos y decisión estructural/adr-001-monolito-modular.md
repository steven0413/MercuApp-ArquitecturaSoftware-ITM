# ADR-001: Monolito modular para MercuApp

## Estado

Decisión propuesta para la etapa inicial del proyecto.

## Contexto

MercuApp debe reunir pedidos que llegan desde varios canales, coordinar inventario de distintas tiendas y acompañar la entrega hasta que se confirme o se registre una incidencia. Los errores de inventario y la pérdida de trazabilidad afectan directamente al cliente y al trabajo de la operación.

En esta etapa académica no contamos con cifras confirmadas de volumen, equipos independientes por dominio ni necesidades de despliegue separado. Sí necesitamos mostrar cómo se relacionan los dominios y cómo mantener coherencia en el flujo de pedido e inventario.

## Opciones consideradas

1. **Monolito modular:** una aplicación desplegable con módulos internos separados por responsabilidades, como Ingesta, Órdenes, Inventario, Logística y Soporte.
2. **Servicios distribuidos por dominio:** varios servicios desplegables de manera independiente, comunicados mediante APIs o eventos.

## Decisión

Para la etapa inicial se propone un monolito modular con una base de datos relacional central. Los módulos tendrán límites explícitos y cada uno será responsable de sus reglas y datos de dominio. Las operaciones que deban reservar inventario y registrar el resultado podrán coordinarse con transacciones locales.

Los pagos, mapas, notificaciones y sistemas de venta se integrarán como servicios externos. Sus fallos y reintentos deben registrarse sin duplicar pedidos ni perder el estado ya conocido.

## Por qué esta opción

El monolito modular permite empezar con una sola unidad de despliegue y menos trabajo operativo. También facilita coordinar cambios que afectan a pedido e inventario sin resolver desde el principio transacciones entre varios servicios. La separación interna mantiene visible la estructura por dominios y deja abierta la posibilidad de extraer un módulo más adelante, si los datos del negocio lo justifican.

## Consecuencias y trade-offs

- El despliegue y el escalamiento iniciales se hacen para la aplicación completa, aunque algunos módulos podrían tener más carga que otros.
- Los módulos comparten proceso y base de datos; por eso es necesario evitar que accedan sin control a las responsabilidades de otros módulos.
- Una falla de la aplicación puede afectar más de una capacidad. Se requiere monitoreo y recuperación adecuados para el conjunto.
- A cambio, el equipo evita operar una red de servicios y puede usar transacciones locales para los primeros flujos críticos.
- Si se extrae un módulo en el futuro, habrá que definir contratos, manejo de fallos y consistencia entre servicios.

## Riesgos y medidas

| Riesgo | Medida propuesta |
| :--- | :--- |
| Los módulos terminan acoplados y cualquier cambio afecta todo el sistema. | Definir responsabilidades, interfaces internas y pruebas que protejan los límites entre dominios. |
| El crecimiento de un dominio satura la aplicación completa. | Medir carga y tiempos por capacidad; reevaluar la decisión si se identifica una necesidad real de escalamiento independiente. |
| Un servicio externo falla o responde tarde. | Registrar el estado de la integración, reintentar de forma controlada y conservar el pedido sin duplicarlo. |
| La reserva de inventario queda activa después de un pago fallido. | Definir vencimiento y liberación de reservas, y verificar ambos casos en los escenarios de calidad. |

## Cómo revisaremos la decisión

La decisión se considerará adecuada para esta etapa si los escenarios de calidad pueden cumplirse, los límites entre módulos se mantienen y el equipo puede operar el sistema sin una infraestructura distribuida innecesaria. Se revisará si aparecen necesidades comprobables de escalar o desplegar dominios por separado, o si los límites modulares ya no permiten evolucionar el sistema con seguridad.

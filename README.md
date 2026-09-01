# MercuApp - Plataforma de Gestión Logística de Última Milla (Retail Mirror)

## Resumen Ejecutivo
¡Hola! Bienvenidos a **MercuApp**. Este proyecto es el punto de partida para entender cómo la arquitectura de software resuelve problemas de negocio reales sin caer en sobreingeniería.

Para mantener una excelente disponibilidad y escalabilidad inicial sin la complejidad masiva de los microservicios, hemos decidido implementar un **monolito modular**. Esto nos permite mantener el código ordenado, asegurar la consistencia del inventario espejo y escalar de forma simple conforme el negocio crece.

* **Problema Principal:** Hoy los pedidos llegan por muchos lados, el inventario de las tiendas no está sincronizado y nadie sabe exactamente dónde va el pedido, lo que causa retrasos y dolores de cabeza.
* **Estilo Arquitectónico:** Monolito modular enfocado en la simplicidad, alta cohesión y bajo acoplamiento interno.
* **Alcance:** Desde que el cliente paga y el pedido entra al sistema, hasta que el repartidor hace la entrega final en la puerta de su casa.
* **Enlace de Sustentación:** 
# Supuestos y Decisiones Iniciales - MercuApp

## ¿Qué estamos asumiendo?
* Suponemos que los canales de venta se pueden conectar fácilmente mediante avisos automáticos (*webhooks*).
* Asumimos que los repartidores tienen un teléfono inteligente con datos móviles en la ciudad.

## ¿Qué decisiones ya tomamos?
* **Apuesta por un Monolito Modular (Cero Sobreingeniería):** Evitamos adoptar microservicios o arquitecturas distribuidas complejas en esta etapa inicial. Un monolito bien estructurado en módulos (Órdenes, Inventario, Repartidores) nos otorga la disponibilidad y escalabilidad vertical necesaria, facilitando el desarrollo y reduciendo costos operativos.
* **Delegar lo complejo:** No vamos a inventar un mapa ni un sistema de mensajes de texto masivos; usaremos herramientas de terceros que ya funcionan muy bien.
# Selección de Monolito Modular para MercuApp

## Contexto
MercuApp requiere gestionar una operación basada en inventarios distribuidos con alta exigencia en consistencia transaccional y disponibilidad. Debemos elegir una estructura arquitectónica inicial que permita validar el modelo de negocio con rapidez, manteniendo bajos costos operativos y evitando la complejidad innecesaria de sistemas distribuidos prematuros.

## Decisión
Se decide implementar un **Monolito Modular** estructurado en dominios claros (Ingesta, Órdenes, Inventario, Logística y Soporte), utilizando una base de datos relacional centralizada y aplicando principios de diseño limpio y separación de dependencias.

## Consecuencias
* **Ventajas:** 
  * Reducción drástica de la complejidad operativa e infraestructura inicial.
  * Garantía de consistencia transaccional estricta en el inventario  mediante transacciones locales de base de datos.
  * Mayor velocidad de desarrollo y facilidad de despliegue.
* **Desafíos:**
  * Si el negocio escala masivamente a nivel nacional de forma descontrolada, algunos módulos altamente demandados (como geolocalización o ingesta) podrían requerir una futura refactorización para extraerlos como servicios independientes.

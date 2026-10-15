# ADR 001: Selección de Monolito Modular para MercuApp

## Estado
Aprobado

## Contexto
MercuApp requiere gestionar una operación de última milla basada en inventarios distribuidos (modelo espejo) con alta exigencia en consistencia transaccional y disponibilidad moderada/alta. Debemos elegir una estructura arquitectónica inicial que permita validar el modelo de negocio con rapidez, manteniendo bajos costos operativos y evitando la complejidad innecesaria de sistemas distribuidos prematuros.

## Decisión
Se decide implementar un **Monolito Modular** estructurado en dominios claros (Ingesta, Órdenes, Inventario Espejo, Logística y Soporte), utilizando una base de datos relacional centralizada y aplicando principios de diseño limpio y separación de dependencias.

## Consecuencias y Trade-offs
* **Ventajas:** 
  * Reducción drástica de la complejidad operativa e infraestructura inicial.
  * Garantía de consistencia transaccional estricta (ACID) en el inventario espejo mediante transacciones locales de base de datos.
  * Mayor velocidad de desarrollo y facilidad de despliegue.
* **Desafíos (Trade-offs):**
  * Si el negocio escala masivamente a nivel nacional de forma descontrolada, algunos módulos altamente demandados (como geolocalización o ingesta) podrían requerir una futura refactorización para extraerlos como servicios independientes.

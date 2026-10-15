# Catálogo de Requisitos - MercuApp

## 1. Requisitos Funcionales
* **RF-01 (Ingesta de Órdenes):** El sistema debe recibir y registrar pedidos provenientes de múltiples canales externos (web, apps, aggregators) asegurando idempotencia.
* **RF-02 (Control de Inventario Espejo):** El sistema debe validar y bloquear temporalmente el stock disponible en las tiendas o dark stores de forma atómica durante la pasarela de pago.
* **RF-03 (Asignación de Repartidores):** El sistema debe permitir asignar una entrega a un repartidor disponible y validado geográficamente.
* **RF-04 (Trazabilidad en Vivo):** El sistema debe permitir a los clientes consultar el estado actualizado y la posición de su entrega en tiempo real.
* **RF-05 (Gestión de Incidencias):** El sistema debe registrar novedades, cancelaciones o excepciones gestionadas por el equipo de soporte.

## 2. Requisitos No Funcionales (Atributos de Calidad)
* **RNF-01 (Disponibilidad):** El monolito modular debe garantizar una disponibilidad operativa del 99.5% durante las horas de alta demanda comercial.
* **RNF-02 (Rendimiento):** Las consultas de estado de pedidos y catálogos deben responder en un tiempo menor a 2 segundos.
* **RNF-03 (Seguridad):** La información sensible de los usuarios y transacciones debe estar cifrada en tránsito y en reposo.
* **RNF-04 (Mantenibilidad y Evolución):** La separación en módulos independientes debe permitir modificar reglas de negocio de un dominio sin alterar toda la aplicación.

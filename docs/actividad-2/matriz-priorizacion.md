# MercuApp - Plataforma de Gestión Logística de Última Milla (Retail Mirror)

## Resumen Ejecutivo (Actividades 1 y 2)
**MercuApp** es una plataforma centralizada diseñada para resolver el caos logístico del retail digital mediante un **modelo de inventario en espejo (*mirror stock*)** sincronizado con tiendas físicas y dark stores.

* **Problema Principal:** Fragmentación en la ingesta multicanal, desalineación del inventario distribuido y falta de trazabilidad en tiempo real.
* **Estilo Arquitectónico:** Monolito modular enfocado en la simplicidad, alta cohesión interna, bajo acoplamiento y transacciones ACID nativas, evitando la sobreingeniería de sistemas distribuidos prematuros.
* **Alcance:** Desde que el cliente paga y el pedido entra al sistema, hasta que el repartidor ejecuta la entrega final en campo.

---

## Estructura de la Documentación en el Repositorio

```text
├── README.md
└── docs/
    ├── actividad-1/
    │   ├── analisis-problema.md
    │   ├── diagrama-contexto.png.jpg
    │   ├── riesgos.md
    │   └── supuestos-y-decisiones.md
    └── actividad-2/
        ├── catalogo-requisitos.md
        ├── matriz-priorizacion.md
        ├── escenarios-calidad.md
        ├── comparacion-alternativas.md
        └── adr-001-monolito-modular.md
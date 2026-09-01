# ¿Qué puede salir mal? (Matriz de Riesgos)

| Riesgo Identificado | Impacto | Probabilidad | ¿Cómo lo vamos a prevenir? (Mitigación) |
| :--- | :--- | :--- | :--- |
| **Inconsistencias de inventario** (vender lo que no hay). | Alto | Media | Bloquear temporalmente el producto en la base de datos relacional del monolito mientras el cliente paga. |
| **Pérdida de trazabilidad** si el repartidor se queda sin internet. | Alto | Alta | Diseñar la app móvil para que funcione sin red un momento y guarde los datos hasta que recupere señal. |
| **Duplicación de pedidos** si el cliente le da dos veces al botón de pagar. | Medio | Media | Usar llaves únicas de control (*Idempotency Keys*) en las peticiones del monolito. |
| **Crecimiento operativo sin control** y saturación de rutas. | Alto | Media | Dejar que un servicio externo de mapas especializado calcule las rutas difíciles. |
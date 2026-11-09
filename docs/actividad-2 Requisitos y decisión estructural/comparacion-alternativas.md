# Comparación de alternativas estructurales

Para elegir una estructura, comparamos dos opciones para el mismo alcance de MercuApp: recibir pedidos, coordinar inventario y entregas, y registrar incidencias. La pregunta no es cuál arquitectura es mejor en cualquier situación, sino cuál permite atender este caso con un costo y un riesgo razonables para la etapa actual.

| Criterio | Monolito modular | Servicios distribuidos por dominio |
| :--- | :--- | :--- |
| Complejidad inicial | Una aplicación desplegable, organizada internamente en módulos. Hay que cuidar las dependencias entre ellos. | Cada servicio necesita configuración, despliegue, comunicación de red y monitoreo propios. |
| Consistencia de pedidos e inventario | Las operaciones que pertenecen a una misma base de datos pueden coordinarse con transacciones locales. | Las operaciones cruzan servicios y pueden requerir consistencia eventual, compensaciones y manejo de fallos parciales. |
| Costo y esfuerzo del equipo | Menor esfuerzo de infraestructura y operación para comenzar. | Mayor esfuerzo en automatización, observabilidad, seguridad de servicios y coordinación de cambios. |
| Evolución | Los módulos pueden evolucionar con límites claros, pero se despliega la aplicación como una unidad. | Permite desplegar y escalar servicios por separado, a cambio de mantener contratos y compatibilidad entre ellos. |
| Escalamiento | La aplicación se escala como unidad; si un dominio exige mucho más, puede convertirse en una limitación. | Se puede escalar cada servicio por separado, siempre que haya una necesidad real y capacidad para operarlo. |
| Riesgos principales | Que los módulos se mezclen y el monolito se vuelva difícil de cambiar; una falla de la aplicación puede afectar varias funciones. | Más puntos de falla, latencia de red, consistencia distribuida y diagnóstico más complejo. |
| Ajuste al proyecto | Adecuado para validar el flujo central con un equipo y una operación iniciales, si se respetan los límites modulares. | Puede ser útil con cargas desiguales, equipos independientes o necesidades de despliegue autónomo ya comprobadas. |

## Evaluación

Los dos enfoques pueden resolver el problema. Para esta etapa no hay datos que demuestren que MercuApp necesite escalar cada dominio por separado ni que existan equipos distintos responsables de cada servicio. Sí hay una necesidad clara de coordinar pedidos e inventario sin añadir demasiada complejidad operativa.

Por ese motivo, el monolito modular ofrece un punto de partida más sencillo. La decisión tiene un costo: todos los módulos comparten ciclo de despliegue y la escalabilidad se gestiona inicialmente para la aplicación en conjunto. Para que esa opción siga siendo viable, los límites entre dominios deben hacerse explícitos y revisarse a medida que evolucione el sistema.

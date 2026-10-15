# Comparación de Alternativas Estructurales

| Criterio de Evaluación | Alternativa A: Monolito Modular | Alternativa B: Microservicios Distribuidos |
| :--- | :--- | :--- |
| **Complejidad Operativa** | Baja / Moderada. Una sola unidad de despliegue y base de datos centralizada. | Alta. Requiere orquestadores (Kubernetes), Service Mesh y gestión de red distribuida. |
| **Costo de Infraestructura** | Bajo. Despliegue en un único servidor o instancia optimizada. | Alto. Múltiples contenedores, balanceadores y bases de datos independientes por servicio. |
| **Rapidez de Implementación** | Alta. Ideal para etapas iniciales y equipos con recursos acotados. | Baja. Overhead inicial elevado en configuración de contratos de red y despliegue. |
| **Facilidad de Evolución** | Media. Clara separación por carpetas/módulos lógicos que permiten escalar verticalmente. | Alta. Escalabilidad horizontal independiente por cada servicio de dominio. |
| **Riesgo Operativo** | Bajo. Se evitan fallas por latencia de red entre servicios y transacciones distribuidas complejas. | Alto. Riesgo de consistencia eventual y depuración compleja en entornos distribuidos. |
| **Alineación con el Negocio** | Total. Resuelve la complejidad actual del retail sin incurrir en sobreingeniería prematura. | Sobredimensionado para la madurez actual del proyecto. |

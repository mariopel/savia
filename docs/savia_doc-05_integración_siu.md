[ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: DOC-05
ID TEMPORAL: 260618T0213 - Patrones de Integración: Push vs. Pull (SIU Guaraní)
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: API REST, SIU Guaraní, Payload CMS
ESTADO: Pendiente de Implementación
===========================================================

- Resumen del Concepto: Patrones de Comunicación API
La integración de dos sistemas robustos requiere definir la dirección del flujo de datos.
1. Modelo Push (SIU es proactivo): SIU Guaraní detecta un egreso y "empuja" los datos hacia la API de SAVIA.
2. Modelo Pull (SAVIA es proactivo): SAVIA (o un script intermedio) "tira" de la API del SIU Guaraní periódicamente para ver si hay nuevos egresados y luego los inyecta en su propia base.

- Justificación Técnica y Evidencia:
La documentación que enviaste de SIU Guaraní muestra que exponen endpoints para ser consumidos (Modelo Pull). Sin embargo, Payload CMS (el núcleo de SAVIA) no tiene un "recolector" nativo programado de fábrica para ir a buscar datos a otros sistemas; está diseñado para *recibir* peticiones POST en sus endpoints como `/api/credential-batches` (Modelo Push).

- Configuración / Lógica Acordada (Opciones para el MVP):
* OPCIÓN A (Simulación Push rápida): El equipo del SIU (o vos mismo) utiliza un cliente como Postman para enviar un JSON directamente a la API de SAVIA simulando que el SIU disparó el evento. Es la vía más rápida para demostrar el MVP en los próximos 10 días.
* OPCIÓN B (Middleware Pull): Desarrollamos un pequeño script en Node.js o Python (un "puente") que se ejecute todos los días a medianoche. Este puente se conecta a la API del SIU Guaraní, descarga la lista de egresados y se la inyecta automáticamente a la API de SAVIA.

----------------------------------------------------------------------
SAVIA modelo federal | Reporte Técnico Nº: 05 | Página 1 de 1
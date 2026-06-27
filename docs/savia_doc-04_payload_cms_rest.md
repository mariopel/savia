[ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: DOC-04
ID TEMPORAL: 260618T0207 - Arquitectura de Integración API SIU Guaraní
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: Payload CMS Headless, API REST, Webhooks
ESTADO: Pendiente de Implementación
===========================================================

- Resumen del Concepto: Integración Headless (API REST)
Payload CMS, el núcleo sobre el que corre `dcc-admin-dashboard`, es un sistema "Headless" (sin cabeza). Esto significa que la interfaz web que usaste hasta ahora es solo una máscara opcional. Su verdadera potencia radica en que genera automáticamente una API REST completa para cada base de datos.
El SIU Guaraní no necesita saber qué es el W3C, ni qué es Ed25519, ni cómo firmar un JSON. El equipo de la Dirección de Computación (DCPD) solo necesita programar un evento (trigger) en el SIU para que, al momento de registrar el egreso de un alumno, dispare una petición HTTP POST segura hacia nuestro servidor Traefik (`gecer.unr.edu.ar/api/credential-batches`). SAVIA tomará esos datos planos, los firmará con la llave de la UNR y emitirá la credencial automáticamente.

- Justificación Técnica y Evidencia:
El estándar de arquitectura de DCC confía el enrutamiento de datos a las capacidades nativas de Payload CMS.
* URL de la fuente: `https://payloadcms.com/docs/rest-api/overview`
* Párrafo de soporte: "Payload automatically generates a fully functional REST API from your collections and globals... all CRUD operations are exposed via standard HTTP methods."
* URL de la fuente oficial DCC: `https://github.com/digitalcredentials/dcc-admin-dashboard`
* Párrafo de soporte: "The dashboard is built on Payload CMS... You can create credentials in bulk by uploading a CSV or by interacting with the API."

- Configuración / Lógica Acordada:
Para lograr este hito en el MVP, la estrategia de integración será:
1. Generar una API Key inmutable dentro del panel de SAVIA asociada a un "Usuario de Sistema" (ej. `siu-service-account`).
2. Diseñar el esquema JSON exacto que el SIU Guaraní debe enviar.
3. Consumir el endpoint `/api/credential-batches` para inyectar a los alumnos.

----------------------------------------------------------------------
SAVIA modelo federal | Reporte Técnico Nº: 04 | Página 1 de 1
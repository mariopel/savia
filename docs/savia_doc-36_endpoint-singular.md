### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-36
ID Temporal: 260701T1040
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: API REST, Payload CMS, Ruteo Singular
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
Durante la integracion M2M, el ruteo de la API en Payload CMS impone una
restriccion estricta de nomenclatura: los endpoints correspondientes a
las colecciones se definen en singular. Intentar enviar datos a rutas
pluralizadas (como /api/credential-batches) resulta en un error 404.

#### Justificacion Tecnica y Evidencia
Payload CMS mapea de forma automatica el nombre de la coleccion directo
al endpoint HTTP en su forma singular, a pesar de que en la base de
datos MongoDB las tablas internas se almacenen en plural.
URL: https://payloadcms.com/docs/rest-api/overview
Cita: "By default, the REST API endpoints are generated using the
singular slug defined in your collection configuration."

#### Configuracion / Logica Acordada
1. Configurar el cliente HTTP o middleware para apuntar estrictamente a
la URL singular: https://gecer.unr.edu.ar/api/credential-batch.
2. Descartar cualquier reintento o regla de ruteo que añada sufijos de
pluralizacion en las llamadas de inyeccion de diplomas.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 36 | Pagina 1 de 1
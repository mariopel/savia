### [ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 57
ID TEMPORAL: 260701T1049 - IDs Relacionales M2M
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: MongoDB, ObjectId, Payload CMS
ESTADO: Consolidado
===========================================================
### [CUERPO DEL DOCUMENTO]
- Resumen del Concepto:
En la inyeccion de credenciales M2M, los campos relacionales como el
'template' (plantilla grafica) y 'emailTemplate' (diseño de correo) no
aceptan nombres ni slugs. Requieren obligatoriamente la inyeccion del
ObjectId hexadecimal de 24 caracteres nativo de MongoDB.

- Justificacion Tecnica y Evidencia:
Payload CMS valida las relaciones exigiendo el ID exacto del documento
referenciado para mantener la integridad de la base de datos.
URL: https://payloadcms.com/docs/fields/relationship
Cita: "When creating or updating a document with a relationship field,
you must provide the ID of the related document."

- Configuracion / Logica Acordada:
1. Localizar los ObjectIds generados al crear los templates en el panel.
2. En el JSON del middleware (cURL/SIU), estructurar los datos asi:
"template": "60d5ec49f1b2c8a1b4e8b0a1"
3. Rechazar inyecciones que intenten usar cadenas de texto comunes.
----------------------------------------------------------------------
### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 57 | Pagina 1 de 1
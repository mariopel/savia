### [ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 69
ID TEMPORAL: 260701T1100 - Estructuracion del Lote JSON
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: JSON Schema, Payload CMS
ESTADO: Consolidado
===========================================================
### [CUERPO DEL DOCUMENTO]
- Resumen del Concepto:
Antes de ejecutar la inyeccion, se debe estructurar meticulosamente
el JSON del lote (credential-batch). Este bloque integra los ObjectIds
de las plantillas y el array batchData con la informacion especifica
de cada estudiante, asegurando ademas el estado inicial como "draft".

- Justificacion Tecnica y Evidencia:
La API rechazara peticiones donde falten relaciones requeridas o donde
los tipos de datos (como la fecha ISO) no coincidan con el esquema.
URL: https://payloadcms.com/docs/rest-api/overview
Cita: "When creating documents containing arrays and relationships, the
payload must perfectly mirror the expected field schema."

- Configuracion / Logica Acordada:
1. Definir los IDs estaticos de Payload:
"template": "6a42f...", "emailTemplate": "6a42f..."
2. Configurar "_status": "draft" en la raiz del objeto JSON.
3. Declarar "batchData": [{...}] encapsulando los nombres, DNI,
carreras y fechas de graduacion en el formato exigido.
----------------------------------------------------------------------
### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 69 | Pagina 1 de 1
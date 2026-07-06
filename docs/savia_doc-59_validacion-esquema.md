### [ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 59
ID TEMPORAL: 260701T1049 - Validacion de Esquema
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: Payload CMS, HTTP 400, Schema
ESTADO: Consolidado
===========================================================
### [CUERPO DEL DOCUMENTO]
- Resumen del Concepto:
Payload CMS actua como un firewall de datos. Compara el JSON entrante
contra el esquema de la coleccion (Credential Batch). Si el script cURL
envia campos que no existen en el esquema, o ignora campos obligatorios,
el motor aborta la transaccion sin escribir nada en MongoDB.

- Justificacion Tecnica y Evidencia:
Garantizar la pureza de los datos antes de firmarlos criptograficamente
es innegociable para el estandar Open Badges v3.
URL: https://payloadcms.com/docs/fields/overview#validation
Cita: "Payload validates data against your field configuration before
saving. Validation errors prevent the document from being created."

- Configuracion / Logica Acordada:
1. Depurar el payload JSON del cURL para asegurar que coincida campo
por campo con las propiedades definidas en el codigo fuente de SAVIA.
2. Analizar el cuerpo de la respuesta HTTP 400, ya que Payload CMS
detalla exactamente que campo fallo en la matriz de errores (errors[]).
----------------------------------------------------------------------
### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 59 | Pagina 1 de 1
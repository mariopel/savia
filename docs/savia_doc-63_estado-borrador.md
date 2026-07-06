### [ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 63
ID TEMPORAL: 260701T1054 - Flujo de Estado Draft
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: Payload CMS, Flujo de Trabajo
ESTADO: Consolidado
===========================================================
### [CUERPO DEL DOCUMENTO]
- Resumen del Concepto:
El motor SAVIA integra un flujo de trabajo documental mediante la
propiedad '_status'. Al inyectar un lote via API, el sistema de origen
(LMS) debe marcarlo obligatoriamente como 'draft' (borrador). Esto
permite auditar los datos en el dashboard antes de la firma definitiva.

- Justificacion Tecnica y Evidencia:
Firmar criptograficamente una credencial la hace inmutable. El estado de
borrador añade una capa de aprobacion humana (o automatizada posterior)
que previene la emision de titulos con errores formales.
URL: https://payloadcms.com/docs/versions/drafts
Cita: "Drafts allow you to save documents without publishing them.
Published documents are considered final and live."

- Configuracion / Logica Acordada:
1. El middleware M2M debe incluir "_status": "draft" en el JSON raiz.
2. El personal administrativo de la UNR revisara los lotes ingresados
desde la interfaz de Payload CMS.
3. Una vez aprobados, el sistema cambia el estado a "published" y ejecuta
la firma Ed25519 sobre cada registro del lote.
----------------------------------------------------------------------
### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 63 | Pagina 1 de 1
### [ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 71
ID TEMPORAL: 260701T1100 - Analisis de HTTP 400
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: Debugging API, HTTP 400
ESTADO: Consolidado
===========================================================
### [CUERPO DEL DOCUMENTO]
- Resumen del Concepto:
Si la inyeccion POST falla, la API devuelve codigos de estado. Un error
HTTP 401 delata un token mal formado o vencido. Un error HTTP 400 (Bad
Request) confirma que la conexion fue exitosa, pero el JSON enviado
incumple el esquema de la base de datos MongoDB.

- Justificacion Tecnica y Evidencia:
El codigo 400 nunca es un problema de red, sino de reglas de negocio.
Payload rechaza la transaccion y devuelve un array detallando el fallo.
URL: https://payloadcms.com/docs/rest-api/overview
Cita: "Payload returns a 400 status code along with a structured array
of validation errors if the request body fails schema checks."

- Configuracion / Logica Acordada:
1. En caso de error, agregar '| jq' al final del comando cURL.
2. Leer la matriz "errors" devuelta para identificar si falta un campo
obligatorio en batchData, o si se envio una relacion invalida.
3. Corregir el string JSON basado unicamente en la devolucion del motor.
----------------------------------------------------------------------
### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 71 | Pagina 1 de 1
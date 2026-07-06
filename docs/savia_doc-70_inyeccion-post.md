### [ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 70
ID TEMPORAL: 260701T1100 - Inyeccion POST (cURL)
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: cURL, POST, API REST
ESTADO: Consolidado
===========================================================
### [CUERPO DEL DOCUMENTO]
- Resumen del Concepto:
Con el token capturado y el JSON estructurado, se ejecuta el metodo
POST hacia el endpoint singular del orquestador. El comando integra los
encabezados de validacion (Content-Type) y seguridad (Authorization)
con los datos que alimentaran la base de datos (mongo-1).

- Justificacion Tecnica y Evidencia:
Payload CMS requiere estrictamente el prefijo JWT para desencriptar y
validar la identidad de la Cuenta de Servicio antes de insertar datos.
URL: https://curl.se/docs/manual.html
Cita: "Use the -H, --header option to include custom header lines when
contacting the server, such as authorization tokens."

- Configuracion / Logica Acordada:
1. Ejecutar el comando cURL apuntando a /api/credential-batch.
2. Incluir cabecera: -H "Authorization: JWT $TOKEN".
3. Inyectar los datos escapando todo el bloque JSON con comillas simples:
-d '{"template":"...", "batchData":[...], "_status":"draft"}'
----------------------------------------------------------------------
### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 70 | Pagina 1 de 1
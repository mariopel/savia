### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-56
ID Temporal: 260701T1047
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: JSON, Payload cURL, Estructura
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
Para el exito de la peticion cURL de inyeccion, el cuerpo de la solicitud
(Payload JSON) debe estar perfectamente escapado y estructurado. Un error
de sintaxis en las comillas o en la definicion de las variables
(template, emailTemplate) resultara en un rechazo inmediato por la API.

#### Justificacion Tecnica y Evidencia
Payload CMS requiere que las cabeceras HTTP incluyan explicitamente el
tipo de contenido y el token JWT para procesar el cuerpo JSON de entrada.
URL: https://payloadcms.com/docs/rest-api/overview
Cita: "When making POST requests, ensure the Content-Type header is set
to application/json and the body is valid stringified JSON."

#### Configuracion / Logica Acordada
1. Definir el header: -H "Content-Type: application/json".
2. Definir el header: -H "Authorization: Bearer <TOKEN>".
3. Enviar el JSON asegurando que los arrays (batchData) esten bien
formados, lo cual es el paso previo y esencial para analizar y resolver
los errores de inyeccion M2M (que abordaremos en el DOC-72).

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 56 | Pagina 1 de 1
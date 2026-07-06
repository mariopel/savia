### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-51
ID Temporal: 260701T1047
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Payload CMS, CORS, Seguridad API
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
Para proteger los endpoints M2M de SAVIA contra ataques web y accesos no
autorizados, se debe implementar una politica estricta de CORS. Esto
restringe que dominios externos pueden realizar peticiones HTTP a la API,
garantizando que solo la IP del middleware de SIU Guarani tenga acceso.

#### Justificacion Tecnica y Evidencia
Payload permite configurar un array de dominios permitidos (whitelist).
Cualquier peticion originada fuera de esta lista blanca es rechazada.
URL: https://payloadcms.com/docs/configuration/overview
Cita: "The cors property can be set to an array of string URLs... Payload
will restrict cross-origin requests to only those specific domains."

#### Configuracion / Logica Acordada
1. Editar la configuracion de inicializacion de Payload CMS.
2. Establecer la propiedad cors restrictiva apuntando al dominio del LMS.
3. Habilitar metodos HTTP estrictos (POST, GET) bloqueando metodos
destructivos como DELETE para la cuenta de servicio M2M.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 51 | Pagina 1 de 1
### [ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 58
ID TEMPORAL: 260701T1049 - Ciclo de Vida JWT M2M
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: JWT, cURL, Autenticacion
ESTADO: Consolidado
===========================================================
### [CUERPO DEL DOCUMENTO]
- Resumen del Concepto:
El token JWT obtenido por la Cuenta de Servicio tiene un tiempo de vida
finito (Time-To-Live). Si un script M2M de SIU Guarani intenta realizar
una inyeccion con un token expirado, la API rechazara la conexion
inmediatamente, protegiendo al orquestador contra tokens robados.

- Justificacion Tecnica y Evidencia:
La expiracion de tokens es vital en arquitecturas descentralizadas para
limitar la ventana de vulnerabilidad ante secuestros de sesion.
URL: https://payloadcms.com/docs/authentication/overview
Cita: "Tokens are signed with your secret and set to expire after a
configured duration. Expired tokens will result in a 401 response."

- Configuracion / Logica Acordada:
1. Configurar una duracion prudente para la Cuenta de Servicio (ej. 2h).
2. El script cURL debe capturar errores HTTP 401 (Unauthorized).
3. Ante un 401, el middleware debe re-autenticarse contra /api/users/login
para obtener un nuevo token antes de reintentar la inyeccion.
----------------------------------------------------------------------
### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 58 | Pagina 1 de 1
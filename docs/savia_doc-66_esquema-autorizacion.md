### [ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 66
ID TEMPORAL: 260701T1054 - Esquema de Autorizacion JWT
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: HTTP Headers, Autenticacion M2M
ESTADO: Consolidado
===========================================================
### [CUERPO DEL DOCUMENTO]
- Resumen del Concepto:
El encabezado HTTP para la autorizacion es vital. En la implementacion
especifica de SAVIA sobre Payload CMS, el token JWT debe enviarse bajo el
esquema 'JWT', no el tradicional 'Bearer'. Omitir esta palabra clave
resultara en un error de autorizacion HTTP 401 (Unauthorized).

- Justificacion Tecnica y Evidencia:
El motor de autenticacion de Payload fue configurado en este ecosistema
para validar el prefijo especifico 'JWT' dentro de las cabeceras REST.
URL: https://payloadcms.com/docs/authentication/overview
Cita: "Depending on your Payload initialization, the Authorization header
may require the 'JWT' prefix instead of the standard Bearer."

- Configuracion / Logica Acordada:
1. El script de inyeccion M2M debe concatenar el token capturado.
2. La cabecera HTTP (header) en cURL debe configurarse estrictamente
con este formato: -H "Authorization: JWT EL_TOKEN_CAPTURADO"
3. Asegurar la inclusion del espacio en blanco entre el prefijo y el hash.
----------------------------------------------------------------------
### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 66 | Pagina 1 de 1
### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-29
ID Temporal: 260701T0059
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Traefik Proxy, SSL Auto-firmado, Bypass
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
Durante el desarrollo local y fase MVP, el servidor de SAVIA no cuenta con 
certificados SSL emitidos por una Autoridad Certificante publica (CA).
Por ello, Traefik utiliza certificados auto-firmados. Esto protege el
transito de los datos, pero genera advertencias en herramientas cliente.

#### Justificacion Tecnica y Evidencia
Clientes como curl rechazan conexiones HTTPS auto-firmadas por defecto para
prevenir ataques Man-in-the-Middle. En entornos de prueba M2M es necesario
hacer un bypass explicito de esta comprobacion de seguridad.
URL: https://curl.se/docs/manpage.html
Cita: "-k, --insecure: By default, every SSL connection curl makes is
verified to be secure. This option allows curl to proceed and operate even
for server connections otherwise considered insecure."

#### Configuracion / Logica Acordada
1. Proveer certificados generados localmente a la configuracion de Traefik.
2. Al ejecutar rutinas M2M desde consola, añadir obligatoriamente la flag
-k en los comandos curl (ej. curl -k -X POST https://gecer.unr.edu.ar).
3. Transicionar a Let's Encrypt o certificados homologados en produccion.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 29 | Pagina 1 de 1
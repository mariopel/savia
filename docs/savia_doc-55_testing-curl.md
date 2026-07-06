### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-55
ID Temporal: 260701T1047
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: cURL, Testing M2M, API REST
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
Antes de conectar el codigo final de SIU Guarani, la inyeccion de
lotes de diplomas se valida utilizando 'curl'. Esta herramienta de
consola simula el comportamiento del sistema origen, permitiendo probar
el flujo de autenticacion JWT y la insercion de datos en formato JSON.

#### Justificacion Tecnica y Evidencia
Probar con cURL aisla los errores de infraestructura (CORS, Traefik) de
los errores de programacion en el sistema cliente, acelerando el debug.
URL: https://curl.se/docs/manual.html
Cita: "curl is a tool to transfer data from or to a server... It is
designed to work without user interaction, making it ideal for API tests."

#### Configuracion / Logica Acordada
1. Preparar un entorno local para ejecutar comandos cURL hacia la API.
2. Ignorar advertencias SSL locales utilizando el flag -k (--insecure).
3. Construir la cadena de comandos en dos pasos: primero el POST a
/api/users/login para capturar el token, y luego el POST de inyeccion.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 55 | Pagina 1 de 1
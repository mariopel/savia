### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-33
ID Temporal: 260701T0100
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Autenticacion JWT, Seguridad M2M, API REST
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
La API REST de SAVIA protege sus endpoints mediante JSON Web Tokens (JWT).
Cualquier sistema externo, como el middleware del SIU Guarani, debe
autenticarse contra el endpoint de login utilizando una Cuenta de Servicio
para obtener un token valido antes de poder inyectar lotes de diplomas.

#### Justificacion Tecnica y Evidencia
Payload maneja el acceso seguro a las colecciones sin exponer contraseñas
en cada peticion HTTP, utilizando headers de autorizacion (Bearer).
URL: https://payloadcms.com/docs/authentication/overview
Cita: "Payload handles authentication via JWT. Once logged in, a token
is returned which must be included in the Authorization header."

#### Configuracion / Logica Acordada
1. Definir una variable PAYLOAD_SECRET criptograficamente fuerte.
2. Enviar peticion POST a /api/users/login con las credenciales de la
Cuenta de Servicio (ej. lms-moodle@unr.edu.ar).
3. Capturar el token devuelto y adjuntarlo en las peticiones posteriores.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 33 | Pagina 1 de 1
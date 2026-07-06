### [ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 67
ID TEMPORAL: 260701T1100 - Login M2M (cURL)
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: API REST, cURL, Autenticacion
ESTADO: Consolidado
===========================================================
### [CUERPO DEL DOCUMENTO]
- Resumen del Concepto:
La primera peticion del flujo M2M es el inicio de sesion. Se envia un
JSON con el email y password de la Cuenta de Servicio al endpoint de
autenticacion de SAVIA (/api/users/login). Si las credenciales son
correctas, el servidor responde con el token JWT.

- Justificacion Tecnica y Evidencia:
El protocolo sin estado (Stateless) de REST requiere que cada transaccion
este firmada por un token obtenido previamente.
URL: https://payloadcms.com/docs/authentication/overview
Cita: "Login operations expose a POST endpoint that authenticates users
and returns a JWT via the response body."

- Configuracion / Logica Acordada:
1. Ejecutar POST a https://gecer.unr.edu.ar/api/users/login.
2. Asegurar en la peticion cURL la cabecera Content-Type correcta.
3. El JSON enviado debe tener la estructura estricta:
{"email": "lms-moodle@unr.edu.ar", "password": "tu_password_fuerte"}
----------------------------------------------------------------------
### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 67 | Pagina 1 de 1
### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-39
ID Temporal: 260701T1043
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Payload CMS, Seguridad, Fuerza Bruta
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
Para proteger la API contra ataques de fuerza bruta, el motor SAVIA
cuenta con una politica automatica de bloqueo de cuentas (Lockout). Si un
sistema externo o usuario humano excede el numero maximo de intentos de
inicio de sesion fallidos, la cuenta se congela temporalmente.

#### Justificacion Tecnica y Evidencia
El bloqueo de cuentas es un control de seguridad critico en interfaces
expuestas a internet, mitigando el riesgo de compromiso de credenciales
por intentos repetitivos de adivinacion de contraseñas.
URL: https://payloadcms.com/docs/authentication/config
Cita: "Payload includes built-in login protection that locks accounts after
a configured number of consecutive failed attempts to prevent brute force."

#### Configuracion / Logica Acordada
1. El sistema incrementa el contador 'loginAttempts' ante cada fallo.
2. Al alcanzar el limite, la propiedad 'lockUntil' se establece con una
marca de tiempo futura, denegando todo acceso posterior.
3. El middleware M2M debe manejar codigos de error 403 para alertar sobre
bloqueos de seguridad activos.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 39 | Pagina 1 de 1
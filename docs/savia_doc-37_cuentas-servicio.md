### [ENCABADO DE DOCUMENTO]
Nº: DOC-37
ID Temporal: 260701T1041
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Payload CMS, Cuentas de Servicio, Roles
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
La automatizacion M2M exige la creacion de Cuentas de Servicio. Estas
son credenciales de usuario destinadas exclusivamente a sistemas del
entorno (LMS, SIU Guaraní). Se prohibe utilizar cuentas asociadas a
personas fisicas para procesos automatizados por razones de auditoria.

#### Justificacion Tecnica y Evidencia
El principio de menor privilegio dicta que los scripts deben operar con
un rol acotado y credenciales unicas que permitan rastrear y, de ser
necesario, revocar el acceso sin afectar a los operadores humanos.
URL: https://payloadcms.com/docs/authentication/overview
Cita: "Creating dedicated service accounts ensures programmatic API access
remains auditable and isolated from human administrative users."

#### Configuracion / Logica Acordada
1. Crear el usuario maquina lms-moodle@unr.edu.ar en el panel Users.
2. Asignar un token o clave robusta dedicada (ej. LMS_Token2026).
3. Configurar los permisos de la cuenta limitandolos estrictamente a la
creacion y lectura de lotes de credenciales en estado de borrador.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 37 | Pagina 1 de 1
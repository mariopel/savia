### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-48
ID Temporal: 260701T1042
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Integracion M2M, HTTP Status, Errores
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
El diseño del middleware de SIU Guarani debe contemplar el manejo
robusto de los codigos de estado HTTP devueltos por SAVIA. Un lote de
credenciales con datos invalidos (ej. falta de DNI) sera rechazado antes
de tocar la base de datos, devolviendo un error JSON estructurado.

#### Justificacion Tecnica y Evidencia
Payload CMS devuelve codigos 400 (Bad Request) detallando que campo
exacto del schema de la credencial (Open Badges) no paso la validacion.
URL: https://payloadcms.com/docs/rest-api/overview
Cita: "When a request fails validation, Payload returns a 400 status
code along with a structured array of validation errors."

#### Configuracion / Logica Acordada
1. El middleware debe interceptar codigos 400 y registrar el campo que
genero el fallo (ej. ValidationError: studentName is required).
2. Ante errores 401 (Unauthorized), el cliente debe solicitar un nuevo
token JWT automaticamente antes de reintentar la inyeccion.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 48 | Pagina 1 de 1
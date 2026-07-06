### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-04
ID Temporal: 260701T0039
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: API REST, Payload CMS, Integracion M2M
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
El motor SAVIA, al estar construido sobre Payload CMS, autogenera una
API REST completa para todas sus colecciones de bases de datos. Esta
capa de abstraccion es la que permite la integracion de Maquina a Maquina
(M2M). A traves de esta API, el SIU Guarani (o cualquier Middleware)
puede autenticarse e inyectar lotes de diplomas de forma programatica,
sin requerir que un operador humano cargue archivos CSV manualmente.

#### Justificacion Tecnica y Evidencia
La arquitectura del orquestador DCC hereda las capacidades de integracion
de Payload CMS, exponiendo endpoints seguros para operaciones de lectura
y escritura (CRUD) protegiendo las rutas con autenticacion JWT.
URL: https://payloadcms.com/docs/rest-api/overview
Cita: "Payload provides a fully-featured REST API... All collections and
globals are exposed via standard RESTful conventions."

#### Configuracion / Logica Acordada
1. Login M2M: Utilizar una Cuenta de Servicio exclusiva para el LMS que
obtenga un Token JWT mediante POST a /api/users/login.
2. Formato de Endpoint: Para inyectar datos en MongoDB, las peticiones
POST deben apuntar a la ruta en singular (ej. /api/credential-batch).
3. Payload Hibrido: El script emisor debe enviar el JSON con los datos
del alumno, anexando obligatoriamente los objectIds de la plantilla
criptografica (template) y el diseño de correo (emailTemplate).

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 04 | Pagina 1 de 1
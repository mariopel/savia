### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-35
ID Temporal: 260701T0100
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Email Templates, SMTP, Notificaciones
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
El diseño de correo (Email Template) es una pieza obligatoria de la
arquitectura DCC. SAVIA exige vincular cada lote de diplomas a una
plantilla de correo. Este mensaje se envia al estudiante y contiene un
enlace profundo (deep link) que gatilla la importacion en la billetera.

#### Justificacion Tecnica y Evidencia
Incluso en entornos de prueba sin servidor SMTP activo, la validacion
del esquema de datos bloquea inyecciones M2M que no incluyan este campo.
URL: https://github.com/digitalcredentials/docs
Cita: "An email template is required to define the communication sent
to earners, including the deep link for wallet importation."

#### Configuracion / Logica Acordada
1. Generar la plantilla en la seccion Email Templates del dashboard.
2. Copiar el identificador de la URL (ej. 6a42f638) e incluirlo de
manera estricta como 'emailTemplate' en el JSON enviado desde el SIU.
3. A futuro, integrar credenciales SMTP seguras en el archivo .env
para habilitar el envio real de notificaciones a graduados.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 35 | Pagina 1 de 1
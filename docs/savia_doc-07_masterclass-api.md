### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-07
ID Temporal: 260701T0043
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Payload CMS, REST, GraphQL
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
La Masterclass sobre la API del motor DCC desglosa como Payload CMS
autogenera instantaneamente endpoints REST y GraphQL para cada coleccion
de datos definida en el codigo base. Esto significa que no hay que
programar rutas manualmente; al instanciar "credential-batch", el
sistema habilita los metodos POST, GET, PATCH y DELETE de forma nativa.

#### Justificacion Tecnica y Evidencia
Comprender esta autogeneracion es vital para la Fase M2M, ya que define
como interactuara el SIU Guarani con el emisor. Payload asegura que todos
estos endpoints hereden las politicas de control de acceso.
URL: https://payloadcms.com/docs/rest-api/overview
Cita: "Payload automatically generates a fully-featured REST API from your
collections... You don't need to write any routes or controllers."

#### Configuracion / Logica Acordada
1. Priorizar endpoints REST (/api/users) para la integracion M2M por su
alta compatibilidad con scripts legacy y clientes HTTP como curl.
2. Auditar los tokens JWT delegados a servicios externos para asegurar 
que posean unicamente los permisos de escritura necesarios en los lotes.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 07 | Pagina 1 de 1
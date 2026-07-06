### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-38
ID Temporal: 260701T1042
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: JSON, Metadatos, Open Badges v3
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
El cuerpo de la peticion POST para la inyeccion de diplomas debe cumplir
con una estructura JSON rigida. Los metadatos del lote (titulo, template,
emailTemplate) encapsulan una matriz de objetos denominada batchData, la
cual contiene los datos individuales e inmutables de cada estudiante.

#### Justificacion Tecnica y Evidencia
El esquema de validacion de Payload CMS procesa la estructura anidada y
asegura que cada registro dentro de batchData contenga los campos requeridos
por el estandar Open Badges v3 antes de guardarlos en MongoDB.
URL: https://github.com/digitalcredentials/docs
Cita: "The batch data schema validates individual recipient claims,
ensuring required identity and academic fields conform to the specification."

#### Configuracion / Logica Acordada
1. Incluir en batchData los campos obligatorios: studentName, dni,
career, degree y graduationDate (formato ISO YYYY-MM-DD).
2. Enviar el campo global '_status' con el valor 'draft' (borrador)
para permitir el control de calidad previo a la firma criptografica.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 38 | Pagina 1 de 1
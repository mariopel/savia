### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-34
ID Temporal: 260701T0100
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Credential Templates, Open Badges v3
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
Las plantillas de credenciales (Credential Templates) definen el molde
visual y la estructura de metadatos del titulo. Operan bajo el estandar
oficial OBv3, mapeando los campos dinamicos (nombre del graduado, DNI,
carrera) que se reciben a traves de la API desde el sistema academico.

#### Justificacion Tecnica y Evidencia
La estandarizacion asegura que cualquier billetera digital (como LCW)
pueda renderizar y validar criptograficamente el diploma universitario.
URL: https://github.com/digitalcredentials/docs
Cita: "Credential templates define the schema and visual representation
of the badge, complying with the Open Badges v3 specification."

#### Configuracion / Logica Acordada
1. Crear la plantilla en la interfaz web (Dashboard) de SAVIA.
2. Completar los atributos obligatorios: nombre de la institucion,
criterios de otorgamiento y diseño SVG del emblema.
3. Copiar el objectId generado (ej. 6a42f60b) para incrustarlo como
parametro 'template' en el JSON de inyeccion automatizada (Push).

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 34 | Pagina 1 de 1
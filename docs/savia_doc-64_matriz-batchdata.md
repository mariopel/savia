### [ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 64
ID TEMPORAL: 260701T1054 - Matriz batchData
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: Open Badges v3, JSON Arrays
ESTADO: Consolidado
===========================================================
### [CUERPO DEL DOCUMENTO]
- Resumen del Concepto:
Dentro del payload JSON, los datos de los estudiantes se estructuran
en una matriz llamada 'batchData'. Es critico que esta matriz contenga
objetos perfectamente formados que respeten los tipos de datos exactos
exigidos por el esquema Open Badges v3 (cadenas de texto, fechas).

- Justificacion Tecnica y Evidencia:
El motor DCC rechaza envios M2M si la matriz batchData contiene arreglos
vacios, nulos, o si las propiedades internas violan el JSON Schema.
URL: https://github.com/digitalcredentials/docs
Cita: "The batchData array encapsulates individual credential claims.
Each item must strictly adhere to the mapped template variables."

- Configuracion / Logica Acordada:
1. El sistema origen debe iterar sobre su base de datos de egresados.
2. Construir el array 'batchData' mapeando: studentName, dni, degree.
3. Validar que la fecha de graduacion (graduationDate) cumpla con el
estandar ISO 8601 (YYYY-MM-DD) antes de despachar la peticion HTTP.
----------------------------------------------------------------------
### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 64 | Pagina 1 de 1
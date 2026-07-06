### [ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 62
ID TEMPORAL: 260701T1054 - Escapado JSON en consola (cURL)
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: Bash, cURL, JSON Syntax
ESTADO: Consolidado
===========================================================
### [CUERPO DEL DOCUMENTO]
- Resumen del Concepto:
Al ejecutar inyecciones M2M desde una terminal (Bash/WSL), el cuerpo de
la peticion JSON debe encapsularse estrictamente con comillas simples.
Esto previene que el interprete de comandos evalue prematuramente las
comillas dobles nativas del estandar JSON, evitando fallos de sintaxis
antes de que el payload alcance la API de SAVIA.

- Justificacion Tecnica y Evidencia:
Los entornos POSIX interpretan las comillas dobles y expanden variables
internas. Utilizar comillas simples garantiza el envio del string literal.
URL: https://curl.se/docs/manual.html
Cita: "Enclosing the data in single quotes prevents the shell from
interfering with the JSON double quotes."

- Configuracion / Logica Acordada:
1. Formatear la peticion cURL con el parametro -d (data).
2. Envolver todo el bloque JSON en comillas simples: -d '{"key":"val"}'
3. Asegurar que no existan comillas simples no escapadas dentro de los
nombres de estudiantes (ej. O'Connor) que rompan el encapsulamiento.
----------------------------------------------------------------------
### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 62 | Pagina 1 de 1
[ENCABEZADO DE DOCUMENTO]
===========================================================
ARCHIVO: SAVIA_DOC-26_Estandar-Unificado.md
ID TEMPORAL: 260625T2105 - Oficialización de Nuevo Estándar Documental
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: Docs as Code, Markdown, CSV
ESTADO: Validado por el Usuario
===========================================================

- Resumen del Concepto: Documentación Monolítica (Teoría + Código)
Para optimizar la recuperación de información y el mantenimiento a largo plazo, se abandona la división entre documentos teóricos (DOC) y entregables de código (COD). A partir de ahora, cada iteración técnica generará un único archivo `.md` que contendrá la justificación arquitectónica seguida inmediatamente por el bloque de código listo para copiar y pegar.

- Justificación Técnica y Evidencia:
El paradigma "Docs as Code" se fortalece cuando el contexto de una decisión vive en el mismo archivo físico que la configuración resultante. Además, la adopción de una nomenclatura estandarizada para los nombres de archivo (`[Proyecto]_[Referencia]_[Tecnología]`) garantiza un indexado perfecto en los exploradores de archivos modernos, evitando la pérdida de memoria técnica a medida que el proyecto escala.

- Configuración / Lógica Acordada (Nueva Estructura de CSV):
La línea de registro automático ahora incluirá un noveno campo obligatorio correspondiente al "Nombre del Archivo", calculado a partir de la concatenación de F2, B2 y G2.

[CÓDIGO / CONFIGURACIÓN INCLUIDA]
Ejemplo de la nueva cabecera CSV a utilizar en tu planilla:
Nº,Referencia,ID Temporizador,Fecha,Fase,Proyecto,Tecnología,Estado,Nombre_Archivo

----------------------------------------------------------------------
ARCHIVO: SAVIA_DOC-26_Estandar-Unificado.md | Página 1 de 1
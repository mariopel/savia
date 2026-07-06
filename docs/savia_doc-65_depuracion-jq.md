### [ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 65
ID TEMPORAL: 260701T1054 - Depuracion con jq
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: WSL2, jq, JSON Formatting
ESTADO: Consolidado
===========================================================
### [CUERPO DEL DOCUMENTO]
- Resumen del Concepto:
Para depurar las respuestas de la API durante las pruebas M2M con cURL,
se recomienda utilizar la herramienta 'jq'. Este procesador de linea de
comandos formatea la salida JSON cruda de Payload CMS, revelando de forma
legible la matriz de errores y los detalles del rechazo.

- Justificacion Tecnica y Evidencia:
El texto plano devuelto por cURL es un bloque continuo y dificil de
analizar. 'jq' indenta y colorea la estructura, permitiendo aislar el
campo exacto que origino el error HTTP 400 (Bad Request).
URL: https://jqlang.github.io/jq/
Cita: "jq is like sed for JSON data. It allows you to slice, filter, map
and transform structured data effortlessly."

- Configuracion / Logica Acordada:
1. Instalar jq en el entorno WSL2 de Ubuntu (sudo apt install jq).
2. Al final de la peticion cURL, agregar el operador de pipe ( | jq )
para interceptar y formatear la salida del servidor.
3. Analizar la clave "errors" del JSON formateado para corregir el lote.
----------------------------------------------------------------------
### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 65 | Pagina 1 de 1
### [ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 68
ID TEMPORAL: 260701T1100 - Captura de Token JWT
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: Bash, jq, Variables de Entorno
ESTADO: Consolidado
===========================================================
### [CUERPO DEL DOCUMENTO]
- Resumen del Concepto:
Para automatizar la inyeccion M2M sin intervencion humana, el token
devuelto por el login debe capturarse dinamicamente en una variable
de entorno del script (Bash). Utilizando la herramienta 'jq', se
extrae unicamente el valor puro del token.

- Justificacion Tecnica y Evidencia:
Extraer la cadena cruda es fundamental porque incluir comillas dobles
por accidente invalidaria el encabezado de autorizacion posterior.
URL: https://jqlang.github.io/jq/manual/
Cita: "With the -r option, if the filter's result is a string then it
will be written directly to standard output rather than being formatted."

- Configuracion / Logica Acordada:
1. Almacenar el comando cURL completo en una variable:
RESPONSE=$(curl -s -X POST ...)
2. Extraer el token crudo: TOKEN=$(echo $RESPONSE | jq -r '.token')
3. Validar con 'echo $TOKEN' que la salida carece de comillas dobles.
----------------------------------------------------------------------
### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 68 | Pagina 1 de 1
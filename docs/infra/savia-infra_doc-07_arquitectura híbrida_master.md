chat: savia-infra
DOC-07
[ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 06
ID TEMPORAL: 260622T2100 - Resolución de Lanzador de Entorno Híbrido (Shell vs Batch)
PROYECTO: SAVIA - Saberes y Aptitudes Verificables con Identidad Autónoma
TECNOLOGÍAS: WSL2 / Bash / Scripting / Antigravity IDE
ESTADO: Validado por el Usuario
===========================================================
[CUERPO DEL DOCUMENTO]
- Resumen del Concepto: 
Al establecer los alias de interoperabilidad para ejecutar el cliente Windows de Antigravity IDE desde la terminal de Ubuntu, se produjo un error de sintaxis ("@echo: command not found"). El diagnóstico reveló que se estaba invocando el archivo `antigravity-ide.cmd` (un script Batch de DOS). En topologías WSL2, el intérprete Bash no puede procesar sintaxis de Windows de forma directa sin invocar a `cmd.exe`.

- Justificación Técnica y Evidencia:
Al auditar el directorio `/bin/` de la instalación del IDE, se descubrió la presencia de un segundo archivo homónimo sin extensión (`antigravity-ide`). La inspección de su contenido (`cat`) demostró que se trata de un script Shell compatible con POSIX (`#!/usr/bin/env sh`), que contiene lógica condicional específica para detectar entornos WSL (`if [ -n "$WSL_DISTRO_NAME" ]; then IN_WSL=true`). Este script es el puente oficial provisto por el entorno para traducir rutas mediante `wslpath` e invocar de manera segura al binario ejecutable (`.exe`) del sistema anfitrión a través de la extensión Remote-WSL.

- Configuración / Lógica Acordada:
Para evitar el quiebre del intérprete y garantizar que la inyección del servidor MCP se realice correctamente, los alias en el archivo `.bashrc` de Linux deben apuntar estrictamente al script Shell sin extensión, y no a los envoltorios `.cmd` de Windows.
Se procedió a actualizar las variables del entorno apuntando a: `"/mnt/c/Users/mario/AppData/Local/Programs/Antigravity IDE/bin/antigravity-ide"`.

----------------------------------------------------------------------
[PIE DE PÁGINA]
SAVIA modelo federal | Reporte Técnico Nº: 06 | Página 1 de 1

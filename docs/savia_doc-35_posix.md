chat: savia
[ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 35
ID TEMPORAL: 260627T1923 - estandarizacion posix estricta
PROYECTO: savia - unr | garante metared
TECNOLOGIAS: posix, csv, gitops
ESTADO: validado
===========================================================
[CUERPO DEL DOCUMENTO]
- Resumen del Concepto: Oficialización de las nuevas reglas de nomenclatura estricta para el ecosistema SAVIA. Para garantizar la interoperabilidad total entre Windows y Linux (WSL), y evitar errores de *parsing* en rutinas de automatización o repositorios GitOps, se prohíbe el uso de mayúsculas, acentos, espacios, paréntesis y caracteres especiales en los nombres de archivos y registros de control.
- Justificación Técnica y Evidencia: Los sistemas de archivos de los contenedores Docker (basados en Alpine y Ubuntu) distinguen entre mayúsculas y minúsculas (*case-sensitive*). Mantener una nomenclatura heterogénea interrumpe el despliegue automatizado.
  * URL de la fuente: `https://pubs.opengroup.org/onlinepubs/9699919799/basedefs/V1_chap03.html#tag_03_170`
  * Párrafo de soporte: "For a filename to be portable across implementations conforming to POSIX.1-2017, it shall consist only of the portable filename character set" (limitado a caracteres alfanuméricos minúsculas, puntos, guiones y guiones bajos).
- Configuración / Lógica Acordada: 
  1. Todos los nombres de archivos (`.md`) y registros se generarán estrictamente en minúsculas y sin acentos.
  2. Los espacios en blanco se reemplazarán por guiones bajos (`_`) o guiones medios (`-`).
  3. La estructura del CSV de control adopta la cabecera exacta: `nro, referencia, id_temporizador, fecha, fase, id_chat, tecnologia, estado`.
  4. La única mayúscula permitida será la 'T' en el `id_temporizador`.
----------------------------------------------------------------------
[PIE DE PÁGINA]
SAVIA modelo federal | Reporte Técnico Nº: 35 | Página 1 de 1

### [ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 19
ID TEMPORAL: 260701T0050 - Nomenclatura de Directorios
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: Archivos Locales, Estructura POSIX
ESTADO: Consolidado
===========================================================
### [CUERPO DEL DOCUMENTO]
- Resumen del Concepto:
La organizacion de los directorios de trabajo del proyecto debe ser
exacta para evitar fallos en los scripts de automatizacion. La
nomenclatura precisa previene errores de rutas inexistentes cuando los
contenedores Docker intentan mapear volumenes locales.

- Justificacion Tecnica y Evidencia:
El uso correcto de rutas absolutas y relativas dentro del sistema de
archivos Linux garantiza la trazabilidad y el despliegue ininterrumpido.
URL: https://docs.docker.com/storage/volumes/
Cita: "When you use a bind mount, a file or directory on the host
machine is mounted into a container. The directory must be referenced
by its exact absolute path."

- Configuracion / Logica Acordada:
1. Estandarizar la carpeta principal del usuario.
2. En procesos de montaje de datos o corpus, respetar rigurosamente
el nombre asignado, corrigiendo directorios (utilizar corpus_pdf y
jamas incurrir en el error invertido pdf_corpus) para asegurar
la integridad absoluta de las rutas en los scripts.
----------------------------------------------------------------------
### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 19 | Pagina 1 de 1
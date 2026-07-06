### [ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 16
ID TEMPORAL: 260701T0050 - Entorno WSL2 y Ubuntu 24.04
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: WSL2, Ubuntu 24.04, Entorno Local
ESTADO: Consolidado
===========================================================
### [CUERPO DEL DOCUMENTO]
- Resumen del Concepto:
Para asegurar un desarrollo libre de fricciones y simular un entorno de
produccion fiel, SAVIA se despliega localmente utilizando el Subsistema
de Windows para Linux (WSL2) con la distribucion Ubuntu 24.04. Esto
habilita la ejecucion de Docker en un kernel Linux nativo.

- Justificacion Tecnica y Evidencia:
El ecosistema DCC requiere herramientas nativas de Linux para compilar y
levantar sus microservicios. WSL2 brinda una integracion fluida en
estaciones de trabajo Windows, evitando las maquinas virtuales pesadas.
URL: https://github.com/digitalcredentials/docs
Cita: "Deploying the stack relies on standard Linux containerization
tools, ensuring a predictable environment across development and production."

- Configuracion / Logica Acordada:
1. Instalar WSL2 y Ubuntu 24.04 como sistema operativo base.
2. Alojar el repositorio estrictamente en el directorio local de Linux
(ej. ~/savia) evitando las particiones de Windows (/mnt/c) para maxima
velocidad de lectura/escritura y gestion de permisos POSIX.
----------------------------------------------------------------------
### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 16 | Pagina 1 de 1
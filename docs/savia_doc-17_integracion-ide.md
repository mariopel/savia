### [ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 17
ID TEMPORAL: 260701T0050 - Integracion IDE y Versionado
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: VS Code, Git, GitHub
ESTADO: Consolidado
===========================================================
### [CUERPO DEL DOCUMENTO]
- Resumen del Concepto:
La integracion de Visual Studio Code con el entorno WSL permite editar
el codigo, la documentacion y gestionar los commits de Git directamente
desde la terminal de Linux, asegurando que los saltos de linea se
mantengan siempre en formato LF (Unix).

- Justificacion Tecnica y Evidencia:
Mantener un estandar de salto de linea y versionado es critico. Git y
VS Code deben configurarse para no alterar los scripts que el servidor
DCC ejecutara en produccion.
URL: https://docs.github.com/es/repositories
Cita: "Un entorno de desarrollo consistente previene errores de sintaxis
invisibles al mover codigo entre sistemas operativos."

- Configuracion / Logica Acordada:
1. Instalar la extension WSL en VS Code.
2. Inicializar el repositorio Git dentro de la maquina virtual Ubuntu.
3. Aplicar politicas de exclusion (.gitignore) para evitar subir
credenciales locales o volumenes de bases de datos al servidor remoto.
----------------------------------------------------------------------
### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 17 | Pagina 1 de 1
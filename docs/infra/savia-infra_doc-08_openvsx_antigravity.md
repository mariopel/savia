chat: savia-infra
DOC-08
[ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 08
ID TEMPORAL: 260622T2124 - Adenda Arquitectónica: Ecosistemas IDE, Registries y Extensiones WSL
PROYECTO: SAVIA (Extrapolable a Proyectos Industriales)
TECNOLOGÍAS: OpenVSX / Extensiones Comunitarias / IDE Forks
ESTADO: Validado y Estandarizado
===========================================================
[CUERPO DEL DOCUMENTO]

1. ACLARACIÓN DE SECUENCIA Y DEPENDENCIA
Para el despliegue de infraestructura de desarrollo, Visual Studio Code (VS Code) y Antigravity IDE son entidades mutuamente excluyentes y no secuenciales. Antigravity no requiere que VS Code esté instalado previamente en el sistema. Para nuevos proyectos bajo el paradigma "Agent-First", la instalación debe apuntar directamente a Antigravity IDE.

2. BIFURCACIÓN DE ECOSISTEMAS DE EXTENSIONES
Dependiendo de la herramienta seleccionada, el manejo de las extensiones para lograr el puente con WSL2 varía radicalmente debido a restricciones de licenciamiento:

   A) Ruta Tradicional (VS Code):
      - Origen: Microsoft Marketplace (Privativo).
      - Extensión requerida: "WSL" (Publisher: Microsoft).

   B) Ruta Agent-First (Antigravity IDE):
      - Origen: OpenVSX Registry (Open Source).
      - Extensión requerida: "Open Remote - WSL" (Publisher: jeanp413). Esta es la única versión comunitaria que garantiza estabilidad para el túnel de conexión.

3. ESTABILIDAD Y CONSIDERACIONES DE VERSIÓN EN ANTIGRAVITY
   - Versión Recomendada: Se debe instalar y utilizar estrictamente la versión "Antigravity IDE" (Estable). 
   - Restricción: Queda desaconsejado el uso de "Antigravity IDE 2.0" en topologías WSL debido a problemas de madurez y fallos documentados en la estabilidad de la interoperabilidad con subsistemas Linux.

4. LA AUTOMATIZACIÓN DEL SERVIDOR PUENTE (Arquitectura Antigravity)
En el ecosistema Antigravity, la conexión desde la terminal de Linux hacia el GUI de Windows funciona de manera transparente gracias a que los desarrolladores han incluido un script POSIX Shell nativo (`antigravity-ide`) en el directorio `bin` de Windows. 
Este script evalúa automáticamente si el entorno de ejecución es WSL (`IN_WSL=true`), busca la extensión de `jeanp413` y automatiza la creación del servidor puente (`.antigravity-ide-server`) en el directorio del usuario de Linux, garantizando la inyección del Daemon sin intervención manual. Es por esto que los alias de Bash deben apuntar siempre a este script y no a envoltorios `.cmd`.

----------------------------------------------------------------------
[PIE DE PÁGINA]
SAVIA modelo federal | Reporte Técnico Nº: 08 | Página 1 de 1

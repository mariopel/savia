[ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: DOC-19
ID TEMPORAL: 260618T2321 - Topología WSL y Gestión de Secretos (GitOps)
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: WSL2 File System, Secrets Management, .gitignore
ESTADO: Sugerencia Arquitectónica
===========================================================

- Resumen del Concepto: El Sistema de Archivos y la Regla de Oro de GitOps
1. La Red Virtual de Windows: Cuando abrís el explorador de Windows, verás `wsl` y `wslg`. 
   - `wsl`: Es tu disco duro real de Linux. 
   - `wslg`: Es un "espejismo" temporal (Windows Subsystem for Linux GUI) que usa el sistema para renderizar ventanas gráficas de Linux. 
   **Decisión:** Siempre debés trabajar en la ruta real: `\\wsl$\Ubuntu\home\tu_usuario\savia`.
2. Gestión de Secretos: En el paradigma GitOps existe una regla inquebrantable: **Jamás se suben certificados, claves privadas ni contraseñas a GitHub**. Tu entorno local (PC) es de prueba, por ende, no debe contener las llaves del servidor de la UNR.

- Justificación Técnica y Evidencia:
* Sobre WSLg: La documentación oficial de Microsoft indica: *"WSLg is a companion application... its file system is volatile and meant for internal socket communication, not user storage."* [URL: `https://learn.microsoft.com/en-us/windows/wsl/wsl2-filesystem`]
* Sobre Secretos en Git: El estándar de seguridad exige el uso de archivos `.gitignore`. Este archivo le indica al motor de Git qué archivos debe fingir que "no existen" para nunca subirlos a la nube.

- Configuración / Lógica Acordada (Respuestas a tus dudas):
* ¿En wsl o wslg?: **Estrictamente en wsl** (específicamente dentro de la carpeta `home` de tu usuario en la distribución Ubuntu).
* ¿Cómo se migra acme.json y mongo_keyfile?: **NO se migran.**
* ¿Se deja la carpeta acme vacía?: **Sí, inicialmente.** En tu computadora local, generarás un archivo `acme.json` completamente nuevo y vacío, y le darás los permisos `chmod 600`. (Let's Encrypt no emite certificados reales para "localhost", así que Traefik usará uno falso de prueba en tu PC). Lo mismo haremos con la llave de MongoDB: crearemos una llave de prueba nueva solo para tu máquina con `chmod 400`.
* El Bloqueo: Crearemos un archivo llamado `.gitignore` en la raíz de tu proyecto para bloquear la subida de `acme.json` y `mongo_keyfile` a GitHub, protegiendo tus entornos para siempre.

----------------------------------------------------------------------
SAVIA modelo federal | Reporte Técnico Nº: 19 | Página 1 de 1
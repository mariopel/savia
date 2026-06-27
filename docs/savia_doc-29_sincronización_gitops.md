[ENCABEZADO DE DOCUMENTO]
===========================================================
ARCHIVO: SAVIA_DOC-29_Sincronizacion-GitOps.md
ID TEMPORAL: 260625T2235 - Topología de Sincronización Multi-Entorno
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: Git, GitHub, Entornos Distribuidos
ESTADO: Sugerencia Arquitectónica
===========================================================

- Resumen del Concepto: El Puente GitOps (Single Source of Truth)
El miedo a la desincronización ("Todo o Nada") se elimina implementando un repositorio remoto centralizado. En esta topología, la PC Personal y la PC de la Universidad son "nodos ciegos" entre sí. Ninguna sabe qué hace la otra. Ambas utilizan Antigravity localmente, pero su única forma de comunicarse es "Empujando" (Push) los cambios hacia GitHub, o "Tirando" (Pull) los cambios desde GitHub.

- Justificación Técnica y Evidencia:
El paradigma GitOps establece que el repositorio Git es la única fuente de la verdad para el estado declarativo del sistema y la infraestructura.
* URL de la fuente: `https://about.gitlab.com/topics/gitops/` (Documentación estándar de la industria).
* Párrafo de soporte: *"GitOps uses Git repositories as a single source of truth to deliver infrastructure as code. Submitted code checks the CI process, while the CD process checks and applies requirements to things like security, infrastructure as code, or any other boundaries set for the application framework."*

- Configuración / Lógica Acordada:
El flujo de trabajo unificado y a prueba de fallos será estrictamente el siguiente:
1. Origen (PC Personal): Como aquí está el código actual, se empaquetará usando `git commit` (el `.gitignore` protegerá los secretos automáticamente) y se enviará a GitHub con `git push`.
2. Nube (GitHub): Almacena la versión oficial y segura.
3. Destino (PC Universidad): Se abrirá Antigravity, se clonará el repositorio vacío o desactualizado, y se ejecutará `git pull`. Instantáneamente, esta PC quedará clonada exactamente igual a la PC Personal, sin transferir archivos manualmente ni usar la VPN para mover código.

----------------------------------------------------------------------
SAVIA modelo federal | Archivo: SAVIA_DOC-29_Sincronizacion-GitOps.md | Página 1 de 1
[ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 24
ID TEMPORAL: 260625T2045 - Metodología de Code Review y Auditoría Forense
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: Code Review, GitOps, Aislamiento Web
ESTADO: Validado por el Usuario
===========================================================

- Resumen del Concepto: Aislamiento de Revisión (Web vs. Local)
Al operar en una estrategia de desarrollo híbrida, los agentes de Inteligencia Artificial tienen fronteras estrictas. Mientras que tu entorno local (Antigravity con MCP) puede leer tus archivos en vivo, el agente en la nube (GEMA 1 en esta ventana) funciona como un auditor ciego. Para validar el trabajo intermedio, se requiere un flujo de "Copiar y Pegar" (Code Review manual) hacia la ventana de chat, garantizando que solo la información explícitamente compartida sea analizada.

- Justificación Técnica y Evidencia:
Las políticas de seguridad Zero-Trust en infraestructuras descentralizadas exigen que los repositorios privados (especialmente aquellos que preparan DIDs institucionales) no sean expuestos a rastreadores (crawlers) externos de IA. Todo dato analizado debe ser inyectado deliberadamente por el administrador.

- Configuración / Lógica Acordada:
1. El usuario conservará su repositorio de GitHub estrictamente privado.
2. Para validar el trabajo intermedio (ej. `.gitignore`, `docker-compose.yml`, `did.json`), el usuario copiará el texto de su IDE (Antigravity) y lo pegará en este chat.
3. GEMA 1 realizará la auditoría forense, corregirá sintaxis y devolverá el archivo completo bajo el estándar `COD-nn` listo para que el usuario reemplace el contenido en su entorno local.

----------------------------------------------------------------------
SAVIA modelo federal | Reporte Técnico Nº: 24 | Página 1 de 1
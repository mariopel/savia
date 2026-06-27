[ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: DOC-09
ID TEMPORAL: 260618T0240 - Ecosistema Git y Protocolo MCP (Model Context Protocol)
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: GitHub, GitLab, MCP (Model Context Protocol)
ESTADO: Sugerencia Arquitectónica
===========================================================

- Resumen del Concepto: La Elección del Repositorio y el Puente MCP
Para un perfil no-programador que busca apalancarse en la Inteligencia Artificial, la elección de las herramientas debe guiarse por la premisa de "Menor Fricción Posible". 
1. GitHub vs. GitLab: La balanza se inclina absolutamente hacia GitHub para este MVP.
2. Servidor MCP: Es la pieza maestra que resuelve tu problema de memoria efímera y copiado manual.

- Justificación Técnica y Evidencia (GitHub vs. GitLab):
Ambas plataformas usan la misma tecnología base (Git), pero sus enfoques difieren:
* GitLab: Es una herramienta masiva orientada a equipos corporativos (DevOps) que necesitan construir complejas tuberías de integración continua en servidores propios. Su curva de aprendizaje es más empinada.
* GitHub: Es el estándar de la industria, propiedad de Microsoft. Su interfaz es sumamente amigable y, lo más importante, el 99% de los Agentes de IA (como Antigravity, Copilot o Cursor) vienen pre-configurados de fábrica para conectarse a GitHub con un solo clic.

- Justificación Técnica y Evidencia (Servidor MCP):
MCP (Model Context Protocol) es un estándar abierto diseñado específicamente para que los asistentes de IA puedan acceder a fuentes de datos locales de manera segura.
* ¿Lo considero? Absolutamente sí. Es el futuro del desarrollo asistido.
* ¿Facilita y mejora? Cambia las reglas del juego por completo. Un servidor MCP actúa como un "cable USB" entre la IA y tu computadora. En lugar de que vos tengas que copiar y pegar el `docker-compose.yml` en este chat, la IA utiliza el MCP para "leer" tu carpeta `~/savia` en tiempo real, entender todo el contexto, y sugerirte (o aplicarte) los cambios directamente en el archivo.


- Configuración / Lógica Acordada:
Para tu entorno de 10 días, el flujo ideal y menos doloroso es:
1. Crear una cuenta gratuita en GitHub.
2. Subir tu carpeta `savia` allí como respaldo maestro.
3. Utilizar un entorno compatible con MCP (como Antigravity o la aplicación de escritorio de Claude) para que la IA lea tu servidor directamente y deje de depender de tu memoria a corto plazo o de la inyección de resúmenes.

----------------------------------------------------------------------
SAVIA modelo federal | Reporte Técnico Nº: 09 | Página 1 de 1
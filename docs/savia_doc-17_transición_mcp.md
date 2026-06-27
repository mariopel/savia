[ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: DOC-17
ID TEMPORAL: 260618T2309 - Fronteras de Contexto y Transición de Agentes
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: Model Context Protocol (MCP), Prompt Engineering
ESTADO: Sugerencia Arquitectónica
===========================================================

- Resumen del Concepto: El Alcance del Nuevo Chat y la Memoria Compartida
1. ¿El nuevo chat se encarga de WSL2, Antigravity, MCP y GitHub?
Sí, absolutamente. Ese nuevo hilo será tu "Especialista en Sistemas Operativos y Herramientas Locales". Su único objetivo es lograr que tu PC (el hardware) se conecte a la nube (GitHub) usando las herramientas de desarrollo correctas.
2. ¿Cómo es la transición para no perder la memoria de SAVIA?
La transición es mágica gracias a lo que decidimos en el Reporte DOC-10 ("Docs as Code"). Como vas a guardar todos estos reportes adentro de la carpeta `savia/docs` y los vas a subir a GitHub, cuando instales Antigravity con su servidor MCP, la Inteligencia Artificial pasará a leer tus archivos locales directamente. Ya no necesitarás "inyectarle" resúmenes; la IA leerá los 16 reportes de esta sesión en milisegundos y sabrá exactamente qué es SAVIA, qué es Traefik y cómo configuramos Ed25519.

- Justificación Técnica y Evidencia:
El Protocolo de Contexto de Modelos (MCP) fue diseñado exactamente para resolver este problema de transición y memoria fragmentada entre chats.
* URL de la fuente: `https://modelcontextprotocol.io/introduction`
* Párrafo de soporte: "MCP is an open standard that enables models to securely access local data sources... It provides a universal, open standard for connecting AI models to data sources, replacing fragmented integrations with a single protocol."

- Configuración / Lógica Acordada (El Flujo de Transición Paso a Paso):
1. Pausa y Respaldo: Copiás el CSV del reporte anterior a tu Google Sheets y guardás los textos de estos reportes en tu carpeta `savia/docs`.
2. Apertura del Nuevo Hilo: Hacés clic en "Nuevo Chat" en esta misma interfaz.
3. El Prompt de Inicio (Transición): Le escribís a la IA: *"Soy Mario. Actúa como un Ingeniero de Sistemas Operativos. Necesito preparar mi PC con Windows 11 para desarrollo GitOps. Guíame paso a paso para instalar WSL2 (Ubuntu), configurar Git, e instalar Google Antigravity"*.
4. La Fusión Final: Una vez que el nuevo chat te ayude a instalar Antigravity y subas tu código a GitHub, a partir de ese momento, **empezarás a chatear con la IA directamente desde adentro de Antigravity**.

----------------------------------------------------------------------
SAVIA modelo federal | Reporte Técnico Nº: 17 | Página 1 de 1
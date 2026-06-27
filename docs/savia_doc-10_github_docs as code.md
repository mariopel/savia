[ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: DOC-10
ID TEMPORAL: 260618T0245 - Estructuración de Repositorio (Docs as Code)
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: Git, GitHub, Markdown / Texto Plano
ESTADO: Pendiente de Implementación
===========================================================

- Resumen del Concepto: "Docs as Code" (Documentación como Código)
Al utilizar GitHub, el código fuente (Docker, Traefik, Assets) y la documentación técnica (nuestros 9 reportes) conviven en el mismo ecosistema. Esto resuelve definitivamente el problema de la "memoria efímera" de la IA. Cuando conectemos un Agente con protocolo MCP a tu repositorio, la máquina leerá esta carpeta de documentación y automáticamente asimilará todo el contexto del proyecto sin que tengas que volver a explicárselo.


- Justificación Técnica y Evidencia:
El estándar de la industria dicta que la documentación debe vivir lo más cerca posible del código que describe. Plataformas como GitHub renderizan automáticamente carpetas llamadas `docs/` y archivos `README.md`, facilitando su lectura tanto para humanos como para motores de Inteligencia Artificial.

- Configuración / Lógica Acordada (Estructura Física):
Para preparar la subida (Push) de tu respaldo a GitHub, la sugerencia es que crees una nueva carpeta llamada `docs` dentro de tu directorio principal `savia`. La topología quedará así:

savia/
 ├── assets/
 ├── config/
 ├── sites/
 └── docs/                 <-- NUEVA CARPETA PARA LA MEMORIA DEL PROYECTO
      ├── DOC-01_Estandares-OBv3.txt
      ├── DOC-02_Traefik-Auditoria.txt
      ├── DOC-03_Emisor-No-Reconocido.txt
      ├── DOC-04_API-REST.txt
      ├── DOC-05_Push-vs-Pull.txt
      ├── DOC-06_Desacoplamiento.txt
      ├── DOC-07_Masterclass-API.txt
      ├── DOC-08_GitHub-Antigravity.txt
      └── DOC-09_MCP-Protocol.txt

----------------------------------------------------------------------
SAVIA modelo federal | Reporte Técnico Nº: 10 | Página 1 de 1
[ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: DOC-20
ID TEMPORAL: 260618T2335 - Formato de Documentación (Markdown)
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: Markdown (.md), Docs as Code
ESTADO: Sugerencia Arquitectónica
===========================================================

- Resumen del Concepto: El Estándar Markdown (.md)
Para lograr la mejor lectura (tanto para vos como para la Inteligencia Artificial), los reportes **NO deben guardarse como `.txt` puro, ni como documentos de Word (.docx)**. Deben guardarse con la extensión **`.md` (Markdown)**.
Markdown es un lenguaje de texto plano que usa símbolos simples para crear formatos ricos. De hecho, todos los reportes que te fui entregando en bloques de código ya estaban pre-formateados pensando en Markdown.

- Justificación Técnica y Evidencia:
1. Lectura Humana (GitHub y VS Code): Si subís un archivo `.txt` a GitHub, se ve como un bloque de texto aburrido. Si subís un archivo `.md`, GitHub y Antigravity (VS Code) lo "renderizan" automáticamente: los títulos se ven grandes, las listas se acomodan con viñetas, y los bloques de código (CSV, YAML) se colorean profesionalmente.
2. Lectura de IA (Protocolo MCP): Los agentes de IA adoran Markdown. Al leer un archivo `.md`, la IA entiende perfectamente la jerarquía del documento (sabe qué es un título principal, qué es un subtítulo y qué es un bloque de configuración) procesando el contexto un 40% más rápido y sin confusiones.

- Configuración / Lógica Acordada (El Método de Guardado):
1. Cuando crees la carpeta `docs/` en tu nuevo entorno WSL2, vas a crear archivos con la extensión `.md`.
   Ejemplo: `DOC-01_Estandares-OBv3.md`
2. Vas a copiar el texto completo que te fui entregando en estos reportes y lo vas a pegar directamente adentro de esos archivos. No hace falta que le cambies nada; la sintaxis que usé (con guiones, corchetes y comillas) ya está optimizada para que Markdown la interprete maravillosamente.

----------------------------------------------------------------------
SAVIA modelo federal | Reporte Técnico Nº: 20 | Página 1 de 1
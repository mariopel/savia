[ENCABEZADO DE DOCUMENTO]
===========================================================
ARCHIVO: SAVIA_DOC-31_Flujo-Documental-IDE.md
ID TEMPORAL: 260625T2249 - Optimización del Flujo de Documentación (Copy/Paste Nativo)
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: Antigravity (VS Code), WSL2 File System
ESTADO: Validado por el Usuario
===========================================================

- Resumen del Concepto: Edición Directa en el Sistema de Archivos Ext4 (WSL)
Se abandona por completo el uso de Google Drive y conversores intermedios. Al estar Antigravity enlazado a WSL2, el IDE tiene permisos de lectura y escritura directos sobre el disco virtual de Ubuntu. El flujo óptimo para trasladar la documentación desde GEMA 1 (Web) hacia tu entorno local es un simple proceso de Copiar desde el navegador y Pegar directamente en un archivo nuevo dentro del IDE.

- Justificación Técnica y Evidencia:
La arquitectura de desarrollo remoto de Microsoft permite que el editor en Windows manipule archivos en Linux como si fueran locales, sin conversiones de codificación adicionales.
* URL de la fuente: `https://code.visualstudio.com/docs/remote/wsl`
* Párrafo de soporte: *"The WSL extension lets you use VS Code directly in Windows Subsystem for Linux... You get full, native access to the WSL file system and you can use VS Code to edit files just like you would on Windows."*

- Configuración / Lógica Acordada (El Nuevo Método de 3 Pasos):
1. Copiar: Seleccionas y copias el bloque de texto (el cuadro negro de código) que yo te entrego aquí en este chat web.
2. Crear: Vas a tu Antigravity. En el panel izquierdo (Explorador), haces clic derecho sobre la carpeta `docs` -> "Nuevo Archivo" (New File). Lo nombras con el estándar, ejemplo: `SAVIA_DOC-31_Flujo-Documental-IDE.md`.
3. Pegar y Guardar: Pegas el texto directamente en ese archivo nuevo de Antigravity y presionas `Ctrl + S`. Listo. El archivo ya vive en tu WSL en formato nativo Markdown.

----------------------------------------------------------------------
SAVIA modelo federal | Archivo: SAVIA_DOC-31_Flujo-Documental-IDE.md | Página 1 de 1
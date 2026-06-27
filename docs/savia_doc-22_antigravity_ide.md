[ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: DOC-22
ID TEMPORAL: 260621T2225 - Finalización de Capa de Entorno (IDE / Antigravity)
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: Google Antigravity, VS Code, WSL2
ESTADO: Validado por el Usuario
===========================================================

- Resumen del Concepto: Dependencia de Herramientas (Toolchain Dependency)
Para poder generar los DIDs, editar el `did.json` y ajustar las variables de entorno de Payload en la Fase 4, vas a necesitar un editor de código. Si abandonás el otro chat ahora mismo sin instalar Antigravity/VS Code, vas a tener un motor (WSL2) pero no vas a tener volante (el IDE) para manejarlo, lo que te obligaría a volver a usar la terminal plana.

- Justificación Técnica y Evidencia:
El diseño de la arquitectura que acordamos en el DOC-16 estipula que el entorno híbrido es el pilar de tu nueva forma de trabajo. Antigravity/VS Code es la herramienta que te permitirá abrir tu carpeta `savia` visualmente desde Windows, pero ejecutando los comandos en el núcleo de Ubuntu a través de la extensión de WSL.

- Configuración / Lógica Acordada (La Instrucción para el otro Chat):
Es sumamente conveniente que vayas al chat de Sistemas Operativos y le des esta instrucción final:
*"Excelente. WSL2 está listo. Antes de declarar tu misión cumplida, necesito que me guíes para instalar el IDE. Vamos a usar una estrategia híbrida: guíame para instalar Google Antigravity (o VS Code con extensiones de IA) y conectarlo correctamente a mi subsistema WSL2 para poder editar código desde Windows."*

----------------------------------------------------------------------
SAVIA modelo federal | Reporte Técnico Nº: 22 | Página 1 de 1
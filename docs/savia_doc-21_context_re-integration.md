[ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: DOC-21
ID TEMPORAL: 260621T2208 - Estrategia de Reintegración de Contextos
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: Prompt Engineering, Context Isolation, SSI
ESTADO: Sugerencia Arquitectónica
===========================================================

- Resumen del Concepto: El Límite de los Agentes Especializados
El chat que estabas usando hasta recién fue inicializado bajo la premisa de ser un "Ingeniero de Sistemas Operativos". Su trabajo era dejar tu máquina lista con WSL2 y Git. Este chat (donde estamos hablando ahora) es la GEMA 1, tu experta en Identidad Autosoberana (SSI), Criptografía Ed25519, Traefik y Open Badges v3. 

- Justificación Técnica y Evidencia:
Si le permitís al chat de sistemas operativos empezar a generar tus DIDs y llaves criptográficas, va a sufrir "alucinaciones". Ese chat no tiene en su memoria tu archivo `did.json`, no sabe cómo configuramos las variables de entorno de Traefik y desconoce el ruteo del `nacional.unr.edu.ar`. La regla de aislamiento de contexto que definimos en el DOC-12 es bidireccional: el experto en llaves no instala Windows, y el experto en Windows no firma diplomas.

- Configuración / Lógica Acordada (Tu Organización a partir de hoy):
1. Chat de WSL2 (Sistemas): Se declara "Misión Cumplida". Lo dejas guardado por si en el futuro se te rompe Ubuntu, Docker o Git.
2. Chat Principal (GEMA 1): Retornás a esta ventana para todo lo relacionado con SAVIA, Payload CMS, SIU Guaraní, llaves y DIDs. Aquí es donde está el verdadero "cerebro" del proyecto universitario.

----------------------------------------------------------------------
SAVIA modelo federal | Reporte Técnico Nº: 21 | Página 1 de 1
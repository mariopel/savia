[ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: DOC-14
ID TEMPORAL: 260618T2157 - Topología GitOps y Desacoplamiento de Entornos
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: Arquitectura Distribuida, GitHub, WSL2, SSH
ESTADO: Sugerencia Arquitectónica
===========================================================

- Resumen del Concepto: Desacoplamiento (GitOps Paradigm)
Actualmente, tu flujo de trabajo es lineal y acoplado: usás tu PC (Oficina o Casa) solo como una "pantalla tonta" a través de Putty para editar archivos que viven físicamente adentro de la Máquina Virtual (VM) de la UNR. 
Con la nueva arquitectura, **GitHub se convierte en el gran centralizador de tu código, no tu PC de oficina**. Tu PC de oficina, tu PC personal y la VM de la UNR pasarán a ser "nodos" que simplemente se sincronizan con la nube.

- Justificación Técnica y Evidencia (Tus Preguntas):
1. ¿Debo instalar WSL2 en la PC de oficina y centralizar todo ahí?
Sí debes instalar WSL2 allí, porque será tu "Entorno de Desarrollo Local". Pero NO centralizarás el proyecto ahí. Escribirás el código en el VS Code de tu oficina, y el Agente de IA (Antigravity/MCP) guardará los cambios. Luego, "empujarás" (Push) esos cambios a GitHub. 
2. ¿Conviene que haga la misma instalación en mi PC personal?
¡Absolutamente! Esa es la magia de esta tecnología. Al tener WSL2 y VS Code en tu casa, ya no necesitás conectarte por VPN a la VM para programar. Simplemente abrís VS Code en tu casa, "tiras" (Pull) el código actualizado desde GitHub, seguís trabajando donde lo dejaste en la oficina, y lo volvés a subir a la nube.
3. ¿Qué pasa con Putty, SSH y la VM?
La VM de la UNR se convierte estrictamente en el "Entorno de Producción". Ya no entrarás por Putty a escribir código o a pelear con nano/vim. Solo usarás la VPN y Putty para entrar a la VM, descargar (Pull) la versión final y pulida desde GitHub, y ejecutar `docker compose up -d`. 

> Nota Estratégica: Al sacar el desarrollo fuera de la VM, si el día de mañana el servidor de la UNR se rompe, se inunda o falla el disco, tu proyecto SAVIA está intacto y a salvo en GitHub, y podés levantarlo en otra máquina en cuestión de minutos.

- Configuración / Lógica Acordada:
La topología a implementar será:
* Nodo 1 (Oficina): Windows 11 + WSL2 + VS Code + Git.
* Nodo 2 (Casa): Windows 11 + WSL2 + VS Code + Git.
* Nodo Central (Nube): Repositorio Privado en GitHub.
* Nodo 3 (Producción): VM UNR 10.1.7.164 (Solo ejecuta Docker, no se usa para desarrollar).

----------------------------------------------------------------------
SAVIA modelo federal | Reporte Técnico Nº: 14 | Página 1 de 1
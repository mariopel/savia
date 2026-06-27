[ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: DOC-11
ID TEMPORAL: 260618T0253 - Preparación de Entorno de Desarrollo Local
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: OS, WSL2, VS Code, Entorno CLI
ESTADO: Sugerencia Arquitectónica
===========================================================

- Resumen del Concepto: El Ecosistema Híbrido (Windows 11 + WSL2)
La sugerencia categórica para tu perfil y urgencia es utilizar **Windows 11 combinado con WSL2** (Windows Subsystem for Linux). 
Si instalás un Linux puro (especialmente versión Server, que no tiene interfaz gráfica), vas a chocar contra una curva de aprendizaje durísima solo para gestionar ventanas, archivos y permisos, perdiendo días vitales de tu MVP. WSL2 te da lo mejor de ambos mundos: la comodidad visual y el manejo de ventanas de Windows 11, junto con un núcleo de Linux (Ubuntu) real corriendo por debajo, 100% integrado.

- Justificación Técnica y Evidencia:
1. Compatibilidad de Herramientas: Las herramientas que mencionaste (`nvm`, `Node.js`, `npm`) nacieron para Linux. En Windows nativo suelen dar dolores de cabeza (por ejemplo, `nvm` en Windows requiere un instalador distinto llamado `nvm-windows`). Al usar WSL2, instalás la versión nativa de Linux directamente.
2. Integración con VS Code: Visual Studio Code tiene una extensión oficial de Microsoft llamada "WSL". Te permite abrir VS Code en tu escritorio de Windows 11, pero la terminal integrada y la ejecución del código ocurren mágicamente dentro del entorno Linux.
3. Docker Desktop: Docker corre infinitamente mejor y más rápido en Windows 11 si tiene WSL2 activado por debajo.

- Configuración / Lógica Acordada (El Stack Ideal):
1. OS Base: Windows 11.
2. Subsistema: WSL2 (Instalando Ubuntu desde la Microsoft Store).
3. Editor: VS Code (con la extensión WSL).
4. Herramientas internas en Ubuntu: Git (ya viene integrado, no necesitás GitBash), nvm, Node.js y npm.

----------------------------------------------------------------------
SAVIA modelo federal | Reporte Técnico Nº: 11 | Página 1 de 1
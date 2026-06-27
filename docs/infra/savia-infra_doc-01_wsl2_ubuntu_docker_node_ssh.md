[ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 01
ID TEMPORAL: 260620T2238 - Inicialización y aprovisionamiento del entorno base WSL2
PROYECTO: SAVIA - Saberes y Aptitudes Verificables con Identidad Autónoma
TECNOLOGÍAS: Windows 11 -> WSL2 (Ubuntu 24.04 LTS), Git, Node.js 22 LTS, Docker Engine, VS Code
ESTADO: Validado por el Usuario
===========================================================
[CUERPO DEL DOCUMENTO]
- Resumen del Concepto:
Aprovisionamiento e instalación desde cero de la infraestructura base de desarrollo local en un entorno Windows 11 utilizando el Subsistema de Windows para Linux (WSL2) con la distribución Ubuntu 24.04 LTS. Se configuraron las herramientas del stack principal de backend para el proyecto SAVIA bajo el namespace fijo 'savia', abstrayendo el entorno criptográfico y de ejecución de contenedores mediante Docker Engine nativo, aislamiento de versiones de Node.js (v22 LTS) vía NVM, control de versiones Git integrado globalmente y emparejamiento seguro mediante llaves asimétricas SSH Ed25519 para la futura conexión con GitHub. El entorno gráfico queda acoplado eficientemente mediante VS Code en modo remoto (WSL Server).

- Justificación Técnica y Evidencia:
1. Instanciación de WSL2 y Selección de Ubuntu 24.04 LTS:
   - URL: https://learn.microsoft.com/es-es/windows/wsl/install
   - Soporte: "El comando `--install` realiza las siguientes acciones: Habilita los componentes opcionales de WSL y Plataforma de máquina virtual. Descarga e instala el kernel de Linux más reciente. Establece WSL 2 como valor predeterminado." La especificación de Ubuntu 24.04 proporciona estabilidad a largo plazo para infraestructuras de backend.

2. Aislamiento de Node.js via NVM:
   - URL: https://learn.microsoft.com/es-es/windows/wsl/tutorials/wsl-nodejs
   - Soporte: "Node Version Manager (nvm) le permite instalar varias versiones de Node.js y alternar entre ellas... se recomienda usar Node.js 22, ya que es la versión LTS actual... Es fundamental evitar el uso de `sudo apt-get install nodejs` si planea trabajar en proyectos de desarrollo modernos."

3. Orquestación de Contenedores con Docker Engine:
   - URL: https://docs.docker.com/engine/install/ubuntu/
   - Soporte: La instalación nativa de Docker Engine dentro de Ubuntu (en lugar de Docker Desktop pesado en Windows) optimiza el uso de recursos y garantiza la paridad de entornos con producción. Agregar el usuario no root al grupo `docker` evita riesgos de seguridad en la ejecución.

4. Conexión Remota Eficiente (VS Code + WSL Extension):
   - URL: https://learn.microsoft.com/es-es/windows/wsl/tutorials/wsl-vscode
   - Soporte: "La extensión WSL le permite usar VS Code en Windows para compilar aplicaciones que se ejecutan en el subsistema de Windows para Linux (WSL). VS Code ejecuta un servidor en WSL para que pueda interactuar con las herramientas y datos de Linux directamente."

5. Criptografía Asimétrica para Identidad de Código (SSH Ed25519):
   - URL: https://docs.github.com/es/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
   - Soporte: "El algoritmo Ed25519 es la opción de clave pública recomendada... Este comando crea una nueva clave SSH, utilizando el correo electrónico proporcionado como etiqueta: `ssh-keygen -t ed25519 -C 'your_email@example.com'`."

- Configuración / Lógica Acordada:
1. Habilitación de WSL2 e instalación de la distribución específica de Linux (Ubuntu-24.04) mediante PowerShell.
2. Saneamiento del sistema operativo mediante comandos `apt update && apt upgrade -y` e instalación de Git.
3. Despliegue de Node Version Manager (NVM v0.39.7), instalación de Node.js v22 y seteo de alias por defecto.
4. Repositorios GPG oficiales de Docker añadidos a la lista APT, instalación de `docker-ce` junto a `docker-compose-plugin`, y asignación de permisos locales al usuario Unix del sistema sin privilegios de root (`usermod -aG docker $USER`).
5. Generación del espacio de trabajo físico mandatorio en el Home del sistema (`mkdir -p ~/savia`) e instanciación del servidor de desarrollo con el comando `code .`.
6. Firma global de identidad en Git (`git config --global`) y par de llaves criptográficas Ed25519 añadidas de forma segura al agente de autenticación en segundo plano (`ssh-agent`).
----------------------------------------------------------------------
[PIE DE PÁGINA]
SAVIA modelo federal | Reporte Técnico Nº: 01 | Página 1 de 1


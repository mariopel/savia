[ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 02
ID TEMPORAL: 260620T2353 - Inicialización de repositorio y vinculación remota
PROYECTO: SAVIA - Saberes y Aptitudes Verificables con Identidad Autónoma chat savia-infra
TECNOLOGÍAS: Git, GitHub, SSH
ESTADO: Validado por el Usuario
===========================================================
[CUERPO DEL DOCUMENTO]
- Resumen del Concepto:
Aseguramiento del código base de la infraestructura SAVIA mediante la inicialización de un repositorio local Git. Se aplicaron políticas estrictas de exclusión de archivos (.gitignore) diseñadas para entornos SSI, previniendo la filtración accidental de claves criptográficas, variables de entorno y material de los DIDs. Finalmente, se estableció el vínculo persistente y seguro (vía protocolo SSH Ed25519) con el repositorio remoto alojado en GitHub, empujando la rama 'main' como origen upstream.

- Justificación Técnica y Evidencia:
1. Política de Exclusión (.gitignore):
   - URL: https://docs.github.com/es/get-started/getting-started-with-git/ignoring-files
   - Soporte: "Puedes crear un archivo .gitignore en el directorio raíz del repositorio para indicar a Git qué archivos y directorios no controlados debe ignorar. [...] Es una buena práctica crear un archivo .gitignore al crear un repositorio, antes de confirmar ningún archivo."

2. Vinculación con Repositorio Remoto mediante SSH:
   - URL: https://docs.github.com/es/get-started/getting-started-with-git/managing-remote-repositories
   - Soporte: "El comando `git remote add` toma dos argumentos: Un nombre de remoto, por ejemplo, `origin` y una URL de remoto... Las direcciones URL de SSH proporcionan acceso a un repositorio de Git por medio de SSH, un protocolo seguro."

- Configuración / Lógica Acordada:

COD-08
ID: 260620T2245 | Fecha: 20/06/2026 | Versión: 1.0
Descripción: Inicialización de Git local y creación del archivo .gitignore
--------------------------------------------------
cd ~/savia
git init
git branch -M main

cat << 'EOF' > .gitignore
# Dependencias de Node
node_modules/

# Variables de Entorno y Secretos SSI (¡CRÍTICO PARA SAVIA!)
.env
.env.local
*.pem
*.key

# Archivos de caché, logs y Sistema Operativo
logs/
*.log
npm-debug.log*
.DS_Store
Thumbs.db
.docker/
EOF

git add .gitignore
git commit -m "chore: inicializacion del repositorio y politicas de exclusión"
--------------------------------------------------

COD-09
ID: 260620T2258 | Fecha: 20/06/2026 | Versión: 1.0
Descripción: Vinculación del repositorio local de SAVIA con GitHub (Remote Origin)
--------------------------------------------------
git branch -M main
git remote add origin git@github.com:<TU_USUARIO>/<NOMBRE_DEL_REPO>.git
git remote -v
git push -u origin main
--------------------------------------------------
----------------------------------------------------------------------
[PIE DE PÁGINA]
SAVIA modelo federal | Reporte Técnico Nº: 02 | Página 1 de 1
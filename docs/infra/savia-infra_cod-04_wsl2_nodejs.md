chat: savia-infraCOD-04
ID: 260619T2303
Fecha: 19/06/2026
Versión: 1.0
Descripción: Instalación de NVM e implementación de Node.js 22 LTS

Bash
# 1. Descarga y ejecuta el script oficial de instalación de NVM v0.39.7
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash

# 2. Recarga la configuración de tu terminal actual (.bashrc) para habilitar NVM inmediatamente
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"

# 3. Descarga e instala la versión específica solicitada (Node.js 22)
nvm install 22

# 4. Establece la versión 22 como predeterminada para nuevas terminales
nvm use 22
nvm alias default 22

# 5. Verifica las versiones del entorno de ejecución de Node y de su gestor de paquetes npm
node --version
npm --version

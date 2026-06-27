chat: savia-infra
COD-08
ID: 260620T2245
Fecha: 20/06/2026
Versión: 1.0
Descripción: Inicialización de Git local y creación del archivo .gitignore

Bash
# 1. Aseguramos estar en el directorio raíz del proyecto
cd ~/savia

# 2. Inicializamos el repositorio de Git
git init

# 3. Renombramos la rama principal a 'main' (estándar actual de GitHub)
git branch -M main

# 4. Generamos el archivo .gitignore con las reglas de seguridad y dependencias
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

# 5. Agregamos el archivo a staging y generamos el primer commit
git add .gitignore
git commit -m "chore: inicializacion del repositorio y politicas de exclusión"

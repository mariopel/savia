# ==============================================================================
# COD-09
# ID: 260626T0749
# Fecha: 2026-06-26
# Versión: 1.1.0-SEC
# Descripción: Escudo perimetral GitOps (Agregado de bloqueo de Ofimática)
# ==============================================================================
# Dependencias de Node y Build de Payload CMS
node_modules/
payload_build/

# Variables de Entorno y Secretos SSI (¡CRÍTICO PARA SAVIA!)
.env
.env.*
*.pem
*.key

# Claves específicas de la Arquitectura SAVIA (Traefik y MongoDB)
acme.json
acme/
mongo_keyfile

# Archivos ZIP de respaldo generados por CLI (Semillas Privadas de Emisores)
*.zip

# Archivos de caché, logs y Sistema Operativo
logs/
*.log
npm-debug.log*
.DS_Store
Thumbs.db
.docker/

# Google Antigravity Verifiable Artifacts
.antigravity/artifacts/

# Archivos de Ofimática y Control Documental Personal
*.xlsx
*.csv
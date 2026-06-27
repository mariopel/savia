# ==============================================================================
# COD-03
# ID: 260625T2055
# Fecha: 2026-06-25
# Versión: 1.0.0-SEC
# Descripción: Escudo perimetral GitOps para SAVIA (Bloqueo de secretos)
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
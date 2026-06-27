chat savia-infra
COD-12
ID: 260621T0120
Fecha: 21/06/2026
Versión: 1.0
Descripción: Creación del archivo de variables de entorno (.env) para SAVIA

Bash
cat << 'EOF' > .env
# ==========================================
# CONFIGURACIÓN CORE - PROYECTO SAVIA
# ==========================================
# Entorno de ejecución
NODE_ENV=development
PORT=3000

# ==========================================
# IDENTIDAD AUTOSOBERANA (NAMESPACE FIJO)
# ==========================================
SAVIA_SIGLA=SAV
SAVIA_REGISTRO_OFICIAL=nacional.unr.edu.ar
SAVIA_DID_ACTIVO=did:web:id.unr.edu.ar

# (Futuras claves privadas y tokens de SIU Guaraní se inyectarán aquí)
EOF

# Verificamos que el archivo se haya creado correctamente mostrando su contenido
cat .env

# Opcional: Si ejecutas 'git status', notarás que Git NO te sugiere hacer un commit de este archivo, gracias a tu política de exclusión.

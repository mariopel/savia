chat: savia-infra
# ====================================================================
# COD-18
# ID: 260622T2025
# Fecha: 22/06/2026
# Versión: 1.0
# Descripción: Corrección de alias con rutas absolutas entrecomilladas
# para mitigar el quiebre de cadena por espacios en el PATH.
# ====================================================================

# 1. Eliminamos de forma segura los alias relativos anteriores
sed -i '/alias agy/d' ~/.bashrc
sed -i '/alias antigravity/d' ~/.bashrc

# 2. Inyectamos los alias con la ruta absoluta exacta a tu unidad C:
cat << 'EOF' >> ~/.bashrc
alias agy='"/mnt/c/Users/mario/AppData/Local/Programs/Antigravity IDE/bin/agy.cmd"'
alias antigravity='"/mnt/c/Users/mario/AppData/Local/Programs/Antigravity IDE/bin/antigravity.cmd"'
EOF

# 3. Recargamos la configuración de bash en la sesión actual
source ~/.bashrc

# 4. Probamos lanzar el IDE mediante el comando corto
agy .

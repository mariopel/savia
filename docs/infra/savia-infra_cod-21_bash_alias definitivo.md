chat: savia-infra

Bash
# ====================================================================
# COD-21
# ID: 260622T2100
# Fecha: 22/06/2026
# Versión: 1.0
# Descripción: Actualización de alias hacia el script shell nativo de WSL (antigravity-ide)
# ====================================================================

# 1. Limpiamos los alias que apuntaban al archivo .cmd de Windows
sed -i '/alias agy=/d' ~/.bashrc
sed -i '/alias antigravity=/d' ~/.bashrc

# 2. Inyectamos la ruta hacia el script puente de Linux (sin extensión .cmd)
cat << 'EOF' >> ~/.bashrc
alias agy='"/mnt/c/Users/mario/AppData/Local/Programs/Antigravity IDE/bin/antigravity-ide"'
alias antigravity='"/mnt/c/Users/mario/AppData/Local/Programs/Antigravity IDE/bin/antigravity-ide"'
EOF

# 3. Recargamos la configuración de bash en la sesión actual
source ~/.bashrc

# 4. Lanzamos la prueba definitiva
cd ~/savia
agy .
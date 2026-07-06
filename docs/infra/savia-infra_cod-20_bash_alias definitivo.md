chat: savia-infra
# ====================================================================
# COD-20
# ID: 260622T2045
# Fecha: 22/06/2026
# Versión: 1.0
# Descripción: Configuración del alias definitivo apuntando al ejecutable real (antigravity-ide.cmd)
# ====================================================================

# 1. Limpiamos los alias erróneos anteriores de forma segura
sed -i '/alias agy=/d' ~/.bashrc
sed -i '/alias antigravity=/d' ~/.bashrc

# 2. Inyectamos los alias con el nombre de archivo exacto que descubriste
cat << 'EOF' >> ~/.bashrc
alias agy='"/mnt/c/Users/mario/AppData/Local/Programs/Antigravity IDE/bin/antigravity-ide.cmd"'
alias antigravity='"/mnt/c/Users/mario/AppData/Local/Programs/Antigravity IDE/bin/antigravity-ide.cmd"'
EOF

# 3. Recargamos la configuración de bash en la sesión actual
source ~/.bashrc

# 4. Nos posicionamos en la carpeta del proyecto y lanzamos la prueba final
cd ~/savia
agy .


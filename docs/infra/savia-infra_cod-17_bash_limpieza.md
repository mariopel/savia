chat: savia-infra
Bash
# ====================================================================
# COD-17
# ID: 260622T2003
# Fecha: 22/06/2026
# Versión: 1.0
# Descripción: Corrección de alias duplicados y recarga forzada de entorno Bash
# ====================================================================

# 1. Eliminamos TODAS las declaraciones previas de alias para agy y antigravity
sed -i '/alias agy=/d' ~/.bashrc
sed -i '/alias antigravity=/d' ~/.bashrc

# 2. Insertamos los alias limpios una única vez al final del archivo
echo "alias agy='agy.cmd'" >> ~/.bashrc
echo "alias antigravity='antigravity.cmd'" >> ~/.bashrc

# 3. Recargamos el perfil en la sesión actual
source ~/.bashrc

# 4. Mensaje de confirmación en terminal
echo "Limpieza completada. Por favor, cierra esta ventana, abre una nueva terminal y ejecuta: agy ."


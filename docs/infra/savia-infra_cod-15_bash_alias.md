chat: savia-infra
# COD-15
# ID: 260622T0233
# Fecha: 22/06/2026
# Versión: 1.0
# Descripción: Corrección de interoperabilidad WSL y creación de alias para Antigravity IDE.

# 1. Añadimos el alias al final de tu archivo de configuración de Bash
echo "alias agy='agy.cmd'" >> ~/.bashrc

# 2. Recargamos el perfil para que el cambio surta efecto en esta misma sesión
source ~/.bashrc

# 3. Comprobamos la vinculación ejecutando el comando (debería lanzar Antigravity en Windows)
cd ~/savia
agy .

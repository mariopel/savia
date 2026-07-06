chat: savia-infra
# COD-16
# ID: 260622T1835
# Fecha: 22/06/2026
# Versión: 1.0
# Descripción: Purga de Antigravity CLI en Linux y corrección de alias de interoperabilidad

# 1. Limpiamos el caché de los servidores remotos para forzar una reinstalación limpia
rm -rf ~/.antigravity-server
rm -rf ~/.vscode-server

# 2. Eliminamos los binarios de la CLI de Linux que están causando el conflicto
rm -f ~/.local/bin/agy
rm -f ~/.local/bin/antigravity

# 3. Eliminamos de forma segura las líneas residuales del instalador CLI en tu .bashrc
sed -i '/# Added by Antigravity CLI installer/d' ~/.bashrc
sed -i '/export PATH="\/home\/mario\/.local\/bin:\$PATH"/d' ~/.bashrc

# 4. Inyectamos los alias correctos para llamar a la interfaz gráfica de Windows
echo "alias agy='agy.cmd'" >> ~/.bashrc
echo "alias antigravity='antigravity.cmd'" >> ~/.bashrc

# 5. Recargamos la configuración de bash en la sesión actual
source ~/.bashrc

# 6. Prueba de ejecución (debería abrir el IDE en Windows conectado a WSL)
cd ~/savia
agy .


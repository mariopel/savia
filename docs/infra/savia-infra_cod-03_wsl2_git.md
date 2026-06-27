chat: savia-infra
COD-03
ID: 260619T2258
Fecha: 19/06/2026
Versión: 1.0
Descripción: Actualización de repositorios base e instalación de Git en Ubuntu 24.04

Bash
# Sincroniza la lista de paquetes con los repositorios oficiales de Ubuntu
sudo apt update

# Aplica las actualizaciones disponibles a los paquetes instalados (el flag -y acepta automáticamente)
sudo apt upgrade -y

# Instala Git para el control de versiones (o lo actualiza a la última versión disponible)
sudo apt install git -y

# Verifica que Git se haya instalado correctamente mostrando su versión
git --version

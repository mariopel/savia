chat: savia-infra
COD-05
ID: 260619T2305
Fecha: 19/06/2026
Versión: 1.0
Descripción: Instalación de Docker Engine nativo y Docker Compose en WSL2

Bash
# 1. Instala utilidades base e importa las claves GPG oficiales de Docker
sudo apt-get update
sudo apt-get install ca-certificates curl -y
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# 2. Añade el repositorio estable de Docker validando tu arquitectura
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# 3. Sincroniza e instala el motor Docker, el CLI y los plugins de Compose
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y

# 4. Agrega tu usuario actual al grupo de Docker (evita el uso constante de 'sudo')
sudo usermod -aG docker $USER

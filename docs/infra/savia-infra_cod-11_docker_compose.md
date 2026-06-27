chat: savia-infra
COD-11
ID: 260621T0055
Fecha: 21/06/2026
Versión: 1.0
Descripción: Creación del orquestador base docker-compose.yml para SAVIA

Bash
cat << 'EOF' > docker-compose.yml
# COD-11
# ID: 260621T0055
# Fecha: 21/06/2026
# Versión: 1.0
# Descripción: Archivo maestro de orquestación para SAVIA (Core Headless)

version: '3.8'

services:
  # Servicio de Verificación (DCC Verifier-Plus)
  verifier:
    container_name: savia_verifier
    build:
      context: ./core-dcc/verifier-plus
      # Utilizamos el Dockerfile que viene por defecto en el repositorio de DCC
      dockerfile: Dockerfile
    ports:
      - "3000:3000"
    networks:
      - savia-network
    restart: unless-stopped
    environment:
      # Definimos el entorno para el motor de Next.js que usa el verifier
      - NODE_ENV=development

# Definición de la red virtual privada para aislar la comunicación M2M
networks:
  savia-network:
    driver: bridge
    name: savia_internal_net
EOF

# Agregamos el archivo al control de versiones Git
git add docker-compose.yml
git commit -m "feat: orquestacion base con docker-compose y servicio verifier"

Bash
# Muestra el historial de tus "fotografías" (commits) más recientes de forma resumida
git log --oneline -3

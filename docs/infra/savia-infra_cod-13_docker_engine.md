chat: savia-infra
COD-13
ID: 260621T0155
Fecha: 21/06/2026
Versión: 1.0
Descripción: Inicialización y validación del contenedor verifier-plus en Docker

Bash
# 1. Construye e inicia el contenedor en modo "detached" (segundo plano)
# Nota: La primera vez demorará unos minutos porque descargará la imagen de Node y compilará la app.
docker compose up -d --build

# 2. Lista los contenedores activos de este directorio para validar que su estado sea "Up"
docker compose ps

# 3. Muestra las últimas 20 líneas de registro del servicio para confirmar que la app está lista
docker compose logs --tail=20 verifier

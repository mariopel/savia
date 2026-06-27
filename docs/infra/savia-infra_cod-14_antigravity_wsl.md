chat: savia-infra
# ====================================================================
# COD-14
# ID: 260621T2237
# Fecha: 21/06/2026
# Versión: 1.0
# Descripción: Preparación del entorno híbrido para Google Antigravity 
# y estructura local de Artefactos Verificables
# ====================================================================

# 1. Nos aseguramos de estar en la raíz del motor SAVIA
cd ~/savia

# 2. Creamos el directorio oculto para el output de los agentes
mkdir -p .antigravity/artifacts

# 3. Excluimos los artefactos del control de versiones (para no ensuciar GitHub)
echo -e "\n# Google Antigravity Verifiable Artifacts\n.antigravity/artifacts/" >> .gitignore

# 4. Registramos esta nueva política en el historial del proyecto
git add .gitignore
git commit -m "chore: configuracion de directorio para artefactos verificables de Antigravity"

# 5. Lanzamos el nuevo IDE apuntando directamente al subsistema Linux
# (Si el binario no está mapeado en tu PATH de Linux, simplemente abre 
# Antigravity desde Windows y haz clic en el botón inferior izquierdo "Conectar a WSL")
antigravity .

Google Antigravity: Configuración y análisis técnico en la era agent-first
https://www.youtube.com/watch?v=Icm48g0OH3Y


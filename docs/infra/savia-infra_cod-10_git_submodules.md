chat: savia-infra
COD-10
ID: 260621T0035
Fecha: 21/06/2026
Versión: 1.0
Descripción: Integración del motor Verifier-Plus de DCC como submódulo de Git

Bash
# 1. Aseguramos estar en el directorio raíz de la API
cd ~/savia

# 2. Creamos un directorio específico para aislar los componentes del consorcio
mkdir -p core-dcc

# 3. Añadimos el repositorio oficial de verifier-plus como submódulo de Git
git submodule add https://github.com/digitalcredentials/verifier-plus.git core-dcc/verifier-plus

# 4. Registramos los cambios (Git creará automáticamente el archivo .gitmodules)
git commit -m "feat: integracion de submódulo verifier-plus para validaciones SACAU"

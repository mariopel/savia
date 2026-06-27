# ==============================================================================
# COD-07
# ID: 260626T0725
# Fecha: 2026-06-26
# Versión: 1.0.0
# Descripción: Purga de archivos Zone.Identifier y normalización de espacios
# ==============================================================================
# 1. Aseguramos estar en el directorio de documentación
cd ~/savia/docs

# 2. Eliminamos recursivamente toda la basura de Windows (Zone.Identifier)
find . -type f -name "*:Zone.Identifier" -delete

# 3. Renombramos todos los archivos con espacios, reemplazándolos por guiones bajos
find . -type f -name "* *" | while read -r file; do
    mv "$file" "${file// /_}"
done

# 4. Verificamos que el directorio haya quedado completamente limpio
ls -la
ls -la infra/
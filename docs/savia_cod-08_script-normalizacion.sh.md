# ==============================================================================
# COD-08
# ID: 260626T0738
# Fecha: 2026-06-26
# Versión: 1.0.0
# Descripción: Script de normalización POSIX (Minúsculas y sin paréntesis)
# ==============================================================================
# 1. Aseguramos estar en la carpeta raíz de la documentación
cd ~/savia/docs

# 2. Iteramos sobre todos los archivos (incluyendo subcarpetas como /infra)
find . -type f | while read -r file; do
    # Separamos la ruta del nombre del archivo para no romper directorios
    dir=$(dirname "$file")
    base=$(basename "$file")
    
    # Transformamos el nombre: a minúsculas y eliminamos ( y )
    nuevo_base=$(echo "$base" | tr '[:upper:]' '[:lower:]' | tr -d '()')
    
    # Si el nombre necesita corrección, aplicamos el renombramiento
    if [ "$base" != "$nuevo_base" ]; then
        mv "$dir/$base" "$dir/$nuevo_base"
    fi
done

# 3. Verificamos la limpieza final
ls -la
ls -la infra/
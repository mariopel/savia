[ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 33
ID TEMPORAL: 260626T0738 - Estandarización Estricta POSIX (Filesystem)
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: Linux bash, POSIX Naming Convention
ESTADO: Pendiente de Implementación
===========================================================
[CUERPO DEL DOCUMENTO]
- Resumen del Concepto: 
Se ejecutará una normalización recursiva de toda la estructura de archivos dentro de la carpeta de documentación. El objetivo es alinear el proyecto con el estándar POSIX para servidores Linux: conversión absoluta a minúsculas y eliminación de caracteres especiales reservados por la terminal (como los paréntesis) para garantizar un ruteo y versionado GitOps libre de fricciones.

- Justificación Técnica y Evidencia:
El entorno de producción de SAVIA (Traefik, Payload y DCC) corre sobre contenedores Alpine/Ubuntu basados en Unix. A diferencia de Windows (NTFS), los sistemas de archivos de estos contenedores (ext4/overlay2) distinguen entre mayúsculas y minúsculas. Mantener una nomenclatura heterogénea interrumpe el despliegue automatizado continuo (CI/CD). Además, la eliminación de metacaracteres del shell (paréntesis) previene errores de escape en scripts de automatización.

- Configuración / Lógica Acordada:
Ejecutar un bucle iterativo en Bash (COD-08) que detectará todos los archivos, pasará sus nombres a minúsculas (`tr '[:upper:]' '[:lower:]'`) y eliminará los paréntesis (`tr -d '()'`), renombrándolos de forma segura.

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

----------------------------------------------------------------------
[PIE DE PÁGINA]
SAVIA modelo federal | Reporte Técnico Nº: 33 | Página 1 de 1
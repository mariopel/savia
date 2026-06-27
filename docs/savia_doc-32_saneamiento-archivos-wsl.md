[ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 32
ID TEMPORAL: 260626T0725 - Saneamiento del Sistema de Archivos en WSL2
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: Linux bash, ext4, NTFS Alternate Data Streams
ESTADO: Pendiente de Implementación
===========================================================
[CUERPO DEL DOCUMENTO]
- Resumen del Concepto: 
Se ejecutará una purga de metadatos residuales de Windows (Zone.Identifier) y una normalización de nomenclatura (reemplazo de espacios por guiones bajos) en la carpeta de documentación para garantizar la compatibilidad estricta con entornos Linux y herramientas de control de versiones GitOps.

- Justificación Técnica y Evidencia:
Los Alternate Data Streams (ADS) son exclusivos del sistema NTFS y generan archivos fantasma al transferirse a particiones ext4 a través del subsistema de interoperabilidad de WSL2. Su eliminación es segura y recomendada. Asimismo, el estándar POSIX para nombres de archivo sugiere evitar espacios para prevenir fallos en el parsing de variables en scripts de automatización.

- Configuración / Lógica Acordada:
Ejecutar el script bash (COD-07) que buscará de forma recursiva los archivos residuales para eliminarlos y luego renombrará todos los archivos que contengan espacios, consolidando el formato nativo Linux.

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

----------------------------------------------------------------------
[PIE DE PÁGINA]
SAVIA modelo federal | Reporte Técnico Nº: 32 | Página 1 de 1
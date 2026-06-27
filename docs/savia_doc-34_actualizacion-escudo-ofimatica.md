[ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 34
ID TEMPORAL: 260626T0749 - Actualización de Escudo GitOps (Ofimática)
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: Git, .gitignore
ESTADO: Pendiente de Implementación
===========================================================
[CUERPO DEL DOCUMENTO]
- Resumen del Concepto: Exclusión de Archivos de Control Personal
Los archivos de ofimática y hojas de cálculo (Excel, CSV) son herramientas vitales para el control de la gestión del administrador local (WSL2 / Antigravity). Sin embargo, se los debe excluir explícitamente del control de versiones (Git) para evitar la contaminación del repositorio remoto con archivos binarios pesados que no forman parte del despliegue de infraestructura.

- Justificación Técnica y Evidencia:
El paradigma de Infraestructura como Código (IaC) y el protocolo de control de versiones dictan que los repositorios deben mantenerse magros, rastreando únicamente el código fuente y las configuraciones. Los archivos binarios como `.xlsx` causan conflictos en el historial de Git (merge conflicts) porque el motor no puede leer sus diferencias por líneas.

- Configuración / Lógica Acordada:
Se actualizará el archivo `.gitignore` ubicado en la raíz del proyecto (`~/savia/.gitignore`) inyectando una regla al final del documento para ignorar globalmente las extensiones `*.xlsx` y `*.csv`. Esto permitirá que los archivos existan en la PC del usuario, pero nunca viajen a la nube.

# ==============================================================================
# COD-09
# ID: 260626T0749
# Fecha: 2026-06-26
# Versión: 1.1.0-SEC
# Descripción: Escudo perimetral GitOps (Agregado de bloqueo de Ofimática)
# ==============================================================================
# Dependencias de Node y Build de Payload CMS
node_modules/
payload_build/

# Variables de Entorno y Secretos SSI (¡CRÍTICO PARA SAVIA!)
.env
.env.*
*.pem
*.key

# Claves específicas de la Arquitectura SAVIA (Traefik y MongoDB)
acme.json
acme/
mongo_keyfile

# Archivos ZIP de respaldo generados por CLI (Semillas Privadas de Emisores)
*.zip

# Archivos de caché, logs y Sistema Operativo
logs/
*.log
npm-debug.log*
.DS_Store
Thumbs.db
.docker/

# Google Antigravity Verifiable Artifacts
.antigravity/artifacts/

# Archivos de Ofimática y Control Documental Personal
*.xlsx
*.csv

----------------------------------------------------------------------
[PIE DE PÁGINA]
SAVIA modelo federal | Reporte Técnico Nº: 34 | Página 1 de 1
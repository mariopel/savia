chat: savia-infra
COD-06
ID: 260619T2322
Fecha: 19/06/2026
Versión: 1.0
Descripción: Creación de la carpeta raíz del proyecto e integración con VS Code Server

Bash
# 1. Asegura que estamos en el directorio HOME de tu usuario Linux
cd ~

# 2. Crea la carpeta raíz con el nombre del namespace fijo en minúsculas
mkdir -p savia

# 3. Accede al directorio del proyecto
cd savia

# 4. Llama a VS Code desde Linux (la primera vez descargará el servidor de VS Code en Ubuntu automáticamente)
code .

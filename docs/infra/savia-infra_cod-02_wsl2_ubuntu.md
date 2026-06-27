chat: savia-infra
COD-02
ID: 260619T2255
Fecha: 19/06/2026
Versión: 1.0
Descripción: Selección e instalación específica de Ubuntu 24.04 en WSL2

PowerShell
# 1. Verifica cómo nombra Microsoft a la distribución (verás Ubuntu-24.04 en la lista)
wsl --list --online

# 2. Instala explícitamente Ubuntu 24.04
wsl --install -d Ubuntu-24.04
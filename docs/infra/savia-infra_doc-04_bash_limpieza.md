chat: savia-infra
[ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 04
ID TEMPORAL: 260622T1934 - Resolución de Conflicto en Despliegue Híbrido de Antigravity IDE
PROYECTO: SAVIA - Saberes y Aptitudes Verificables con Identidad Autónoma
TECNOLOGÍAS: WSL2 / Bash / Antigravity IDE
ESTADO: Validado por el Usuario
===========================================================
[CUERPO DEL DOCUMENTO]
- Resumen del Concepto: 
Durante la Fase 4, se detectó un error de interoperabilidad (WSL Interop) al intentar lanzar el IDE desde la terminal de Ubuntu. El problema consistió en que se instaló la versión CLI nativa de Linux de Antigravity dentro de WSL2. Esto inyectó rutas en el `.bashrc` y binarios locales (`/home/mario/.local/bin/agy`) que interceptaban el comando, abriendo una consola de texto pura y bloqueando la llamada al cliente gráfico (IDE) instalado en el sistema anfitrión (Windows 11). El error "not found" al usar "antigravity ." o "agy ." se produce por un conflicto directo con el caché de la herramienta y la ruptura del lanzador[cite: 1].

- Justificación Técnica y Evidencia:
Para solucionar problemas de conexión, dependencias y conflictos de lanzadores rotos en WSL, es mandatorio limpiar el caché del servidor remoto forzando su reinstalación (`rm -rf ~/.antigravity-server`), eliminar los scripts binarios conflictivos en el entorno Linux y realizar un reinicio limpio[cite: 1]. El despliegue correcto en arquitecturas híbridas requiere instalar únicamente el cliente pesado en Windows y utilizar la extensión "Remote-WSL" para que el IDE gestione el puente automáticamente, vinculando la ejecución mediante alias de Bash.

- Configuración / Lógica Acordada:
Para conocimiento posterior, los pasos correctos para un despliegue limpio son:
1. Instalar exclusivamente Antigravity IDE en Windows 11.
2. Instalar la extensión Remote-WSL (ej. jeanp413) dentro del IDE en Windows.
3. No ejecutar scripts de instalación de CLI dentro de WSL.
4. Configurar alias en `.bashrc` para que Linux llame a los ejecutables `.cmd` de Windows.

A continuación, se detalla el código exacto de la solución aplicada para purgar el entorno y restaurar el puente de conexión:

# ====================================================================
# COD-16
# ID: 260622T1835
# Fecha: 22/06/2026
# Versión: 1.0
# Descripción: Purga de Antigravity CLI en Linux y corrección de alias de interoperabilidad
# ====================================================================

# 1. Limpiamos el caché de los servidores remotos para forzar una reinstalación limpia
rm -rf ~/.antigravity-server
rm -rf ~/.vscode-server

# 2. Eliminamos los binarios de la CLI de Linux que están causando el conflicto
rm -f ~/.local/bin/agy
rm -f ~/.local/bin/antigravity

# 3. Eliminamos de forma segura las líneas residuales del instalador CLI en tu .bashrc
sed -i '/# Added by Antigravity CLI installer/d' ~/.bashrc
sed -i '/export PATH="\/home\/mario\/.local\/bin:\$PATH"/d' ~/.bashrc

# 4. Inyectamos los alias correctos para llamar a la interfaz gráfica de Windows
echo "alias agy='agy.cmd'" >> ~/.bashrc
echo "alias antigravity='antigravity.cmd'" >> ~/.bashrc

# 5. Recargamos la configuración de bash en la sesión actual
source ~/.bashrc
----------------------------------------------------------------------
[PIE DE PÁGINA]
SAVIA modelo federal | Reporte Técnico Nº: 04 | Página 1 de 1


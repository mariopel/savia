chat-infra
[ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 05
ID TEMPORAL: 260622T2003 - Corrección de Variables PATH y Alias Duplicados en WSL2
PROYECTO: SAVIA - Saberes y Aptitudes Verificables con Identidad Autónoma
TECNOLOGÍAS: WSL2 / Bash / Interoperabilidad Windows-Linux
ESTADO: Validado por el Usuario
===========================================================
[CUERPO DEL DOCUMENTO]
- Resumen del Concepto: 
Tras la purga de la versión CLI de Antigravity, se reportó que los comandos `agy .` y `antigravity .` continuaban devolviendo el error "Command not found"[cite: 4]. La auditoría del sistema reveló dos factores: el archivo de configuración `.bashrc` presentaba declaraciones de alias duplicadas[cite: 2], y la sesión de terminal activa no había cargado en memoria las nuevas directivas ni heredado el nuevo `$PATH` del sistema anfitrión Windows. 

- Justificación Técnica y Evidencia:
En arquitecturas WSL2, la modificación de variables de entorno o la instalación de nuevos ejecutables gráficos en el sistema operativo anfitrión (Windows) requiere que la sesión de la terminal de Linux sea recargada (`source ~/.bashrc`) o, en caso de persistir la falta de sincronización del PATH, que la máquina virtual sea reiniciada en su totalidad mediante el comando de host `wsl --shutdown`. El error de falta de expansión del alias (`Command 'agy' not found`[cite: 4]) certifica empíricamente que la configuración no estaba instanciada en el subshell activo. Por otro lado, la verificación del directorio raíz confirma que la purga previa de los servidores anidados fue exitosa[cite: 3].

- Configuración / Lógica Acordada:
Se aplicó un flujo de corrección consistente en:
1. Purgar mediante `sed` todas las líneas duplicadas de los alias en `.bashrc`.
2. Escribir los alias correctos (`alias agy='agy.cmd'`) de forma única.
3. Instruir el cierre total de la sesión de terminal o el apagado de la instancia WSL para forzar la propagación de las variables PATH de Windows hacia Linux.

----------------------------------------------------------------------
[PIE DE PÁGINA]
SAVIA modelo federal | Reporte Técnico Nº: 05 | Página 1 de 1


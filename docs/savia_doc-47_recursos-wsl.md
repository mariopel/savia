### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-47
ID Temporal: 260701T1042
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: WSL2, Asignacion de Recursos, Memoria
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
Al ejecutar la orquestacion completa de SAVIA (Traefik, MongoDB,
Payload y Verifier-Plus) en el entorno WSL2 local, es vital restringir
los recursos de hardware (RAM y CPU) asignados a la maquina virtual
Linux para evitar el colapso de los recursos del host en Windows.

#### Justificacion Tecnica y Evidencia
WSL2 por defecto consume agresivamente la memoria del sistema host. En
operaciones de compilacion, este consumo causa inestabilidad severa.
URL: https://learn.microsoft.com/en-us/windows/wsl/wsl-config
Cita: "You can configure global settings for WSL using the .wslconfig
file, including limits for memory and processors."

#### Configuracion / Logica Acordada
1. Crear el archivo .wslconfig en la raiz del usuario de Windows.
2. Establecer un limite estricto de memoria (ej. memory=8GB) y
procesadores (ej. processors=4) en la directiva [wsl2].
3. Reiniciar el hipervisor con 'wsl --shutdown' para aplicar los cambios.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 47 | Pagina 1 de 1
chat: savia-infra
DOC-09
[ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 09
ID TEMPORAL: 260625T1903 - Interoperabilidad de Archivos Windows-WSL2
PROYECTO: SAVIA - Saberes y Aptitudes Verificables con Identidad Autónoma
TECNOLOGÍAS: WSL2 / Plan 9 Protocol / Antigravity IDE
ESTADO: Validado por el Usuario
===========================================================
[CUERPO DEL DOCUMENTO]
- Resumen del Concepto: 
En topologías de desarrollo basadas en Windows Subsystem for Linux (WSL2), se desaconseja el uso de herramientas de transferencia de red tradicionales (como WinSCP o servidores OpenSSH) debido a que WSL2 opera tras un conmutador virtual (Hyper-V Virtual Switch) que asigna direcciones IP dinámicas y NATeables en cada reinicio, provocando bloqueos de firewall en el puerto 22. En su lugar, se validaron y aprobaron tres métodos de transferencia nativos y directos:
1. Explorador de Windows mediante protocolo de red local (`\\wsl.localhost\Ubuntu-24.04`).
2. Terminal Linux mediante el punto de montaje nativo (`/mnt/c/`).
3. Interfaz gráfica de Antigravity IDE (Drag & Drop en el panel explorador conectado mediante Remote-WSL).

- Justificación Técnica y Evidencia:
Microsoft implementó un servidor de archivos basado en el protocolo Plan 9 (9P) integrado directamente en el kernel de WSL2, lo que permite una comunicación nativa entre el hipervisor y el sistema anfitrión sin necesidad de protocolos de capa de red externa como FTP o SSH.
> "Puedes acceder a los archivos del proyecto de Linux desde Windows con el Explorador de archivos... dirígete a `\\wsl$\<DistroName>` (o `\\wsl.localhost\<DistroName>` para versiones más recientes) para acceder de forma segura a los sistemas de archivos de tu distribución."
> URL: https://learn.microsoft.com/es-es/windows/wsl/filesystems

- Configuración / Lógica Acordada:
El usuario validó la transferencia exitosa hacia la ruta raíz `/home/mario/savia` utilizando el puente nativo sin requerir modificaciones en el Windows Defender Firewall ni la instanciación de servicios SSH.
----------------------------------------------------------------------
[PIE DE PÁGINA]
SAVIA modelo federal | Reporte Técnico Nº: 09 | Página 1 de 1

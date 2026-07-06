### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-46
ID Temporal: 260701T1042
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Docker Logs, Monitoreo, Auditoria
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
El monitoreo de la infraestructura SAVIA se realiza a traves de la
auditoria de logs de contenedores. Dado que la aplicacion corre de
forma aislada, los registros de eventos, errores de emision y bloqueos
M2M quedan encapsulados en el standard output (stdout) de Docker.

#### Justificacion Tecnica y Evidencia
Revisar los logs en tiempo real es el metodo oficial para depurar fallos
de inyeccion de Payload CMS o problemas de resolucion de red en Traefik.
URL: https://docs.docker.com/engine/logging/
Cita: "The docker logs command shows information logged by a running
container, specifically the stdout and stderr data streams."

#### Configuracion / Logica Acordada
1. Para auditar el motor de emision, ejecutar en la terminal WSL:
docker logs -f [nombre_contenedor_api]
2. Filtrar eventos especificos de la cuenta de servicio M2M utilizando
grep: docker logs [nombre] | grep "lms-moodle@unr.edu.ar"
3. Configurar rotacion de logs en daemon.json para evitar saturacion.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 46 | Pagina 1 de 1
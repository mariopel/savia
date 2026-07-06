### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-02
ID Temporal: 260701T0037
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Traefik, Proxy Inverso, Docker
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
Traefik actua como un proxy inverso dinamico y enrutador de frontera
para la arquitectura de SAVIA. Su funcion principal es interceptar las
peticiones externas, gestionar los certificados de seguridad (SSL/TLS)
y derivar el trafico de manera segura hacia los contenedores internos
del ecosistema DCC (orquestador, base de datos, emisor), sin exponer
los puertos nativos de la red privada al exterior.

#### Justificacion Tecnica y Evidencia
En infraestructuras de microservicios con Docker, Traefik es el
estandar para el descubrimiento automatico de servicios. Al auditar
los accesos, Traefik garantiza que solo los dominios autorizados
(ej. id.unr.edu.ar) interactuen con la API, previniendo ataques.
URL: github.com/traefik/traefik
Cita: "Traefik is a modern HTTP reverse proxy and load balancer that
makes deploying microservices easy. It routes every incoming request
to the corresponding microservice."

#### Configuracion / Logica Acordada
1. Desplegar Traefik en el archivo docker-compose.yml global.
2. Configurar el endpoint de escucha seguro (puerto 443) habilitando
el ruteo estricto por nombre de host.
3. Implementar un certificado auto-firmado para el entorno de MVP,
requiriendo el bypass de SSL (flag -k) en herramientas como curl.
4. No exponer puertos de bases de datos de Payload CMS hacia el host.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 02 | Pagina 1 de 1
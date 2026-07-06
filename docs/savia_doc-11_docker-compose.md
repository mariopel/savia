### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-11
ID Temporal: 260701T0047
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Docker Compose, MongoDB, Orquestacion
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
El archivo docker-compose.yml es la espina dorsal de la infraestructura
SAVIA. Define la orquestacion de los microservicios necesarios para que el
motor de credenciales opere de forma autonoma, desplegando simultaneamente
la base de datos MongoDB y el orquestador Payload CMS en una red privada.

#### Justificacion Tecnica y Evidencia
Docker Compose permite aislar servicios asegurando que compartan el mismo
ciclo de vida y red interna sin exponer puertos sensibles al exterior.
URL: https://docs.docker.com/compose/
Cita: "Compose is a tool for defining and running multi-container Docker
applications. With Compose, you use a YAML file to configure services."

#### Configuracion / Logica Acordada
1. Crear el archivo docker-compose.yml en la raiz del proyecto savia.
2. Definir el servicio de MongoDB con volumenes persistentes locales.
3. Es obligatorio definir explicitamente la variable container_name en el
codigo de cada servicio para evitar errores de resolucion (ej. mongo-1).
4. Restringir la exposicion de puertos unicamente al proxy Traefik.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 11 | Pagina 1 de 1
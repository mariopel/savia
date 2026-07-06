### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-06
ID Temporal: 260701T0041
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Docker Compose, Desacoplamiento, Microservicios
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
El desacoplamiento arquitectonico separa el motor de credenciales 
(SAVIA/DCC) del sistema de gestion academica legacy (SIU Guarani). En
lugar de instalar el emisor dentro de la base de datos principal, se
despliega en contenedores Docker aislados. Esto garantiza que cualquier
caida o saturacion en la emision no afecte las operaciones criticas
de la universidad, como inscripciones o examenes.

#### Justificacion Tecnica y Evidencia
La implementacion con Docker Compose permite aislar recursos, redes y
volumenes. El motor DCC asume esta separacion, requiriendo su propia
base de datos MongoDB y comunicandose unicamente a traves de su API
REST para mantener la integridad de las fronteras de los servicios.
URL: https://github.com/digitalcredentials/docs
Cita: "Using Docker for deployment ensures the DCC stack remains
isolated from host systems, packaging its own dependencies safely."

#### Configuracion / Logica Acordada
1. Aislar los servicios de SAVIA en su propia red de Docker (red_savia).
2. Evitar conexiones directas desde SAVIA hacia la base de datos de
SIU Guarani; la comunicacion sera exclusivamente a traves de la API M2M.
3. Asegurar que cada actualizacion de componentes DCC se gestione 
independientemente sin requerir tiempos de inactividad en otros sistemas.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 06 | Pagina 1 de 1
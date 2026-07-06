### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-30
ID Temporal: 260701T0059
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Docker Compose, Dependencias (depends_on)
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
En un entorno multicontenedor, el orden de arranque es vital. La directiva
depends_on asegura que la base de datos se inicie antes que la API del
motor SAVIA. Si el emisor intenta conectarse a una base de datos apagada,
el proceso fallara originando un bucle de reinicio (crash loop).

#### Justificacion Tecnica y Evidencia
Docker Compose inicia los servicios en paralelo por defecto. Forzar una
secuencia de dependencias garantiza que la conexion del backend se
establezca de manera exitosa.
URL: https://docs.docker.com/compose/compose-file/05-services/#depends_on
Cita: "depends_on expresses startup and shutdown dependencies between
services. Compose starts services in dependency order."

#### Configuracion / Logica Acordada
1. En el servicio de la API (DCC), agregar la directiva depends_on.
2. Especificar rigurosamente el nombre explicito del contenedor de la base
de datos (ej. mongo-1) respetando la nomenclatura acordada en el proyecto.
3. Considerar que depends_on no espera a que MongoDB este "listo" para
recibir consultas, solo a que el contenedor arranque fisicamente.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 30 | Pagina 1 de 1
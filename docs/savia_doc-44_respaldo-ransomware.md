### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-44
ID Temporal: 260701T1041
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: MongoDB, Backup, mongodump
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
La continuidad operativa (mitigacion de ransomware o corrupcion de datos)
exige una politica de respaldos periodicos. Para SAVIA, esto implica
extraer un volcado (dump) completo de la base de datos MongoDB desde el
contenedor en ejecucion hacia el host fisico local.

#### Justificacion Tecnica y Evidencia
Las utilidades nativas de MongoDB son el estandar de la industria para
garantizar la consistencia de los datos durante la extraccion, sin
necesidad de detener el motor de emision.
URL: https://www.mongodb.com/docs/database-tools/mongodump/
Cita: "mongodump is a utility for creating a binary export of the
contents of a database. It can export data from mongod instances."

#### Configuracion / Logica Acordada
1. Ejecutar el comando de extraccion desde la terminal WSL del host,
apuntando estrictamente al nombre explicito del contenedor (mongo-1).
2. Comando: docker exec mongo-1 mongodump --authenticationDatabase admin
-u root -p Clave01mpUNR --db savia_unr_db --out /data/db/backups/
3. Copiar el respaldo generado en el volumen hacia un disco desconectado
de la red para garantizar inmunidad contra ransomware.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 44 | Pagina 1 de 1
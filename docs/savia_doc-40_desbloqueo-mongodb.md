### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-40
ID Temporal: 260701T1044
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: MongoDB, Mongosh, Administracion de BD
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
Cuando una Cuenta de Servicio M2M resulta bloqueada por seguridad debido
a errores de tipeo o desincronizacion de claves, el desbloqueo puede
forzarse de manera inmediata mediante una cirugia directa sobre la base de
datos MongoDB, evitando esperar el tiempo de expiracion automatico.

#### Justificacion Tecnica y Evidencia
El acceso directo a la terminal de MongoDB (mongosh) desde el host local
permite al administrador alterar las propiedades 'loginAttempts' y
'lockUntil' de la coleccion de usuarios para restablecer la continuidad.
URL: https://www.mongodb.com/docs/mongodb-shell/
Cita: "The MongoDB Shell, mongosh, is a fully functional JavaScript and
Node.js REPL environment for interacting with MongoDB deployments."

#### Configuracion / Logica Acordada
1. Acceder al contenedor de base de datos desde la linea de comandos WSL.
2. Ejecutar la actualizacion directa poniendo en cero los intentos y
anulando el bloqueo temporal. El comando de emergencia acordado es:
docker exec mongo-1 mongosh -u root -p Clave01mpUNR --authenticationDatabase
admin --eval 'db.getSiblingDB("savia_unr_db").users.updateOne({email:
"lms-moodle@unr.edu.ar"}, {$set: {loginAttempts: 0, lockUntil: null}});'

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 40 | Pagina 1 de 1
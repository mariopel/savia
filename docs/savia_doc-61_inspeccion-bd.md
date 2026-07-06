### [ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 61
ID TEMPORAL: 260701T1049 - Inspeccion DB M2M
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: MongoDB, mongosh, Debugging
ESTADO: Consolidado
===========================================================
### [CUERPO DEL DOCUMENTO]
- Resumen del Concepto:
Ante fallos silenciosos en la inyeccion M2M, el administrador debe
inspeccionar directamente MongoDB para verificar si se crearon documentos
parciales. Para evitar errores de "No such container", es obligatorio
utilizar el nombre explicito del contenedor de la base de datos.

- Justificacion Tecnica y Evidencia:
El acceso via mongosh permite auditar la coleccion 'credential-batch'
y contrastar la data guardada contra la estructura del JSON inyectado.
URL: https://www.mongodb.com/docs/mongodb-shell/
Cita: "The mongosh shell allows database administrators to directly
query collections and evaluate document structure."

- Configuracion / Logica Acordada:
1. Como regla de infraestructura, usar el nombre estricto: mongo-1.
2. Comando: docker exec -it mongo-1 mongosh -u root -p Clave01mpUNR
3. Dentro de la shell, ejecutar: use savia_unr_db y luego
db.getCollection('credential-batch').find().pretty() para auditar.
----------------------------------------------------------------------
### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 61 | Pagina 1 de 1
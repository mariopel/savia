### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-31
ID Temporal: 260701T0100
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: MongoDB, Volumenes Persistentes, Docker
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
Al desplegar la base de datos MongoDB en contenedores Docker, la
informacion es efimera por defecto. Para prevenir la perdida de registros
de diplomas y credenciales tras un reinicio o actualizacion del motor,
es obligatorio mapear un volumen local persistente hacia el contenedor.

#### Justificacion Tecnica y Evidencia
La arquitectura de base de datos exige almacenamiento inmutable para
garantizar que los lotes de emision y las cuentas de usuario sobrevivan.
URL: https://docs.docker.com/storage/volumes/
Cita: "Volumes are the preferred mechanism for persisting data generated
by and used by Docker containers."

#### Configuracion / Logica Acordada
1. Declarar un volumen local (ej. mongo_data) en docker-compose.yml.
2. Vincular este volumen a la ruta interna /data/db del contenedor.
3. Excluir rigurosamente la carpeta del volumen en el archivo .gitignore
para evitar subir datos sensibles al repositorio de GitHub.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 31 | Pagina 1 de 1
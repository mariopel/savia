### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-45
ID Temporal: 260701T1041
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Git Pull, Docker Compose, Actualizacion
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
El consorcio DCC libera actualizaciones frecuentes de seguridad y nuevas
caracteristicas. Actualizar el nucleo de SAVIA implica sincronizar el
codigo base desde el repositorio oficial y reconstruir los contenedores
sin afectar el volumen de datos persistentes ni las reglas de negocio.

#### Justificacion Tecnica y Evidencia
Docker Compose permite recrear los servicios manteniendo intactos los
volumenes montados. Esto asegura que los historiales de emision, perfiles
institucionales y claves maestras no se destruyan durante el parcheo.
URL: https://docs.docker.com/compose/
Cita: "Compose preserves all volumes used by your services. When docker
compose up runs, if it finds any containers from previous runs, it copies
the volumes from the old container to the new container."

#### Configuracion / Logica Acordada
1. Realizar el respaldo de la base de datos (segun DOC-44).
2. Ejecutar 'git pull upstream main' para traer los cambios del DCC.
3. Reconstruir la infraestructura con 'docker compose up -d --build'.
4. Verificar los logs del contenedor de la API para asegurar que Payload
CMS se inicializo correctamente con la nueva version.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 45 | Pagina 1 de 1
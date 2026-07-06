### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-26
ID Temporal: 260701T0059
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Docker, Variables de Entorno, Seguridad
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
El uso de archivos .env externaliza la configuracion sensible del codigo
fuente. En la arquitectura SAVIA, contraseñas de bases de datos, semillas
criptograficas y tokens M2M se inyectan estrictamente en tiempo de
ejecucion para cumplir con normativas de seguridad y evitar fugas.

#### Justificacion Tecnica y Evidencia
La metodologia Twelve-Factor App exige el almacenamiento de la configuracion
en el entorno. Docker soporta nativamente la lectura de variables de
entorno para instanciar contenedores sin codificar secretos (hardcoding).
URL: https://docs.docker.com/compose/environment-variables/
Cita: "You can set environment variables in your containers using the
environment key, or by pulling them from an .env file."

#### Configuracion / Logica Acordada
1. Crear un archivo .env en el directorio raiz del proyecto (~/savia).
2. Declarar las variables necesarias (ej. MONGO_INITDB_ROOT_PASSWORD).
3. Asegurar que .env se encuentre listado dentro del archivo .gitignore
para prohibir su sincronizacion en el repositorio publico de GitHub.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 26 | Pagina 1 de 1
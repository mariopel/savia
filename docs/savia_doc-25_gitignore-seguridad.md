### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-25
ID Temporal: 260701T0055
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Gitignore, Seguridad, Exclusion
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
El archivo .gitignore es la primera linea de defensa del proyecto. Le
indica al sistema de control de versiones que archivos y directorios
deben ser ignorados intencionalmente, evitando que secretos, claves
privadas o bases de datos se publiquen en repositorios remotos.

#### Justificacion Tecnica y Evidencia
Subir credenciales o archivos de entorno (.env) a GitHub expone la
infraestructura a ataques automatizados. La exclusion proactiva es un
estandar critico de la metodologia DevSecOps.
URL: https://git-scm.com/docs/gitignore
Cita: "A gitignore file specifies intentionally untracked files that
Git should ignore. Files already tracked by Git are not affected."

#### Configuracion / Logica Acordada
1. Crear el archivo .gitignore en la raiz del proyecto SAVIA.
2. Declarar explicitamente la exclusion de directorios de bases de
datos (mongo_data), modulos, y archivos de variables de entorno
(.env) para proteger el entorno de produccion.
3. Validar con 'git status' que los archivos excluidos no aparezcan.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 25 | Pagina 1 de 1
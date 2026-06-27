[ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: DOC-23
ID TEMPORAL: 260625T2040 - Protección Perimetral de Secretos Criptográficos
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: GitOps, .gitignore, Secrets Management
ESTADO: Pendiente de Implementación
===========================================================

- Resumen del Concepto: El Escudo .gitignore
En la arquitectura GitOps, el repositorio público/privado en GitHub contiene la "receta" (el código, la infraestructura), pero jamás los "ingredientes secretos" (claves, certificados, semillas W3C). El archivo `.gitignore` se coloca en la raíz del proyecto para indicarle al motor de control de versiones de Antigravity qué archivos y carpetas debe ignorar y nunca rastrear.

- Justificación Técnica y Evidencia:
El manejo seguro de las variables de entorno y los archivos de claves es un mandato estricto en el despliegue del ecosistema DCC para evitar comprometer la emisión de credenciales.
* URL de la fuente: `https://github.com/digitalcredentials/dcc-admin-dashboard`
* Párrafo de soporte: La documentación oficial de despliegue exige inicializar las variables críticas localmente: *"Create an .env file in the root directory. You can copy the contents of .env.example as a starting point."* Las mejores prácticas de seguridad inherentes a este ecosistema dictan que los archivos `.env`, `mongo_keyfile`, y los almacenes de certificados dinámicos como `acme.json` deben excluirse explícitamente del control de versiones.

- Configuración / Lógica Acordada:
Se creará un archivo llamado `.gitignore` en la ruta `~/savia/`. Este archivo bloqueará específicamente:
1. La carpeta de certificados dinámicos de Traefik (`acme/`).
2. El archivo de llaves de la base de datos (`mongo_keyfile`).
3. Cualquier archivo de variables oculto (`.env`).
4. Los archivos generados por compilaciones de Node.js (`node_modules/`, `payload_build/`).
5. Los archivos `.zip` generados por tu herramienta `garante-identidad-savia.js`.

----------------------------------------------------------------------
SAVIA modelo federal | Reporte Técnico Nº: 23 | Página 1 de 1
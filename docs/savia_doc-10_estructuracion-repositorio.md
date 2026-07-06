### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-10
ID Temporal: 260701T0045
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Git, GitHub, Docs as Code
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
Al utilizar GitHub, el codigo fuente (Docker, Traefik, Assets) y la
documentacion tecnica (nuestros reportes) conviven en el mismo
ecosistema. Esto resuelve definitivamente el problema de la memoria
efimera de la IA. Cuando conectemos un Agente a tu repositorio, la
maquina leera esta carpeta de documentacion y automaticamente
asimilara todo el contexto del proyecto sin que tengas que volver a
explicarselo.


#### Justificacion Tecnica y Evidencia
El estandar de la industria dicta que la documentacion debe vivir lo
mas cerca posible del codigo que describe. Plataformas como GitHub
renderizan automaticamente carpetas llamadas docs/ y archivos
README.md, facilitando su lectura tanto para humanos como para
motores de Inteligencia Artificial.


#### Configuracion / Logica Acordada
Para preparar la subida (Push) de tu respaldo a GitHub, la sugerencia
es que crees una nueva carpeta llamada docs/ dentro de tu directorio
principal savia. La topologia quedara asi:
savia/
├── assets/
├── config/
├── sites/
└── docs/ <-- NUEVA CARPETA PARA LA MEMORIA DEL PROYECTO


### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 10 | Pagina 1 de 1
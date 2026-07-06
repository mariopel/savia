### [ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 73
ID TEMPORAL: 260704T2020 - Definicion de Fases del Proyecto
PROYECTO: SAVIA - UNR
TECNOLOGÍAS: Gestion de Proyecto, Arquitectura SSI
ESTADO: Consolidado
===========================================================
### [CUERPO DEL DOCUMENTO]
- Resumen del Concepto:
El campo 'fase' en la trazabilidad (CSV) representa etapas macro de
evolucion arquitectonica, no tareas diarias. Agrupa los documentos
segun hitos de madurez del producto minimo viable (MVP) de SAVIA.

- Justificacion Tecnica y Evidencia:
Organizar la documentacion en bloques tematicos permite a futuros
desarrolladores o instancias de IA entender la arquitectura de manera
secuencial, desde los cimientos teoricos hasta la integracion.

- Configuracion / Logica Acordada:
Se establecen las siguientes 7 fases de desarrollo consolidadas:
* Fase 1 (DOC-01 a DOC-09): Arquitectura y Protocolos Base. Conceptualizacion,
  diseño de API REST y protocolo Push/Pull.
* Fase 2 (DOC-10 a DOC-20): Infraestructura Local y Orquestacion. Despliegue
  con Docker, WSL2, Verifier-Plus y DIDs en el entorno local.
* Fase 3 (DOC-21 a DOC-30): Versionado y Enrutamiento. Control con Git,
  proxy inverso Traefik, certificados SSL y variables de entorno.
* Fase 4 (DOC-31 a DOC-40): Persistencia y Core SAVIA. Configuracion de
  MongoDB, inicializacion de Payload CMS y Cuentas de Servicio M2M.
* Fase 5 (DOC-41 a DOC-50): Ciclo de Vida y Produccion. Presentaciones
  Verificables (VP), Revocacion (Status List), Backups y Checklist MVP.
* Fase 6 (DOC-51 a DOC-72): Resolucion M2M y Testing. Pruebas con cURL,
  estructuracion JSON, manejo de CORS y fix de inyeccion de credenciales.
* Fase 7 (Actual/Proxima): Middleware SIU Guarani. Desarrollo de la app
  puente para conectar el sistema legacy de la universidad con la API.
----------------------------------------------------------------------
### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 73 | Archivo:
savia_doc-73_fases-proyecto.md | Pagina 1 de 1
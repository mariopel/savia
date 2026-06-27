[ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: DOC-07
ID TEMPORAL: 260618T0226 - Masterclass de Arquitectura API (Modelo Push)
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: API REST, SIU Guaraní, Payload CMS
ESTADO: Validado por el Usuario
===========================================================

- Resumen del Concepto: Arquitectura de Integración (SIU -> SAVIA)
La arquitectura que vamos a implementar se basa en el patrón de comunicación **API RESTful unidireccional (Modelo Push)**. 
En este escenario, SAVIA actúa como un "Servidor de Recursos" pasivo y SIU Guaraní actúa como el "Cliente" activo. Las interacciones ocurren exclusivamente cuando hay un evento desencadenante (un alumno se gradúa).


1. Flujo de Interacción (Paso a Paso):
   * Evento: El operador en SIU Guaraní aprueba el egreso de un alumno.
   * Empuje (Push): El servidor del SIU empaqueta los datos del alumno (Nombre, Email, Título) en un formato de texto estructurado llamado JSON.
   * Tránsito: El SIU envía ese paquete JSON a través de internet usando el protocolo seguro HTTPS directamente hacia la puerta de SAVIA (`gecer.unr.edu.ar`).
   * Recepción: Traefik recibe la petición, valida el certificado SSL y la enruta al contenedor `sav-payload`.
   * Validación: Payload CMS lee la "API Key" (llave secreta) que viene en el paquete. Si es válida, procesa los datos.
   * Emisión: SAVIA contacta internamente al motor `sav-signing`, firma la credencial criptográficamente con la semilla de la UNR y la envía al correo del alumno.

2. Ventajas de esta Arquitectura (Desacoplamiento):
   * Seguridad Perimetral: SAVIA no tiene acceso a la base de datos central de la UNR. Si SAVIA cae, el SIU sigue funcionando perfectamente.
   * Agnosticismo Tecnológico: A SAVIA no le importa si el SIU está programado en PHP, Java o Python. Se comunican mediante un lenguaje universal (JSON).
   * Escalabilidad: Mañana podés conectar el sistema de RRHH o la Biblioteca de la misma manera, simplemente dándoles una API Key diferente.

3. Menú de Tareas (Roadmap de Implementación):
   [ ] 1. Generar una API Key (Token de Autorización) permanente dentro del panel de SAVIA.
   [ ] 2. Definir y documentar el esquema JSON exacto (qué campos son obligatorios).
   [ ] 3. Realizar una simulación manual de inyección utilizando herramientas auxiliares.
   [ ] 4. Entregar la documentación al equipo de DCPD para que programen el "gatillo" en el SIU.

4. Herramientas Auxiliares (Para el Administrador):
   * Postman o Insomnia: Software de interfaz gráfica para simular peticiones API sin necesidad de programar.
   * cURL: Herramienta de línea de comandos (nativa en Linux/Mac) para enviar peticiones rápidas desde la terminal.
   * JSONLint: Validador web gratuito para comprobar que el código JSON no tenga errores de sintaxis.

5. Comandos API y Datos Básicos a Consumir:
   * Endpoint Destino: `POST https://gecer.unr.edu.ar/api/credential-batches`
   * Headers (Cabeceras de Control):
     - `Authorization`: Llevará la API Key secreta.
     - `Content-Type`: `application/json` (Le avisa a SAVIA el formato del mensaje).
   * Body (Carga Útil Básica):
     - Datos del receptor (Nombre, Apellido, Email).
     - ID de la Plantilla (El diseño de la credencial previamente creado en SAVIA).
     - Estado de publicación (`published`).

----------------------------------------------------------------------
SAVIA modelo federal | Reporte Técnico Nº: 07 | Página 1 de 1
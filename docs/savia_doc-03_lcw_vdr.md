[ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: DOC-03
ID TEMPORAL: 260618T0142 - Arquitectura Unificada y Concepto de Emisor No Reconocido
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: Traefik, Docker Compose, Trust Registry (VDR)
ESTADO: Validado por el Usuario
===========================================================

- Resumen del Concepto: "Unrecognized Issuer" (Emisor No Reconocido)
En el ecosistema de Identidad Autosoberana (SSI), la matemática criptográfica garantiza que el título es auténtico e inalterable. Sin embargo, no garantiza que la institución que firmó sea "prestigiosa" o "aprobada". El cartel amarillo de advertencia ("Links disabled - unrecognized issuer") que observamos en la captura se activa como mecanismo de defensa de la billetera. La app LCW desactiva los enlaces temporalmente porque la identidad did:web:id.unr.edu.ar aún no se encuentra inscripta en una "Lista Blanca" o Registro de Confianza (Trust Registry) que la billetera conozca.

- Justificación Técnica y Evidencia:
El estándar requiere un "Verifiable Data Registry" (VDR). La billetera móvil viene configurada de fábrica para consultar listas internacionales del MIT o de OWF. Como nuestra llave es nueva y soberana de la UNR, es completamente desconocida para el resto del mundo. 
Para solucionar esto, la arquitectura que diseñaste prevé la creación del nodo `nacional.unr.edu.ar`. Una vez que encendamos ese nodo y publiquemos allí nuestra propia lista blanca en formato JSON, le diremos a los verificadores que consulten ese archivo para validar el prestigio de la universidad.

- Configuración / Lógica Acordada:
1. Eliminar físicamente los archivos sueltos `portal.yml` y `nacional.yml`.
2. Modificar `traefik.yml` para corregir la ruta del proveedor de archivos al path interno del contenedor.
3. Integrar los contenedores `identidad-web` y el nuevo `nacional-web` directamente en el `docker-compose.yml` utilizando Traefik Labels para ruteo absoluto.

----------------------------------------------------------------------
SAVIA modelo federal | Reporte Técnico Nº: 03 | Página 1 de 1
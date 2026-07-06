### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-52
ID Temporal: 260701T1047
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Traefik, Rate Limiting, Prevencion DDoS
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
Como capa adicional al bloqueo de cuentas (Lockout) de Payload, Traefik
debe implementar un middleware de Rate Limiting. Esto evita ataques de
denegacion de servicio (DDoS) limitando la cantidad de peticiones por
segundo que una misma IP puede realizar hacia los endpoints de emision.

#### Justificacion Tecnica y Evidencia
Delegar la limitacion de trafico al proxy inverso (Traefik) protege a los
contenedores internos (Node.js/MongoDB) de la saturacion de recursos.
URL: https://doc.traefik.io/traefik/middlewares/http/ratelimit/
Cita: "The RateLimit middleware ensures that services will receive a
fair amount of requests, and allows one to define what fair is."

#### Configuracion / Logica Acordada
1. Agregar el middleware en las etiquetas del docker-compose.yml.
2. Configurar 'average' y 'burst' admisibles para el endpoint de login.
3. Asegurar que las etiquetas referencien correctamente el servicio
interno y no interfieran con la resolucion de la red_savia.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 52 | Pagina 1 de 1
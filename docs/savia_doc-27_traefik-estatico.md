### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-27
ID Temporal: 260701T0059
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Traefik Proxy, Configuracion Estatica
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
Traefik se configura a traves de dos mecanismos: estatico y dinamico.
La configuracion estatica (traefik.yml) define los puntos de entrada 
(entrypoints) del servidor, como los puertos 80 y 443, y establece a Docker
como el proveedor (provider) para el autodescubrimiento de servicios.

#### Justificacion Tecnica y Evidencia
Separar la configuracion del proxy permite que la infraestructura base no
requiera reinicios. Los servicios de backend, como el emisor DCC, pueden
conectarse o desconectarse dinamicamente sin afectar a los demas.
URL: https://doc.traefik.io/traefik/getting-started/configuration-overview/
Cita: "The static configuration sets up connections to providers and defines
the entrypoints Traefik will listen to."

#### Configuracion / Logica Acordada
1. Generar el archivo estatico traefik.yml en el host.
2. Definir entrypoints para HTTP (80) y HTTPS (443).
3. Habilitar la integracion nativa declarando 'provider: docker' y exponer
la API interna del proxy (dashboard) unicamente bajo autenticacion o en la
red virtual interna para auditoria local.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 27 | Pagina 1 de 1
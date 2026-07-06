### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-28
ID Temporal: 260701T0059
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Traefik Proxy, Enrutamiento Dinamico
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
La configuracion dinamica de Traefik se inyecta directamente mediante
etiquetas (labels) dentro del archivo docker-compose.yml de cada servicio.
Al levantar el orquestador DCC, las etiquetas indican que el trafico
dirigido a id.unr.edu.ar debe enrutarse hacia ese contenedor especifico.

#### Justificacion Tecnica y Evidencia
Esta arquitectura elimina la necesidad de mantener archivos de ruteo
manuales. Traefik detecta los metadatos de los contenedores y genera las
rutas HTTP instantaneamente.
URL: https://doc.traefik.io/traefik/providers/docker/
Cita: "Traefik reads the labels of your containers and creates the routing
configuration automatically."

#### Configuracion / Logica Acordada
1. En el docker-compose.yml, añadir etiquetas Traefik al nodo emisor.
2. Configurar la regla Host:
- "traefik.http.routers.dcc.rule=Host(`id.unr.edu.ar`)"
3. Asegurar que Traefik y el servicio emisor compartan la red puente
(red_savia) para permitir la derivacion del trafico hacia los puertos
expuestos internamente.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 28 | Pagina 1 de 1
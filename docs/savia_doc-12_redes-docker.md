### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-12
ID Temporal: 260701T0047
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Redes Docker, Aislamiento, Seguridad
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
La topologia de red del ecosistema SAVIA se basa en redes virtuales bridge
dentro de Docker. Esto garantiza que Traefik, MongoDB y la API del motor
DCC puedan comunicarse entre si mediante resolucion DNS interna, mientras
permanecen invisibles e inaccesibles desde el exterior del servidor host.

#### Justificacion Tecnica y Evidencia
El aislamiento de red previene que atacantes accedan directamente a los
puertos de la base de datos, forzando todo el trafico a traves del proxy.
URL: https://docs.docker.com/network/
Cita: "In terms of Docker, a bridge network uses a software bridge which
allows containers connected to the same bridge network to communicate."

#### Configuracion / Logica Acordada
1. Declarar una red personalizada llamada red_savia en docker-compose.yml.
2. Asignar todos los servicios del stack a esta red especifica.
3. Eliminar cualquier mapeo de puertos (ports: "27017:27017") en la base
de datos MongoDB para forzar el encapsulamiento interno absoluto.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 12 | Pagina 1 de 1
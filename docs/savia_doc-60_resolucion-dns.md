### [ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 60
ID TEMPORAL: 260701T1049 - Resolucion DNS Local (cURL)
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: DNS, Traefik, /etc/hosts
ESTADO: Consolidado
===========================================================
### [CUERPO DEL DOCUMENTO]
- Resumen del Concepto:
Para que las pruebas de inyeccion cURL desde la maquina local alcancen
a la API de SAVIA a traves de su dominio oficial (id.unr.edu.ar), es
imperativo engañar al ruteo del sistema operativo. Sin resolucion publica
durante el MVP, el trafico debe ser forzado hacia Traefik localmente.

- Justificacion Tecnica y Evidencia:
Traefik enruta basandose en el encabezado 'Host'. Si cURL apunta a
localhost, Traefik no sabra a que contenedor derivar la peticion.
URL: https://doc.traefik.io/traefik/routing/routers/
Cita: "Routers match incoming requests (by Host, Path, etc.) and forward
them to the correct services."

- Configuracion / Logica Acordada:
1. Editar el archivo /etc/hosts dentro del entorno Linux/WSL2.
2. Añadir la directiva: 127.0.0.1 id.unr.edu.ar gecer.unr.edu.ar
3. Ejecutar los comandos cURL utilizando directamente la URL con
dominio para que Traefik procese la regla Host correctamente.
----------------------------------------------------------------------
### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 60 | Pagina 1 de 1
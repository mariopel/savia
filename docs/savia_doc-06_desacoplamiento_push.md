[ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: DOC-06
ID TEMPORAL: 260618T0217 - Arquitectura de Mínima Invasión (Desacoplamiento)
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: Arquitectura Orientada a Eventos (Push), Payload CMS
ESTADO: Pendiente de Implementación
===========================================================

- Resumen del Concepto: Principio de Mínimo Privilegio y Desacoplamiento (Modelo Push)
Para ser lo menos invasivos posible con un entorno de producción, la sugerencia absoluta es optar por el **Modelo Push (Opción A)**. 
En este modelo, SAVIA funciona como una "caja negra" pasiva. No sale a buscar datos, no necesita credenciales de la base de datos del SIU, ni requiere que se abran puertos especiales en la red interna de la universidad hacia tu servidor. SAVIA simplemente se queda escuchando en su puerta principal (`gecer.unr.edu.ar/api/credential-batches`) esperando que alguien con la llave correcta le entregue un paquete.

- Justificación Técnica y Evidencia:
1. Seguridad Perimetral: Si programamos un script "Pull" dentro de SAVIA, tendríamos que almacenar credenciales críticas del SIU Guaraní dentro de tu contenedor. Si SAVIA es comprometido, el SIU también lo estaría. 
2. Estabilidad de Payload CMS: Payload está diseñado nativamente para recibir peticiones POST externas. No requiere instalar plugins ni modificar el código fuente de tu contenedor en producción para habilitar esta escucha.
3. Simulación MVP: Para tus 10 días de plazo, el modelo Push te permite simular al SIU Guaraní desde tu propia computadora usando herramientas estándar como Postman o un simple comando cURL, sin tocar ni una línea de código de los sistemas del rectorado.

- Configuración / Lógica Acordada:
Adoptaremos el flujo pasivo (Push). El sistema externo (o nuestro simulador Postman) será el único responsable de armar el paquete de datos y empujarlo hacia SAVIA.

----------------------------------------------------------------------
SAVIA modelo federal | Reporte Técnico Nº: 06 | Página 1 de 1
### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-05
ID Temporal: 260701T0040
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Arquitectura de Integracion, Push, Pull
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
En la integracion de sistemas legacy como SIU Guarani con el motor de
emision DCC, existen dos paradigmas de sincronizacion de datos: Push
(empujar) y Pull (tirar). En el modelo Push, un middleware lee la base
del SIU y dispara activamente los datos hacia la API de SAVIA (M2M). En
el modelo Pull, SAVIA deberia consultar periodicamente al SIU. SAVIA
adopta el modelo Push delegando la carga operativa al sistema origen.

#### Justificacion Tecnica y Evidencia
La arquitectura Push aisla el motor de credenciales de las reglas de
negocio externas, permitiendo que actue como un receptor agnostico.
Esto minimiza la superficie de ataque y reduce el acoplamiento
arquitectonico entre bases de datos heterogeneas.
URL: github.com/digitalcredentials/docs
Cita: "The issuing system acts as a secure endpoint, receiving batches
of credential data authenticated via bearer tokens."

#### Configuracion / Logica Acordada
1. Adoptar el modelo Push como estandar de integracion para la UNR.
2. Desarrollar un Middleware externo (script o plugin Moodle/SIU) que
consuma los endpoints /api/users/login y /api/credential-batch.
3. Asegurar que el motor SAVIA jamas almacene credenciales de acceso a
sistemas externos, manteniendo un rol pasivo y securizado.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 05 | Pagina 1 de 1
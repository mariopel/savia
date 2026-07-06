### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-32
ID Temporal: 260701T0100
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Payload CMS, Inicializacion, Backend
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
Payload CMS opera como el motor central (backend) del ecosistema SAVIA.
Administra la interfaz web (dashboard) y provee la estructura de base de
datos subyacente para almacenar usuarios con distintos roles, plantillas
de diplomas y lotes de emision M2M.

#### Justificacion Tecnica y Evidencia
El consorcio DCC eligio Payload por su capacidad de autogenerar APIs y
su integracion nativa con bases documentales, ideal para credenciales.
URL: https://github.com/digitalcredentials/docs
Cita: "The issuer core uses Payload CMS to provide the underlying
administrative dashboard and API layer for managing verifiable credentials."

#### Configuracion / Logica Acordada
1. Configurar la cadena de conexion (MONGODB_URI) en el archivo .env.
2. Inicializar Payload asegurando que el puerto 3000 quede encapsulado
en la red virtual interna (red_savia) y expuesto solo a traves de Traefik.
3. Crear el primer usuario administrador durante el despliegue inicial.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 32 | Pagina 1 de 1
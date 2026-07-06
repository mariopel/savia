### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-14
ID Temporal: 260701T0047
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Trust Registry, Ecosistema Federado
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
El Trust Registry (Registro de Confianza) es el mecanismo por el cual el
ecosistema federado reconoce a la UNR como un emisor valido. Es un
directorio descentralizado donde se asocia el DID de la universidad con
su perfil institucional, habilitando la emision de titulos oficiales.

#### Justificacion Tecnica y Evidencia
Sin registro de confianza, las credenciales tecnicamente validas son
marcadas como "No Reconocidas" por las billeteras digitales (LCW).
URL: https://github.com/digitalcredentials/docs
Cita: "A trust registry serves as a list of authorized issuers. Verifiers
rely on this registry to ensure credentials come from approved entities."

#### Configuracion / Logica Acordada
1. Configurar el perfil del emisor (Issuer Profile) dentro del motor DCC.
2. Vincular el DID oficial (did:web:id.unr.edu.ar) con los metadatos de
la institucion (nombre, logotipo SVG, descripcion).
3. Inscribir la identidad en el registro matriz nacional.unr.edu.ar.
4. Realizar una emision de prueba para verificar el tilde verde en LCW.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 14 | Pagina 1 de 1
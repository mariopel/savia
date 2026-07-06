### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-13
ID Temporal: 260701T0047
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Identidad Descentralizada, DID Web
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
El estandar did:web permite transformar el dominio oficial de la UNR en un
identificador soberano y criptografico. Consiste en alojar un documento
JSON estatico (did.json) en una ruta especifica del servidor web,
vinculando la clave publica del emisor a la autoridad del dominio web.

#### Justificacion Tecnica y Evidencia
El ecosistema DCC requiere que todo emisor posea un DID resoluble para
verificar la firma de las credenciales de los alumnos.
URL: https://w3c-ccg.github.io/did-method-web/
Cita: "The target system of the did:web method is the Domain Name System,
which is used to resolve the domain name to a web server."

#### Configuracion / Logica Acordada
1. Generar el par de claves criptograficas (Ed25519) para la universidad.
2. Construir el archivo did.json declarando la clave publica.
3. Publicar el archivo exactamente en la ruta estandarizada:
https://id.unr.edu.ar/.well-known/did.json
4. Validar la resolucion publica del documento DID via navegador.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 13 | Pagina 1 de 1
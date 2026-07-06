### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-53
ID Temporal: 260701T1047
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Ed25519, Rotacion de Claves, SSI
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
La seguridad de las credenciales W3C depende de la clave privada de la
UNR. El protocolo de seguridad exige la rotacion periodica de estas
claves. Al rotar, no se borra la clave antigua, sino que se genera un
nuevo par y se actualiza el documento did.json para mantener la validez.

#### Justificacion Tecnica y Evidencia
Mantener el historial de claves publicas en el DID asegura que las
credenciales emitidas hace años sigan siendo verificables por SACAU.
URL: https://w3c-ccg.github.io/did-method-web/
Cita: "When keys are rotated, the new verification methods are appended to
the DID document. Old keys should be retained to verify old signatures."

#### Configuracion / Logica Acordada
1. Generar un nuevo par de claves Ed25519 para el entorno de emision.
2. Actualizar el documento did.json alojado en id.unr.edu.ar añadiendo
la nueva clave publica bajo un nuevo ID (ej. #key-2).
3. Configurar el motor SAVIA para firmar los nuevos lotes con la key-2.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 53 | Pagina 1 de 1
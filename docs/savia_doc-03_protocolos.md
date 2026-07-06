### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-03
ID Temporal: 260701T0038
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: DCC, Trust Registry, W3C VC
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
Al emitir una credencial, la firma criptografica garantiza que el
documento no fue alterado. Sin embargo, si el identificador del
emisor (su DID) no esta inscripto en un Registro de Confianza (Trust
Registry), las billeteras y verificadores mostraran una advertencia
de "Emisor No Reconocido". La identidad es matematicamente valida,
pero carece de respaldo institucional publico.

#### Justificacion Tecnica y Evidencia
El ecosistema DCC utiliza registros federados para establecer
quien tiene autoridad legitima para emitir titulos. Las billeteras
(como Learner Credential Wallet) consultan estos nodos antes de
otorgar el tilde de confianza institucional.
URL: github.com/digitalcredentials/docs
Cita: "Verifiers check the issuer's decentralized identifier against
a known trust registry to confirm institutional authenticity."

#### Configuracion / Logica Acordada
1. Generar y publicar el documento DID de la universidad en la URL
oficial (did:web:id.unr.edu.ar).
2. Inscribir el Perfil del Emisor (Issuer Profile) en el registro
nacional federado (nacional.unr.edu.ar) administrado por SAVIA.
3. Validar que la aplicacion LCW reconozca la autoridad del nodo
emisor al escanear una nueva credencial universitaria.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 03 | Pagina 1 de 1
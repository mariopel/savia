### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-49
ID Temporal: 260701T1042
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: W3C VC, Interoperabilidad, Wallets
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
Aunque la billetera oficial recomendada es Learner Credential Wallet
(LCW), los titulos emitidos por la UNR son agnosticos al cliente.
Cualquier billetera digital que soporte los estandares W3C Verifiable
Credentials y JSON-LD puede almacenar y presentar las credenciales.

#### Justificacion Tecnica y Evidencia
El nucleo de la Identidad Autosoberana (SSI) es evitar el monopolio
tecnologico (vendor lock-in), asegurando que el alumno es el verdadero
dueño de sus datos institucionales.
URL: https://w3c.github.io/vc-data-model/
Cita: "Verifiable credentials are designed to be interoperable across
different wallet implementations and ecosystems."

#### Configuracion / Logica Acordada
1. Mantener estricto cumplimiento del esquema Open Badges v3.
2. La verificacion criptografica (Verifier-Plus) debe validar firmas
Ed25519 de manera transversal, sin depender de metadatos exclusivos
de la aplicacion movil LCW.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 49 | Pagina 1 de 1
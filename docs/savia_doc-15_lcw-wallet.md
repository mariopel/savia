### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-15
ID Temporal: 260701T0047
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Learner Credential Wallet, LCW
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
La Learner Credential Wallet (LCW) es la billetera movil de codigo abierto
donde el estudiante recibe, almacena y presenta sus titulos universitarios.
La integracion requiere asegurar que los enlaces profundos (deep links)
enviados por correo dirijan al alumno directamente a la aplicacion.

#### Justificacion Tecnica y Evidencia
La LCW lee el payload JSON-LD de la credencial y verifica
criptograficamente al emisor. La compatibilidad estricta con Open Badges v3
es el puente que permite la interoperabilidad total.
URL: https://github.com/openwallet-foundation-labs/learner-credential-wallet
Cita: "The Learner Credential Wallet allows users to store and share W3C
Verifiable Credentials and Open Badges v3 seamlessly."

#### Configuracion / Logica Acordada
1. Diseñar la plantilla de correo electronico (emailTemplate) incluyendo
las instrucciones para descargar la billetera en iOS/Android.
2. Configurar la variable de entorno para inyectar el deep link dinamico
que gatilla la importacion automatica de la credencial.
3. Verificar que los codigos QR generados apunten correctamente al schema
de la aplicacion movil.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 15 | Pagina 1 de 1
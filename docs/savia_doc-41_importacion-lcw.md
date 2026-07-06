### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-41
ID Temporal: 260701T1041
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: LCW, Deep Links, Importacion
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
Una vez que el lote M2M es procesado y firmado criptograficamente, el
motor SAVIA genera una URL unica de emision. Este enlace se envia por
correo y utiliza un esquema de "deep link" (enlace profundo) que abre
directamente la Learner Credential Wallet (LCW) en el celular del alumno.

#### Justificacion Tecnica y Evidencia
La especificacion exige que las billeteras intercepten el esquema de la
URL para importar el JSON-LD de la credencial sin requerir que el usuario
manipule archivos manualmente.
URL: https://github.com/openwallet-foundation-labs/learner-credential-wallet
Cita: "The wallet handles deep links for importing credentials securely and
seamlessly directly from the issuer's notification email."

#### Configuracion / Logica Acordada
1. Verificar que el emailTemplate contenga la variable {{credentialUrl}}.
2. Al abrir el correo en el movil, el enlace redirigira al esquema
registrado por la LCW (ej. lcw://import?url=...).
3. Realizar pruebas de extremo a extremo (E2E) emitiendo una credencial a
un correo de prueba y escaneando el codigo QR desde la aplicacion movil.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 41 | Pagina 1 de 1
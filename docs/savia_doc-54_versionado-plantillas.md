### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-54
ID Temporal: 260701T1047
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Credential Templates, Versionado
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
Una regla inquebrantable en SAVIA es la inmutabilidad de las plantillas
de credenciales. Si el diseño grafico o los criterios de una carrera
cambian, la plantilla original no debe editarse jamas. Se debe clonar
y crear una nueva version para no alterar el historial de los egresados.

#### Justificacion Tecnica y Evidencia
Modificar una plantilla activa puede causar desajustes criptograficos
si las billeteras (LCW) intentan re-validar los atributos contra el nuevo
esquema JSON-LD, invalidando credenciales legitimas y vigentes.
URL: https://github.com/digitalcredentials/docs
Cita: "Templates should be treated as immutable once published. For any
updates to styling or claim structure, create a new template instance."

#### Configuracion / Logica Acordada
1. Crear una nueva plantilla en Payload CMS para el nuevo plan de estudio.
2. Obtener el nuevo objectId generado por la base de datos MongoDB.
3. Actualizar el script del middleware M2M en SIU Guarani para que
apunte al nuevo ID al emitir la cohorte correspondiente.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 54 | Pagina 1 de 1
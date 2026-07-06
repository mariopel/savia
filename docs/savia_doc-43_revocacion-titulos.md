### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-43
ID Temporal: 260701T1041
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Revocacion, Status List 2021
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
Si un titulo universitario es anulado por resolucion administrativa, el
motor SAVIA no puede borrar el archivo del celular del alumno. En su
lugar, utiliza el estandar Status List 2021. Actualiza un mapa de bits
publico indicando que el indice de esa credencial especifica ha sido
revocado.

#### Justificacion Tecnica y Evidencia
El mecanismo de revocacion descentralizada permite a los verificadores
consultar el estado en tiempo real sin violar la privacidad del titular,
ya que el mapa de bits esta comprimido y anonimizado.
URL: https://github.com/digitalcredentials/docs
Cita: "The issuer supports the Status List 2021 specification, allowing
credentials to be revoked or suspended via a hosted bitstring."

#### Configuracion / Logica Acordada
1. Acceder al dashboard de Payload CMS en SAVIA.
2. Localizar la credencial emitida en la coleccion correspondiente.
3. Cambiar el estado a "Revoked". Esto actualizara automaticamente el
documento StatusList alojado en id.unr.edu.ar.
4. Verifier-Plus consultara este indice y marcara el titulo como invalido.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 43 | Pagina 1 de 1
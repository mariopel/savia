### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-42
ID Temporal: 260701T1041
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: VP, SACAU, Verifier-Plus
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
Cuando un egresado necesita demostrar su titulo ante un empleador o en la
transicion a otra universidad (estandar SACAU 2027), no envia la
credencial original. En su lugar, la billetera (LCW) genera una
Presentacion Verificable (VP), un paquete criptografico derivado.

#### Justificacion Tecnica y Evidencia
Las VPs permiten al titular de la credencial compartir sus datos de forma
segura y probatoria. Verifier-Plus desempaqueta esta presentacion para
validar la firma del emisor original (UNR) y la integridad del titulo.
URL: https://github.com/digitalcredentials/verifier-plus
Cita: "Verifier Plus validates W3C Verifiable Presentations, ensuring the
holder is the legitimate owner and the issuer's signature is intact."

#### Configuracion / Logica Acordada
1. Utilizar la instancia local de Verifier-Plus (contenedor verifier-1).
2. Solicitar al alumno que comparta su titulo desde la LCW, generando un
archivo .jsonp o un enlace de presentacion.
3. Subir la Presentacion Verificable a Verifier-Plus para comprobar el
estado de la firma y la validez contra el Trust Registry.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 42 | Pagina 1 de 1
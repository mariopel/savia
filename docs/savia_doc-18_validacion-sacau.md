### [ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 18
ID TEMPORAL: 260701T0050 - Motor de Validacion SACAU
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: Verifier-Plus, SACAU, Node.js
ESTADO: Consolidado
===========================================================
### [CUERPO DEL DOCUMENTO]
- Resumen del Concepto:
De cara a la transicion al estandar SACAU para 2027, SAVIA incorpora
el servicio Verifier-Plus. Este modulo permite verificar la validez
criptografica de las credenciales recibidas o emitidas localmente
a traves de una interfaz web independiente.

- Justificacion Tecnica y Evidencia:
Verifier-Plus es la aplicacion oficial del consorcio para validar
Credenciales Verificables y Open Badges v3 de manera descentralizada.
URL: https://github.com/digitalcredentials/verifier-plus
Cita: "Verifier Plus is a web application that allows users to verify
the cryptographic signature and status of W3C Verifiable Credentials."

- Configuracion / Logica Acordada:
1. Instalar instancia local de Verifier-Plus (Node.js 18.20.8).
2. Clonar el repositorio oficial e integrarlo a la orquestacion.
3. Como regla inquebrantable, definir explicitamente el nombre del
contenedor en el docker-compose.yml (ej. container_name: verifier-1)
para evitar fallos de resolucion "No such container" en la red.
----------------------------------------------------------------------
### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 18 | Pagina 1 de 1
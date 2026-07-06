### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-23
ID Temporal: 260701T0055
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Arquitectura, MVP, Alcance Federal
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
El desarrollo de SAVIA requiere un equilibrio estrategico entre dos
enfoques: el proyecto headless integrado via API con SIU Guarani, y
el MVP de Emision DCC con alcance nacional federado. Se acordo
priorizar estrategicamente el enfoque institucional (integracion M2M)
sin perder la arquitectura descentralizada que otorga alcance nacional.

#### Justificacion Tecnica y Evidencia
Mantener un diseño modular permite satisfacer la demanda inmediata de
la universidad (emision M2M) mientras se preserva el marco normativo
y la escalabilidad hacia una red nacional (Trust Registry).
URL: https://github.com/digitalcredentials/docs
Cita: "A flexible architecture allows institutions to integrate with
legacy systems while participating in decentralized federations."

#### Configuracion / Logica Acordada
1. Priorizar la integracion via API REST para el sistema SIU Guarani.
2. Asegurar que los componentes de red y los registros de confianza
(id.unr.edu.ar, nacional.unr.edu.ar) sigan configurados para habilitar
la validacion cruzada de credenciales a nivel federal (SACAU).

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 23 | Pagina 1 de 1
### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-24
ID Temporal: 260701T0055
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Git Submodules, Verifier-Plus
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
Al integrar componentes desarrollados por terceros (como el motor de
validacion Verifier-Plus del DCC), se utiliza el mecanismo de Git
Submodules. Esto permite anidar un repositorio dentro de otro,
manteniendo la referencia a una version especifica del codigo original
sin mezclar su historial con el del proyecto principal (SAVIA).

#### Justificacion Tecnica y Evidencia
Los submodulos garantizan que SAVIA siempre ejecute una version
auditada e inmutable de Verifier-Plus, facilitando actualizaciones
controladas desde el repositorio oficial del MIT/DCC.
URL: https://git-scm.com/docs/git-submodule
Cita: "Submodules allow foreign repositories to be embedded within a
dedicated subdirectory of the source tree, always pointed at a
particular commit."

#### Configuracion / Logica Acordada
1. Integrar el repositorio oficial de verifier-plus como submodulo.
2. Evitar la modificacion directa del codigo dentro del directorio del
submodulo; cualquier configuracion personalizada debe inyectarse a
traves de variables de entorno (archivos .env).

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 24 | Pagina 1 de 1
### [ENCABEZADO DE DOCUMENTO]
Nº: DOC-21
ID Temporal: 260701T0055
Proyecto: SAVIA - UNR | GARANTE METARED
Tecnologias: Git, Commit, Versionado Local
Estado: Consolidado

### [CUERPO DEL DOCUMENTO]
#### Resumen del Concepto
El comando 'git commit' es el mecanismo mediante el cual se consolida
una version inmutable del estado del proyecto en el repositorio local.
A diferencia de simplemente guardar un archivo, el commit genera una
firma criptografica (hash) que documenta quien hizo el cambio, cuando
lo hizo y que archivos exactos fueron modificados.

#### Justificacion Tecnica y Evidencia
La trazabilidad del codigo base requiere que cada hito arquitectonico
quede registrado para permitir auditorias o reversiones seguras.
URL: https://git-scm.com/docs/git-commit
Cita: "Record changes to the repository. Stores the current contents
of the index in a new commit along with a log message from the user."

#### Configuracion / Logica Acordada
1. Antes de realizar un commit, los archivos deben pasar al area de
preparacion utilizando el comando 'git add'.
2. Todo commit debe llevar un mensaje descriptivo y estructurado
(ej. 'feat: orquestacion base con docker-compose') para que el
historial sea legible por humanos y maquinas.

### [PIE DE PAGINA]
SAVIA modelo federal | Reporte Tecnico Nº: 21 | Pagina 1 de 1
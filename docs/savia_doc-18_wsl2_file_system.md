[ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: DOC-18
ID TEMPORAL: 260618T2314 - Topología de Archivos en WSL2 (File System)
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: WSL2 (ext4), Windows NTFS, Docker I/O
ESTADO: Sugerencia Arquitectónica
===========================================================

- Resumen del Concepto: La Frontera de los Discos Duros (Windows vs. Linux)
Cuando instalás WSL2, tu computadora pasa a tener dos "mundos" de archivos conviviendo al mismo tiempo:
1. El mundo Windows (NTFS): Tu clásico `C:\Users\Mario\Documentos`.
2. El mundo Linux (ext4): Un disco duro virtual encapsulado cuya raíz de usuario es `/home/tu_usuario_linux/` (también conocido con el símbolo de la tilde: `~`).

- Justificación Técnica y Evidencia (La Regla de Oro de WSL2):
Aunque desde Linux podés ver y editar los archivos de Windows (a través de la ruta montada `/mnt/c/...`), **NUNCA debes guardar tus proyectos de Docker allí.**
Si guardás la carpeta `savia` en tu disco de Windows y le pedís al Docker de Linux que la lea, la información tiene que cruzar constantemente la "frontera" entre ambos mundos. Esto genera dos problemas catastróficos:
1. Penalización masiva de rendimiento: La lectura/escritura de bases de datos (MongoDB) será un 90% más lenta.
2. Destrucción de permisos: Como vimos en sesiones anteriores, archivos como `acme.json` de Traefik y tus claves de identidad requieren permisos estrictos de Linux (`chmod 600`). Windows NTFS no entiende esos permisos y te dará error al levantar los contenedores.

- Configuración / Lógica Acordada (La Ubicación Correcta):
La carpeta raíz de tu proyecto `savia` debe ir **estrictamente dentro del mundo Linux**. 
Cuando abras la terminal de tu nuevo Ubuntu en WSL2, simplemente vas a arrancar en tu carpeta personal (ejemplo: `/home/mario`). Allí mismo es donde vas a clonar o copiar tu proyecto. 
La ruta final correcta y definitiva será: `~/savia` (que es exactamente la misma ruta que usamos en Traefik en el Reporte DOC-03).

----------------------------------------------------------------------
SAVIA modelo federal | Reporte Técnico Nº: 18 | Página 1 de 1
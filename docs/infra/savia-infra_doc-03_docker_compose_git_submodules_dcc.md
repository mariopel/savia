chat: savia-infra
[ENCABEZADO DE DOCUMENTO]
===========================================================
REPORTE Nº: 03
ID TEMPORAL: 260621T0215 - Orquestación Base e Integración del Motor Verificador DCC
PROYECTO: SAVIA - Saberes y Aptitudes Verificables con Identidad Autónoma
TECNOLOGÍAS: Git Submodules, Docker Compose, Node.js, DCC Verifier-Plus
ESTADO: Validado por el Usuario
===========================================================
[CUERPO DEL DOCUMENTO]
- Resumen del Concepto:
Instanciación del core transaccional de SAVIA mediante una arquitectura desacoplada (Headless). Se importó el motor oficial de verificación criptográfica (verifier-plus) del Digital Credentials Consortium utilizando submódulos de Git, preservando la integridad del versionado upstream. Se estableció el plano de orquestación (docker-compose.yml) con una red virtual interna aislada, y se blindó la capa de configuración inyectando parámetros a través de un archivo de variables de entorno (.env) protegido por políticas de exclusión. Finalmente, se compiló y ejecutó el contenedor del verificador en segundo plano (modo detached), comprobando su disponibilidad en la red local.

- Configuración / Lógica Acordada (Infraestructura Documentada):

Paso 1: Integración del motor Verifier-Plus de DCC como submódulo de Git
- Justificación: Incorporar repositorios externos mediante submódulos permite mantener el código oficial de DCC aislado y actualizable sin ensuciar el historial de transacciones M2M de SAVIA. (Fuente: Digital Credentials Consortium - Verification Tools).
- Ejecución (COD-10):
--------------------------------------------------
cd ~/savia
mkdir -p core-dcc
git submodule add https://github.com/digitalcredentials/verifier-plus.git core-dcc/verifier-plus
git commit -m "feat: integracion de submódulo verifier-plus para validaciones SACAU"
--------------------------------------------------

Paso 2: Creación del orquestador base docker-compose.yml para SAVIA
- Justificación: Aislar los entornos mediante redes personalizadas garantiza que los servicios solo se expongan según sea necesario, estructurando el "plano arquitectónico" de los microservicios. (Fuente: Documentación Oficial de Docker Compose).
- Ejecución (COD-11):
--------------------------------------------------
cat << 'EOF' > docker-compose.yml
version: '3.8'
services:
  verifier:
    container_name: savia_verifier
    build:
      context: ./core-dcc/verifier-plus
      dockerfile: Dockerfile
    ports:
      - "3000:3000"
    networks:
      - savia-network
    restart: unless-stopped
    environment:
      - NODE_ENV=development
networks:
  savia-network:
    driver: bridge
    name: savia_internal_net
EOF
git add docker-compose.yml
git commit -m "feat: orquestacion base con docker-compose y servicio verifier"
--------------------------------------------------

Paso 3: Creación del archivo de variables de entorno (.env)
- Justificación: Para el desarrollo y configuración de parámetros institucionales (sigla, registro oficial, DIDs), las aplicaciones basadas en DCC requieren definir estas variables fuera del código fuente por seguridad criptográfica.
- Ejecución (COD-12):
--------------------------------------------------
cat << 'EOF' > .env
NODE_ENV=development
PORT=3000
SAVIA_SIGLA=SAV
SAVIA_REGISTRO_OFICIAL=nacional.unr.edu.ar
SAVIA_DID_ACTIVO=did:web:id.unr.edu.ar
EOF
--------------------------------------------------

Paso 4: Inicialización y validación del contenedor verifier-plus
- Justificación: La ejecución en modo "detached" (-d) permite levantar contenedores completos en segundo plano, liberando la terminal para consultar el estado (ps) o leer la salida estándar (logs).
- Ejecución (COD-13):
--------------------------------------------------
docker compose up -d --build
docker compose ps
docker compose logs --tail=20 verifier
--------------------------------------------------
----------------------------------------------------------------------
[PIE DE PÁGINA]
SAVIA modelo federal | Reporte Técnico Nº: 03 | Página 1 de 1


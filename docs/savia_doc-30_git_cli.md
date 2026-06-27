[ENCABEZADO DE DOCUMENTO]
===========================================================
ARCHIVO: SAVIA_DOC-30_Primer-Commit-GitOps.md
ID TEMPORAL: 260625T2241 - Empaquetado y Sincronización Inicial (Origin Push)
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: Git CLI, GitHub, GitOps
ESTADO: Pendiente de Implementación
===========================================================

[CUERPO DEL DOCUMENTO]
- Resumen del Concepto: Consolidación y Sincronización Segura
Al ejecutar los comandos de sincronización, el motor Git escaneará tu carpeta `~/savia/`. Gracias al escudo `.gitignore` que creamos previamente, el motor ignorará cualquier llave privada, semilla o variable de entorno (`.env`). Agrupará únicamente tu código estructural, tu `docker-compose.yml` y tu documentación en un "paquete" (Commit) y lo enviará (Push) de forma encriptada a tu bóveda privada en GitHub.

- Justificación Técnica y Evidencia:
El flujo de control de versiones es el paso fundamental exigido por los repositorios del consorcio para mantener la infraestructura como código.
* URL de la fuente: `https://github.com/digitalcredentials/dcc-admin-dashboard`
* Párrafo de soporte: Las mejores prácticas operativas dictan que cualquier modificación en la infraestructura local (como la inyección del `DEFAULT_ISSUER_DID` o la configuración de Traefik) debe ser consolidada mediante herramientas de control de versiones antes de desplegarse en entornos de producción u otras terminales institucionales.

- Configuración / Lógica Acordada:
Se utilizarán los comandos nativos de Git desde la terminal de WSL2 (dentro de Antigravity) para añadir los archivos modificados, crear el punto de restauración y enviarlos a la rama principal (main) del repositorio remoto.

# ==============================================================================
# COD-06
# ID: 260625T2241 | Fecha: 2026-06-25 | Versión: 1.0.0
# Descripción: Script Git para sincronización segura del entorno local a GitHub
# ==============================================================================
# 1. Aseguramos estar posicionados en la carpeta raíz del proyecto
cd ~/savia

# 2. Preparamos todos los archivos (el .gitignore bloqueará automáticamente los secretos)
git add .

# 3. Empaquetamos los cambios con un mensaje claro que documente el hito
git commit -m "feat: consolidacion fase 4 - integracion did:web, perimetro de seguridad y documentacion docs as code"

# 4. Sincronizamos (empujamos) el paquete hacia el repositorio privado en GitHub
git push origin main

----------------------------------------------------------------------
[PIE DE PÁGINA]
SAVIA modelo federal | Archivo: SAVIA_DOC-30_Primer-Commit-GitOps.md | Página 1 de 1
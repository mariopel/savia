[ENCABEZADO DE DOCUMENTO]
===========================================================
ARCHIVO: SAVIA_DOC-27_Auditoria-Criptografica.md
ID TEMPORAL: 260625T2148 - Auditoría Forense de Llaves y Resolución de DID
PROYECTO: SAVIA - UNR | GARANTE METARED
TECNOLOGÍAS: W3C DIDs, Ed25519, JSON-LD
ESTADO: Pendiente de Implementación
===========================================================

- Resumen del Concepto: El Desvío hacia `did:key` vs. `did:web`
En la credencial que emitiste, el identificador del emisor quedó sellado como `"id": "did:key:z6MkftDck..."`[cite: 70]. Aunque esto es criptográficamente válido, en un modelo federal (SSI) esto impide que el Registro Nacional y la billetera LCW validen el dominio de la universidad. El objetivo del proyecto SAVIA es que el emisor sea estrictamente `"id": "did:web:id.unr.edu.ar"`. Este desvío ocurre cuando Payload CMS o el Signing Service no tienen forzadas las variables de entorno para usar el método web.

- Justificación Técnica y Evidencia:
El consorcio W3C y DCC especifican que para anclar la confianza a un dominio DNS (como el de la UNR), el método de resolución debe ser explícito.
* URL de la fuente: `https://github.com/digitalcredentials/signing-service`
* Párrafo de soporte: *"To use did:web, the tenant must be configured with `didMethod: 'web'` and `didUrl: '<domain>'`. If not provided, the system defaults to the did:key method derived from the tenant seed."*
Nuestra misión ahora es asegurar que el archivo `did.json` público esté perfectamente posicionado en tu entorno local antes de forzar estas variables en Docker.

- Configuración / Lógica Acordada:
1. Validamos que el archivo `did.json` es sintácticamente perfecto.
2. Deberás crear la ruta en tu entorno local WSL2: `~/savia/sites/id.unr.edu.ar/.well-known/`
3. Dentro de esa carpeta, crearás el archivo `did.json` y pegarás el bloque de código a continuación.

# ==============================================================================
# COD-04 | ID: 260625T2148 | Fecha: 2026-06-25 | Versión: 2.0.0-PROD
# Descripción: Documento DID Oficial de la UNR (Método did:web)
# ==============================================================================
{
  "@context": [
    "https://www.w3.org/ns/did/v1",
    "https://w3id.org/security/suites/ed25519-2020/v1"
  ],
  "id": "did:web:id.unr.edu.ar",
  "verificationMethod": [
    {
      "id": "did:web:id.unr.edu.ar#key-1",
      "type": "Ed25519VerificationKey2020",
      "controller": "did:web:id.unr.edu.ar",
      "publicKeyMultibase": "z6MkftDckBBzhceTWQvKcnKffWFofqMBUutqg3JujPquL2wA"
    }
  ],
  "assertionMethod": [
    "did:web:id.unr.edu.ar#key-1"
  ],
  "authentication": [
    "did:web:id.unr.edu.ar#key-1"
  ]
}

----------------------------------------------------------------------
SAVIA modelo federal | Archivo: SAVIA_DOC-27_Auditoria-Criptografica.md | Página 1 de 1
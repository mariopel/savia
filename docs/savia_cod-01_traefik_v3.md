# ==============================================================================
# COD-01
# ID: 260618T0142
# Fecha: 2026-06-18
# Versión: 1.3.5-PROD
# Descripción: Configuración estática Traefik con path interno corregido.
# ==============================================================================
api:
  dashboard: true
  insecure: false

entryPoints:
  web:
    address: ":80"
    http:
      redirections:
        entryPoint: { to: websecure, scheme: https }
  websecure:
    address: ":443"
  traefik:
    address: ":8080"

providers:
  docker: { exposedByDefault: false }
  file:
    # Apuntamos estrictamente a la ruta interna del contenedor (volumen mapeado)
    directory: /etc/traefik/dynamic
    watch: true

certificatesResolvers:
  letsencrypt:
    acme:
      email: mariopel@gmail.com      storage: /etc/traefik/acme/acme.json
      httpChallenge: { entryPoint: web }
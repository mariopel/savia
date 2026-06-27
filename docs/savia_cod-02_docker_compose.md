# ==============================================================================
# COD-02
# ID: 260618T0142
# Fecha: 2026-06-18
# Versión: 2.16.103.0
# Descripción: Master stable unificado. Contenedores identidad y nacional integrados.
# ==============================================================================
services:
  traefik:
    image: traefik:v3.0
    container_name: sav-traefik
    restart: unless-stopped
    environment:
      - TRAEFIK_API_INSECURE=true
      - TRAEFIK_API_DASHBOARD=true
    ports:
      - "80:80"
      - "443:443"
      - "127.0.0.1:8080:8080"
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock:ro
      - ./traefik/acme:/etc/traefik/acme
      - ./traefik/traefik.yml:/etc/traefik/traefik.yml
      - ./traefik/dynamic:/etc/traefik/dynamic
    networks: [sav-net]

  sav-assets:
    image: nginx:alpine
    container_name: sav-assets
    restart: unless-stopped
    volumes:
      - ../assets:/usr/share/nginx/html/assets:ro
    networks: [sav-net]
    labels:
      - "traefik.enable=true"
      - "traefik.http.routers.assets.rule=Host(`gecer.unr.edu.ar`) && PathPrefix(`/assets/`)"
      - "traefik.http.routers.assets.entrypoints=websecure"
      - "traefik.http.routers.assets.tls=true"
      - "traefik.http.services.assets.loadbalancer.server.port=80"
      - "traefik.http.routers.assets.priority=100"
      # INYECCIÓN FORENSE: Cabeceras CORS Universales obligatorias para LCW
      - "traefik.http.middlewares.assets-cors.headers.accesscontrolallowmethods=GET,OPTIONS"
      - "traefik.http.middlewares.assets-cors.headers.accesscontrolalloworiginlist=*"
      - "traefik.http.middlewares.assets-cors.headers.accesscontrolmaxage=100"
      - "traefik.http.routers.assets.middlewares=assets-cors"

  mongodb:
    image: mongo:latest
    container_name: sav-mongodb
    environment:
      - MONGO_INITDB_ROOT_USERNAME=root
      - MONGO_INITDB_ROOT_PASSWORD=Clave01mpUNR
    command: mongod --replSet rs0 --keyFile /opt/mongo/mongodb_keyfile --bind_ip_all
    volumes:
      - sav-db-data:/data/db
      - ./mongodb_keyfile:/opt/mongo/mongodb_keyfile:ro
    healthcheck:
      test: ["CMD", "mongosh", "--eval", "db.adminCommand('ping')"]
      interval: 10s
    networks: [sav-net]

  redis:
    image: redis:alpine
    container_name: sav-redis
    networks: [sav-net]

  status:
    image: digitalcredentials/status-service-db:0.1.0
    container_name: sav-status
    environment:
      - CRED_STATUS_SERVICE=mongodb
      - CRED_STATUS_DB_URL=mongodb://root:Clave01mpUNR@mongodb:27017/savia_unr_db?authSource=admin
      - CRED_STATUS_DID_SEED=z1AmYHFFkczckDJ3Jf9k3vcrFVQrrdUPNuoi3Af2JXNxC6B
      - STATUS_CRED_SITE_ORIGIN=https://gecer.unr.edu.ar/api/coordinator/status
      - PORT=4008
      - ENABLE_HTTPS_FOR_DEV=false
    networks: [sav-net]

  signing:
    image: digitalcredentials/signing-service:1.2.0
    container_name: sav-signing
    environment:
      - TENANT_SEED_UNR=z1AmYHFFkczckDJ3Jf9k3vcrFVQrrdUPNuoi3Af2JXNxC6B
      - TENANT_SEED_DEFAULT=z1AmYHFFkczckDJ3Jf9k3vcrFVQrrdUPNuoi3Af2JXNxC6B
      - TENANT_SEED_TEST=z1AmYHFFkczckDJ3Jf9k3vcrFVQrrdUPNuoi3Af2JXNxC6B
      - TENANT_SEED_TESTING=z1AmYHFFkczckDJ3Jf9k3vcrFVQrrdUPNuoi3Af2JXNxC6B
      - TENANT_DIDMETHOD_DEFAULT=web
      - TENANT_DID_URL_DEFAULT=id.unr.edu.ar
      - PORT=4006
    ports:
      - "127.0.0.1:4006:4006"
    networks: [sav-net]

  payload:
    image: digitalcredentials/dcc-admin-dashboard:1.0.1
    container_name: sav-payload
    restart: unless-stopped
    environment:
      - NODE_ENV=production
      - TRUST_PROXY=true
      - SERVER_URL=https://gecer.unr.edu.ar
      - PAYLOAD_PUBLIC_SERVER_URL=https://gecer.unr.edu.ar
      - CORS=https://gecer.unr.edu.ar
      - CSRF=https://gecer.unr.edu.ar
      - CLAIM_PAGE_URL=https://gecer.unr.edu.ar/claim
      - COORDINATOR_URL=http://sav-coordinator:4005
      - DEFAULT_ISSUER_DID=did:web:id.unr.edu.ar
      - MONGODB_URI=mongodb://root:Clave01mpUNR@mongodb:27017/savia_unr_db?authSource=admin&replicaSet=rs0
      - REDIS_URL=redis
      - PAYLOAD_SECRET=ClaveSecretaSavia2026
      - SMTP_HOST=smtp.unr.edu.ar
      - SMTP_PORT=587
      - SMTP_USER=mario.pellegrini@unr.edu.ar
      - SMTP_PASS=Clave01mpUNR
      - EMAIL_FROM=mario.pellegrini@unr.edu.ar
    volumes:
      - ./payload_build:/home/node/app/build
    networks: [sav-net]
    depends_on:
      mongodb: { condition: service_healthy }
    labels:
      - "traefik.enable=true"
      - "traefik.http.routers.payload.rule=Host(`gecer.unr.edu.ar`) && (PathPrefix(`/admin`) || PathPrefix(`/api`))"
      - "traefik.http.routers.payload.entrypoints=websecure"
      - "traefik.http.routers.payload.tls=true"
      - "traefik.http.services.payload.loadbalancer.server.port=3000"

  coordinator:
    image: digitalcredentials/workflow-coordinator:1.0.1
    container_name: sav-coordinator
    environment:
      - MONGODB_URI=mongodb://root:Clave01mpUNR@mongodb:27017/savia_unr_db?authSource=admin&replicaSet=rs0
      - SIGNING_SERVICE_ENDPOINT=sav-signing:4006
      - PUBLIC_EXCHANGE_HOST=https://gecer.unr.edu.ar/api
      - ENABLE_STATUS_SERVICE=true
    networks: [sav-net]

  claim-page:
    image: digitalcredentials/admin-dashboard-claim-page:1.1.0
    container_name: sav-claim-page
    environment:
      - PUBLIC_PAYLOAD_URL=https://gecer.unr.edu.ar/api
    networks: [sav-net]

  transactions:
    image: digitalcredentials/transaction-service:0.3.0
    container_name: sav-transactions
    networks: [sav-net]

  identidad-web:
    image: nginx:alpine
    container_name: sav-identidad
    restart: unless-stopped
    volumes:
      - ../sites/id.unr.edu.ar:/usr/share/nginx/html:ro
    networks:
      - sav-net
    labels:
      - "traefik.enable=true"
      - "traefik.http.routers.identidad.rule=Host(`id.unr.edu.ar`)"
      - "traefik.http.routers.identidad.entrypoints=websecure"
      - "traefik.http.routers.identidad.tls=true"
      - "traefik.http.services.identidad.loadbalancer.server.port=80"
      
  nacional-web:
    image: nginx:alpine
    container_name: sav-nacional
    restart: unless-stopped
    volumes:
      - ../sites/nacional.unr.edu.ar:/usr/share/nginx/html:ro
    networks:
      - sav-net
    labels:
      - "traefik.enable=true"
      - "traefik.http.routers.nacional.rule=Host(`nacional.unr.edu.ar`)"
      - "traefik.http.routers.nacional.entrypoints=websecure"
      - "traefik.http.routers.nacional.tls=true"
      - "traefik.http.services.nacional.loadbalancer.server.port=80"

networks:
  sav-net: { name: savia_sav-net, external: true }
volumes:
  sav-db-data: { name: savia_sav-db-data }
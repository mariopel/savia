chat: savia-infraCOD-07
ID: 260620T1945
Fecha: 20/06/2026
Versión: 1.0
Descripción: Configuración global de identidad Git y generación de claves SSH Ed25519

Bash
# 1. Configurar identidad global para los registros de SAVIA (Reemplazar con tus datos)
git config --global user.name "Tu Nombre"
git config --global user.email "tu_correo@ejemplo.com"

# 2. Generar el par de claves SSH (Presiona la tecla ENTER a cada pregunta para aceptar las rutas y dejar sin contraseña extra)
ssh-keygen -t ed25519 -C "tu_correo@ejemplo.com"

# 3. Iniciar el agente SSH nativo en segundo plano
eval "$(ssh-agent -s)"

# 4. Añadir la llave privada recién creada a tu agente SSH
ssh-add ~/.ssh/id_ed25519

# 5. Imprimir en pantalla tu clave PÚBLICA (debes copiar el resultado que empieza con 'ssh-ed25519')
cat ~/.ssh/id_ed25519.pub

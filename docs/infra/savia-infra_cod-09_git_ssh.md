chat: savia-infra
COD-09
ID: 260620T2258
Fecha: 20/06/2026
Versión: 1.0
Descripción: Vinculación del repositorio local de SAVIA con GitHub (Remote Origin)

Bash
# 1. Aseguramos estar en la rama main
git branch -M main

# 2. Añadimos el repositorio remoto usando el protocolo SSH (Reemplazar valores entre <>)
git remote add origin git@github.com:<TU_USUARIO>/<NOMBRE_DEL_REPO>.git

# 3. Validamos que el remoto se haya guardado correctamente
git remote -v

# 4. Empujamos el código inicial a la nube y vinculamos la rama local con la remota (-u upstream)
git push -u origin main

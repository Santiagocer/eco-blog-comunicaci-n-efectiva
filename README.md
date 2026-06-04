# Eco Blog — Subir cambios a GitHub

Este README resume los pasos para gestionar el repositorio y subir cambios a GitHub desde tu máquina (Windows / PowerShell).

## Comprobaciones iniciales
```powershell
cd "c:\Users\Santiago\Documents\SCHOOL\Semestre 2\Comunicación efectiva 2\Parcial 3\Página web blog\v1.0"
git status
git branch
```

## Añadir remoto (si no existe)
```powershell
git remote add origin https://github.com/Santiagocer/eco-blog-comunicaci-n-efectiva.git
git remote -v
```

## Hacer commit de cambios locales
```powershell
git add .
git status
git commit -m "Mensaje claro del cambio"
```
(Si ya has hecho commits, omite `git commit`.)

## Traer cambios remotos antes de empujar (recomendado)
```powershell
git fetch origin
git pull --rebase origin main
```
Si aparecen conflictos: edita los archivos afectados, luego:
```powershell
git add <archivos_resueltos>
git rebase --continue
```

## Empujar y fijar upstream
```powershell
git push -u origin main
```
Para pushes futuros:
```powershell
git add .
git commit -m "Descripción corta"
git pull --rebase origin main
git push
```

## Autenticación
- HTTPS: GitHub pedirá credenciales; usa un Personal Access Token (PAT) en lugar de la contraseña. Genera uno en GitHub → Settings → Developer settings → Personal access tokens (marca scope `repo`).
- SSH (recomendado para evitar pedir credenciales):
```powershell
ssh-keygen -t ed25519 -C "tu-email@example.com"
# Luego copia el contenido de ~/.ssh/id_ed25519.pub a GitHub > Settings > SSH and GPG keys
# Cambia el remoto a SSH si quieres:
git remote set-url origin git@github.com:Santiagocer/eco-blog-comunicaci-n-efectiva.git
```

## Crear repo desde la terminal (opcional, con GitHub CLI `gh`)
```powershell
# requiere gh autenticado
gh repo create Santiagocer/eco-blog-comunicaci-n-efectiva --public --source=. --remote=origin --push
```

## Comandos útiles
- Ver remotos: `git remote -v`
- Ver historial: `git log --oneline --graph --decorate -n 20`
- Cambiar/crear rama: `git checkout -b mi-rama` / `git checkout main`
- Ver diferencias: `git diff`

---
Si quieres, puedo:
- Generar un PAT y guiarte en cómo usarlo (te muestro pasos seguros), o
- Generar una clave SSH aquí y mostrarte la pública para añadir a GitHub.

Archivo creado: `README.md` (en la raíz del proyecto).
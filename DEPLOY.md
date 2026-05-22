# Deploy JumpMarkers website → GitHub Pages + Porkbun

## 1. Crear repo en GitHub

1. Ve a https://github.com/new
2. Nombre del repo: `jumpmarkers-website` (o `jumpmarkers.com`)
3. Público · sin README · Create repository

## 2. Subir los archivos

```bash
cd "E:\creaciones_AI\Jump Markers\website"
git init
git add .
git commit -m "Initial website"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/jumpmarkers-website.git
git push -u origin main
```

## 3. Activar GitHub Pages

1. En GitHub → tu repo → **Settings** → **Pages**
2. Source: `Deploy from a branch` → Branch: `main` → `/ (root)`
3. Save → espera ~1 minuto → te da una URL `https://tu-usuario.github.io/jumpmarkers-website`

## 4. Conectar dominio en GitHub Pages

1. En **Pages → Custom domain** escribe: `jumpmarkers.com`
2. Activa **Enforce HTTPS**
3. GitHub te pedirá añadir registros DNS en Porkbun

## 5. DNS en Porkbun

Ve a https://porkbun.com → tu dominio → **DNS** y añade estos registros:

### Registros A (para jumpmarkers.com)
| Type | Host | Answer         | TTL  |
|------|------|----------------|------|
| A    | @    | 185.199.108.153 | 600 |
| A    | @    | 185.199.109.153 | 600 |
| A    | @    | 185.199.110.153 | 600 |
| A    | @    | 185.199.111.153 | 600 |

### Registro CNAME (para www.jumpmarkers.com)
| Type  | Host | Answer                          | TTL  |
|-------|------|---------------------------------|------|
| CNAME | www  | TU_USUARIO.github.io            | 600  |

### Archivo CNAME en el repo
Crea un archivo llamado `CNAME` (sin extensión) en la carpeta website con este contenido:
```
jumpmarkers.com
```

## 6. Actualizar URLs en index.html

Busca y reemplaza estas cadenas en `index.html`:
- `EXTENSION_ID` → el ID real de tu extensión en Chrome Web Store
- `YOURSTORE.lemonsqueezy.com/buy/PRODUCT_ID` → tu URL real de Lemon Squeezy

## 7. Propagación

- DNS tarda entre 5 minutos y 24 horas en propagarse
- Puedes comprobar el estado en https://dnschecker.org/#A/jumpmarkers.com

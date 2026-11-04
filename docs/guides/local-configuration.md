# Configuración Local - Epic Things Platform

**Versión:** 1.0  
**Fecha:** 2026-09-01  
**Audiencia:** Desarrolladores

---

## Requisitos Previos

Antes de empezar, asegúrate de tener instalado:

| Herramienta | Versión Mínima | ¿Cómo Verificar? |
| :--- | :--- | :--- |
| **Docker Desktop** | 24.0+ | `docker --version` |
| **Docker Compose** | 2.20+ | `docker compose version` |
| **Node.js** | 18.x LTS | `node --version` |
| **npm** | 9.x+ | `npm --version` |
| **Git** | 2.40+ | `git --version` |
| **Python** | 3.11+ | `python --version` |

### ¿No tienes Docker?

Descarga Docker Desktop desde: https://www.docker.com/products/docker-desktop

**Requisitos de sistema:**
- **RAM:** 8GB mínimo (16GB recomendado)
- **Disco:** 20GB libres
- **CPU:** 4 cores mínimo

---

## 1. Clonar el Repositorio

```bash
# Clonar el repositorio
git clone https://github.com/Alepro418/epic-things-platform.git

# Entrar al directorio
cd epic-things-platform

# Verificar que estás en la rama correcta
git branch
# Debería mostrar: * main
```

## 2. Configurar variables de entorno

# Copiar el archivo de ejemplo
cp .env.example .env

# Editar el archivo .env con tus valores
# (usa tu editor favorito: nano, vim, code, etc.)
nano .env

# Base de datos
POSTGRES_PASSWORD=tu_password_seguro

# JWT (genera uno aleatorio para desarrollo)
JWT_SECRET=tu_secreto_jwt_muy_largo_y_aleatorio

# Stripe (obtén tus claves de prueba de https://dashboard.stripe.com)
STRIPE_SECRET_KEY=sk_test_tu_clave_de_prueba
STRIPE_PUBLISHABLE_KEY=pk_test_tu_clave_de_prueba
STRIPE_WEBHOOK_SECRET=whsec_tu_secreto_webhook

# Email (para desarrollo, puedes usar Mailhog)
SENDGRID_API_KEY=tu_api_key_de_sendgrid

# En Linux/macOS
openssl rand -base64 64

# En Windows (PowerShell)
[Convert]::ToBase64String((1..64 | ForEach-Object { Get-Random -Maximum 256 }))

## 3. Levantar servicios

## 3.1. Modo desarrollo (con Hot-reload)

# Levantar todos los servicios en segundo plano
docker compose up -d

# Ver el estado de los servicios
docker compose ps

# Ver los logs en tiempo real
docker compose logs -f

# Ver los logs de un servicio específico
docker compose logs -f auth-service

## 3.3 Verificar que todo funciona

| Servicio | URL | Verificación |
| :--- | :--- | :--- |
| **API Gateway** | http://localhost | Debería retornar 200 OK |
| **Frontend** | http://localhost:5173 | Debería mostrar la landing page |
| **PostgreSQL** | localhost:5432 | docker compose exec postgres psql -U epic_user -d epic_things |
| **Redis** | localhost:6379 | docker compose exec redis redis-cli ping |
| **RabbitMQ** | http://localhost:15672 | Usuario: epic_user, Password: (del .env) |
| **MinIO Console** | http://localhost:9001 | Usuario: epic_user, Password: (del .env) |
| **Elasticsearch** | http://localhost:9200 | Debería retornar JSON con info |
  
## 4. Inicializar Base de Datos

## 4.1 Ejecutar migraciones

# Entrar al contenedor de auth-service
docker compose exec auth-service sh

# Ejecutar migraciones (ejemplo con Node.js)
pnpm run migrate

## 4.2 Cargar datos de prueba (seed)
  
# Desde el contenedor de auth-service
pnpm run seed

# O desde el host (si tienes Node.js instalado)
cd backend/auth-service
pnpm run seed
  

## 4.3 Datos de prueba incluidos

| Usuario | Email | Password | Rol |
| :--- | :--- | :--- | :--- |
| **admin** | admin@epic-things.com | Admin123! | Administrador |
| **creador** | creador@epic-things.com | Creador123! | Creador (Gold) |
| **jugador** | jugador@epic-things.com | Jugador123! | Jugador (Silver) |
| **explorador** | explorador@epic-things.com | Explorador123! | Explorador |

## 5. Acceder a los Servicios

## 5.1. Frontend
   
Abre tu navegador en https://localhost:5173

## 5.2. API Gateway
   
# Probar el endpoint de health
curl http://localhost/health

# Probar login
curl -X POST http://localhost/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email_or_username": "jugador@epic-things.com", "password": "Jugador123!"}'

## 5.3. Base de datos 

# Conectarse a PostgreSQL
docker compose exec postgres psql -U epic_user -d epic_things

# Dentro de psql:
\dt                    # Listar tablas
\d usuarios            # Describir tabla usuarios
SELECT * FROM usuarios; # Ver usuarios
\q                     # Salir

## 5.4. Redis

# Conectarse a Redis
docker compose exec redis redis-cli

# Dentro de redis-cli:
KEYS *                 # Listar todas las claves
GET session:123        # Obtener valor de una clave
TTL session:123        # Ver tiempo de expiración
FLUSHALL               # Limpiar todas las claves (¡cuidado!)

## 6. Desarrollo con Hot-Reload

El docker-compose-override.yml está configurado para montar el código fuente dentro del contenedor, permitiendo hot-reload

# Los cambios en ./backend/auth-service/src se reflejan automáticamente
# No necesitas reiniciar el contenedor

# 6.1. Frontend (React + Vite) 

# Vite tiene HMR (Hot Module Replacement) integrado
# Los cambios en ./frontend/web-app/src se reflejan al instante

# Ver los logs para confirmar
docker compose logs -f frontend-web

# 6.2. Reiniciar un servicio específico

# Si necesitas reiniciar un servicio
docker compose restart auth-service

# Si cambias el package.json, necesitas rebuild
docker compose up -d --build auth-service

## 7. Comandos Útiles

# 7.1. Gestión de Servicios

# Levantar servicios
docker compose up -d

# Detener servicios (mantiene datos)
docker compose stop

# Detener y eliminar contenedores (mantiene volúmenes)
docker compose down

# Detener y eliminar TODO (incluyendo datos)
docker compose down -v

# Ver logs
docker compose logs -f [servicio]

# Escalar un servicio (ej. 3 instancias de auth-service)
docker compose up -d --scale auth-service=3

## 7.2. Acceder a Contenedores

# Entrar a un contenedor con shell
docker compose exec auth-service sh

# Ejecutar un comando específico
docker compose exec postgres pg_dump -U epic_user epic_things > backup.sql

## 7.3. Limpieza

# Eliminar imágenes huérfanas
docker image prune -a

# Eliminar volúmenes huérfanos
docker volume prune

# Limpieza completa (¡cuidado!)
docker system prune -a --volumes

## 8. Solución de Problemas Comunes

## 8.1. Error: "Port already in use"

# Ver qué proceso está usando el puerto (Linux/macOS)
lsof -i :5432

# En Windows
netstat -ano | findstr :5432

# Solución: Cambiar el puerto en docker-compose.override.yml
ports:
  - "5433:5432"  # Mapear a otro puerto

## 8.2. Error: "Cannot connect to Docker daemon"

Causa: Docker Desktop no está ejecutándose.

Solución:

Windows/macOS: Abrir Docker Desktop.

Linux: sudo systemctl start docker

## 8.3. Error: "Database does not exist"

# Ejecutar la inicialización manualmente
docker compose exec postgres psql -U epic_user -c "CREATE DATABASE epic_things;"

# Luego ejecutar las migraciones
docker compose exec auth-service pnpm run migrate

## 8.4. Error: "Out of memory"
Causa: Docker Desktop tiene poca memoria asignada.

Solución:

1. Abrir Docker Desktop.

2. Settings → Resources → Memory.

3. Aumentar a 8GB mínimo.

4. Apply & Restart.

## 8.5. Los cambios no se reflejan (hot-reload no funciona)

# Verificar que los volúmenes estén montados correctamente
docker compose config | grep volumes

# Reiniciar el servicio
docker compose restart auth-service

# Si persiste, rebuild
docker compose up -d --build auth-service

## 8.6. Error: "Permission denied" en Linux

# Agregar tu usuario al grupo docker
sudo usermod -aG docker $USER

# Cerrar sesión y volver a entrar
# O ejecutar:
newgrp docker

## 9. Configuración del Editor

## 9.1. VS Code (Recomendado)

Extensiones recomendadas:

{
  "recommendations": [
    "dbaeumer.vscode-eslint",
    "esbenp.prettier-vscode",
    "ms-azuretools.vscode-docker",
    "ms-python.python",
    "bradlc.vscode-tailwindcss",
    "dsznajder.es7-react-js-snippets",
    "eamodio.gitlens",
    "streetsidesoftware.code-spell-checker"
  ]
}

Configuración recomendada (.vscode/settings.json):

{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  "files.exclude": {
    "**/node_modules": true,
    "**/.git": true,
    "**/dist": true
  }
}

## 9.2. Estructura Recomendada de VS Code

.vscode/
├── settings.json        # Configuración del editor
├── extensions.json      # Extensiones recomendadas
├── launch.json          # Configuración de debugging
└── tasks.json           # Tareas personalizadas

## 10. Próximos Pasos
Una vez configurado el entorno:

✅ Lee la guía de contribución.

✅ Revisa el estilo de código.

✅ Consulta el flujo de trabajo con Git.

✅ Busca un issue para empezar.

✅ Únete al Discord para pedir ayuda.

¿Necesitas Ayuda?

Discord: Canal #ayuda-programacion

GitHub Issues: Reportar problema

Email: parraalavaro418@gmail.com
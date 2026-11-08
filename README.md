# 🎮 Epic Things Platform

> **Versión:** `v0.1.0-alpha`  
> **Estado:** ✅ Documentación completada – En desarrollo activo (Fase 1: Fundación)  
> **Filosofía:** "De las cosas épicas que empiezan con un sueño, nacen las plataformas que mueven al mundo."

---

## 📌 ¿Qué es esto?

**Epic Things Platform** es el renacimiento de mi primer proyecto universitario.  
Lo que comenzó como un sitio web estático en 2025, hoy se reinventa como una  
**plataforma de juegos con alma de creadores**.

Inspirada en portales como Y8 y Miniclip, pero con un giro único:  
**los miembros no solo juegan, también pueden crear y monetizar sus propios juegos**.

> 🔒 **Proyecto privado** – El código fuente está restringido al equipo autorizado.

---

## 🎯 Visión

**Crear el ecosistema de juegos donde los jugadores se convierten en creadores,  
y los creadores en emprendedores.**

### Misión

Democratizar la creación de juegos, proporcionando una plataforma donde cualquier persona,  
sin importar su nivel técnico, pueda crear, compartir y monetizar sus propios juegos.

---

## ✨ Características Principales

| Área | Características |
| :--- | :--- |
| **Para Jugadores** | 🎮 Catálogo de juegos (gratuitos y premium) <br> 🏆 Tablas de clasificación <br> 🌙 Modo oscuro <br> ❤️ Juegos favoritos <br> ⭐ Valoraciones y comentarios |
| **Para Creadores** | 🛠 Herramientas para crear juegos <br> 📊 Panel de métricas <br> 💰 Sistema de regalías (70%) <br> 🏷️ Badge de creador verificado |
| **Para Administradores** | 📈 Dashboard de métricas <br> 🧑‍💻 Gestión de usuarios y juegos <br> 🛡️ Moderación de contenido <br> 📝 Logs de auditoría |

---

## 🏗️ Arquitectura (Alto Nivel)

┌─────────────────────────────────────────────────────────────┐
│               Frontend (React + AcadFrame)                  │
└──────────────────────────────┬──────────────────────────────┘
                               │ 
┌──────────────────────────────▼──────────────────────────────┐
│                       API Gateway (Nginx)                   │
└───────┬───────────┬───────────┬───────────┬─────────────────┘
        │           │           │           │
┌───────▼───┐ ┌─────▼────┐ ┌────▼───┐ ┌─────▼──────┐
│   Auth    │ │  Games   │ │Payment │ │ Community  │
│  Service  │ │ Service  │ │Service │ │  Service   │
└───────────┘ └──────────┘ └────────┘ └────────────┘
        │           │           │           │
┌───────▼───────────▼───────────▼───────────▼─────────────────┐
│           PostgreSQL + Redis + RabbitMQ + MinIO             │
└─────────────────────────────────────────────────────────────┘


📚 Para más detalles, consulta la [Documentación de Arquitectura](./docs/arquitectura/).

---

## 🛠️ Stack Tecnológico

| Capa | Tecnología | ¿Por qué? |
| :--- | :--- | :--- |
| **Frontend** | React + Vite + TypeScript + AcadFrame | Estándar de la industria, rápido y tipado seguro |
| **Backend** | Node.js (Express) + TypeScript | APIs rápidas, mismo lenguaje que el frontend |
| **Base de Datos** | PostgreSQL + Redis | Datos transaccionales + caché ultrarrápida |
| **Colas** | RabbitMQ | Comunicación asíncrona entre servicios |
| **Almacenamiento** | MinIO (S3 compatible) | Almacenamiento de juegos y assets |
| **Búsqueda** | Elasticsearch | Búsqueda en tiempo real |
| **Autenticación** | JWT | Stateless y escalable para microservicios |
| **Pagos** | Stripe | La mejor integración para suscripciones |
| **Juegos** | Phaser (HTML5) + Unity (WebGL) | Ligero para 2D, potente para 3D |
| **Infraestructura** | Docker + Docker Compose | Orquestación sencilla y reproducible |

---

## 📁 Estructura del Proyecto

epic-things-platform/
├── docs/ # 📚 Documentación (el corazón del proyecto)
│ ├── vision-general.md # Misión, visión, objetivos
│ ├── arquitectura/ # Diagramas, ADRs, APIs
│ ├── modelo_negocio/ # Business plan, monetización, roadmap
│ ├── guias/ # Guías del equipo
│ └── manuals/ # Manuales de usuario, creador, admin
│
├── infrastructure/ # 🐳 Docker, Kubernetes, Nginx
│ ├── docker/
│ ├── kubernetes/
│ └── nginx/
│
├── backend/ # ⚙️ Microservicios
│ ├── api-gateway/ # Punto de entrada (Nginx)
│ ├── auth-service/ # Autenticación y usuarios
│ ├── games-service/ # Catálogo y subida de juegos
│ ├── payment-service/ # Suscripciones y Stripe
│ ├── community-service/ # Valoraciones y comentarios
│ ├── notification-service/ # Emails y WebSockets
│ ├── analytics-service/ # Métricas y reportes (Python)
│ └── shared/ # Código compartido
│
├── frontend/ # 🎨 Aplicaciones
│ ├── web-app/ # React + Vite + TypeScript + AcadFrame
│ └── games/ # Juegos (HTML5, Unity, WebGL)
│
└── scripts/ # 🛠 Herramientas de desarrollo


---

## 🚀 Estado del Proyecto

### Versión Actual: `v0.1.0-alpha`

| Fase | Estado | Notas |
| :--- | :--- | :--- |
| **Fase 0: Documentación** | ✅ **Completado** | ~46 documentos (arquitectura, ADRs, APIs, guías, manuales) |
| **Fase 1: Fundación** | ⏳ **En progreso** | Docker Compose, Auth Service, Frontend básico |
| **Fase 2: Catálogo** | ⏳ Pendiente | Games Service, 10+ juegos HTML5 |
| **Fase 3: Monetización** | ⏳ Pendiente | Payment Service, Stripe, suscripciones |
| **Fase 4: Comunidad** | ⏳ Pendiente | Creadores, regalías, foros |
| **Fase 5: Lanzamiento** | ⏳ Pendiente | Beta pública, marketing, escalado |

### Hitos Alcanzados

- ✅ **Documentación completa** (~46 documentos)
- ✅ **Arquitectura de microservicios** definida
- ✅ **8 ADRs** documentando decisiones técnicas
- ✅ **3 APIs OpenAPI 3.0** (Auth, Games, Payment)
- ✅ **Modelo de negocio** y estrategia de monetización
- ✅ **Manuales** para usuario, creador y administrador
- ✅ **Configuración de Docker** lista

---

## 💰 Modelo de Negocio (Resumen)

### Planes de Suscripción

| Plan | Precio | Beneficios Principales |
| :--- | :--- | :--- |
| **Free (Explorador)** | $0/mes | 5 juegos gratuitos, con anuncios |
| **Silver (Jugador)** | $5/mes | Todos los juegos, sin anuncios |
| **Gold (Creador)** | $15/mes | Todo Silver + crear juegos + regalías 70% |
| **Legend (Mecenas)** | $30/mes | Todo Gold + beta + voto en desarrollo |

### Proyecciones (Año 1)

| Métrica | Objetivo |
| :--- | :--- |
| **Usuarios Registrados** | 5,000 |
| **Suscriptores Activos** | 500 |
| **Ingresos Anuales (ARR)** | $45,000 |
| **Punto de Equilibrio** | Mes 10 |

📖 Para más detalles: [Plan de Negocio](./docs/modelo_negocio/business-plan.md) · [Monetización](./docs/modelo_negocio/monetization.md)

---

## 📚 Documentación

La documentación es **el pilar de este proyecto**. Toda la documentación interna está en [`docs/`](./docs/):

| Categoría | Documentos | Estado |
| :--- | :---: | :---: |
| [Visión General](./docs/vision-general.md) | 1 | ✅ |
| [Arquitectura](./docs/arquitectura/) | ~15 | ✅ |
| [Modelo de Negocio](./docs/modelo_negocio/) | 5 | ✅ |
| [Guías del Equipo](./docs/guias/) | 6 | ✅ |
| [Manuales](./docs/manuals/) | 13 | ✅ |
| **Total** | **~40+** | ✅ |

### Enlaces Rápidos

- 📖 [Índice Completo de Documentación](./docs/index.md)
- 🏗️ [Arquitectura General](./docs/arquitectura/diagramas/arquitectura-general.puml)
- 📊 [API Reference](./docs/arquitectura/api/)
- 💰 [Modelo de Negocio](./docs/modelo_negocio/)
- 🗺️ [Roadmap](./docs/modelo_negocio/roadmap.md)
- 👤 [Manuales de Usuario](./docs/manuals/user/)
- 🎨 [Manuales de Creadores](./docs/manuals/developer/)
- 🛡️ [Manuales de Administradores](./docs/manuals/admin/)

---

## 🚀 Cómo Empezar (Para el Equipo)

### Requisitos

- Docker Desktop 24.0+
- Node.js 18.x LTS
- Git 2.40+
- 8GB de RAM mínimo (16GB recomendado)

### Configuración Rápida

```bash
# 1. Clonar el repositorio (necesitas acceso al repo privado)
git clone https://github.com/Alepro418/epic-things-platform.git
cd epic-things-platform

# 2. Copiar variables de entorno
cp .env.example .env

# 3. Editar .env con los valores proporcionados por el administrador
nano .env

# 4. Levantar los servicios
docker compose up -d

# 5. Verificar que todo funcione
docker compose ps

# 6. Acceder al frontend
# http://localhost:5173
```

📖 Para instrucciones detalladas: `Configuración Local`.

👥 Equipo

| Rol | Persona | Responsabilidad |
| :--- | :--- | :--- |
| **Fundador & Desarrollador** | Álvaro Parra | Backend, frontend, infraestructura, documentación |
| **Diseñador UX/UI** | (Por definir) | Diseño de interfaz y experiencia de usuario |
| **Community Manager** | (Por definir) | Gestión de comunidad y redes sociales |

🔒 Licencia

Copyright (c) 2026 Álvaro Parra / Epic Things Platform

Todos los derechos reservados.

Este software y su código fuente son propiedad exclusiva de Epic Things Platform.
Queda estrictamente prohibida la reproducción, distribución, modificación o uso
comercial de este software, en su totalidad o en parte, sin el consentimiento
previo y por escrito del propietario.

El acceso al código fuente está restringido únicamente al personal autorizado
de Epic Things Platform.

📄 Para más detalles, consulta el archivo `LICENSE`.

| Canal | Información |
| :--- | :--- |
| **Email** | parraalavaro418@gmail.com |
| **GitHub** | `@Alepro418` |
| **Ubicació** | Puerto Cabello, Venezuela |

🙏 Agradecimientos

• **A mi yo del pasado**, por crear el primer "Epic Things" en 2025.

• A **AcadFrame**, por ser la base de la interfaz moderna.

• A la **comunidad de desarrolladores venezolanos**, por la inspiración constante.

• A **todos los que creen que los juegos pueden ser un vehículo de creación y emprendimiento**.

"La mejor manera de aprender es construir, y la mejor manera de construir es documentar."

**Hecho con ❤️ desde Puerto Cabello, Venezuela**.

``` html
<div align="center">
Documentación · Arquitectura · Modelo de Negocio · Guías · Manuales

</div> 
```

📊 Comparativa de Cambios

| Sección | Antes | Después |
| :--- | :--- | :--- |
| **Encabezado** | "⚠️ En diseño y planificación" | "✅ Documentación completada – En desarrollo activo" |
| **Versión** | No mencionada | v0.1.0-alpha |
| **Licencia** | MIT | Propietaria (todos los derechos reservados) |
| **Contribuciones** | Sección completa | ❌ Eliminada (proyecto privado) |
| **Estado del proyecto** | "Documentación: En progreso" | "Documentación: ✅ Completado" |
| **Estructura** | 5 microservicios | 6 + api-gateway + shared |
| **Stack** | Sin RabbitMQ, MinIO, Elasticsearch | ✅ Añadidos |
| **Enlaces de docs** | ./docs/manuales/ | ./docs/manuals/ |
| **Hitos alcanzados** | No mencionados | ✅ Lista completa |
| **Cómo empezar** | No incluido | ✅ Sección para el equipo |
| **Equipo** | No mencionado | ✅ Tabla de roles |

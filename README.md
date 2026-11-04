# 🎮 Epic Things Platform

> **Estado:** ⚠️ En diseño y planificación – Documentación en construcción.
> 
> **Filosofía:** "De las cosas épicas que empiezan con un sueño, nacen las plataformas que mueven al mundo."

---

## 📌 ¿Qué es esto?

**Epic Things Platform** es el renacimiento de mi primer proyecto universitario. 
Lo que comenzó como un sitio web estático en 2025, hoy se reinventa como una 
**plataforma de juegos con alma de creadores**.

Inspirada en portales como Y8 y Miniclip, pero con un giro único: 
**los miembros no solo juegan, también pueden crear y monetizar sus propios juegos**.

---

## 🎯 Visión

**Crear el ecosistema de juegos donde los jugadores se convierten en creadores, 
y los creadores en emprendedores.**

---

## ✨ Características Principales

| Área | Características |
| :--- | :--- |
| **Para Jugadores** | 🎮 Catálogo de juegos (gratuitos y premium) <br> 🏆 Tablas de clasificación <br> 🌙 Modo oscuro (gracias a AcadFrame) |
| **Para Creadores** | 🛠 Herramientas para crear juegos (tutoriales, plantillas) <br> 📊 Panel de control con métricas <br> 💰 Sistema de regalías (70% de los ingresos) |
| **Para Administradores** | 📈 Dashboard de métricas <br> 🧑‍💻 Gestión de usuarios y juegos <br> 📝 Sistema de logs y auditoría |

---

## 🏗️ Arquitectura (Alto Nivel)

┌─────────────────────────────────────────────────────────────┐
│ Frontend (React + AcadFrame) │
└───────────────┬─────────────────────────────────────────────┘
│
┌───────────────▼─────────────────────────────────────────────┐
│ API Gateway (Nginx) │
└───────┬───────────┬───────────┬───────────┬─────────────────┘
│ │ │ │
┌───────▼───┐ ┌─────▼────┐ ┌───▼────┐ ┌───▼────────┐
│ Auth │ │ Games │ │Payment │ │Community │
│ Service │ │ Service │ │Service │ │ Service │
└───────────┘ └──────────┘ └────────┘ └────────────┘
│ │ │ │
┌───────▼───────────▼───────────▼───────────▼─────────────────┐
│ PostgreSQL + Redis │
└─────────────────────────────────────────────────────────────┘


---

## 🛠️ Stack Tecnológico

| Capa | Tecnología | ¿Por qué? |
| :--- | :--- | :--- |
| **Frontend** | React + Vite + TypeScript | Estándar de la industria, rápido y tipado seguro. |
| **Estilos** | **AcadFrame** + Tailwind | Framework propio + personalización ágil. |
| **Backend** | Node.js (Express) | APIs rápidas, mismo lenguaje que el frontend. |
| **Autenticación** | JWT | Stateless y escalable para microservicios. |
| **Pagos** | Stripe | La mejor integración para suscripciones. |
| **Base de Datos** | PostgreSQL + Redis | Robusto + caché ultrarrápida. |
| **Juegos** | Phaser (HTML5) + Unity (WebGL) | Ligero para juegos 2D, potente para 3D. |
| **Infraestructura** | Docker + Docker Compose | Orquestación sencilla y reproducible. |

---

## 📁 Estructura del Proyecto

epic-things-platform/
├── docs/ # 📚 Documentación (el corazón del proyecto)
├── infrastructure/ # 🐳 Docker, Kubernetes, Nginx
├── backend/ # ⚙️ Microservicios
│ ├── api-gateway/
│ ├── auth-service/
│ ├── games-service/
│ ├── payment-service/
│ └── community-service/
├── frontend/ # 🎨 Aplicaciones
│ ├── web-app/ # React + AcadFrame
│ └── games/ # 🎮 Juegos (HTML5, Unity)
└── scripts/ # 🛠 Herramientas


---

## 🚀 Estado del Proyecto

| Fase | Estado | Notas |
| :--- | :--- | :--- |
| **1. Documentación** | ✅ En progreso | Este README y la visión general están listos. |
| **2. Diseño de Arquitectura** | ⏳ Pendiente | Diagramas y ADRs en construcción. |
| **3. Configuración Inicial** | ⏳ Pendiente | Docker Compose y repositorios. |
| **4. Desarrollo del Core** | ⏳ Pendiente | Auth Service y frontend básico. |
| **5. Juegos y Monetización** | ⏳ Pendiente | Implementación de juegos y Stripe. |
| **6. Lanzamiento** | ⏳ Pendiente | Despliegue en producción. |

---

## 📚 Documentación

La documentación es **el pilar de este proyecto**. Puedes explorarla aquí:

- [📖 Visión General](./docs/vision-general.md)
- [🏗️ Arquitectura](./docs/arquitectura/)
- [📊 Modelo de Negocio](./docs/modelo_negocio/)
- [👤 Manuales de Usuario](./docs/manuales/)

---

## 🤝 Contribuciones

Este es un proyecto **personal y académico**, pero si te inspira y quieres contribuir:

1.  Lee la [guía de contribución](./docs/guias/contribucion.md).
2.  Revisa los [issues](https://github.com/Alepro418/epic-things-platform/issues) abiertos.
3.  Envía un Pull Request con tus cambios.

---

## 📄 Licencia

MIT License – libre para uso personal y comercial.

---

## 🌟 Créditos

Creado con ❤️ por **Álvaro Parra**  
📍 Puerto Cabello, Venezuela  
📧 parraalavaro418@gmail.com

---

*"La mejor manera de aprender es construir, y la mejor manera de construir es documentar."*
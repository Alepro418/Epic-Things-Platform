# 📚 Documentación - Epic Things Platform

> **Bienvenido a la documentación oficial de Epic Things Platform**  
> La plataforma donde los jugadores se convierten en creadores.

---

## 🎯 ¿Qué es Epic Things Platform?

**Epic Things Platform** es una plataforma de juegos que combina entretenimiento con creación comunitaria. Los miembros pueden:

- 🎮 **Jugar** juegos exclusivos (gratuitos y premium).
- 🛠️ **Crear** y subir sus propios juegos.
- 💰 **Ganar regalías** del 70% por sus creaciones.
- 🌟 **Apoyar** el desarrollo de la plataforma.

Este proyecto es el **renacimiento de mi primer proyecto universitario** (2025), ahora con una arquitectura moderna, un modelo de negocio sostenible y una documentación exhaustiva.

> ⚠️ **Nota:** Este es un proyecto **privado**. El código fuente está restringido al equipo autorizado. La documentación aquí presente es de uso interno.

---

## 🚀 Navegación Rápida por Rol

Selecciona tu perfil para acceder directamente a la documentación relevante:

### 👤 Soy Jugador

| Documento | Descripción |
| :--- | :--- |
| [🎮 Guía para Jugar](./manuals/user/play.md) | Descubre cómo explorar y jugar |
| [🏆 Récords y Estadísticas](./manuals/user/record.md) | Consulta tus logros y récords |
| [💳 Suscripciones](./manuals/user/subscriptions.md) | Conoce los planes y cómo suscribirte |

### 🎨 Soy Creador de Juegos

| Documento | Descripción |
| :--- | :--- |
| [🚀 Primeros Pasos](./manuals/developer/primeros-pasos.md) | Comienza tu viaje como creador |
| [📤 Subir un Juego](./manuals/developer/subir-juego.md) | Proceso paso a paso |
| [🕹️ Crear Juego HTML5](./manuals/developer/crear-juego-html5.md) | Guía completa para HTML5 |
| [🎮 Crear Juego Unity](./manuals/developer/crear-juego-unity.md) | Guía completa para Unity WebGL |
| [🔌 Integración con la API](./manuals/developer/api-integration.md) | Automatiza con la API |
| [💰 Regalías](./manuals/developer/regalias.md) | Cómo funcionan tus ingresos |

### 🛡️ Soy Administrador

| Documento | Descripción |
| :--- | :--- |
| [🎮 Gestión de Juegos](./manuals/admin/gestion-juegos.md) | Revisión y aprobación de juegos |
| [👥 Gestión de Usuarios](./manuals/admin/gestion-usuarios.md) | Administración de cuentas |
| [📊 Métricas](./manuals/admin/metricas.md) | Análisis y KPIs |
| [🛡️ Moderación](./manuals/admin/moderacion.md) | Moderación de contenido |

### 💻 Soy Desarrollador del Equipo

| Documento | Descripción |
| :--- | :--- |
| [⚙️ Configuración Local](./guias/configuracion-local.md) | Configura tu entorno |
| [🎨 Estilo de Código](./guias/estilo-codigo.md) | Convenciones del equipo |
| [🔀 Flujo de Trabajo Git](./guias/flujo-trabajo-git.md) | Git workflow |
| [🏗️ Arquitectura](./arquitectura/) | Diagramas y ADRs |
| [🔌 APIs](./arquitectura/api/) | Documentación OpenAPI |

---

## 📖 Mapa Completo de la Documentación

### 📋 Visión General

| Documento | Descripción |
| :--- | :--- |
| [Visión General](./vision-general.md) | Misión, visión, objetivos y perfiles de usuario |

---

### 🏗️ Arquitectura

Documentación técnica del sistema: diagramas, decisiones arquitectónicas y APIs.

#### Diagramas

| Documento | Descripción |
| :--- | :--- |
| [Diagrama de Arquitectura](./arquitectura/diagramas/arquitectura-general.puml) | Vista general de microservicios |
| [Diagrama de Casos de Uso](./arquitectura/diagramas/casos-de-uso.puml) | Actores y funcionalidades |
| [Modelo Entidad-Relación](./arquitectura/diagramas/entidad-relacion.puml) | Base de datos completa |
| [Diagramas de Secuencia](./arquitectura/diagramas/secuencias/) | Login, registro, suscripción, subida, valoración |
| [Diagramas en Texto Plano](./arquitectura/texto-plano/) | Versiones .txt de los diagramas |

#### Architecture Decision Records (ADRs)

| ADR | Descripción | Estado |
| :--- | :--- | :--- |
| [ADR-001](./arquitectura/adr/001-usar-nodejs-en-backend.md) | Usar Node.js en el backend | ✅ Aceptado |
| [ADR-002](./arquitectura/adr/002-arquitectura-microservicios.md) | Arquitectura de microservicios | ✅ Aceptado |
| [ADR-003](./arquitectura/adr/003-postgresql-como-bd-principal.md) | PostgreSQL como BD principal | ✅ Aceptado |
| [ADR-004](./arquitectura/adr/004-stripe-para-pagos.md) | Stripe para pagos | ✅ Aceptado |
| [ADR-005](./arquitectura/adr/005-react-y-acadframe-frontend.md) | React + AcadFrame para frontend | ✅ Aceptado |
| [ADR-006](./arquitectura/adr/006-docker-para-orquestacion.md) | Docker para orquestación | ✅ Aceptado |
| [ADR-007](./arquitectura/adr/007-jwt-para-autenticacion.md) | JWT para autenticación | ✅ Aceptado |
| [ADR-008](./arquitectura/adr/008-redis-para-cache-y-sesiones.md) | Redis para caché y sesiones | ✅ Aceptado |

#### API Reference (OpenAPI 3.0)

| Documento | Descripción |
| :--- | :--- |
| [API README](./arquitectura/api/README.md) | Índice general de APIs |
| [Auth API](./arquitectura/api/auth.yaml) | Autenticación, registro, JWT |
| [Games API](./arquitectura/api/games.yaml) | Catálogo, subida, revisión |
| [Payment API](./arquitectura/api/payment.yaml) | Suscripciones, Stripe, regalías |

---

### 💰 Modelo de Negocio

Estrategia, mercado, monetización y hoja de ruta del proyecto.

| Documento | Descripción |
| :--- | :--- |
| [Business Plan](./modelo_negocio/business-plan.md) | Plan de negocio completo |
| [Análisis de Mercado](./modelo_negocio/market-analysis.md) | Competencia, TAM, SAM, SOM |
| [Estrategia de Monetización](./modelo_negocio/monetization.md) | Planes, precios, ingresos |
| [Roadmap](./modelo_negocio/roadmap.md) | Hoja de ruta Q1 2026 - Q4 2027 |
| [Estrategia de Marketing](./modelo_negocio/marketing-strategy.md) | Canales, contenidos, growth |

---

### 📘 Guías del Equipo

Documentación para desarrolladores y colaboradores del proyecto.

| Documento | Descripción |
| :--- | :--- |
| [Contribución](./guias/contribucion.md) | Cómo contribuir al proyecto |
| [Código de Conducta](./guias/codigo-conducta.md) | Normas de convivencia |
| [Configuración Local](./guias/configuracion-local.md) | Configura tu entorno de desarrollo |
| [Estilo de Código](./guias/estilo-codigo.md) | Convenciones del proyecto |
| [Flujo de Trabajo Git](./guias/flujo-trabajo-git.md) | Git workflow y convenciones |
| [Preguntas Frecuentes](./guias/preguntas-frecuentes.md) | FAQ técnica |

---

### 📖 Manuales

Documentación de usuario final, organizada por rol.

#### 👤 Manuales de Usuario (Jugadores)

| Documento | Descripción |
| :--- | :--- |
| [Guía para Jugar](./manuals/user/play.md) | Catálogo, controles, favoritos, valoraciones |
| [Récords y Estadísticas](./manuals/user/record.md) | Récords, tablas, logros, privacidad |
| [Suscripciones](./manuals/user/subscriptions.md) | Planes, pagos, cancelación, seguridad |

#### 🎨 Manuales de Creadores (Desarrolladores de Juegos)

| Documento | Descripción |
| :--- | :--- |
| [Primeros Pasos](./manuals/developer/primeros-pasos.md) | Introducción al programa de creadores |
| [Subir un Juego](./manuals/developer/subir-juego.md) | Proceso paso a paso |
| [Crear Juego HTML5](./manuals/developer/crear-juego-html5.md) | Guía completa con ejemplo |
| [Crear Juego Unity](./manuals/developer/crear-juego-unity.md) | Guía completa para WebGL |
| [Integración con la API](./manuals/developer/api-integration.md) | API REST, webhooks, ejemplos |
| [Regalías](./manuals/developer/regalias.md) | Cómo funcionan tus ingresos |

#### 🛡️ Manuales de Administradores

| Documento | Descripción |
| :--- | :--- |
| [Gestión de Juegos](./manuals/admin/gestion-juegos.md) | Revisión, aprobación, clasificación por edad |
| [Gestión de Usuarios](./manuals/admin/gestion-usuarios.md) | Roles, suscripciones, bloqueos |
| [Métricas](./manuals/admin/metricas.md) | KPIs, dashboards, reportes |
| [Moderación](./manuals/admin/moderacion.md) | Moderación de contenido y sanciones |

---

## 📊 Estado de la Documentación

| Categoría | Documentos | Estado |
| :--- | :---: | :---: |
| **Visión General** | 1 | ✅ Completado |
| **Arquitectura (diagramas)** | 10+ | ✅ Completado |
| **Arquitectura (ADRs)** | 8 | ✅ Completado |
| **Arquitectura (APIs)** | 3 + README | ✅ Completado |
| **Modelo de Negocio** | 5 | ✅ Completado |
| **Guías del Equipo** | 6 | ✅ Completado |
| **Manuales de Usuario** | 3 | ✅ Completado |
| **Manuales de Creadores** | 6 | ✅ Completado |
| **Manuales de Admin** | 4 | ✅ Completado |
| **TOTAL** | **~46 documentos** | ✅ **100%** |

**Última actualización:** 2026-11-04

---

## 🗂️ Estructura de la Carpeta `docs/`

docs/
├── index.md ← Este archivo
├── vision-general.md # Misión, visión, objetivos
│
├── arquitectura/ # 🏗️ Documentación técnica
│ ├── adr/ # Decisiones arquitectónicas
│ ├── diagramas/ # Diagramas PlantUML
│ ├── texto-plano/ # Versiones .txt
│ └── api/ # OpenAPI specs
│
├── modelo_negocio/ # 💰 Estrategia y negocio
│ ├── business-plan.md
│ ├── market-analysis.md
│ ├── monetization.md
│ ├── roadmap.md
│ └── marketing-strategy.md
│
├── guias/ # 📘 Guías del equipo
│ ├── contribucion.md
│ ├── codigo-conducta.md
│ ├── configuracion-local.md
│ ├── estilo-codigo.md
│ ├── flujo-trabajo-git.md
│ └── preguntas-frecuentes.md
│
└── manuals/ # 📖 Manuales por rol
├── user/ # Jugadores
│ ├── play.md
│ ├── record.md
│ └── subscriptions.md
├── developer/ # Creadores
│ ├── primeros-pasos.md
│ ├── subir-juego.md
│ ├── crear-juego-html5.md
│ ├── crear-juego-unity.md
│ ├── api-integration.md
│ └── regalias.md
└── admin/ # Administradores
├── gestion-juegos.md
├── gestion-usuarios.md
├── metricas.md
└── moderacion.md


---

## 🔍 Búsqueda Rápida

### Por Tema

| Tema | Documentos Relacionados |
| :--- | :--- |
| **Autenticación** | [Auth API](./arquitectura/api/auth.yaml), [ADR-007](./arquitectura/adr/007-jwt-para-autenticacion.md) |
| **Base de Datos** | [MER](./arquitectura/diagramas/entidad-relacion.puml), [ADR-003](./arquitectura/adr/003-postgresql-como-bd-principal.md) |
| **Clasificación por Edad** | [Gestión de Juegos](./manuals/admin/gestion-juegos.md), [Crear HTML5](./manuals/developer/crear-juego-html5.md) |
| **Docker** | [ADR-006](./arquitectura/adr/006-docker-para-orquestacion.md), [Configuración Local](./guias/configuracion-local.md) |
| **Microservicios** | [ADR-002](./arquitectura/adr/002-arquitectura-microservicios.md), [Arquitectura General](./arquitectura/diagramas/arquitectura-general.puml) |
| **Pagos / Stripe** | [Payment API](./arquitectura/api/payment.yaml), [ADR-004](./arquitectura/adr/004-stripe-para-pagos.md), [Suscripciones](./manuals/user/subscriptions.md) |
| **Regalías** | [Regalías](./manuals/developer/regalias.md), [Monetización](./modelo_negocio/monetization.md) |
| **Seguridad** | [Código de Conducta](./guias/codigo-conducta.md), [Moderación](./manuals/admin/moderacion.md) |
| **Webhooks** | [Integración API](./manuals/developer/api-integration.md) |

### Por Tecnología

| Tecnología | Documentos |
| :--- | :--- |
| **Node.js** | [ADR-001](./arquitectura/adr/001-usar-nodejs-en-backend.md) |
| **React** | [ADR-005](./arquitectura/adr/005-react-y-acadframe-frontend.md) |
| **PostgreSQL** | [ADR-003](./arquitectura/adr/003-postgresql-como-bd-principal.md) |
| **Redis** | [ADR-008](./arquitectura/adr/008-redis-para-cache-y-sesiones.md) |
| **Docker** | [ADR-006](./arquitectura/adr/006-docker-para-orquestacion.md) |
| **Stripe** | [ADR-004](./arquitectura/adr/004-stripe-para-pagos.md) |
| **AcadFrame** | [ADR-005](./arquitectura/adr/005-react-y-acadframe-frontend.md) |

---

## 📝 Convenciones de la Documentación

Toda la documentación de Epic Things Platform sigue estas convenciones:

### Estructura de Archivos

- **Nombres en kebab-case**: `gestion-juegos.md`, `crear-juego-html5.md`
- **Carpetas en inglés**: `docs/manuals/`, `docs/architecture/`
- **Contenido en español**: Toda la documentación está en español

### Formato Markdown

- **Títulos con emojis**: Para facilitar la navegación visual
- **Tablas**: Para comparativas y datos estructurados
- **Bloques de código**: Con sintaxis resaltada
- **Enlaces relativos**: Para navegación interna
- **Tabla de contenidos**: Al inicio de cada documento extenso

### Versionado

Cada documento incluye:

- **Audiencia**: A quién va dirigido
- **Última actualización**: Fecha de la última revisión
- **Versión**: Número de versión del documento
- **Historial de cambios**: Al final del documento

---

## 🎯 Principios Rectores

Toda la documentación se basa en estos principios:

1. 📝 **Documentación Primero**: Cada decisión técnica y de negocio debe estar documentada antes de implementarse.
2. 🎯 **Claridad sobre Complejidad**: Explicar conceptos complejos de forma sencilla.
3. 🔄 **Actualización Constante**: La documentación se revisa y actualiza regularmente.
4. 🌍 **Accesibilidad**: Documentación para todos los niveles (principiante a avanzado).
5. 🤝 **Colaboración**: La documentación es de y para el equipo.

---

## 🔗 Enlaces Externos

| Recurso | Enlace |
| :--- | :--- |
| **Repositorio GitHub** | [Alepro418/epic-things-platform](https://github.com/Alepro418/epic-things-platform) |
| **AcadFrame** | [Alepro418/AcadFrame](https://github.com/Alepro418/AcadFrame) |
| **Stripe Dashboard** | [dashboard.stripe.com](https://dashboard.stripe.com) |
| **Docker Hub** | [hub.docker.com](https://hub.docker.com) |

---

## 📞 Contacto

### Equipo de Desarrollo

| Canal | Información |
| :--- | :--- |
| **Email** | parraalavaro418@gmail.com |
| **GitHub** | [@Alepro418](https://github.com/Alepro418) |
| **Ubicación** | Puerto Cabello, Venezuela |

### Soporte Interno

| Canal | Uso |
| :--- | :--- |
| **Discord** | Canal `#soporte-admin`, `#soporte-api`, `#ayuda-programacion` |
| **GitHub Issues** | [Reportar problemas](https://github.com/Alepro418/epic-things-platform/issues) |

---

## 🎉 Agradecimientos

Esta documentación es el resultado de **años de aprendizaje, errores, aciertos y pasión por construir cosas épicas**. Si estás leyendo esto como parte del equipo: **bienvenido, vamos a construir algo increíble**.

---

<div align="center">

**📚 Documentación de Epic Things Platform**

*"La mejor manera de aprender es construir, y la mejor manera de construir es documentar."*

**Hecho con ❤️ desde Puerto Cabello, Venezuela**

**Última actualización:** 2026-11-04 · **Versión:** 1.0 · **Estado:** ✅ Completado

</div>
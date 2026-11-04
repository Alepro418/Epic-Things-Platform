# 📖 Visión General de Epic Things Platform

---

## 🎯 Misión

**Crear un espacio donde los juegos y la creatividad se encuentren**, permitiendo que cualquier persona, desde un jugador casual hasta un desarrollador experimentado, encuentre su lugar para jugar, crear y compartir.

---

## 👁️ Visión

**Convertirnos en la plataforma de referencia para creadores de juegos independientes**, ofreciendo un ecosistema completo donde la creación, distribución y monetización de juegos sea accesible para todos.

---

## 🎯 Objetivos Estratégicos

### 1. Técnicos
- Construir una plataforma escalable con microservicios.
- Utilizar tecnologías modernas y probadas.
- Mantener una documentación exhaustiva y actualizada (¡porque es lo que nos apasiona!).
- Garantizar la seguridad de los datos de usuarios y creadores.

### 2. De Negocio
- Generar ingresos sostenibles a través de un modelo freemium.
- Crear un ecosistema donde los creadores puedan monetizar su trabajo.
- Construir una comunidad leal y participativa.

### 3. De Usuario
- Ofrecer una experiencia de usuario fluida y agradable.
- Proveer herramientas y tutoriales para que cualquiera pueda crear juegos.
- Fomentar un ambiente de respeto y colaboración.

---

## 🧑‍🤝‍🧑 Perfiles de Usuario (Actores)

| Perfil | Descripción | Motivación Principal |
| :--- | :--- | :--- |
| **Explorador (Free)** | Usuario que juega gratuitamente sin compromiso. | Entretenerse y descubrir nuevos juegos. |
| **Jugador (Silver)** | Usuario que paga por acceso completo y sin anuncios. | Experiencia premium y contenido exclusivo. |
| **Creador (Gold)** | Usuario que crea y sube sus propios juegos. | Expresarse, ganar reconocimiento y dinero. |
| **Mecenas (Legend)** | Usuario que apoya el desarrollo de la plataforma. | Sentirse parte del proceso creativo y tener voz en las decisiones. |
| **Administrador** | Gestiona la plataforma y la comunidad. | Mantener el orden, la calidad y el buen funcionamiento. |

---

## 🔒 Alcance del Proyecto

### Incluye (In-Scope) para la V1
- ✅ Plataforma web con catálogo de juegos.
- ✅ Sistema de autenticación y roles (JWT).
- ✅ Suscripciones con Stripe.
- ✅ Panel de creadores con métricas.
- ✅ Juegos propios (HTML5 y Unity).
- ✅ Documentación completa (¡nuestro sello de calidad!).
- ✅ Sistema básico de tablas de clasificación.

### No Incluye (Out-of-Scope) para la V1
- ❌ App móvil nativa (futuro).
- ❌ Juegos multijugador en tiempo real (futuro).
- ❌ Integración con consolas (futuro).
- ❌ Mercado de NFTs (por ahora no tiene sentido).

---

## 📜 Principios Rectores

1.  **Documentación Primero**: Cada decisión técnica y de negocio debe estar documentada antes de implementarse.
2.  **Calidad sobre Cantidad**: Preferimos 10 juegos bien hechos a 100 juegos mediocres.
3.  **Comunidad como Motor**: Los creadores son el corazón del proyecto.
4.  **Transparencia**: Los ingresos, las reglas y las decisiones son públicas.
5.  **Sostenibilidad**: El modelo de negocio debe ser viable a largo plazo.

---

## 🗺️ Roadmap (Versión 1.0)

| Hito | Fecha Estimada | Entregables |
| :--- | :--- | :--- |
| **Fase 0: Documentación** | Q1 2026 (Ahora) | README, Visión General, Diagramas, ADRs. |
| **Fase 1: Fundación** | Q2 2026 | Docker Compose, Auth Service, Frontend básico con AcadFrame. |
| **Fase 2: Catálogo** | Q3 2026 | Games Service, 5 juegos HTML5, integración completa. |
| **Fase 3: Monetización** | Q4 2026 | Payment Service, suscripciones, restricción de acceso. |
| **Fase 4: Comunidad** | Q1 2027 | Panel de creadores, sistema de regalías, foros básicos. |
| **Fase 5: Lanzamiento** | Q2 2027 | Beta pública, marketing, feedback de usuarios reales. |

---

## 🔗 Documentos Relacionados

- [README](../README.md)
- [Casos de Uso](./arquitectura/casos-de-uso.puml)
- [Modelo de Datos](./arquitectura/entidad-relacion.puml)
- [Decisiones Técnicas](./arquitectura/decisiones-tecnicas/)
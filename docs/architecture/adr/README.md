# Architecture Decision Records (ADRs)

Este directorio contiene los **Architecture Decision Records** de Epic Things Platform.

## ¿Qué es un ADR?

Un ADR es un documento que captura una decisión arquitectónica importante, incluyendo el contexto, la decisión y las consecuencias. Estos documentos ayudan a:

1. **Documentar el "por qué"** detrás de las decisiones técnicas.
2. **Servir de referencia** para futuros desarrolladores.
3. **Facilitar el onboarding** de nuevos miembros del equipo.
4. **Evaluar decisiones** en el futuro.

---

## Lista de ADRs

| ID | Título | Estado | Fecha |
| :--- | :--- | :--- | :--- |
| [001](./001-usar-nodejs-en-backend.md) | Usar Node.js en el Backend | ✅ Aceptado | 2026-09-01 |
| [002](./002-arquitectura-microservicios.md) | Arquitectura de Microservicios | ✅ Aceptado | 2026-09-01 |
| [003](./003-postgresql-como-bd-principal.md) | PostgreSQL como BD Principal | ✅ Aceptado | 2026-09-01 |
| [004](./004-stripe-para-pagos.md) | Stripe para Pagos | ✅ Aceptado | 2026-09-01 |
| [005](./005-react-y-acadframe-frontend.md) | React y AcadFrame para Frontend | ✅ Aceptado | 2026-09-01 |
| [006](./006-docker-para-orquestacion.md) | Docker para Orquestación | ✅ Aceptado | 2026-09-01 |
| [007](./007-jwt-para-autenticacion.md) | JWT para Autenticación | ✅ Aceptado | 2026-09-01 |
| [008](./008-redis-para-cache-y-sesiones.md) | Redis para Caché y Sesiones | ✅ Aceptado | 2026-09-01 |

---

## Estado de los ADRs

| Estado | Significado |
| :--- | :--- |
| **Propuesto** | La decisión está siendo considerada. |
| **Aceptado** | La decisión ha sido aprobada y se implementará. |
| **Rechazado** | La decisión fue considerada pero no seleccionada. |
| **Obsoleto** | La decisión ya no es aplicable. |
| **Reemplazado** | La decisión ha sido reemplazada por otra. |

---

## Plantilla

Para crear un nuevo ADR, usa la plantilla [template.md](./template.md).

---

## Referencias

- [Architecture Decision Records - GitHub](https://adr.github.io/)
- [Documenting Architecture Decisions - ThoughtWorks](https://www.thoughtworks.com/radar/techniques/documenting-architecture-decisions)
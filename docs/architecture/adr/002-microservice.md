# ADR-002: Adoptar Arquitectura de Microservicios

**Fecha:** 2026-09-05
**Estado:** Aceptado  
**Autores:** Álvaro Parra  
**Última Actualización:** 2026-09-05 

---

## Contexto

Epic Things Platform necesita manejar funcionalidades diversas: autenticación, catálogo de juegos, pagos, comunidad, notificaciones y análisis. Cada una tiene requisitos diferentes en términos de rendimiento, escalabilidad y frecuencia de cambios.

### Factores a Considerar

1. **Escalabilidad independiente**: Algunos servicios (Games) necesitarán más recursos que otros (Auth).
2. **Despliegue independiente**: Poder actualizar un servicio sin afectar a los demás.
3. **Equipo de desarrollo**: Aunque actualmente es una persona, la arquitectura debe permitir crecimiento.
4. **Tecnologías mixtas**: Algunos servicios pueden beneficiarse de lenguajes específicos (Python para análisis).
5. **Complejidad operacional**: La orquestación de múltiples servicios añade complejidad.
6. **Tolerancia a fallos**: Un fallo en un servicio no debe tumbar toda la plataforma.

### Restricciones

- El proyecto debe ser desplegable con Docker Compose para desarrollo y Kubernetes para producción.
- La comunicación entre servicios debe ser eficiente.
- Se requiere autenticación centralizada (API Gateway).

---

## Decisión

**Adoptaremos una arquitectura de microservicios, con 6 servicios principales:**

| Servicio | Tecnología | Responsabilidad |
| :--- | :--- | :--- |
| **Auth Service** | Node.js/PHP | Autenticación, JWT, roles, 2FA |
| **Games Service** | Node.js | Catálogo, subida, revisión, búsqueda |
| **Payment Service** | Node.js | Stripe, suscripciones, regalías |
| **Community Service** | Node.js | Valoraciones, comentarios, reportes |
| **Notification Service** | Node.js | Emails, WebSockets, notificaciones |
| **Analytics Service** | Python | Métricas, reportes, dashboards |

**Comunicación:**
- **Síncrona**: REST API a través de API Gateway (Nginx).
- **Asíncrona**: RabbitMQ para eventos (usuario.registrado, pago.completado, etc.).

### Alternativas Consideradas

1. **Monolito Modular**
   - ✅ Más simple de desarrollar y desplegar inicialmente.
   - ✅ Menor complejidad operacional.
   - ❌ Escalabilidad limitada (todo escala junto).
   - ❌ Los cambios afectan a todo el sistema.
   - ❌ Dificultad para usar diferentes tecnologías.

2. **Serverless (AWS Lambda)**
   - ✅ Escala automática.
   - ✅ Pago por uso.
   - ❌ Cold starts.
   - ❌ Limitaciones de ejecución.
   - ❌ Vendor lock-in.

3. **Microservicios con Kubernetes**
   - ✅ Escalabilidad granular.
   - ✅ Despliegue independiente.
   - ✅ Tolerancia a fallos.
   - ❌ Mayor complejidad operacional.
   - ❌ Curva de aprendizaje más empinada.

---

## Consecuencias

### Positivas

1. **Escalabilidad granular**: Cada servicio escala según su demanda.
2. **Despliegue independiente**: Podemos actualizar Payment sin tocar Auth.
3. **Tecnologías mixtas**: Analytics en Python, el resto en Node.js.
4. **Tolerancia a fallos**: Si Notification falla, los demás servicios siguen funcionando.
5. **Equipos autónomos**: En el futuro, diferentes equipos pueden encargarse de servicios distintos.

### Negativas (Riesgos)

1. **Complejidad operacional**: Necesitamos orquestar 6 servicios + infraestructura.
2. **Latencia de red**: Comunicación entre servicios añade latencia.
3. **Gestión de transacciones distribuidas**: Más complejo que en un monolito.
4. **Curva de aprendizaje**: Docker, Kubernetes, RabbitMQ, etc.

### Compromisos

1. **API Gateway centralizado**: Nginx maneja autenticación y enrutamiento.
2. **Cola de mensajes**: RabbitMQ para comunicación asíncrona y desacoplamiento.
3. **Monitoreo centralizado**: Logs agregados en Elasticsearch.
4. **Circuit Breaker**: Para evitar fallos en cascada.

---

## Justificación

La arquitectura de microservicios nos da la flexibilidad que Epic Things Platform necesita. Aunque añade complejidad, esta es manejable con Docker Compose para desarrollo y Kubernetes para producción.

La separación en servicios nos permite:
- Escalar Games Service independientemente (que tendrá más carga).
- Usar Python para Analytics (mejor ecosistema de datos).
- Desplegar nuevas versiones de Payment sin riesgo para los demás servicios.

El **API Gateway** centraliza la autenticación, simplificando la seguridad, y **RabbitMQ** permite comunicación asíncrona para eventos como notificaciones y análisis.

---

## Referencias

- [Microservices Pattern - Martin Fowler](https://martinfowler.com/articles/microservices.html)
- [Building Microservices - Sam Newman](https://samnewman.io/books/building-microservices/)
- [Nginx as API Gateway](https://www.nginx.com/learn/api-gateway/)
- [RabbitMQ - Message Queuing](https://www.rabbitmq.com/)

---

## Historial de Cambios

| Fecha | Versión | Cambio |
| :--- | :--- | :--- |
| 2026-09-05 | 1.0 | Creación inicial |
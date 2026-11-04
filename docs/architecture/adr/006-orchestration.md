# ADR-006: Usar Docker y Docker Compose para Orquestación

**Fecha:** 2026-09-05
**Estado:** Aceptado  
**Autores:** Álvaro Parra  
**Última Actualización:** 2026-09-05

---

## Contexto

Epic Things Platform tiene múltiples microservicios, bases de datos, colas de mensajes y otros componentes. Necesitamos una forma estandarizada y reproducible de ejecutar el sistema en desarrollo, pruebas y producción.

### Factores a Considerar

1. **Reproducibilidad**: Mismo entorno en todas las máquinas.
2. **Aislamiento**: Cada servicio debe ser independiente.
3. **Escalabilidad**: Fácil de escalar servicios en producción.
4. **Portabilidad**: Funcionar en cualquier sistema (Linux, macOS, Windows).
5. **Automatización**: Integración con CI/CD (GitHub Actions).
6. **Gestión de dependencias**: Orquestar servicios, volúmenes y redes.

### Restricciones

- Debe ser open-source y sin costos de licencia.
- Debe ser compatible con Kubernetes (para producción).
- Debe permitir desarrollo local con hot-reload.

---

## Decisión

**Usaremos Docker para contenerización y Docker Compose para orquestación en desarrollo y pruebas.**

- **Docker**: Cada microservicio se empaqueta en una imagen.
- **Docker Compose**: Orquesta todos los servicios, redes y volúmenes.
- **Kubernetes**: (Futuro) Para producción, cuando el sistema crezca.

### Estructura de Imágenes Docker

| Servicio | Imagen Base | Contexto |
| :--- | :--- | :--- |
| auth-service | node:18-alpine | ./backend/auth-service |
| games-service | node:18-alpine | ./backend/games-service |
| payment-service | node:18-alpine | ./backend/payment-service |
| community-service | node:18-alpine | ./backend/community-service |
| notification-service | node:18-alpine | ./backend/notification-service |
| analytics-service | python:3.11-slim | ./backend/analytics-service |
| frontend-web | node:18-alpine | ./frontend/web-app |
| postgres | postgres:15-alpine | - |
| redis | redis:7-alpine | - |
| rabbitmq | rabbitmq:3-management-alpine | - |
| minio | minio/minio:latest | - |
| elasticsearch | elasticsearch:8.11.0 | - |

### Alternativas Consideradas

1. **Sin contenedores (instalación directa)**
   - ✅ Simple para empezar.
   - ❌ Dependencias conflictivas.
   - ❌ Difícil de reproducir.
   - ❌ No escala bien.

2. **Vagrant**
   - ✅ Máquinas virtuales aisladas.
   - ✅ Configuración reproducible.
   - ❌ Uso intensivo de recursos.
   - ❌ Lento para arrancar.

3. **Kubernetes desde el inicio**
   - ✅ Escalabilidad nativa.
   - ✅ Self-healing.
   - ❌ Curva de aprendizaje muy empinada.
   - ❌ Overkill para desarrollo local.

---

## Consecuencias

### Positivas

1. **Reproducibilidad**: `docker-compose up` y todo funciona.
2. **Aislamiento**: Cada servicio tiene sus propias dependencias.
3. **Portabilidad**: Funciona en Linux, macOS y Windows.
4. **Escalabilidad**: Fácil de escalar con `docker-compose up --scale`.
5. **Integración CI/CD**: GitHub Actions puede construir y desplegar imágenes.
6. **Estandarización**: Mismo entorno en desarrollo, pruebas y producción.

### Negativas (Riesgos)

1. **Recursos**: Docker puede consumir mucha RAM/CPU.
2. **Curva de aprendizaje**: Conceptos como volúmenes, redes y compose files.
3. **Persistencia de datos**: Requiere manejar volúmenes cuidadosamente.

### Compromisos

1. **Docker Compose para desarrollo**: `docker-compose up` con hot-reload.
2. **Docker Compose para producción**: `docker-compose -f docker-compose.prod.yml up`.
3. **Volúmenes para datos persistentes**: PostgreSQL, Redis, MinIO.
4. **Healthchecks**: Para asegurar que los servicios están listos.

---

## Justificación

Docker es el estándar de facto para contenerización y Docker Compose simplifica la orquestación en entornos de desarrollo y pruebas.

Para un sistema con 6 microservicios + infraestructura, Docker Compose es la **herramienta adecuada** por su balance entre simplicidad y funcionalidad. Kubernetes se añadirá cuando el sistema llegue a producción.

---

## Referencias

- [Docker Official Documentation](https://docs.docker.com/)
- [Docker Compose Documentation](https://docs.docker.com/compose/)
- [Best Practices for Dockerfiles](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)

---

## Historial de Cambios

| Fecha | Versión | Cambio |
| :--- | :--- | :--- |
| 2026-09-05 | 1.0 | Creación inicial |
# ADR-008: Redis para Caché, Sesiones y Colas Ligeras

**Fecha:** 2026-09-05 
**Estado:** Aceptado  
**Autores:** Álvaro Parra  
**Última Actualización:** 2026-09-05

---

## Contexto

Epic Things Platform necesita manejar caché para reducir carga en la base de datos, almacenar sesiones/refresh tokens, y procesar colas ligeras (notificaciones, eventos). Redis es una base de datos en memoria que puede cubrir estos casos de uso.

### Factores a Considerar

1. **Rendimiento**: Necesitamos respuestas en milisegundos para caché.
2. **Persistencia**: Los datos importantes (refresh tokens) deben sobrevivir a reinicios.
3. **Estructuras de datos**: Necesitamos strings, hashes, sets y listas.
4. **Escalabilidad**: Capacidad para manejar miles de sesiones concurrentes.
5. **Simplicidad**: Fácil de configurar y administrar.

### Restricciones

- Debe ser open-source y sin costos de licencia.
- Debe ser compatible con Docker.
- Debe tener soporte para TTL (Time To Live) en claves.

---

## Decisión

**Usaremos Redis para caché, almacenamiento de refresh tokens, rate limiting y colas ligeras.**

### Casos de Uso en Redis

| Caso de Uso | Estructura | TTL |
| :--- | :--- | :--- |
| **Refresh Tokens** | String (key: `refresh_token:{token}`) | 7 días |
| **Sesiones de Usuario** | Hash (key: `session:{user_id}`) | 24h |
| **Caché de Juegos Populares** | Hash o String | 1h - 24h |
| **Rate Limiting** | String + INCR | 1 minuto |
| **Cola de Notificaciones** | List (LPUSH / RPOP) | - |
| **Blacklist de JWT** | Set (key: `blacklist:{jti}`) | 24h |

### Alternativas Consideradas

1. **Memcached**
   - ✅ Muy rápido.
   - ✅ Simple.
   - ❌ Sin persistencia.
   - ❌ Estructuras de datos limitadas (solo strings).

2. **Caché en Base de Datos (PostgreSQL)**
   - ✅ Coherencia de datos.
   - ❌ Más lento que Redis.
   - ❌ Añade carga a la base de datos.

3. **Sin caché**
   - ✅ Simple.
   - ❌ Mayor latencia.
   - ❌ Mayor carga en la base de datos.

---

## Consecuencias

### Positivas

1. **Rendimiento excepcional**: Responde en microsegundos.
2. **Estructuras de datos versátiles**: Strings, hashes, lists, sets, sorted sets.
3. **Persistencia opcional**: AOF/RDB para guardar datos importantes.
4. **TTL nativo**: Expiración automática de claves.
5. **Operaciones atómicas**: INCR para rate limiting.
6. **Pub/Sub**: Para notificaciones en tiempo real.

### Negativas (Riesgos)

1. **Consumo de memoria**: Todo se almacena en RAM.
2. **Persistencia limitada**: RDB/AOF pueden perder datos si no se configuran correctamente.
3. **Single-threaded**: En versiones antiguas, pero Redis 7 tiene mejoras.

### Compromisos

1. **Persistencia RDB + AOF**: Para balancear rendimiento y durabilidad.
2. **Monitoreo de memoria**: Alertas cuando el uso supere el 80%.
3. **Cache invalidation**: Estrategia clara para invalidar caché (TTL + eventos).
4. **Redis Cluster**: (Futuro) para alta disponibilidad.

---

## Justificación

Redis es la **mejor herramienta** para casos de uso que requieren **alta velocidad** y **estructuras de datos versátiles**. Su soporte nativo para TTL y operaciones atómicas lo hace ideal para rate limiting, sesiones y refresh tokens.

Aunque no es una base de datos de propósito general, su uso complementario con PostgreSQL nos da lo mejor de ambos mundos: **durabilidad** (PostgreSQL) y **velocidad** (Redis).

---

## Referencias

- [Redis Official Documentation](https://redis.io/docs/)
- [Redis as a Cache](https://redis.io/topics/cache)
- [Redis Persistence](https://redis.io/docs/management/persistence/)
- [Redis with Node.js](https://redis.io/docs/clients/nodejs/)

---

## Historial de Cambios

| Fecha | Versión | Cambio |
| :--- | :--- | :--- |
| 2026-09-05 | 1.0 | Creación inicial |
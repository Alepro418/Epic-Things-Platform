# ADR-003: PostgreSQL como Base de Datos Principal

**Fecha:** 2026-09-05
**Estado:** Aceptado  
**Autores:** Álvaro Parra  
**Última Actualización:** 2026-09-05

---

## Contexto

Epic Things Platform necesita almacenar datos estructurados: usuarios, juegos, suscripciones, transacciones, valoraciones, etc. Estos datos tienen relaciones complejas y requieren integridad referencial.

### Factores a Considerar

1. **Integridad de datos**: Necesitamos transacciones ACID para pagos y suscripciones.
2. **Relaciones complejas**: Usuarios-Juegos, Valoraciones-Usuarios, etc.
3. **Escalabilidad**: Capacidad para manejar miles de usuarios y juegos.
4. **Flexibilidad**: Posibilidad de almacenar campos JSON para características dinámicas.
5. **Madurez**: Estabilidad, seguridad y herramientas de monitoreo.
6. **Costo**: Solución open-source sin licencias.

### Restricciones

- Debe ser compatible con Docker para desarrollo y producción.
- Debe tener soporte para backups y replicación.
- Debe permitir migraciones controladas.

---

## Decisión

**Usaremos PostgreSQL como base de datos principal para todos los microservicios.**

Cada servicio tendrá su propio esquema/tablas dentro de la misma base de datos (o bases de datos separadas en producción para mayor aislamiento).

### Alternativas Consideradas

1. **MySQL**
   - ✅ Muy maduro y ampliamente usado.
   - ✅ Excelente rendimiento en lecturas.
   - ❌ Menor soporte para JSON y tipos avanzados.
   - ❌ Menos funcionalidades de integridad referencial.

2. **MongoDB (NoSQL)**
   - ✅ Flexibilidad de esquema.
   - ✅ Escalabilidad horizontal nativa.
   - ❌ No tiene transacciones ACID robustas (crítico para pagos).
   - ❌ Menor soporte para consultas complejas (JOINs).

3. **SQLite**
   - ✅ Sencillo y sin configuración.
   - ✅ Ideal para desarrollo.
   - ❌ No escala para producción.
   - ❌ No soporta alta concurrencia.

---

## Consecuencias

### Positivas

1. **Integridad referencial**: Foreign keys, constraints, triggers.
2. **Transacciones ACID**: Garantía para pagos y suscripciones.
3. **Soporte JSON**: Podemos almacenar atributos dinámicos en campos JSON.
4. **Full-text search**: Búsqueda de juegos por título/descripción.
5. **Extensibilidad**: PostGIS (geolocalización), TimescaleDB (series temporales).
6. **Open-source**: Sin costos de licencia.

### Negativas (Riesgos)

1. **Escalabilidad vertical**: PostgreSQL escala bien hacia arriba, pero el sharding es complejo.
2. **Configuración de replicación**: Requiere configuración cuidadosa.
3. **Costo de migraciones**: Cambios de esquema en producción requieren planificación.

### Compromisos

1. **Read replicas**: Para consultas de lectura (analytics, búsqueda).
2. **Caché con Redis**: Para reducir carga en la base de datos.
3. **Particionamiento**: Para tablas grandes (logs, transacciones).
4. **Backups automáticos**: Diarios con retención de 30 días.

---

## Justificación

PostgreSQL es la mejor opción para un sistema que maneja **datos transaccionales** (pagos, suscripciones) con **relaciones complejas**. Su soporte nativo para JSON nos da flexibilidad sin sacrificar la integridad de datos.

Aunque NoSQL como MongoDB ofrece mayor flexibilidad, la falta de transacciones ACID robustas es un **riesgo inaceptable** para un sistema de pagos.

---

## Referencias

- [PostgreSQL Official Documentation](https://www.postgresql.org/docs/)
- [PostgreSQL vs MySQL - Comparativa](https://www.postgresql.org/about/advantages/)
- [JSON in PostgreSQL](https://www.postgresql.org/docs/current/functions-json.html)
- [PostgreSQL Replication](https://www.postgresql.org/docs/current/different-replication-solutions.html)

---

## Historial de Cambios

| Fecha | Versión | Cambio |
| :--- | :--- | :--- |
| 2026-09-05 | 1.0 | Creación inicial |
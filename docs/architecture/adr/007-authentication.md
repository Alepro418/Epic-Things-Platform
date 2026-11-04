# ADR-007: Usar JWT (JSON Web Tokens) para Autenticación

**Fecha:** 2026-09-05
**Estado:** Aceptado  
**Autores:** Álvaro Parra  
**Última Actualización:** 2026-09-05  

---

## Contexto

Epic Things Platform necesita un sistema de autenticación seguro y escalable. Los usuarios deben poder registrarse, iniciar sesión y acceder a recursos según su rol (Explorador, Jugador, Creador, Mecenas, Administrador).

### Factores a Considerar

1. **Stateless**: No queremos almacenar sesiones en el servidor (escalabilidad).
2. **Seguridad**: Proteger contra ataques CSRF, XSS y robo de tokens.
3. **Escalabilidad**: Funcionar en arquitectura de microservicios.
4. **Rendimiento**: Autenticación sin consultas a base de datos en cada request.
5. **Compatibilidad**: Integración con API Gateway y microservicios.
6. **Revocación**: Posibilidad de invalidar tokens (logout, cambio de contraseña).

### Restricciones

- Debe ser compatible con arquitectura de microservicios.
- Debe integrarse con API Gateway (Nginx).
- Debe soportar refresh tokens para sesiones prolongadas.

---

## Decisión

**Usaremos JWT (JSON Web Tokens) para autenticación, con refresh tokens y blacklist en Redis.**

- **Access Token**: JWT con expiración de 24h, firmado con HS256.
- **Refresh Token**: Token de larga duración (7 días) almacenado en Redis.
- **Blacklist**: Para revocar tokens (logout, cambio de contraseña).
- **API Gateway**: Verifica el JWT en cada request antes de reenviar al microservicio.

### Flujo de Autenticación

1. **Login**: Usuario envía credenciales → Auth Service verifica → Retorna access + refresh tokens.
2. **Requests**: Cliente envía access token en header `Authorization: Bearer <token>`.
3. **Refresh**: Cuando el access token expira, cliente envía refresh token para obtener uno nuevo.
4. **Logout**: Cliente envía refresh token → Auth Service invalida en Redis.

### Alternativas Consideradas

1. **Sesiones tradicionales (Cookies + Session ID)**
   - ✅ Simple de implementar.
   - ✅ Revocación fácil.
   - ❌ Stateful (requiere almacenamiento en servidor).
   - ❌ Dificil de escalar en microservicios.

2. **OAuth 2.0 + OpenID Connect**
   - ✅ Estándar robusto.
   - ✅ Soporte para third-party auth (Google, GitHub).
   - ❌ Complejidad de implementación.
   - ❌ Overkill para un sistema cerrado.

3. **Solo API Keys**
   - ✅ Simple.
   - ❌ No es seguro para usuarios finales.
   - ❌ Sin mecanismo de expiración fácil.

---

## Consecuencias

### Positivas

1. **Stateless**: No requiere almacenamiento de sesiones en servidor.
2. **Escalable**: Funciona en microservicios sin compartir sesiones.
3. **Integración simple**: El API Gateway verifica el JWT y añade `user_id` al request.
4. **Seguridad**: Tokens firmados, no modificables.
5. **Flexibilidad**: Puede incluir roles y permisos en el payload.

### Negativas (Riesgos)

1. **Token invalidation**: Requiere blacklist en Redis para logout.
2. **Robo de tokens**: Si un token es robado, el atacante tiene acceso hasta que expire.
3. **Tamaño**: Los tokens pueden ser grandes si incluyen muchos claims.

### Compromisos

1. **Refresh tokens**: Reducen la necesidad de reautenticación frecuente.
2. **Blacklist en Redis**: Para revocación inmediata.
3. **HTTPS obligatorio**: Para proteger tokens en tránsito.
4. **Tiempo de expiración corto**: 24h para access token.

---

## Justificación

JWT es el **estándar moderno** para autenticación en arquitecturas de microservicios. Es stateless, escalable y fácil de integrar con API Gateways.

Aunque la revocación de tokens es más compleja que con sesiones tradicionales, el uso de **refresh tokens + blacklist en Redis** soluciona este problema de manera efectiva.

---

## Referencias

- [JWT Official Documentation](https://jwt.io/)
- [JWT Best Practices](https://auth0.com/blog/ten-things-you-should-know-about-tokens-and-cookies/)
- [Refresh Tokens in JWT](https://auth0.com/blog/refresh-tokens-what-are-they-and-when-to-use-them/)

---

## Historial de Cambios

| Fecha | Versión | Cambio |
| :--- | :--- | :--- |
| 2026-09-05 | 1.0 | Creación inicial |
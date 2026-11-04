# API Documentation - Epic Things Platform

Este directorio contiene la documentación OpenAPI 3.0 para todos los microservicios de la plataforma.

## 📋 Índice de APIs

| Servicio | Archivo | Descripción | Estado |
| :--- | :--- | :--- | :--- |
| **Auth Service** | [auth.yaml](./auth.yaml) | Autenticación, registro, JWT, 2FA | ✅ Diseñado |
| **Games Service** | [games.yaml](./games.yaml) | Catálogo, subida, revisión, búsqueda | ✅ Diseñado |
| **Payment Service** | [payment.yaml](./payment.yaml) | Suscripciones, Stripe, facturas | ✅ Diseñado |
| **Community Service** | [community.yaml](./community.yaml) | Valoraciones, comentarios, reportes | ⏳ Pendiente |

---

## 🏗️ Arquitectura de la API

┌─────────────────────────────────────────────────────────────────────────────┐
│ API Gateway (Nginx) │
│ Base URL: https://api.epic-things.com │
├─────────────────────────────────────────────────────────────────────────────┤
│ │
│ /api/auth/* → Auth Service (Puerto 3001) │
│ /api/games/* → Games Service (Puerto 3002) │
│ /api/payment/* → Payment Service (Puerto 3003) │
│ /api/community/* → Community Service (Puerto 3004) │
│ │
└─────────────────────────────────────────────────────────────────────────────┘


## 🔒 Autenticación

Todas las APIs (excepto `/auth/*`) requieren autenticación mediante **JWT Bearer Token**.

http
Authorization: Bearer <access_token>

Roles y Permisos

         Rol             |             Nivel              |                Permisos
_________________________|________________________________|_________________________________________
      Explorador                         1                          Lectura de juegos gratuitos     
----------------------------------------------------------------------------------------------------
       Jugador                           2                        Juegos preemiun y valoraciones    
----------------------------------------------------------------------------------------------------
       Creador                           3                            Subir juegos, metricas
----------------------------------------------------------------------------------------------------
       Mecenas                           4                           Beta testing, Votación
----------------------------------------------------------------------------------------------------
    Administrador                        5                               Gestión Completa
____________________________________________________________________________________________________


Códigos de estados

Código           |                        Significado
_________________|__________________________________________________________________
200              |                    OK - Operación exitosa
-----------------|------------------------------------------------------------------
201              |                   Created - Recurso creado
-----------------|------------------------------------------------------------------
400              |                   Bad Request - Error en la solicitud
-----------------|------------------------------------------------------------------
401              |                   Unauthorized - No autenticado
-----------------|------------------------------------------------------------------
403              |                   Forbbiden - Sin permisos
-----------------|------------------------------------------------------------------
404              |                   Not Found - Recurso no encontrado
-----------------|------------------------------------------------------------------
409              |                   Conflict - Conflicto (ej. email duplicado)
-----------------|------------------------------------------------------------------
422              |                   Unprocessable Entity - Validación fallida
-----------------|------------------------------------------------------------------
429              |                   Too Many Requests - Rate limit excedido
-----------------|------------------------------------------------------------------
500              |                   Internal Server Error - Error del servidor
_________________|__________________________________________________________________

## Herramientas Recomendadas

- Swagger UI: npx swagger-ui-watcher auth.yaml

- Postman: Importar OpenAPI para pruebas.

- OpenAPI Generator: Generar clientes en TypeScript/React.

## Convenciones

Nombres de Endpoints
Usar sustantivos en plural: /api/games, /api/users

Verbos HTTP: GET, POST, PUT, DELETE, PATCH

## Paginación

{
  "data": [...],
  "pagination": {
    "page": 1,
    "limit": 20,
    "total": 100,
    "pages": 5
  }
}

## Formato de fechas

ISO 8601: 2026-09-05T12:00:00Z

## Referencias

OpenAPI Specification

REST API Best Practices
# 🔌 Integración con la API (Desarrolladores)

> **Audiencia:** Creadores de juegos y desarrolladores que integran sus juegos con Epic Things Platform  
> **Última actualización:** 2026-09-01  
> **Versión:** 1.0

---

## 📋 Tabla de Contenidos

1. [Introducción](#1-introducción)
2. [Conceptos Básicos](#2-conceptos-básicos)
3. [Autenticación](#3-autenticación)
4. [URLs Base y Entornos](#4-urls-base-y-entornos)
5. [Formato de Respuestas](#5-formato-de-respuestas)
6. [Códigos de Estado y Errores](#6-códigos-de-estado-y-errores)
7. [Rate Limiting](#7-rate-limiting)
8. [Endpoints para Creadores](#8-endpoints-para-creadores)
9. [Flujo Completo de Subida de un Juego](#9-flujo-completo-de-subida-de-un-juego)
10. [Webhooks](#10-webhooks)
11. [SDKs y Ejemplos de Código](#11-sdks-y-ejemplos-de-código)
12. [Sandbox y Pruebas](#12-sandbox-y-pruebas)
13. [Buenas Prácticas](#13-buenas-prácticas)
14. [Solución de Problemas](#14-solución-de-problemas)
15. [Preguntas Frecuentes](#15-preguntas-frecuentes)
16. [Contacto](#16-contacto)

---

## 1. Introducción

La **API de Epic Things Platform** permite a los creadores de juegos:

- 🎮 **Subir** sus juegos de forma programática.
- 📊 **Consultar métricas** de sus juegos en tiempo real.
- 💰 **Ver regalías** y pagos.
- 🔔 **Recibir notificaciones** vía webhooks.
- 🔄 **Automatizar** la gestión de sus juegos.

### ¿A Quién va Dirigida esta Guía?

| Perfil | ¿Le Sirve esta Guía? |
| :--- | :--- |
| **Creador principiante** | ✅ Sí, para subir su primer juego |
| **Creador avanzado** | ✅ Sí, para automatizar subidas |
| **Desarrollador de juegos** | ✅ Sí, para integrar métricas en su juego |
| **Estudiante** | ✅ Sí, para aprender sobre APIs REST |

### ¿Qué Necesitas?

- Una cuenta **Gold** o superior (Creador).
- Conocimientos básicos de **HTTP** y **JSON**.
- Un cliente HTTP (Postman, Insomnia, curl, o código).

---

## 2. Conceptos Básicos

### 2.1. ¿Qué es una API REST?

La API de Epic Things Platform es una **API REST** que usa:

- **HTTP** como protocolo de comunicación.
- **JSON** como formato de datos.
- **JWT** para autenticación.
- **HTTPS** para seguridad.

### 2.2. Verbos HTTP

| Verbo | Uso | Ejemplo |
| :--- | :--- | :--- |
| **GET** | Obtener datos | `GET /api/games/456` |
| **POST** | Crear recurso | `POST /api/games/upload` |
| **PUT** | Actualizar recurso | `PUT /api/games/456` |
| **DELETE** | Eliminar recurso | `DELETE /api/games/456` |
| **PATCH** | Actualizar parcialmente | `PATCH /api/games/456` |

### 2.3. Estructura de una Petición

GET https://api.epic-things.com/api/games/456
Headers:
Authorization: Bearer <token>
Content-Type: application/json
Body:
(ninguno, porque es GET)


### 2.4. Estructura de una Respuesta

```json
{
  "status": 200,
  "data": {
    "id_juego": 456,
    "titulo": "Aventura Épica",
    "estado": "publicado"
  },
  "message": "OK"
}
```
### 3. Autenticación

### 3.1. Obtener tu Token

Todas las peticiones (excepto el login) requieren un token JWT.

Paso 1: Iniciar sesión

curl -X POST https://api.epic-things.com/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{
    "email_or_username": "tu_email@ejemplo.com",
    "password": "tu_contraseña"
  }'

**Respuesta:**

``` json {
  "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "refresh_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "expires_in": 86400,
  "user": {
    "id_usuario": 123,
    "username": "juanito123",
    "roles": ["Creador"]
  }
}
```

**Paso 2: Usar el token**

Incluye el access_token en el header Authorization:

curl -X GET https://api.epic-things.com/api/games/my-games \
  -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."

### 3.2. Refresh Token

El access_token expira en 24 horas. Cuando expire, usa el refresh_token para obtener uno nuevo:

curl -X POST https://api.epic-things.com/api/auth/refresh \
  -H "Content-Type: application/json" \
  -d '{
    "refresh_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
  }'

**Respuesta:**

```json {
  "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "expires_in": 86400
}
```
### 3.3. Seguridad del Token

⚠️ NUNCA compartas tu token en:

Repositorios públicos de GitHub.

• Foros o redes sociales.

• Capturas de pantalla.

• Código del cliente (frontend).

✅ Buenas prácticas:

• Guarda el token en variables de entorno.

• Usa HTTPS siempre.

• Rota el token si sospechas que fue comprometido.

• Cierra sesión cuando termines.

## 4. URLs Base y Entornos 

## 4.1. Entornos Disponibles

| Entorno | URL Base | Uso |
| :--- | :--- | :--- |
| **Producción** | `https://api.epic-things.com/api` | Datos reales |
| **SandBox** | `https://sandbox-api.epic-things.com/api` | Pruebas |
| **Local** | `http://localhost:80/api` | Desarrollo |

## 4.2. ¿Cuándo usar cada entorno?

| Situación | Entorno Recomendado |
| :--- | :--- |
| **Desarrollar un juego** | SandBox |
| **Probar subidas** | SandBox |
| **Subir juego final** | Producción |
| **Consultar métricas reales** | Producción |
| **Desarrollo local** | Local |

**⚠️ Importante:** El entorno **SandBox** se reinicia cada 7 días no uses datos reales allí

## 5. Formato de Respuestas

## 5.1. Respuesta Exitosa

```json {
  "status": 200,
  "data": { ... },
  "message": "OK"
}
```

## 5.2. Respuesta con Paginación

```json {
  "status": 200,
  "data": [ ... ],
  "pagination": {
    "page": 1,
    "limit": 20,
    "total": 150,
    "page": 8
  },
  "message": "OK"
}
```

## 5.3. Respuesta de Error

```json {
  "status": "400",
  "error": "Bad Request"
  "message": "El campo 'titulo' es requerido",
  "details": [
    {
      "field": "titulo",
      "error": "Este campo no puede estar vacío"
    }
  ]
}
```

## 5.4. Formato de Datos 

| Tipo | Formato | Ejemplo |
| :--- | :--- | :--- |
| **Fechas** | ISO 8601 | "2026-09-01T12:00:00Z" |
| **Montos** | Decimal | 15.00 |
| **Booleanos** | True/False | true |
| **IDs** | Entero | 456 |

## 6. Códigos de Estado y Errores

## 6.1. Código de Éxito

| Código | Significado | Cuándo Ocurre |
| :--- | :--- | :--- |
| **200** | OK | Petición exitosa |
| **201** | Created | Recurso creado |
| **204** | No Content  | Eliminación exitosa |

## 6.2. Códigos de Error del Cliente

| Código | Significado | Cuándo Ocurre |
| :--- | :--- | :--- |
| **400** | Bad Request | Datos inválidos |
| **401** | Unauthorized | Token inválido o expirado |
| **403** | Forbidden | Sin permisos (ej. No eres creador) |
| **404** | Not Found | Recurso no encontrado |
| **409** | Conflict | Conflicto (ej. título duplicado) |
| **422** | Unprocessable Entity | Validación fallida |
| **429** | Too Many Request | Rate limit excedido |

## 6.3. Códigos de Error del Servidor

| Código | Significado | Cuándo Ocurre |
| :--- | :--- | :--- |
| **500** | Internal Server Error | Error del Servidor |
| **502** | Bad Gateway  | Error de comunicación |
| **503** | Service Unavailable | Servicio temporalmente caido |

## 6.4. Errores Comunes y Soluciones

| Error | Causa | Solución |
| :--- | :--- | :--- |
| **401 Unauthorized** | Token expirado | Usa `refresh_token` |
| **403 Forbidden** | No eres Creador | Suscríbete a Gold |
| **409 Conflict** | Título duplicado | Usa otro título |
| **429 Too Many** | Requests	Rate limit | Espera y reintenta |
| **500 Internal Server Error** | Error de servidor | Reintenta, contacta a soporte |

## 7 Rate limiting

## 7.1 Límites

| Tipo de Petición | Límite |
| :--- | :--- |
| **Lectura (GET)** | 100 peticiones/minuto |
| **Escritura (POST, PUT, DELETE)** | 30 peticiones/minuto |
| **Subida de archivos** | 5 peticiones/minuto |
| **Login** | 5 intentos/minuto |

## 7.2. Headers de Rate Limting

En cada respuesta, verás:

X-RateLimit-Limit: 100
X-RateLimit-Remaining: 95
X-RateLimit-Reset: 1630454400

| Header |	Descripción  |
| :--- | :--- |
| X-RateLimit-Limit |	Límite total  |
| X-RateLimit-Remaining	| Peticiones restantes  |
| X-RateLimit-Reset |	Timestamp de reinicio |

## 7.3. ¿Qué Hacer si Excedes el Límite?

Si recibes un 429 Too Many Requests:

1. Lee el header Retry-After (segundos a esperar).

2. Espera ese tiempo.

3. Reintenta la petición.

4. Implementa backoff exponencial:

``` javascript

async function fetchWithRetry(url, options, maxRetries = 3) {
  for (let i = 0; i < maxRetries; i++) {
    const response = await fetch(url, options);
    
    if (response.status === 429) {
      const retryAfter = response.headers.get('Retry-After') || 60;
      console.log(`Rate limit. Esperando ${retryAfter}s...`);
      await new Promise(resolve => setTimeout(resolve, retryAfter * 1000));
      continue;
    }
    
    return response;
  }
  throw new Error('Máximo de reintentos alcanzado');
}

```

## 8. Endpoints para Creadores

## 8.1. Resumen de Endpoints 

| Método | Endpoint | Descripción |
| :--- | :--- | :-- |
| **POST** | `/api/games/upload` | Iniciar subida de juego |
| **PUT** | `/api/games/finalize-upload` | Finalizar subida |
| **GET** | `/api/games/my-games` | Listar mis juegos |
| **GET** | `/api/games/{id}` | Detalle de un juego |
| **PUT** | `/api/games/{id}` | Actualizar metadatos |
| **DELETE** | `/api/games/{id}` | Eliminar juego (borrador) |
| **GET** | `/api/games/{id}/metrics` | Métricas del juego |
| **GET** | `/api/games/{id}/status` | Estado del juego |
| **GET** | `/api/payment/royalties` | Resumen de regalías |
| **GET** | `/api/payment/rpyalties/details` | Detalle por juego |

## 8.2. Listar Mis Juegos 

**Endpoint** 

`GET /api/games/my-games?estado=publicado&page=1&limit=20`

**Headers**

`Authorization: Bearer <token>`

**Parámetros**

| parámtro | Tipo | Descripción |
| :--- | :--- | :-- |
| **Estado** | string | Borrador, pendiente, publicado, rechazado |
| **page** | integer | Número de página (default: 1) |
| **limit** | integer | Elementos por página (default: 20, max: 100) |

**Respuesta**

``` json {
  "status": 200,
  "data": [
    {
      "id_juego": 456,
      "titulo": "Aventura Épica",
      "estado": "Publicado",
      "categoria": "Aventura",
      "clasificación_edad": "+7",
      "visitas": 15234,
      "puntuacion_media": 4.9,
      "fecha_publicacion": "2026-08-15T10:30:00Z"
    },
    {
      "id_juego": 457,
      "titulo": "Puzzle_Master",
      "estado": "Pendiente",
      "categoria": "Puzzle",
      "clasificación_edad": "+3",
      "visitas": 0,
      "puntuacion_media": 0,
      "fecha_publicacion": "2026-09-01T14:30:00Z"
    }
  ],
  "pagination": {
    "page": 1,
    "limit": 20,
    "total": 5,
    "pages": 1
  }
}
```

## 8.3. Ver Estado de un Juego

**Endpoint:**

`GET /api/games/{id}/status`

**Respuesta:** 

``` json {
  "status": 200,
  "data": {
    "id_juego": 456,
    "titulo": "Aventura Épica",
    "estado": "publicado",
    "historial": [
      {
        "estado": "borrador",
        "fecha": "2026-08-01T10:00:00Z"
      },
      {
        "estado": "pendiente",
        "fecha": "2026-08-10T15:30:00Z"
      },
      {
        "estado": "publicado",
        "fecha": "2026-08-15T10:30:00Z",
        "comentario": "Excelente juego, bienvenido a la plataforma"
      }
    ]
  }
}
```

## 8.4. Ver Métricas de un Juego

`GET /api/games/{id}/metrics?periodo=30d`

**Parámetros:**

| parámtro | Tipo | Descripción |
| :--- | :--- | :-- |
| **Período** | string | `7d`, `30d`, `90d`, `1y` |

**Respuesta:**

``` json {
  "status": 200,
  "data": {
    "id_juego": 456,
    "titulo": "Aventura Épica",
    "periodo": "30d",
    "metricas": {
      "visitas": 4567,
      "jugadores_unicos": 3200,
      "tiempo_promedio_segundos": 1800,
      "sesiones_totales": 8500,
      "valoraciones": 150,
      "puntuacion_media": 4.9,
      "favoritos": 230,
      "reportes": 2
    },
    "distribucion_edad": {
      "+3": 0,
      "+7": 1800,
      "+12": 1000,
      "+16": 300,
      "+18": 100
    },
    "distribucion_paises": [
      { "pais": "Venezuela", "visitas": 2000 },
      { "pais": "Colombia", "visitas": 1200 },
      { "pais": "México", "visitas": 800 }
    ],
    "tendencia_diaria": [
      { "fecha": "2026-08-01", "visitas": 150 },
      { "fecha": "2026-08-02", "visitas": 180 }
    ]
  }
}
```

## 8.5. Ver Regalías

**Endpoint:**

`GET /api/payment/royalties?year=2026&month=9`

**Respuesta**

``` json {
  "status": 200,
  "data": {
    "periodo": { "year": 2026, "month": 9 },
    "total_ingresos": 1250.50,
    "total_juegos_activos": 5,
    "total_suscriptores": 78,
    "regalia_creador": 875.35,
    "comision_plataforma": 375.15,
    "juegos_top": [
      {
        "id_juego": 456,
        "titulo": "Aventura Épica",
        "ingresos": 600.00,
        "regalia": 420.00,
        "suscriptores": 40
      },
      {
        "id_juego": 457,
        "titulo": "Puzzle Master",
        "ingresos": 400.50,
        "regalia": 280.35,
        "suscriptores": 25
      }
    ]
  }
}
```

## 9. Flujo Completo de Subida de un Juego

**El proceso de subida tiene 3 pasos:**

┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│  1. Crear   │───>│  2. Subir   │───>│ 3. Finalizar│
│   registro  │    │   archivo   │    │   subida    │
└─────────────┘    └─────────────┘    └─────────────┘

## Paso 1: Crear Registro del Juego

**Endpoint:**

`POST /api/games/upload`

**Headers:**

Authorization: Bearer <token>
Content-Type: application/json

**Body:**

``` json {
  "titulo": "Mi Juego Increíble",
  "descripcion": "Un juego de plataformas con gráficos pixel art",
  "categoria": "Aventura",
  "tipo": "html5",
  "precio": 0,
  "url_imagen": "https://cdn.ejemplo.com/portada.png"
}
```

**Respuesta:**

``` json {
  "status": 201,
  "data": {
    "id_juego": 458,
    "upload_url": "https://storage.epic-things.com/uploads/458/game.zip?token=abc123...",
    "expires_at": "2026-09-01T13:00:00Z",
    "message": "Registro creado. Sube el archivo a la URL proporcionada."
  }
}
```
**⚠️ Importante:** La `upload_url` expira en 1 hora. Si no subes el archivo en ese tiempo, deberás reiniciar el proceso.

## Paso 2: Subir el Archivo

**Endpoint:** Usa la `upload_url` retornada.

``` bash
curl -X PUT "https://storage.epic-things.com/uploads/458/game.zip?token=abc123..." \
  -H "Content-Type: application/zip" \
  --upload-file mi-juego.zip
```

**Respuesta:**

``` json {
  "status": 200,
  "data": {
    "url_archivo": "https://cdn.epic-things.com/games/458/game.zip",
    "tamaño": 1048576,
    "hash_sha256": "a1b2c3d4e5f6..."
  }
}
```

## Paso 3: Finalizar Subida

**Endpoint:**

`PUT /api/games/finalize-upload`

**Body:**

``` json {
  "id_juego": 458,
  "url_archivo": "https://cdn.epic-things.com/games/458/game.zip",
  "hash_archivo": "a1b2c3d4e5f6...",
  "tamaño": 1048576
}
```

**Respuesta:**

``` json {
  "status": 200,
  "data": {
    "id_juego": 458,
    "estado": "pendiente",
    "message": "Juego enviado a revisión. Recibirás una notificación cuando sea aprobado."
  }
}
```

## Ejemplo Completo en JavaScript

``` javascript
async function uploadGame(token, gameData, gameFile) {
  const baseUrl = 'https://api.epic-things.com/api';
  
  // Paso 1: Crear registro
  const createResponse = await fetch(`${baseUrl}/games/upload`, {
    method: 'POST',
    headers: {
      'Authorization': `Bearer ${token}`,
      'Content-Type': 'application/json'
    },
    body: JSON.stringify(gameData)
  });
  
  if (!createResponse.ok) {
    throw new Error(`Error creando registro: ${createResponse.status}`);
  }
  
  const { data: { id_juego, upload_url } } = await createResponse.json();
  console.log(`Juego registrado con ID: ${id_juego}`);
  
  // Paso 2: Subir archivo
  const uploadResponse = await fetch(upload_url, {
    method: 'PUT',
    headers: {
      'Content-Type': 'application/zip'
    },
    body: gameFile
  });
  
  if (!uploadResponse.ok) {
    throw new Error(`Error subiendo archivo: ${uploadResponse.status}`);
  }
  
  const { data: uploadData } = await uploadResponse.json();
  console.log(`Archivo subido: ${uploadData.url_archivo}`);
  
  // Paso 3: Finalizar
  const finalizeResponse = await fetch(`${baseUrl}/games/finalize-upload`, {
    method: 'PUT',
    headers: {
      'Authorization': `Bearer ${token}`,
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({
      id_juego: id_juego,
      url_archivo: uploadData.url_archivo,
      hash_archivo: uploadData.hash_sha256,
      tamaño: uploadData.tamaño
    })
  });
  
  if (!finalizeResponse.ok) {
    throw new Error(`Error finalizando: ${finalizeResponse.status}`);
  }
  
  const { data: finalizeData } = await finalizeResponse.json();
  console.log(`Juego enviado a revisión: ${finalizeData.message}`);
  
  return id_juego;
}

// Uso
const gameFile = new Blob([fs.readFileSync('mi-juego.zip')]);
uploadGame(token, {
  titulo: 'Mi Juego Increíble',
  descripcion: 'Un juego de plataformas',
  categoria: 'Aventura',
  tipo: 'html5',
  precio: 0
}, gameFile);
```

## 10. Webhooks

## 10.1. ¿Qué son los Webhooks?

Los webhooks son notificaciones automáticas que la plataforma envía a tu servidor cuando ocurre un evento (ej. juego aprobado, pago recibido).

┌─────────────┐         ┌─────────────┐
│  Epic Things│──POST──>│ Tu Servidor │
│  Platform   │         │  (Webhook)  │
└─────────────┘         └─────────────┘

## 10.2. Eventos Disponibles


| Evento  | Descripción |
| :---  | :-- |
| `game.approved` | Tu juego fue aprovado |
| `game.rejected` | Tu juego fue rechazado |
| `game.suspended` | Tu juego fue suspendido |
| `game.reactived` | Tu juego fue reactivado |
| `game.deleted` | Tu juego fue eliminado |
| `royalty.paid` | Se procesó un pago de regalía |
| `subscription.created` | Un usuario se suscribió a tu juego |
| `subscription.cancelled` | Un usuario canceló su suscripción |

## 10.3. Configurar Webhooks

1. Ve a Dashboard → Configuración → Webhooks.

2. Añade la URL de tu servidor (debe ser HTTPS).

3. Selecciona los eventos que quieres recibir.

4. Guarda el secret para verificar la firma.

## 10.4. Formato del Webhook

**Headers:**

Content-Type: application/json
X-Epic-Signature: sha256=abc123...
X-Epic-Event: game.approved

**Body:**

``` json {
  "event": "game.approved",
  "timestamp": "2026-09-01T12:00:00Z",
  "data": {
    "id_juego": 456,
    "titulo": "Aventura Épica",
    "estado": "publicado",
    "clasificacion_edad": "+7"
  }
}
```

## 10.5. Verificar la Firma

**Importante:** Siempre verifica que el webhook viene de Epic Things Platform.

``` javascript 
const crypto = require('crypto');

function verifyWebhook(body, signature, secret) {
  const expectedSignature = 'sha256=' + crypto
    .createHmac('sha256', secret)
    .update(body)
    .digest('hex');
  
  return crypto.timingSafeEqual(
    Buffer.from(signature),
    Buffer.from(expectedSignature)
  );
}

// En tu endpoint
app.post('/webhook/epic-things', (req, res) => {
  const signature = req.headers['x-epic-signature'];
  const secret = process.env.EPIC_THINGS_WEBHOOK_SECRET;
  
  if (!verifyWebhook(JSON.stringify(req.body), signature, secret)) {
    return res.status(401).json({ error: 'Firma inválida' });
  }
  
  const { event, data } = req.body;
  
  switch (event) {
    case 'game.approved':
      console.log(`¡Juego aprobado! ID: ${data.id_juego}`);
      break;
    case 'game.rejected':
      console.log(`Juego rechazado: ${data.motivo}`);
      break;
  }
  
  res.status(200).json({ received: true });
});
```

## 10.6. Reintentos

Si tu servidor no responde con **2xx**, el webhook se reintenta:

| Intento  | Tiempo de Espera |
| :---  | :-- |
| **1** | Inmediato |
| **2** | 5 minutos |
| **3** | 30 minutos |
| **4** | 2 horas |
| **5** | 24 horas |

Si todos fallan, el webhook se marca como fallido y recibirás una notificación.

## 11. SDKs y Ejemplos de Código

## 11.1. Ejemplos con curl

**Login**

``` bash 
  curl -X POST https://api.epic-things.com/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email_or_username": "juan@ejemplo.com", "password": "pass123"}'
```

**Listar mis juegos**

``` bash
  curl -X GET "https://api.epic-things.com/api/games/my-games?estado=publicado" \
  -H "Authorization: Bearer $TOKEN"
```

**Subir un Juego**

``` bash
  # Paso 1
curl -X POST https://api.epic-things.com/api/games/upload \
  -H "Authorization: Bearer $TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"titulo": "Mi Juego", "categoria": "Aventura", "tipo": "html5"}'

# Paso 2 (usar upload_url del paso 1)
curl -X PUT "$UPLOAD_URL" \
  -H "Content-Type: application/zip" \
  --upload-file mi-juego.zip

# Paso 3
curl -X PUT https://api.epic-things.com/api/games/finalize-upload \
  -H "Authorization: Bearer $TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"id_juego": 458, "url_archivo": "...", "hash_archivo": "..."}'
```

## 11.2. Ejemplo con Python

``` python 
  import requests
import os

class EpicThingsClient:
    def __init__(self, token):
        self.base_url = 'https://api.epic-things.com/api'
        self.token = token
        self.headers = {
            'Authorization': f'Bearer {token}',
            'Content-Type': 'application/json'
        }
    
    def list_my_games(self, estado=None):
        params = {'estado': estado} if estado else {}
        response = requests.get(
            f'{self.base_url}/games/my-games',
            headers=self.headers,
            params=params
        )
        response.raise_for_status()
        return response.json()['data']
    
    def upload_game(self, game_data, file_path):
        # Paso 1: Crear registro
        response = requests.post(
            f'{self.base_url}/games/upload',
            headers=self.headers,
            json=game_data
        )
        response.raise_for_status()
        data = response.json()['data']
        id_juego = data['id_juego']
        upload_url = data['upload_url']
        
        # Paso 2: Subir archivo
        with open(file_path, 'rb') as f:
            upload_response = requests.put(
                upload_url,
                data=f,
                headers={'Content-Type': 'application/zip'}
            )
            upload_response.raise_for_status()
            upload_data = upload_response.json()['data']
        
        # Paso 3: Finalizar
        finalize_response = requests.put(
            f'{self.base_url}/games/finalize-upload',
            headers=self.headers,
            json={
                'id_juego': id_juego,
                'url_archivo': upload_data['url_archivo'],
                'hash_archivo': upload_data['hash_sha256'],
                'tamaño': upload_data['tamaño']
            }
        )
        finalize_response.raise_for_status()
        return id_juego

# Uso
client = EpicThingsClient(os.environ['EPIC_TOKEN'])
games = client.list_my_games(estado='publicado')
print(f"Tienes {len(games)} juegos publicados")

id_juego = client.upload_game(
    game_data={
        'titulo': 'Mi Juego Increíble',
        'categoria': 'Aventura',
        'tipo': 'html5',
        'precio': 0
    },
    file_path='mi-juego.zip'
)
print(f"Juego subido con ID: {id_juego}")
```

## 11.3. SDKs Oficiales (Próximamente)

| Intento  | Tiempo de Espera |
| :---  | :-- |
| **Javascript/Typescript** | ⏳ En desarrollo |
| **Python** | ⏳ En desarrollo |
| **PHP** | ⏳ Planificado |
| **C++** | ⏳ Planificado |

Mientras tanto, usa los ejemplos con curl o HTTP nativo.

## 12. Sandbox y Pruebas

## 12.1. ¿Qué es el Sandbox?

El **Sandbox** es un entorno de pruebas que replica la API de producción, pero con datos ficticios.

**URL:** `https://sandbox-api.epic-things.com/api`

## 12.2. Diferencias con Producción

| Aspecto  | SandBox | Producción |
| :---  | :-- | :-- |
| **Datos** | Ficticios | Reales |
| **Pagos** | Simulados | Reales |
| **Reinicio** | Cada 7 días | Nunca |
| **Juegos** | No se publican | Se publican |

## 12.3. Credenciales de Sandbox

| Usuario  | Email | Contraseña |
| :---  | :-- | :-- |
| **Creador** | creador@sandbox.com | Sandbox123! |
| **Jugador** | jugador@sandbox.com | Sandbox123! |
| **Admin** | admin@sandbox.com	| Sandbox123! |

## 12.4. Tarjetas de Prueba (Stripe)

| Número  | Resultado | 
| :---  | :-- | :-- |
| **4242 4242 4242 4242** | Pago exitoso |
| **4000 0000 0000 0002** | Pago declinado |
| **4000 0000 0000 9995** | Fondos insuficientes	|

## 12.5. Probar tu Juego

1. Sube tu juego al Sandbox.

2. Espera la "aprobación automática" (en sandbox es instantánea).

3. Juega en https://sandbox.epic-things.com/games/{id}.

4. Verifica que todo funcione correctamente.

5. Una vez validado, sube a producción.

## 13. Buenas Prácticas

## 13.1. Seguridad

• 🔐 Guarda tu token en variables de entorno, nunca en código.

• 🔒 Verifica las firmas de los webhooks.

• 🚫 No expongas tu token en el frontend.

• 🔄 Rota tokens si sospechas compromiso.

• 🌐 Usa HTTPS siempre.

## 13.2. Manejo de Errores

• ✅ Siempre verifica el status code.

• 🔁 Implementa reintentos con backoff exponencial.

• 📝 Loggea errores para debugging.

• 🎯 Diferencia errores del cliente y del servidor.

## 13.3. Rate Limiting

• 📊 Monitorea los headers de rate limit.

• ⏱️ Respeta el Retry-After.

• 🚦 Distribuye peticiones en el tiempo.

• 📈 Usa caché para reducir peticiones.

## 13.4. Subida de Juegos

• 📦 Comprime bien el archivo (ZIP).

• 🖼️ Optimiza la imagen de portada.

• 📝 Escribe una buena descripción.

• 🧪 Prueba en Sandbox antes de producción.

• ⏰ Respeta el límite de 1 hora para la upload_url.

## 13.5. Webhooks

• 🔒 Verifica siempre la firma.

• ⚡ Responde rápido (menos de 5 segundos).

• 📝 Idempotencia: maneja duplicados.

• 🔁 Implementa reintentos propios.

## 14. Solución de Problemas

## 14.1. Error: "401 Unauthorized"

**Causa:** Token inválido o expirado.

**Solución:**

1. Verifica que el token esté bien copiado.

2. Comprueba la fecha de expiración.

3. Usa refresh_token para renovarlo.

4. Si persiste, vuelve a iniciar sesión.

## 14.2. Error: "403 Forbidden"

**Causa:** No tienes permisos (ej. no eres Creador).

**Solución:**

1. Verifica tu rol en /api/auth/me.

2. Si necesitas ser Creador, suscríbete a Gold.

## 14.3. Error: "409 Conflict"

**Causa:** Ya existe un juego con ese título.

**Solución:**

1. Cambia el título del juego.

2. Verifica en /api/games/my-games si ya existe.

## 14.4. Error: "429 Too Many Requests"

**Causa:** Excediste el rate limit.

**Solución:**

1. Espera el tiempo indicado en Retry-After.

2. Implementa backoff exponencial.

3. Reduce la frecuencia de peticiones.

## 14.5. Error: "500 Internal Server Error"

**Causa:** Error del servidor.

**Solución:**

1. Reintenta en unos segundos.

2. Si persiste, contacta a soporte con:

    ° Endpoint afectado.

    ° Timestamp.

    ° ID de juego (si aplica).

    ° Token (parcial).

## 14.6. La Upload URL Expiró

**Causa:** Pasó más de 1 hora desde que se creó.

**Solución:**

1. Descarta el upload_url anterior.

2. Vuelve a llamar a /api/games/upload.

3. Sube el archivo inmediatamente.

## 14.7. Webhook No Llega

**Causa:** Varios posibles.

**Solución:**

1. Verifica que la URL sea accesible desde internet.

2. Comprueba que use HTTPS.

3. Revisa los logs de tu servidor.

4. Verifica el dashboard de webhooks (historial de reintentos).

5. Contacta a soporte si persiste.

## 15. Preguntas Frecuentes

¿Necesito ser Creador para usar la API?

Respuesta: Para los endpoints de subida de juegos y métricas, sí. Necesitas el rol Gold o superior. Para endpoints de lectura (juegos públicos), no.

¿Cuántos juegos puedo subir?

Respuesta: No hay límite, pero cada juego pasa por revisión. Para mantener calidad, recomendamos máximo 10 juegos activos.

¿Cuánto tarda la revisión?

Respuesta: 24-48 horas en días hábiles. En Sandbox es instantánea.

¿Puedo actualizar un juego ya publicado?

Respuesta: Sí. Usa PUT `/api/games/{id}` para metadatos. Para el archivo, debes subir una nueva versión (pasa por revisión nuevamente).

¿Puedo eliminar un juego?

Respuesta: Solo si está en estado borrador o rechazado. Para juegos publicados, debes solicitar la eliminación a soporte.

¿Cómo obtengo mi token?

Respuesta: Usa POST `/api/auth/login` con tu email/username y contraseña.

¿Qué hago si mi token fue comprometido?

Respuesta:

Cambia tu contraseña inmediatamente.

Cierra sesión en todos los dispositivos.

Contacta a soporte.

Genera un nuevo token.

¿Los webhooks son obligatorios?

Respuesta: No, pero son muy recomendados para automatizar flujos (ej. notificar a tus usuarios cuando un juego es aprobado).

¿Puedo usar la API desde el frontend de mi juego?

Respuesta: No directamente. Los tokens no deben exponerse en el cliente. Usa un backend que haga las peticiones a la API.

¿Dónde reporto un bug de la API?

Respuesta: Contacta a soporte:

Email: parraalavaro418@gmail.com

Discord: Canal #soporte-api

GitHub Issues (solo si tienes acceso)

¿Hay un límite de tamaño para los juegos?

Respuesta:

HTML5: 100 MB

Unity: 500 MB

WebGL: 500 MB

Si necesitas más, contacta a soporte.

¿Puedo monetizar mi juego con la API?

Respuesta: Sí, puedes establecer precio en el registro del juego. Recibirás el 70% de los ingresos como regalía.

## 16. Contacto

Soporte para Desarrolladores

| Canal  | Información |
| :---  | :-- |
| **Email** | parraalavaro418@gmail.com |
| **Discord** | Canal #soporte-api |
| **Documentación** | `API Reference` |
| **Sandbox** | `https://sandbox-api.epic-things.com/api` |

## Recursos Adicionales

• 📖 Primeros Pasos como Creador

• 📖 Subir un Juego

• 📖 Crear Juego HTML5

• 📖 Crear Juego Unity

• 📖 Regalías

• 📖 API de Juegos

• 📖 API de Pagos

• 📖 API de Autenticación

## Changelog de la API

| Versión  | Fecha | Cambios |
| :---  | :-- |
| **v1.0.0** | 2026-09-01 | Versión inicial |

## 📝 Historial de Cambios

---

| Versión  | Fecha | Cambios |
| :---  | :-- |
| 2026-09-01 | 1.0	 | Creación inicial |

---

**Hecho con ❤️ desde Puerto Cabello, Venezuela**

*"Gestionar personas es gestionar confianza."*
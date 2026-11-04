# 👥 Gestión de Usuarios (Admin)

> **Audiencia:** Administradores de Epic Things Platform  
> **Última actualización:** 2026-09-01  
> **Versión:** 1.0

---

## 📋 Tabla de Contenidos

1. [Introducción](#1-introducción)
2. [Acceder al Panel de Usuarios](#2-acceder-al-panel-de-usuarios)
3. [Buscar y Filtrar Usuarios](#3-buscar-y-filtrar-usuarios)
4. [Ver Perfil de Usuario](#4-ver-perfil-de-usuario)
5. [Gestión de Roles y Permisos](#5-gestión-de-roles-y-permisos)
6. [Gestión de Suscripciones](#6-gestión-de-suscripciones)
7. [Bloqueo y Suspensión de Usuarios](#7-bloqueo-y-suspensión-de-usuarios)
8. [Eliminación de Usuarios](#8-eliminación-de-usuarios)
9. [Verificación de Edad y Contenido +18](#9-verificación-de-edad-y-contenido-18)
10. [Gestión de Reportes de Usuarios](#10-gestión-de-reportes-de-usuarios)
11. [Logs de Actividad y Auditoría](#11-logs-de-actividad-y-auditoría)
12. [Comunicación con Usuarios](#12-comunicación-con-usuarios)
13. [Buenas Prácticas](#13-buenas-prácticas)
14. [Preguntas Frecuentes](#14-preguntas-frecuentes)
15. [Contacto](#15-contacto)

---

## 1. Introducción

Esta guía está dirigida a los **administradores** de Epic Things Platform y describe el proceso completo para **gestionar usuarios**: búsqueda, visualización de perfiles, asignación de roles, gestión de suscripciones, bloqueo, eliminación y verificación de edad.

### Responsabilidades del Administrador

| Responsabilidad | Descripción |
| :--- | :--- |
| **Buscar usuarios** | Localizar cuentas por email, username o rol |
| **Ver perfiles** | Consultar información detallada de cada usuario |
| **Asignar roles** | Cambiar el nivel de acceso de un usuario |
| **Gestionar suscripciones** | Ver, cancelar o reembolsar suscripciones |
| **Bloquear/suspender** | Restringir el acceso de usuarios problemáticos |
| **Eliminar cuentas** | Borrar permanentemente cuentas (GDPR) |
| **Verificar edad** | Gestionar la verificación para contenido +18 |
| **Resolver reportes** | Atender reportes de usuarios |
| **Auditar acciones** | Revisar logs de actividad |

### ¿Por Qué es Importante la Gestión de Usuarios?

- ✅ **Seguridad**: Proteger la plataforma de usuarios maliciosos.
- ✅ **Cumplimiento legal**: Cumplir con GDPR, COPPA y otras leyes.
- ✅ **Experiencia de usuario**: Asegurar un ambiente seguro y respetuoso.
- ✅ **Soporte**: Ayudar a usuarios con problemas de cuenta.
- ✅ **Integridad**: Mantener la calidad de la comunidad.

---

## 2. Acceder al Panel de Usuarios

### Requisitos

- Cuenta con rol de **Administrador** (nivel 5).
- Sesión activa en la plataforma.
- Permisos de gestión de usuarios.

### Pasos para Acceder

1. **Inicia sesión** con tu cuenta de administrador.
2. En el menú principal, haz clic en **"Admin"**.
3. Selecciona **"Usuarios"**.

**URL directa:**

https://epic-things.com/admin/users


### Interfaz del Panel

┌─────────────────────────────────────────────────────────────────────────────┐
│ 👥 Gestión de Usuarios [Filtros ▼] │
├─────────────────────────────────────────────────────────────────────────────┤
│ │
│ 🔍 [Buscar por email, username o nombre...] [Exportar CSV] │
│ │
│ ┌─────────────────────────────────────────────────────────────────────┐ │
│ │ 👤 @juanito123 juan@ejemplo.com │ │
│ │ Juan Pérez Rol: Creador (Gold) │ │
│ │ Estado: Activo Suscripción: Gold (activa) │ │
│ │ Registro: 2026-01-15 Edad: 25 años │ │
│ │ │ │
│ │ [Ver perfil] [Cambiar rol] [Bloquear] [Eliminar] │ │
│ └─────────────────────────────────────────────────────────────────────┘ │
│ │
│ ┌─────────────────────────────────────────────────────────────────────┐ │
│ │ 👤 @maria_dev maria@ejemplo.com │ │
│ │ María García Rol: Jugador (Silver) │ │
│ │ Estado: Activo Suscripción: Silver (activa) │ │
│ │ Registro: 2026-02-20 Edad: 22 años │ │
│ │ │ │
│ │ [Ver perfil] [Cambiar rol] [Bloquear] [Eliminar] │ │
│ └─────────────────────────────────────────────────────────────────────┘ │
│ │
│ ┌─────────────────────────────────────────────────────────────────────┐ │
│ │ 👤 @user123 user123@ejemplo.com │ │
│ │ Usuario Problemático Rol: Explorador (Free) │ │
│ │ Estado: Bloqueado Suscripción: Ninguna │ │
│ │ Registro: 2026-03-10 Edad: 17 años │ │
│ │ │ │
│ │ [Ver perfil] [Cambiar rol] [Desbloquear] [Eliminar] │ │
│ └─────────────────────────────────────────────────────────────────────┘ │
│ │
│ 📄 Página 1 de 250 [Anterior] [1] [2] [3] ... [250] [Siguiente] │
│ │
└─────────────────────────────────────────────────────────────────────────────┘


---

## 3. Buscar y Filtrar Usuarios

### 3.1. Búsqueda Rápida

Usa la barra de búsqueda para encontrar usuarios por:

| Campo | Ejemplo |
| :--- | :--- |
| **Email** | `juan@ejemplo.com` |
| **Username** | `@juanito123` |
| **Nombre completo** | `Juan Pérez` |
| **ID de usuario** | `12345` |

### 3.2. Filtros Avanzados

Haz clic en **"Filtros"** para acceder a:

| Filtro | Opciones |
| :--- | :--- |
| **Rol** | Explorador, Jugador, Creador, Mecenas, Administrador |
| **Estado** | Activo, Inactivo, Bloqueado, Suspendido |
| **Suscripción** | Free, Silver, Gold, Legend, Ninguna |
| **Edad** | +3, +7, +12, +16, +18, Verificado, No verificado |
| **Fecha de registro** | Hoy, Última semana, Último mes, Personalizado |
| **Último acceso** | Hoy, Última semana, Último mes, Nunca |
| **País** | Venezuela, Colombia, México, etc. |

### 3.3. Ordenar Resultados

Puedes ordenar por:

- **Nombre** (A-Z, Z-A)
- **Fecha de registro** (más reciente, más antiguo)
- **Último acceso** (más reciente, más antiguo)
- **Rol** (mayor a menor nivel)

### 3.4. Exportar Resultados

1. Aplica los filtros deseados.
2. Haz clic en **"Exportar CSV"**.
3. Selecciona las columnas a incluir.
4. Descarga el archivo.

---

## 4. Ver Perfil de Usuario

### 4.1. Acceder al Perfil

1. Busca el usuario.
2. Haz clic en **"Ver perfil"**.

### 4.2. Información Disponible

#### Datos Personales

| Campo | Descripción |
| :--- | :--- |
| **ID de usuario** | Identificador único |
| **Username** | Nombre de usuario |
| **Email** | Correo electrónico |
| **Nombre completo** | Nombre real |
| **Fecha de nacimiento** | Fecha de nacimiento |
| **Edad** | Edad calculada |
| **País** | País de residencia |
| **Avatar** | Foto de perfil |
| **Biografía** | Descripción personal |
| **Sitio web** | Página personal |
| **Redes sociales** | Twitter, Instagram, etc. |

#### Estado de la Cuenta

| Campo | Descripción |
| :--- | :--- |
| **Estado** | Activo, Inactivo, Bloqueado, Suspendido |
| **Email verificado** | Sí/No |
| **Edad verificada** | Sí/No (para +18) |
| **2FA activado** | Sí/No |
| **Fecha de registro** | Cuándo se registró |
| **Último acceso** | Última vez que inició sesión |

#### Roles y Permisos

| Campo | Descripción |
| :--- | :--- |
| **Rol actual** | Explorador, Jugador, Creador, Mecenas, Administrador |
| **Roles adicionales** | Roles secundarios (si aplica) |
| **Permisos** | Lista de permisos efectivos |

#### Suscripción

| Campo | Descripción |
| :--- | :--- |
| **Plan actual** | Free, Silver, Gold, Legend |
| **Estado** | Activa, Cancelada, Vencida |
| **Fecha de inicio** | Cuándo empezó |
| **Fecha de fin** | Cuándo termina |
| **Método de pago** | Stripe, PayPal, etc. |
| **Historial de pagos** | Lista de transacciones |

#### Actividad

| Campo | Descripción |
| :--- | :--- |
| **Juegos jugados** | Lista de juegos jugados |
| **Juegos favoritos** | Lista de favoritos |
| **Valoraciones** | Comentarios y puntuaciones |
| **Juegos creados** | Si es creador |
| **Reportes recibidos** | Reportes contra el usuario |
| **Sanciones** | Historial de sanciones |

#### Verificación de Edad

| Campo | Descripción |
| :--- | :--- |
| **Edad verificada** | Sí/No |
| **Método de verificación** | Fecha de nacimiento, documento, tarjeta |
| **Fecha de verificación** | Cuándo se verificó |
| **Acceso a +18** | Sí/No |

### 4.3. Acciones desde el Perfil

Desde el perfil del usuario, puedes:

- ✏️ **Editar información** (nombre, email, etc.)
- 🔄 **Cambiar rol**
- 💳 **Gestionar suscripción**
- 🔒 **Bloquear/Desbloquear**
- 🗑️ **Eliminar cuenta**
- 📧 **Enviar email**
- 📝 **Añadir nota interna**

---

## 5. Gestión de Roles y Permisos

### 5.1. Roles Disponibles

| Rol | Nivel | Descripción |
| :--- | :--- | :--- |
| **Explorador (Free)** | 1 | Usuario gratuito, acceso limitado |
| **Jugador (Silver)** | 2 | Suscriptor, acceso a todos los juegos |
| **Creador (Gold)** | 3 | Puede crear y subir juegos |
| **Mecenas (Legend)** | 4 | Soporte especial, acceso a beta |
| **Administrador** | 5 | Gestión completa de la plataforma |

### 5.2. Permisos por Rol

| Permiso | Explorador | Jugador | Creador | Mecenas | Admin |
| :--- | :---: | :---: | :---: | :---: | :---: |
| Jugar juegos gratuitos | ✅ | ✅ | ✅ | ✅ | ✅ |
| Jugar juegos premium | ❌ | ✅ | ✅ | ✅ | ✅ |
| Crear juegos | ❌ | ❌ | ✅ | ✅ | ✅ |
| Subir juegos | ❌ | ❌ | ✅ | ✅ | ✅ |
| Ver métricas de juegos | ❌ | ❌ | ✅ | ✅ | ✅ |
| Acceso a beta | ❌ | ❌ | ❌ | ✅ | ✅ |
| Votar en desarrollo | ❌ | ❌ | ❌ | ✅ | ✅ |
| Gestionar usuarios | ❌ | ❌ | ❌ | ❌ | ✅ |
| Gestionar juegos | ❌ | ❌ | ❌ | ❌ | ✅ |
| Ver métricas globales | ❌ | ❌ | ❌ | ❌ | ✅ |

### 5.3. Cambiar el Rol de un Usuario

**Pasos:**

1. Ve al perfil del usuario.
2. Haz clic en **"Cambiar Rol"**.
3. Selecciona el nuevo rol.
4. Escribe el motivo del cambio.
5. Confirma.

**Ejemplo de motivo:**

El usuario ha demostrado ser un creador activo y ha solicitado el cambio a Gold. Ha subido 3 juegos de calidad.


**Resultado:**
- El rol se actualiza inmediatamente.
- El usuario recibe una notificación.
- Se registra en los logs de auditoría.

### 5.4. Asignar Roles Adicionales

Un usuario puede tener múltiples roles (ej. Creador + Mecenas).

**Pasos:**

1. Ve al perfil del usuario.
2. Haz clic en **"Añadir Rol"**.
3. Selecciona el rol adicional.
4. Confirma.

**Nota:** Los roles se suman, no se reemplazan.

### 5.5. Revocar Roles

1. Ve al perfil del usuario.
2. En la sección de roles, haz clic en **"Revocar"** junto al rol.
3. Confirma.

**Resultado:**
- El rol se elimina.
- El usuario vuelve al rol anterior.
- Se registra en los logs.

### 5.6. Roles Especiales

| Rol | Descripción | Asignación |
| :--- | :--- | :--- |
| **Beta Tester** | Acceso a juegos en beta | Manual por admin |
| **Moderador** | Puede moderar contenido | Manual por admin |
| **Soporte** | Puede atender tickets | Manual por admin |

---

## 6. Gestión de Suscripciones

### 6.1. Ver Suscripción

1. Ve al perfil del usuario.
2. En la sección **"Suscripción"**, verás:
   - Plan actual.
   - Estado.
   - Fecha de inicio y fin.
   - Método de pago.
   - Historial de pagos.

### 6.2. Cancelar Suscripción

**Cuándo cancelar:**
- ⚠️ El usuario lo solicita.
- ⚠️ Violación de términos.
- ⚠️ Fraude o pago no autorizado.

**Pasos:**

1. Ve al perfil del usuario.
2. Haz clic en **"Gestionar Suscripción"**.
3. Selecciona **"Cancelar Suscripción"**.
4. Escribe el motivo.
5. Confirma.

**Resultado:**
- La suscripción se cancela.
- El usuario mantiene acceso hasta el final del período pagado.
- Se registra en los logs.

### 6.3. Reembolsar Pago

**Cuándo reembolsar:**
- ⚠️ Solicitud dentro de los 7 días.
- ⚠️ Problema técnico grave.
- ⚠️ Error de cobro.

**Pasos:**

1. Ve al perfil del usuario.
2. En **"Historial de pagos"**, busca la transacción.
3. Haz clic en **"Reembolsar"**.
4. Escribe el motivo.
5. Confirma.

**Resultado:**
- El reembolso se procesa vía Stripe.
- El usuario recibe el dinero en 5-10 días hábiles.
- Se registra en los logs.

### 6.4. Cambiar Plan

**Cuándo cambiar:**
- El usuario solicita upgrade/downgrade.
- Promoción especial.

**Pasos:**

1. Ve al perfil del usuario.
2. Haz clic en **"Gestionar Suscripción"**.
3. Selecciona **"Cambiar Plan"**.
4. Elige el nuevo plan.
5. Confirma.

**Resultado:**
- El plan se actualiza.
- Se prorratea el pago.
- El usuario recibe una notificación.

### 6.5. Historial de Pagos

| Fecha | Monto | Plan | Estado | Método |
| :--- | :--- | :--- | :--- | :--- |
| 2026-09-01 | $15.00 | Gold | Pagado | Stripe |
| 2026-08-01 | $15.00 | Gold | Pagado | Stripe |
| 2026-07-01 | $15.00 | Gold | Pagado | Stripe |

---

## 7. Bloqueo y Suspensión de Usuarios

### 7.1. Diferencia entre Bloqueo y Suspensión

| Acción | Duración | Efecto |
| :--- | :--- | :--- |
| **Suspensión** | Temporal (7-30 días) | El usuario no puede iniciar sesión |
| **Bloqueo** | Indefinido | El usuario no puede iniciar sesión hasta que se desbloquee |

### 7.2. Cuándo Suspender/Bloquear

- 🚫 **Violación del Código de Conducta** (acoso, discriminación).
- 🚫 **Spam** o publicidad no autorizada.
- 🚫 **Plagio** comprobado.
- 🚫 **Evasión del bloqueo de edad**.
- 🚫 **Fraude** o actividad ilegal.
- 🚫 **Múltiples reportes** válidos.

### 7.3. Suspender un Usuario

**Pasos:**

1. Ve al perfil del usuario.
2. Haz clic en **"Suspender"**.
3. Selecciona la duración:
   - 7 días
   - 15 días
   - 30 días
4. Escribe el motivo.
5. Confirma.

**Resultado:**
- El usuario no puede iniciar sesión.
- Recibe un email con el motivo y la duración.
- Puede apelar respondiendo al email.

### 7.4. Bloquear un Usuario

**Pasos:**

1. Ve al perfil del usuario.
2. Haz clic en **"Bloquear"**.
3. Escribe el motivo.
4. Confirma.

**Resultado:**
- El usuario no puede iniciar sesión.
- Recibe un email con el motivo.
- Puede apelar contactando a soporte.

### 7.5. Desbloquear/Reactivar un Usuario

**Pasos:**

1. Ve al perfil del usuario bloqueado.
2. Haz clic en **"Desbloquear"**.
3. Escribe el motivo (ej. "Apelación aceptada").
4. Confirma.

**Resultado:**
- El usuario puede volver a iniciar sesión.
- Recibe un email de notificación.

### 7.6. Escalado de Sanciones

| Nivel | Infracción | Sanción |
| :--- | :--- | :--- |
| **1** | Leve (spam, lenguaje soez) | Advertencia |
| **2** | Moderada (insultos, acoso leve) | Suspensión 7 días |
| **3** | Grave (acoso, discriminación) | Suspensión 30 días |
| **4** | Muy grave (violencia, contenido ilegal) | Bloqueo permanente |

---

## 8. Eliminación de Usuarios

### 8.1. Cuándo Eliminar una Cuenta

⚠️ **ADVERTENCIA: Esta acción es irreversible.**

- 🗑️ **Solicitud del usuario** (GDPR - derecho al olvido).
- 🗑️ **Cuenta inactiva** por más de 2 años (previa notificación).
- 🗑️ **Fraude comprobado**.
- 🗑️ **Violación grave** de términos.

### 8.2. Proceso de Eliminación

**Pasos:**

1. Ve al perfil del usuario.
2. Haz clic en **"Eliminar Cuenta"**.
3. Escribe el motivo.
4. **Confirma escribiendo el username del usuario**.
5. Confirma la eliminación.

**Resultado:**
- La cuenta se marca como eliminada.
- Los datos personales se anonimizan.
- Los datos financieros se conservan por obligación legal.
- Se registra en los logs de auditoría.

### 8.3. Eliminación por Solicitud del Usuario (GDPR)

Si un usuario solicita la eliminación de su cuenta:

1. Verifica la identidad del usuario.
2. Confirma la solicitud por email.
3. Procede con la eliminación.
4. Envía confirmación al usuario.

**Plazo:** 30 días máximo (según GDPR).

### 8.4. Datos que se Conservan

| Dato | ¿Se conserva? | Razón |
| :--- | :--- | :--- |
| **Email** | ❌ No | Se anonimiza |
| **Nombre** | ❌ No | Se anonimiza |
| **Contraseña** | ❌ No | Se elimina |
| **Historial de pagos** | ✅ Sí | Obligación fiscal |
| **Juegos creados** | ✅ Sí | Propiedad intelectual |
| **Logs de actividad** | ✅ Sí | Auditoría |
| **Reportes** | ✅ Sí | Seguridad |

### 8.5. Anonimización

En lugar de eliminar completamente, se anonimizan los datos:

Antes:
username: @juanito123
email: juan@ejemplo.com
nombre: Juan Pérez

Después:
username: @deleted_user_12345
email: deleted_12345@anonimo.com
nombre: Usuario Eliminado


---

## 9. Verificación de Edad y Contenido +18

### 9.1. Verificar Edad de un Usuario

**Cuándo verificar:**
- El usuario solicita acceso a contenido +18.
- Hay sospecha de edad falsa.
- Reporte de usuario menor accediendo a +18.

**Pasos:**

1. Ve al perfil del usuario.
2. En la sección **"Verificación de Edad"**, haz clic en **"Verificar"**.
3. Selecciona el método:
   - **Documento de identidad**: Sube una foto del documento.
   - **Tarjeta de crédito**: Verificación vía Stripe.
4. Confirma la verificación.

**Resultado:**
- La edad se marca como verificada.
- El usuario puede acceder a contenido +18.
- Se registra en los logs.

### 9.2. Rechazar Verificación

Si el documento no es válido o la edad no coincide:

1. Haz clic en **"Rechazar Verificación"**.
2. Escribe el motivo.
3. Confirma.

**Resultado:**
- El usuario recibe una notificación.
- No puede acceder a contenido +18.

### 9.3. Detectar Evasión de Edad

**Señales de alerta:**
- 🚨 El usuario intenta acceder a +18 repetidamente.
- 🚨 La fecha de nacimiento cambia frecuentemente.
- 🚨 Múltiples cuentas con la misma IP.
- 🚨 Reportes de otros usuarios.

**Acciones:**
1. Suspender la cuenta temporalmente.
2. Investigar el caso.
3. Si se confirma evasión, bloquear permanentemente.

### 9.4. Gestión de Contenido +18

- ✅ **Verificar** que los juegos +18 estén correctamente clasificados.
- ✅ **Monitorear** intentos de acceso de usuarios no verificados.
- ✅ **Alertar** si hay un aumento de intentos de evasión.
- ✅ **Sancionar** a los usuarios que evadan el bloqueo.

---

## 10. Gestión de Reportes de Usuarios

### 10.1. Ver Reportes

1. Ve a **Admin → Reportes**.
2. Filtra por:
   - **Tipo**: Juego, comentario, usuario.
   - **Estado**: Pendiente, Revisado, Resuelto, Rechazado.
   - **Fecha**: Hoy, última semana, último mes.

### 10.2. Resolver un Reporte

1. Haz clic en el reporte.
2. Revisa la evidencia.
3. Toma una acción:
   - **Advertir**: Envía una advertencia.
   - **Suspender**: Suspende temporalmente.
   - **Bloquear**: Bloquea permanentemente.
   - **Rechazar**: El reporte no es válido.
4. Documenta la decisión.

### 10.3. Historial de Reportes

- Ve al perfil del usuario.
- En la sección **"Reportes"**, verás:
  - Reportes recibidos.
  - Reportes realizados.
  - Sanciones aplicadas.

---

## 11. Logs de Actividad y Auditoría

### 11.1. Acceder a Logs

1. Ve a **Admin → Logs**.
2. Filtra por:
   - **Usuario**: Buscar por username.
   - **Acción**: Login, cambio de rol, bloqueo, etc.
   - **Fecha**: Hoy, última semana, último mes.

### 11.2. Acciones Registradas

| Acción | Descripción |
| :--- | :--- |
| `login` | Inicio de sesión |
| `logout` | Cierre de sesión |
| `register` | Registro |
| `change_role` | Cambio de rol |
| `suspend_user` | Suspensión |
| `block_user` | Bloqueo |
| `delete_user` | Eliminación |
| `verify_age` | Verificación de edad |
| `approve_game` | Aprobación de juego |
| `reject_game` | Rechazo de juego |

### 11.3. Exportar Logs

1. Aplica los filtros deseados.
2. Haz clic en **"Exportar CSV"**.
3. Descarga el archivo.

### 11.4. Auditoría de Acciones

Todas las acciones de administradores se registran:

| Campo | Descripción |
| :--- | :--- |
| **Admin** | Quién realizó la acción |
| **Acción** | Qué se hizo |
| **Usuario afectado** | A quién afectó |
| **Fecha** | Cuándo |
| **IP** | Desde dónde |
| **Detalles** | Información adicional |

---

## 12. Comunicación con Usuarios

### 12.1. Enviar Email

**Pasos:**

1. Ve al perfil del usuario.
2. Haz clic en **"Enviar Email"**.
3. Escribe el asunto y el mensaje.
4. Confirma.

**Plantillas predefinidas:**

| Plantilla | Uso |
| :--- | :--- |
| **Bienvenida** | Nuevo usuario |
| **Advertencia** | Primera infracción |
| **Suspensión** | Suspensión temporal |
| **Bloqueo** | Bloqueo permanente |
| **Verificación de edad** | Solicitud de documento |
| **Reembolso** | Confirmación de reembolso |

### 12.2. Notas Internas

Puedes añadir notas internas al perfil del usuario:

1. Ve al perfil.
2. Haz clic en **"Añadir Nota"**.
3. Escribe la nota.
4. Guarda.

**Ejemplo:**

2026-09-01: El usuario solicitó verificación de edad. Documento recibido y aprobado.
2026-09-05: Reporte de spam resuelto con advertencia.


### 12.3. Historial de Comunicación

- Ve al perfil del usuario.
- En la sección **"Comunicación"**, verás:
  - Emails enviados.
  - Notas internas.
  - Respuestas del usuario.

---

## 13. Buenas Prácticas

### 13.1. Al Gestionar Usuarios

- ⏱️ **Sé rápido**: Responde a solicitudes en menos de 48 horas.
- 🔍 **Sé minucioso**: Verifica la identidad antes de acciones críticas.
- 📝 **Documenta**: Registra todas las acciones.
- 💬 **Comunica**: Explica claramente las decisiones.
- ⚖️ **Sé justo**: Aplica las mismas reglas a todos.

### 13.2. Al Sancionar

- 📋 **Sé específico**: Explica exactamente qué violó las normas.
- 🛠️ **Sé constructivo**: Sugiere cómo corregir el comportamiento.
- 🤝 **Sé empático**: Recuerda que hay una persona detrás.
- 📧 **Sé claro**: Usa un lenguaje sencillo y directo.
- 🔄 **Permite apelaciones**: Da la oportunidad de defenderse.

### 13.3. Seguridad

- 🔐 **Usa 2FA**: Activa la autenticación de dos factores.
- 🚫 **No compartas credenciales**: Cada admin debe tener su cuenta.
- 📝 **Audita**: Revisa los logs de actividad regularmente.
- 🚨 **Reporta**: Informa de actividad sospechosa.
- 🔒 **Datos sensibles**: No compartas información personal de usuarios.

### 13.4. Cumplimiento Legal

- 📜 **GDPR**: Responde a solicitudes de acceso/eliminación en 30 días.
- 📜 **COPPA**: Verifica la edad de usuarios menores de 13 años.
- 📜 **Términos y Condiciones**: Asegura que los usuarios los acepten.
- 📜 **Política de Privacidad**: Informa cómo se usan los datos.

---

## 14. Preguntas Frecuentes

### ¿Cómo encuentro a un usuario específico?

**Respuesta:** Usa la barra de búsqueda en **Admin → Usuarios**. Puedes buscar por email, username, nombre o ID.

### ¿Puedo cambiar el email de un usuario?

**Respuesta:** **Sí.** Ve al perfil del usuario, haz clic en **"Editar"** y cambia el email. El usuario recibirá una notificación.

### ¿Qué pasa cuando bloqueo a un usuario?

**Respuesta:** El usuario no puede iniciar sesión. Recibe un email con el motivo. Puede apelar contactando a soporte.

### ¿Puedo eliminar mi propia cuenta de administrador?

**Respuesta:** **No.** Los administradores no pueden eliminar su propia cuenta. Debe hacerlo otro administrador.

### ¿Cómo sé si un usuario está evadiendo el bloqueo de edad?

**Respuesta:** Monitorea los intentos de acceso a +18 por usuarios no verificados. Si hay múltiples intentos, investiga y sanciona.

### ¿Qué hago si un usuario solicita eliminación de cuenta (GDPR)?

**Respuesta:** 
1. Verifica la identidad.
2. Confirma la solicitud por email.
3. Procede con la eliminación.
4. Envía confirmación.
5. Plazo máximo: 30 días.

### ¿Puedo recuperar una cuenta eliminada?

**Respuesta:** **No.** La eliminación es permanente. Los datos se anonimizan y no se pueden recuperar.

### ¿Cómo manejo un usuario que ha sido reportado múltiples veces?

**Respuesta:** 
1. Revisa los reportes.
2. Si son válidos, suspende o bloquea.
3. Documenta la decisión.
4. Notifica al usuario.

### ¿Qué hago si un usuario apela una sanción?

**Respuesta:** 
1. Revisa el caso nuevamente.
2. Consulta con otro administrador.
3. Toma una decisión final.
4. Comunica la decisión al usuario.

### ¿Cómo reporto un problema técnico con el panel de usuarios?

**Respuesta:** Contacta al equipo de desarrollo:
- Email: parraalavaro418@gmail.com
- Discord: Canal `#soporte-admin`

---

## 15. Contacto

### Soporte para Administradores

| Canal | Información |
| :--- | :--- |
| **Email** | parraalavaro418@gmail.com |
| **Discord** | Canal `#soporte-admin` |
| **GitHub Issues** | [Reportar problema](https://github.com/Alepro418/epic-things-platform/issues) |

### Recursos Adicionales

- 📖 [Manual de Gestión de Juegos](./gestion-juegos.md)
- 📖 [Manual de Métricas](./metricas.md)
- 📖 [Manual de Moderación](./moderacion.md)
- 📖 [Código de Conducta](../../guides/code-of-conduct.md)
- 📖 [API de Usuarios](../../architecture/api/auth.yaml)
- 📖 [Modelo de Datos](../../architecture/diagrams/entidad-relacion.puml)

---

## 📝 Historial de Cambios

| Fecha | Versión | Cambio |
| :--- | :--- | :--- |
| 2026-09-01 | 1.0 | Creación inicial |

---

**Hecho con ❤️ desde Puerto Cabello, Venezuela**

*"Gestionar personas es gestionar confianza."*
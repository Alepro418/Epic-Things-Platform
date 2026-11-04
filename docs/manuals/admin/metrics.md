# 📊 Métricas (Admin)

> **Audiencia:** Administradores de Epic Things Platform  
> **Última actualización:** 2026-09-01  
> **Versión:** 1.0

---

## 📋 Tabla de Contenidos

1. [Introducción](#1-introducción)
2. [Acceder al Dashboard](#2-acceder-al-dashboard)
3. [Métricas de Usuarios](#3-métricas-de-usuarios)
4. [Métricas de Juegos](#4-métricas-de-juegos)
5. [Métricas de Ingresos](#5-métricas-de-ingresos)
6. [Métricas de Engagement](#6-métricas-de-engagement)
7. [Métricas de Tráfico](#7-métricas-de-tráfico)
8. [Métricas de Clasificación por Edad](#8-métricas-de-clasificación-por-edad)
9. [Visualizar y Exportar Métricas](#9-visualizar-y-exportar-métricas)
10. [Alertas Automáticas](#10-alertas-automáticas)
11. [Reportes Automáticos](#11-reportes-automáticos)
12. [Herramientas Recomendadas](#12-herramientas-recomendadas)
13. [Interpretación de Métricas](#13-interpretación-de-métricas)
14. [Buenas Prácticas](#14-buenas-prácticas)
15. [Preguntas Frecuentes](#15-preguntas-frecuentes)
16. [Contacto](#16-contacto)

---

## 1. Introducción

Esta guía está dirigida a los **administradores** de Epic Things Platform y describe cómo **acceder, interpretar y utilizar** las métricas de la plataforma para tomar decisiones informadas.

### ¿Por Qué son Importantes las Métricas?

Las métricas son el **pulso de la plataforma**. Permiten:

- 📈 **Medir el crecimiento** de usuarios y juegos.
- 💰 **Evaluar la salud financiera** del negocio.
- 🎯 **Identificar problemas** antes de que sean críticos.
- 🚀 **Tomar decisiones basadas en datos**, no en suposiciones.
- 📊 **Reportar resultados** a inversionistas o al equipo.

### Responsabilidades del Administrador

| Responsabilidad | Descripción |
| :--- | :--- |
| **Monitorear** | Revisar métricas diaria/semanalmente |
| **Interpretar** | Entender qué significan los números |
| **Alertar** | Notificar problemas o tendencias preocupantes |
| **Documentar** | Registrar observaciones y decisiones |
| **Actuar** | Tomar medidas basadas en los datos |

---

## 2. Acceder al Dashboard

### Requisitos

- Cuenta con rol de **Administrador** (nivel 5).
- Sesión activa en la plataforma.
- Permisos de visualización de métricas.

### Pasos para Acceder

1. **Inicia sesión** con tu cuenta de administrador.
2. En el menú principal, haz clic en **"Admin"**.
3. Selecciona **"Métricas"**.

**URL directa:**

https://epic-things.com/admin/metrics


### Interfaz del Dashboard

┌─────────────────────────────────────────────────────────────────────────────┐
│ 📊 Dashboard de Métricas [Filtros ▼] │
├─────────────────────────────────────────────────────────────────────────────┤
│ │
│ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ │
│ │ 👥 Usuarios │ │ 🎮 Juegos │ │ 💰 Ingresos │ │ 📈 MRR │ │
│ │ 5,234 │ │ 127 │ │ $12,450 │ │ $2,500 │ │
│ │ +12% ↑ │ │ +8% ↑ │ │ +15% ↑ │ │ +10% ↑ │ │
│ └─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘ │
│ │
│ ┌─────────────────────────────────────────────────────────────────────┐ │
│ │ 📈 Crecimiento de Usuarios (Últimos 30 días) │ │
│ │ │ │
│ │ 6,000 ┤ ╭─── │ │
│ │ │ ╭─────╯ │ │
│ │ 5,000 ┤ ╭─────╯ │ │
│ │ │ ╭─────╯ │ │
│ │ 4,000 ┤ ╭─────╯ │ │
│ │ │ ╭─────╯ │ │
│ │ 3,000 ┤ ╭─────╯ │ │
│ │ │ ╭─────╯ │ │
│ │ 2,000 ┤ ╭─────╯ │ │
│ │ │╭───╯ │ │
│ │ 1,000 ┤╯ │ │
│ │ └────────────────────────────────────────────────────── │ │
│ │ Sep 1 Sep 8 Sep 15 Sep 22 Sep 29 │ │
│ └─────────────────────────────────────────────────────────────────────┘ │
│ │
│ ┌─────────────────────────────────────────────────────────────────────┐ │
│ │ 🎮 Juegos Más Populares │ │
│ │ │ │
│ │ 1. Aventura Épica ████████████████████ 15,234 visitas │ │
│ │ 2. Puzzle Master ████████████████ 12,456 visitas │ │
│ │ 3. Space Shooter ██████████████ 10,789 visitas │ │
│ │ 4. Racing Fury ████████████ 8,234 visitas │ │
│ │ 5. Mystery Island ██████████ 6,789 visitas │ │
│ └─────────────────────────────────────────────────────────────────────┘ │
│ │
└─────────────────────────────────────────────────────────────────────────────┘


### Filtros Disponibles

| Filtro | Opciones |
| :--- | :--- |
| **Período** | Hoy, Últimos 7 días, Últimos 30 días, Último año, Personalizado |
| **Comparación** | vs. período anterior, vs. mismo período año pasado |
| **Segmento** | Todos, Free, Silver, Gold, Legend |
| **Categoría** | Todas, Acción, Aventura, Puzzle, etc. |

---

## 3. Métricas de Usuarios

### 3.1. Métricas Principales

| Métrica | Descripción | Fórmula |
| :--- | :--- | :--- |
| **Total de usuarios registrados** | Todos los usuarios que se han registrado | `COUNT(*) FROM usuarios` |
| **Usuarios activos (MAU)** | Usuarios que han iniciado sesión en los últimos 30 días | `COUNT(DISTINCT id_usuario) FROM logs_actividad WHERE fecha > NOW() - 30 days` |
| **Usuarios activos diarios (DAU)** | Usuarios que han iniciado sesión en las últimas 24 horas | `COUNT(DISTINCT id_usuario) FROM logs_actividad WHERE fecha > NOW() - 1 day` |
| **Nuevos registros** | Usuarios que se registraron en el período | `COUNT(*) FROM usuarios WHERE fecha_registro > [fecha_inicio]` |
| **Tasa de conversión** | % de usuarios Free que se suscriben | `(suscriptores / usuarios_free) * 100` |
| **Churn rate** | % de usuarios que cancelan suscripción | `(cancelaciones / suscriptores_activos) * 100` |
| **Retención D1** | % de usuarios que vuelven al día siguiente | `(usuarios_que_vuelven_dia_1 / nuevos_usuarios) * 100` |
| **Retención D7** | % de usuarios que vuelven a los 7 días | `(usuarios_que_vuelven_dia_7 / nuevos_usuarios) * 100` |
| **Retención D30** | % de usuarios que vuelven a los 30 días | `(usuarios_que_vuelven_dia_30 / nuevos_usuarios) * 100` |

### 3.2. Distribución de Usuarios por Rol

| Rol | Cantidad | Porcentaje |
| :--- | :--- | :--- |
| **Explorador (Free)** | 2,500 | 47.8% |
| **Jugador (Silver)** | 1,250 | 23.9% |
| **Creador (Gold)** | 750 | 14.3% |
| **Mecenas (Legend)** | 250 | 4.8% |
| **Administrador** | 10 | 0.2% |
| **Total** | **5,234** | **100%** |

### 3.3. Distribución Geográfica

| País | Usuarios | Porcentaje |
| :--- | :--- | :--- |
| **Venezuela** | 2,100 | 40.1% |
| **Colombia** | 1,050 | 20.1% |
| **México** | 780 | 14.9% |
| **Argentina** | 520 | 9.9% |
| **España** | 310 | 5.9% |
| **Otros** | 474 | 9.1% |

### 3.4. Distribución por Edad

| Rango de Edad | Usuarios | Porcentaje |
| :--- | :--- | :--- |
| **Menores de 13** | 250 | 4.8% |
| **13-17** | 1,200 | 22.9% |
| **18-24** | 2,100 | 40.1% |
| **25-34** | 1,200 | 22.9% |
| **35-44** | 350 | 6.7% |
| **45+** | 134 | 2.6% |

> ⚠️ **Nota:** Los usuarios menores de 13 años requieren verificación parental (COPPA/GDPR).

### 3.5. Nuevos Registros (Últimos 30 Días)

| Fecha | Registros | Tendencia |
| :--- | :--- | :--- |
| **Semana 1** | 120 | ↑ 10% |
| **Semana 2** | 150 | ↑ 25% |
| **Semana 3** | 180 | ↑ 20% |
| **Semana 4** | 200 | ↑ 11% |
| **Total** | **650** | ↑ 16% |

---

## 4. Métricas de Juegos

### 4.1. Métricas Principales

| Métrica | Descripción | Fórmula |
| :--- | :--- | :--- |
| **Total de juegos publicados** | Juegos visibles en el catálogo | `COUNT(*) FROM juegos WHERE estado = 'publicado'` |
| **Juegos pendientes** | Juegos esperando revisión | `COUNT(*) FROM juegos WHERE estado = 'pendiente'` |
| **Juegos más jugados** | Top 10 por visitas | `SELECT * FROM juegos ORDER BY visitas DESC LIMIT 10` |
| **Juegos mejor valorados** | Top 10 por puntuación media | `SELECT * FROM juegos WHERE total_valoraciones > 5 ORDER BY puntuacion_media DESC LIMIT 10` |
| **Juegos con más reportes** | Juegos con reportes pendientes | `SELECT * FROM juegos WHERE reportes_pendientes > 0 ORDER BY reportes_pendientes DESC` |
| **Tiempo promedio de juego** | Duración media de sesión | `AVG(tiempo_jugado_total / sesiones)` |
| **Tasa de finalización** | % de usuarios que terminan el juego | `(usuarios_que_terminan / usuarios_totales) * 100` |

### 4.2. Distribución de Juegos por Categoría

| Categoría | Cantidad | Porcentaje |
| :--- | :--- | :--- |
| **Acción** | 35 | 27.6% |
| **Aventura** | 28 | 22.0% |
| **Puzzle** | 22 | 17.3% |
| **Estrategia** | 15 | 11.8% |
| **Deportes** | 12 | 9.4% |
| **Arcade** | 10 | 7.9% |
| **Educativo** | 5 | 3.9% |
| **Total** | **127** | **100%** |

### 4.3. Distribución por Tipo

| Tipo | Cantidad | Porcentaje |
| :--- | :--- | :--- |
| **HTML5** | 85 | 66.9% |
| **Unity** | 30 | 23.6% |
| **WebGL** | 12 | 9.4% |

### 4.4. Juegos Más Populares (Top 5)

| # | Juego | Creador | Visitas | Valoración | Clasificación |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Aventura Épica | @juanito123 | 15,234 | 4.9/5 | +7 |
| 2 | Puzzle Master | @maria_dev | 12,456 | 4.7/5 | +3 |
| 3 | Space Shooter | @space_game | 10,789 | 4.5/5 | +12 |
| 4 | Racing Fury | @speed_dev | 8,234 | 4.3/5 | +7 |
| 5 | Mystery Island | @mystery_maker | 6,789 | 4.6/5 | +12 |

### 4.5. Juegos con Más Reportes

⚠️ **Requieren atención inmediata:**

| Juego | Reportes | Motivo Principal | Clasificación | Estado |
| :--- | :--- | :--- | :--- | :--- |
| Juego X | 15 | Contenido inapropiado | +18 | Pendiente |
| Juego Y | 8 | Errores técnicos | +7 | Pendiente |
| Juego Z | 5 | Spam | +3 | Pendiente |

### 4.6. Tasa de Aprobación de Juegos

| Período | Enviados | Aprobados | Rechazados | Tasa de Aprobación |
| :--- | :--- | :--- | :--- | :--- |
| **Último mes** | 45 | 38 | 7 | 84.4% |
| **Últimos 3 meses** | 120 | 100 | 20 | 83.3% |
| **Último año** | 500 | 420 | 80 | 84.0% |

### 4.7. Tiempo Promedio de Revisión

| Período | Tiempo Promedio |
| :--- | :--- |
| **Último mes** | 36 horas |
| **Últimos 3 meses** | 42 horas |
| **Último año** | 48 horas |

> 🎯 **Objetivo:** Reducir a 24 horas.

---

## 5. Métricas de Ingresos

### 5.1. Métricas Principales

| Métrica | Descripción | Fórmula |
| :--- | :--- | :--- |
| **MRR (Monthly Recurring Revenue)** | Ingresos recurrentes mensuales | `SUM(precio_mensual) FROM suscripciones WHERE estado = 'activa'` |
| **ARR (Annual Recurring Revenue)** | Ingresos recurrentes anuales | `MRR * 12` |
| **ARPU (Average Revenue per User)** | Ingreso promedio por usuario | `MRR / usuarios_activos` |
| **LTV (Lifetime Value)** | Valor total de un usuario | `ARPU * tiempo_promedio_suscripcion` |
| **CAC (Customer Acquisition Cost)** | Costo de adquirir un usuario | `gastos_marketing / nuevos_usuarios` |
| **Payback Period** | Tiempo para recuperar CAC | `CAC / ARPU` |
| **Tasa de conversión de pagos** | % de pagos exitosos | `(pagos_exitosos / intentos_pago) * 100` |

### 5.2. Ingresos por Plan

| Plan | Suscriptores | Precio | MRR | % del Total |
| :--- | :--- | :--- | :--- | :--- |
| **Silver** | 150 | $5 | $750 | 30% |
| **Gold** | 50 | $15 | $750 | 30% |
| **Legend** | 8 | $30 | $240 | 10% |
| **Comisiones** | - | - | $750 | 30% |
| **Total** | **208** | - | **$2,500** | **100%** |

### 5.3. Evolución de MRR (Últimos 12 Meses)

| Mes | MRR | Crecimiento |
| :--- | :--- | :--- |
| **Ene 2026** | $50 | - |
| **Feb 2026** | $150 | +200% |
| **Mar 2026** | $300 | +100% |
| **Abr 2026** | $500 | +67% |
| **May 2026** | $655 | +31% |
| **Jun 2026** | $810 | +24% |
| **Jul 2026** | $965 | +19% |
| **Ago 2026** | $1,120 | +16% |
| **Sep 2026** | $1,275 | +14% |
| **Oct 2026** | $1,430 | +12% |
| **Nov 2026** | $1,585 | +11% |
| **Dic 2026** | $1,740 | +10% |

> 📈 **Nota:** El crecimiento se desacelera a medida que la base de usuarios crece, pero el MRR sigue aumentando.

### 5.4. Ingresos por Juego (Regalías)

| Juego | Ingresos Totales | Regalía Creador (70%) | Comisión Plataforma (30%) |
| :--- | :--- | :--- | :--- |
| Aventura Épica | $1,500 | $1,050 | $450 |
| Puzzle Master | $1,200 | $840 | $360 |
| Space Shooter | $900 | $630 | $270 |
| Racing Fury | $600 | $420 | $180 |
| Mystery Island | $450 | $315 | $135 |

### 5.5. Transacciones Fallidas

| Motivo | Cantidad | % del Total |
| :--- | :--- | :--- |
| **Fondos insuficientes** | 12 | 40% |
| **Tarjeta expirada** | 8 | 26.7% |
| **Tarjeta rechazada** | 6 | 20% |
| **Error de Stripe** | 3 | 10% |
| **Otros** | 1 | 3.3% |
| **Total** | **30** | **100%** |

> 🎯 **Objetivo:** Reducir transacciones fallidas a <5%.

### 5.6. Reembolsos

| Período | Reembolsos | Monto | % de Ingresos |
| :--- | :--- | :--- | :--- |
| **Último mes** | 3 | $45 | 1.8% |
| **Últimos 3 meses** | 8 | $120 | 1.6% |
| **Último año** | 25 | $375 | 1.5% |

> ✅ **Nota:** Un % de reembolsos <3% es saludable.

---

## 6. Métricas de Engagement

### 6.1. Métricas Principales

| Métrica | Descripción | Fórmula |
| :--- | :--- | :--- |
| **Tiempo promedio de juego** | Duración media de una sesión | `AVG(tiempo_sesion)` |
| **Sesiones por usuario** | Número de sesiones por usuario | `COUNT(sesiones) / COUNT(DISTINCT id_usuario)` |
| **Tasa de rebote** | % de usuarios que abandonan sin jugar | `(usuarios_que_abandonan / usuarios_totales) * 100` |
| **Valoraciones por juego** | Promedio de valoraciones | `COUNT(valoraciones) / COUNT(juegos)` |
| **Favoritos por usuario** | Promedio de favoritos | `COUNT(favoritos) / COUNT(DISTINCT id_usuario)` |
| **Comentarios por juego** | Promedio de comentarios | `COUNT(comentarios) / COUNT(juegos)` |

### 6.2. Tiempo Promedio de Juego por Categoría

| Categoría | Tiempo Promedio |
| :--- | :--- |
| **Aventura** | 45 minutos |
| **Estrategia** | 30 minutos |
| **Puzzle** | 15 minutos |
| **Acción** | 10 minutos |
| **Arcade** | 5 minutos |

### 6.3. Retención de Usuarios

| Período | Retención |
| :--- | :--- |
| **D1 (Día 1)** | 45% |
| **D7 (Día 7)** | 25% |
| **D30 (Día 30)** | 15% |
| **D90 (Día 90)** | 8% |

> 🎯 **Objetivo:** Mejorar la retención D30 a 20%.

### 6.4. Sesiones por Usuario (Últimos 30 Días)

| Rango | Usuarios | Porcentaje |
| :--- | :--- | :--- |
| **0 sesiones** | 1,500 | 28.7% |
| **1-5 sesiones** | 2,000 | 38.2% |
| **6-10 sesiones** | 1,000 | 19.1% |
| **11-20 sesiones** | 500 | 9.6% |
| **21+ sesiones** | 234 | 4.5% |

### 6.5. Valoraciones por Juego (Top 5)

| Juego | Valoración Media | Total Valoraciones |
| :--- | :--- | :--- |
| Aventura Épica | 4.9/5 | 150 |
| Puzzle Master | 4.7/5 | 120 |
| Mystery Island | 4.6/5 | 80 |
| Space Shooter | 4.5/5 | 100 |
| Racing Fury | 4.3/5 | 60 |

### 6.6. Favoritos por Usuario

| Rango | Usuarios | Porcentaje |
| :--- | :--- | :--- |
| **0 favoritos** | 2,000 | 38.2% |
| **1-5 favoritos** | 2,500 | 47.8% |
| **6-10 favoritos** | 500 | 9.6% |
| **11+ favoritos** | 234 | 4.5% |

---

## 7. Métricas de Tráfico

### 7.1. Métricas Principales

| Métrica | Descripción | Fórmula |
| :--- | :--- | :--- |
| **Visitas únicas** | Usuarios únicos que visitan la web | `COUNT(DISTINCT ip)` |
| **Páginas vistas** | Total de páginas vistas | `COUNT(page_views)` |
| **Páginas por sesión** | Promedio de páginas por sesión | `page_views / sesiones` |
| **Duración de sesión** | Tiempo promedio en la web | `AVG(duracion_sesion)` |
| **Tasa de rebote** | % de sesiones con una sola página | `(sesiones_1_pagina / sesiones_totales) * 100` |
| **Fuentes de tráfico** | Origen del tráfico | `GROUP BY source` |

### 7.2. Fuentes de Tráfico

| Fuente | Visitas | Porcentaje |
| :--- | :--- | :--- |
| **Orgánico (SEO)** | 5,000 | 40% |
| **Directo** | 3,000 | 24% |
| **Redes sociales** | 2,500 | 20% |
| **Referidos** | 1,500 | 12% |
| **Email** | 500 | 4% |
| **Total** | **12,500** | **100%** |

### 7.3. Páginas Más Visitadas

| Página | Visitas | % del Total |
| :--- | :--- | :--- |
| **Página de inicio** | 5,000 | 40% |
| **Catálogo de juegos** | 3,000 | 24% |
| **Juego: Aventura Épica** | 1,500 | 12% |
| **Juego: Puzzle Master** | 1,200 | 9.6% |
| **Página de precios** | 800 | 6.4% |
| **Otras** | 1,000 | 8% |

### 7.4. Dispositivos

| Dispositivo | Visitas | Porcentaje |
| :--- | :--- | :--- |
| **Desktop** | 6,250 | 50% |
| **Mobile** | 5,000 | 40% |
| **Tablet** | 1,250 | 10% |

### 7.5. Navegadores

| Navegador | Visitas | Porcentaje |
| :--- | :--- | :--- |
| **Chrome** | 8,000 | 64% |
| **Firefox** | 2,000 | 16% |
| **Safari** | 1,500 | 12% |
| **Edge** | 750 | 6% |
| **Otros** | 250 | 2% |

---

## 8. Métricas de Clasificación por Edad

### 8.1. Distribución de Juegos por Clasificación

| Clasificación | Cantidad | Porcentaje |
| :--- | :--- | :--- |
| **+3** | 45 | 35.4% |
| **+7** | 40 | 31.5% |
| **+12** | 25 | 19.7% |
| **+16** | 12 | 9.4% |
| **+18** | 5 | 3.9% |
| **Total** | **127** | **100%** |

### 8.2. Jugadores por Clasificación

| Clasificación | Jugadores | Porcentaje |
| :--- | :--- | :--- |
| **+3** | 2,500 | 47.8% |
| **+7** | 1,500 | 28.7% |
| **+12** | 800 | 15.3% |
| **+16** | 300 | 5.7% |
| **+18** | 134 | 2.6% |

### 8.3. Bloqueos por Edad (Últimos 30 Días)

| Clasificación | Intentos Bloqueados | Usuarios Afectados |
| :--- | :--- | :--- |
| **+18** | 150 | 120 |
| **+16** | 80 | 65 |
| **+12** | 30 | 25 |
| **Total** | **260** | **210** |

### 8.4. Verificaciones de Edad

| Método | Cantidad | % del Total |
| :--- | :--- | :--- |
| **Fecha de nacimiento** | 5,000 | 95.5% |
| **Documento de identidad** | 200 | 3.8% |
| **Tarjeta de crédito** | 34 | 0.7% |
| **Total** | **5,234** | **100%** |

### 8.5. Alertas de Evasión

⚠️ **Usuarios que intentaron evadir el bloqueo de edad:**

| Usuario | Intentos | Acción Tomada |
| :--- | :--- | :--- |
| @user123 | 5 | Advertencia |
| @user456 | 3 | Advertencia |
| @user789 | 10 | Suspensión 7 días |

> 🚨 **Nota:** La evasión del bloqueo de edad es una violación grave y puede resultar en ban permanente.

---

## 9. Visualizar y Exportar Métricas

### 9.1. Visualizar Métricas

#### Dashboard Principal

El dashboard muestra:
- **KPIs principales** (usuarios, juegos, ingresos, MRR).
- **Gráficos de tendencia** (crecimiento, ingresos, engagement).
- **Tablas de top** (juegos populares, juegos con más reportes).
- **Distribuciones** (por categoría, tipo, clasificación).

#### Gráficos Interactivos

- **Hover** sobre los puntos para ver valores exactos.
- **Click** en la leyenda para ocultar/mostrar series.
- **Zoom** en áreas específicas del gráfico.
- **Filtros** por período y segmento.

### 9.2. Exportar Datos

1. Haz clic en **"Exportar"**.
2. Selecciona el formato:
   - **CSV**: Para Excel/Google Sheets.
   - **JSON**: Para integración con otras herramientas.
   - **PDF**: Para reportes ejecutivos.
3. Selecciona el período.
4. Selecciona las métricas a exportar.
5. Descarga el archivo.

**Ejemplo de CSV exportado:**

```csv
Fecha,Usuarios Registrados,Usuarios Activos,Juegos,MRR
2026-09-01,5000,1500,120,2500
2026-09-02,5050,1520,121,2550
2026-09-03,5100,1540,122,2600
```

## 9.3. Compartir Métricas

• Enlace público: Genera un enlace para compartir (solo lectura).

• Programar reportes: Envía reportes automáticos por email.

• Integrar con Slack/Discord: Notificaciones de métricas.

## 10.1. Configurar Alertas

1. Ve a Admin → Configuración → Alertas.

2. Selecciona las métricas a monitorear.

3. Define los umbrales.

4. Elige el canal de notificación.

5. Guarda los cambios. 

## 10.2. Alertas Recomendadas

| Alerta | Umbral | Canal |
| :--- | :--- | :--- |
| **Caída de ingresos** | 20% en una semana | Email + Discord |
| **Aumento de reportes** | 10 en un día | Email + Discord |
| **Juegos con errores** | Tasa de error >5% | Email |
| **Usuarios inactivos** | 30 días sin actividad | Email |
| **Transacciones fallidas** | 10% del total | Email + Discord |
| **Usuarios inactivos** | 30 días sin actividad | Email |
| **Nuevos juegos pendientes** | 20 en cola | Email |
| **Evación de edad** | 5 intentos por usuario | Email + Discord |

## 10.3. Historial de Alertas

• Ve a Admin → Alertas → Historial.

• Verás todas las alertas enviadas.

• Puedes filtrar por tipo, fecha o severidad.

## 11. Reportes Automáticos

## 11.1. Reportes Diarios
**Contenido:**

• Nuevos usuarios registrados.

• Nuevos juegos publicados.

• Ingresos del día.

• Alertas del día.

**Envío:** Todos los días a las 9:00 AM.

## 11.2. Reportes Semanales
**Contenido:**

• Resumen de la semana.

• Comparación con semana anterior.

• Top 5 juegos.

• Top 5 creadores.

• Alertas de la semana.

**Envío:** Todos los lunes a las 9:00 AM.

## 11.3. Reportes Mensuales
**Contenido:**

• Resumen del mes.

• Comparación con mes anterior.

• Análisis de tendencias.

• Recomendaciones.

• Proyecciones.

**Envío:** El primer día de cada mes a las 9:00 AM.

## 11.4. Configurar Reportes

1. Ve a Admin → Configuración → Reportes.

2. Selecciona los reportes a recibir.

3. Elige el formato (PDF, CSV, HTML).

4. Configura los destinatarios.

5. Guarda los cambios.

## 12 Herramientas recomendadas

## 12.1 Herramientas internas

| Herramienta | Uso | Integración |
| :--- | :--- | :--- |
| **Dashboard de Admin** | Métricas en tiempo real | Nativa |
| **API de Métricas** | Acceso programático | REST |
| **Logs de Auditoría** | Historial de acciones | PostgreSQL |

## 12.2 Herramientas Externas

| Herramienta | Uso | Costo |
| :--- | :--- | :--- |
| **Google Analytics** | Tráfico web, comportamiento | Gratis |
| **Mixpanel** | Análisis de eventos, cohortes | Gratis / $25/mes |
| **Stripe** | Dashboard Ingresos, pagos, suscripciones | Gratis |
| **Grafana** | Dashboards técnicos | Gratis / $49/mes |
| **Metabase** | Business intelligence | Gratis / $85/mes |
| **Hotjar** | Mapas de calor, grabaciones | Gratis / $39/mes |

## 12.3. Integraciones

• Google Analytics: Tracking de páginas y eventos.

• Stripe: Sincronización de ingresos.

• Discord: Notificaciones de alertas.

• Slack: Notificaciones de alertas.

## 13. Interpretación de Métricas

## 13.1. Tasa de Conversión Baja (<10%)

**Causa:**

• El plan gratuito es demasiado bueno.

• Los planes premium no ofrecen suficiente valor.

• El proceso de pago es complicado.

**Solución:**

• Añadir más valor a los planes premium.

• Simplificar el proceso de pago.

• Ofrecer pruebas gratuitas.

• Destacar los beneficios de los planes.

## 13.2. Churn Rate Alto (>10%)

**Causa posible:**

• Los usuarios no encuentran valor.

• Contenido nuevo insuficiente.

• Problemas técnicos.

• Competencia más atractiva.

**Solución:**

• Mejorar la retención con contenido nuevo.

• Encuestas de salida para entender motivos.

• Ofertas de retención (descuentos, upgrades).

• Mejorar la calidad del servicio.

## 13.3. Bajo Engagement

**Causa posible:**

• Los juegos no son atractivos.

• Falta de contenido nuevo.

• Problemas de rendimiento.

• Mala experiencia de usuario.

**Solución:**

• Promocionar juegos de calidad.

• Añadir más categorías.

• Optimizar el rendimiento.

• Mejorar la UI/UX.

## 13.4. Alta Tasa de Reembolsos (>5%)

**Causa posible:**

• Calidad del servicio por debajo de las expectativas.

• Problemas técnicos frecuentes.

• Proceso de cancelación complicado.

**Solución:**

• Mejorar la calidad del servicio.

• Resolver problemas técnicos rápidamente.

• Simplificar el proceso de cancelación.

• Ofrecer reembolsos proactivos.

## 13.5. Baja Retención (D30 <10%)

**Causa posible:**

• Los usuarios no ven valor a largo plazo.

• Falta de novedades.

• Comunidad inactiva.

• Competencia más atractiva.

**Solución:**

• Añadir contenido nuevo regularmente.

• Fomentar la comunidad.

• Programa de recompensas por lealtad.

• Notificaciones personalizadas.

## 13.6. Aumento de Reportes

**Causa posible:**

• Aumento de usuarios (más reportes en términos absolutos).

• Contenido inapropiado.

• Spam o bots.

• Problemas técnicos.

**Solución:**

• Revisar los reportes inmediatamente.

• Reforzar la moderación.

• Implementar filtros automáticos.

• Sancionar a los infractores.

## 14. Buenas Prácticas

## 14.1. Al Monitorear Métricas

• 📅 Establece una rutina: Revisa métricas diaria, semanal y mensualmente.

• 🎯 Define objetivos: Establece metas claras para cada métrica.

• 📊 Compara períodos: Siempre compara con el período anterior.

• 🔍 Investiga anomalías: Si algo cambia drásticamente, investiga.

• 📝 Documenta observaciones: Registra lo que aprendes.

## 14.2. Al Interpretar Métricas

• 🧠 No te obsesiones con una sola métrica: Mira el panorama completo.

• 📈 Busca tendencias: No reacciones a fluctuaciones diarias.

• 🎯 Contextualiza: Una métrica aislada no dice mucho.

• 🔬 Haz experimentos: Prueba cambios y mide el impacto.

• 📚 Aprende de los errores: Documenta qué funcionó y qué no.

## 14.3. Al Tomar Decisiones

• 📊 Basate en datos: No en suposiciones.

• 🎯 Prioriza: Enfócate en las métricas más importantes.

• 🤝 Consulta al equipo: Comparte hallazgos y decisiones.

• 📝 Documenta: Registra las decisiones y sus resultados.

• 🔄 Itera: Ajusta según los resultados.

## 14.4. Seguridad

• 🔐 Acceso restringido: Solo administradores pueden ver métricas.

• 📝 Audita accesos: Registra quién ve qué.

• 🚨 Reporta anomalías: Si algo parece sospechoso, investiga.

• 🔒 Datos sensibles: No compartas datos personales de usuarios.

## 15. Preguntas Frecuentes

**¿Con qué frecuencia debo revisar las métricas?**

**Respuesta:**

• Diario: KPIs principales (usuarios, ingresos, alertas).

• Semanal: Análisis de tendencias, reportes semanales.

• Mensual: Análisis profundo, proyecciones, estrategia.

**¿Qué métrica es la más importante?**

**Respuesta:** Depende de la etapa del proyecto:

**Etapa temprana:** Usuarios registrados y retención.

**Etapa de crecimiento:** MRR y tasa de conversión.

**Etapa de madurez:** LTV, CAC y churn rate.

**¿Cómo sé si una métrica es "buena" o "mala"?**

**Respuesta:**

**Compara con tu historial:** ¿Está mejorando o empeorando?

**Compara con la industria:** ¿Estás por encima o por debajo del promedio?

**Compara con tus objetivos:** ¿Estás alcanzando tus metas?

**¿Qué hago si veo una caída repentina en las métricas?**

**Respuesta:**

**Investiga:** ¿Hubo un cambio reciente? ¿Un bug? ¿Un problema técnico?

**Verifica los datos:** ¿Es un error de medición?

**Consulta al equipo:** ¿Alguien sabe qué pasó?

**Toma acción:** Corrige el problema lo antes posible.

**¿Cómo puedo mejorar la retención?**

**Respuesta:**

**Contenido nuevo:** Añade juegos regularmente.

**Comunidad:** Fomenta la interacción entre usuarios.

**Notificaciones:** Recuerda a los usuarios volver.

**Recompensas:** Ofrece beneficios por lealtad.

**Calidad:** Asegura que los juegos funcionen bien.

**¿Cómo puedo aumentar la tasa de conversión?**

**Respuesta:**

**Valor:** Añade más beneficios a los planes premium.

**Prueba gratuita:** Ofrece 7 días gratis.

**Descuentos:** Ofrece descuentos por pago anual.

**Urgencia:** Ofertas por tiempo limitado.

**Confianza:** Muestra testimonios y valoraciones.

**¿Qué hago si un juego +18 recibe muchos reportes?**

**Respuesta:**

**Suspende el juego** temporalmente.

**Investiga** los reportes.

**Verifica** que el bloqueo de edad funcione.

**Toma acción:** Reactivar, reclasificar o eliminar.

**Documenta** la decisión.

**¿Cómo puedo saber si un usuario está evadiendo el bloqueo de edad?**

**Respuesta:**

**Monitorea** los intentos de acceso a juegos +18 por usuarios menores.

**Verifica** que la fecha de nacimiento sea coherente.

**Alerta** si un usuario intenta acceder múltiples veces.

**Sanciona** si se confirma la evasión.

**¿Puedo exportar las métricas a Excel?**

**Respuesta: Sí.** Usa la opción "Exportar" y selecciona CSV. El archivo se puede abrir en Excel o Google Sheets.

**¿Cómo reporto un problema con el dashboard de métricas?**

**Respuesta:** Contacta al equipo de desarrollo:

**Email:** parraalavaro418@gmail.com

**Discord:** Canal #soporte-admin

## 16. Contacto

| Canal | Información |
| :--- | :--- | 
| **Email** | parraalavaro418@gmail.com |
| **Discord** | Canal #soporte-admin |
| **GitHub Issues** | Reportar problema |

 
## Recursos Adicionales

• 📖 Manual de Gestión de Juegos

• 📖 Manual de Usuarios

• 📖 Manual de Moderación

• 📖 API de Métricas

• 📖 Modelo de Datos

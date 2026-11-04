# ADR-004: Stripe como Procesador de Pagos

**Fecha:** 2026-09-05
**Estado:** Aceptado  
**Autores:** Álvaro Parra  
**Última Actualización:** 2026-09-05

---

## Contexto

Epic Things Platform requiere un sistema de pagos para gestionar suscripciones (Silver, Gold, Legend) y futuras compras de juegos. Necesitamos manejar pagos recurrentes, webhooks, y cumplir con normativas de seguridad (PCI DSS).

### Factores a Considerar

1. **Seguridad**: No queremos manejar datos de tarjetas de crédito.
2. **Facilidad de integración**: Documentación clara y SDKs.
3. **Suscripciones**: Soporte nativo para pagos recurrentes.
4. **Webhooks**: Para procesar eventos de pago asíncronamente.
5. **Costo**: Tarifas por transacción.
6. **Mercado**: Disponibilidad en Venezuela/Latinoamérica.

### Restricciones

- Debe cumplir con PCI DSS (Stripe maneja el cumplimiento).
- Debe permitir pruebas en entorno de desarrollo (modo sandbox).
- Debe soportar múltiples monedas (USD, EUR, etc.).

---

## Decisión

**Usaremos Stripe como procesador de pagos principal.**

- **Checkout**: Redirigir al usuario a Stripe Checkout (no almacenamos datos de tarjetas).
- **Suscripciones**: Stripe Billing para pagos recurrentes.
- **Webhooks**: Para eventos como `checkout.session.completed`, `charge.refunded`.
- **Modo Sandbox**: Para pruebas en desarrollo.

### Alternativas Consideradas

1. **PayPal**
   - ✅ Muy conocido y confiable.
   - ✅ Soporte para suscripciones.
   - ❌ Experiencia de usuario menos fluida.
   - ❌ Webhooks menos robustos.
   - ❌ Documentación más compleja.

2. **MercadoPago**
   - ✅ Dominante en Latinoamérica.
   - ✅ Soporte para suscripciones.
   - ❌ Menor penetración global.
   - ❌ SDKs menos maduros.

3. **Procesamiento propio (sin pasarela)**
   - ✅ Control total.
   - ❌ Riesgo de seguridad alto (PCI DSS).
   - ❌ Complejidad operacional enorme.

---

## Consecuencias

### Positivas

1. **Seguridad**: No almacenamos datos de tarjetas (Stripe maneja todo).
2. **Cumplimiento PCI DSS**: Stripe es certificado Level 1.
3. **Suscripciones nativas**: Gestión automática de renovaciones y vencimientos.
4. **Webhooks robustos**: Sistema confiable y con reintentos.
5. **Dashboard completo**: Stripe provee informes y métricas.
6. **SDKs excelentes**: Documentación y soporte en Node.js.

### Negativas (Riesgos)

1. **Costo por transacción**: 2.9% + $0.30 por transacción.
2. **Disponibilidad**: Si Stripe falla, los pagos se ven afectados.
3. **Soporte en Venezuela**: Puede haber restricciones o bloqueos.

### Compromisos

1. **Múltiples pasarelas**: En el futuro, considerar PayPal como alternativa.
2. **Cache de estados**: Guardar estado de suscripciones en Redis para reducir llamadas a Stripe.
3. **Monitoreo**: Alertas para webhooks fallidos.
4. **Pruebas intensivas**: Usar el modo sandbox para cubrir todos los casos.

---

## Justificación

Stripe es el procesador de pagos con **mejor experiencia de desarrollo** y **seguridad**. Su integración con Node.js es excelente, y su sistema de webhooks es robusto.

El **Checkout de Stripe** elimina la necesidad de manejar datos de tarjetas, reduciendo significativamente el riesgo de seguridad y la complejidad de desarrollo.

---

## Referencias

- [Stripe API Documentation](https://stripe.com/docs/api)
- [Stripe Billing for Subscriptions](https://stripe.com/docs/billing)
- [Stripe Webhooks](https://stripe.com/docs/webhooks)
- [Stripe Checkout](https://stripe.com/docs/payments/checkout)

---

## Historial de Cambios

| Fecha | Versión | Cambio |
| :--- | :--- | :--- |
| 2026-09-05 | 1.0 | Creación inicial |
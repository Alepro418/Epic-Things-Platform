# ADR-001: Usar Node.js como Tecnología Principal para el Backend

**Fecha:** 2026-09-05 
**Estado:** Aceptado  
**Autores:** Álvaro Parra  
**Última Actualización:** 2026-09-05 

---

## Contexto

Epic Things Platform requiere un backend robusto, escalable y de rápido desarrollo. Necesitamos manejar autenticación, pagos, subida de juegos, y comunicación en tiempo real (notificaciones). El equipo (actualmente una persona) debe poder desarrollar, mantener y desplegar el sistema eficientemente.

### Factores a Considerar

1. **Curva de aprendizaje**: El equipo debe poder empezar a producir rápidamente.
2. **Ecosistema**: Disponibilidad de librerías y herramientas para las funcionalidades requeridas.
3. **Rendimiento**: Capacidad para manejar operaciones I/O intensivas (subida de archivos, consultas a BD).
4. **Escalabilidad**: Facilidad para escalar horizontalmente.
5. **Comunidad**: Soporte, documentación y recursos disponibles.
6. **Tiempo de desarrollo**: Rapidez para construir e iterar.

### Restricciones

- El proyecto es desarrollado por una sola persona (Álvaro Parra).
- Se requiere despliegue en contenedores (Docker/Kubernetes).
- Debe integrarse con servicios externos (Stripe, SendGrid).
- Debe soportar WebSockets para notificaciones en tiempo real.

---

## Decisión

**Usaremos Node.js (con Express) como tecnología principal para los microservicios del backend.**

El 90% de los microservicios estarán escritos en Node.js, con la excepción de:

- **Auth Service**: Opcionalmente en PHP (por familiaridad), pero migrando a Node.js.
- **Analytics Service**: En Python (por su ecosistema de datos).

### Alternativas Consideradas

1. **PHP (Laravel/Slim)**
   - ✅ Lenguaje conocido por el desarrollador.
   - ✅ Ecosistema maduro para web.
   - ❌ Menos eficiente para operaciones I/O concurrentes.
   - ❌ WebSockets menos nativos.
   - ❌ Menor rendimiento para tiempo real.

2. **Python (Django/Flask)**
   - ✅ Ecosistema rico para datos y ML.
   - ✅ Curva de aprendizaje moderada.
   - ❌ Menos eficiente para alta concurrencia.
   - ❌ WebSockets menos nativos.

3. **Java (Spring Boot)**
   - ✅ Alto rendimiento.
   - ✅ Escalabilidad probada.
   - ❌ Curva de aprendizaje más empinada.
   - ❌ Desarrollo más verboso y lento.

4. **Go**
   - ✅ Excelente rendimiento y concurrencia.
   - ✅ Compilación a binario.
   - ❌ Ecosistema menos maduro para web.
   - ❌ Curva de aprendizaje más pronunciada.

---

## Consecuencias

### Positivas

1. **Rapidez de desarrollo**: JavaScript/TypeScript permite iterar rápidamente.
2. **Ecosistema vasto**: npm tiene librerías para todo (JWT, Stripe, WebSockets, etc.).
3. **Mismo lenguaje en frontend y backend**: Compartir tipos, validaciones, y lógica.
4. **Soporte nativo para WebSockets**: Socket.io es maduro y fácil de integrar.
5. **Escalabilidad horizontal**: Node.js maneja bien conexiones concurrentes.
6. **Comunidad activa**: Documentación abundante y soporte.

### Negativas (Riesgos)

1. **Rendimiento en operaciones CPU-intensivas**: Node.js no es ideal para cálculos pesados.
2. **Manejo de errores asíncronos**: Requiere disciplina para evitar callbacks hell.
3. **Single-threaded**: Puede ser un cuello de botella si no se maneja correctamente.

### Compromisos

1. **Usar TypeScript**: Para añadir tipado estático y mejorar la mantenibilidad.
2. **Usar Worker Threads**: Para operaciones CPU-intensivas (ej. procesamiento de imágenes).
3. **Delegar tareas pesadas a servicios especializados**: Analytics Service en Python.

---

## Justificación

Node.js ofrece el mejor equilibrio entre **velocidad de desarrollo** y **rendimiento** para un proyecto que necesita manejar múltiples conexiones (usuarios jugando, notificaciones en tiempo real). Además, al compartir el mismo lenguaje con el frontend (React), podemos reutilizar código, validaciones y tipos, lo que acelera el desarrollo y reduce errores.

La experiencia del desarrollador (DX) es excelente, y el ecosistema de npm nos permite añadir funcionalidades complejas (Stripe, JWT, WebSockets) con solo instalar un paquete.

---

## Referencias

- [Node.js Official Website](https://nodejs.org/)
- [Express.js Framework](https://expressjs.com/)
- [TypeScript for Node.js](https://www.typescriptlang.org/docs/handbook/node.html)
- [Socket.io for WebSockets](https://socket.io/)

---

## Historial de Cambios

| Fecha | Versión | Cambio |
| :--- | :--- | :--- |
| 2026-09-05 | 1.0 | Creación inicial |
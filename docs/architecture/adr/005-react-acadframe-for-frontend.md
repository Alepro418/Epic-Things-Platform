# ADR-005: React con AcadFrame como Framework de Frontend

**Fecha:** 2026-09-05
**Estado:** Aceptado  
**Autores:** Álvaro Parra  
**Última Actualización:** 2026-09-05  

---

## Contexto

Epic Things Platform necesita una interfaz de usuario moderna, interactiva y responsiva. La interfaz debe ser atractiva para jugadores y fácil de usar para creadores y administradores.

### Factores a Considerar

1. **Interactividad**: Juegos, valoraciones, suscripciones, etc.
2. **Velocidad de desarrollo**: Poder construir UI rápidamente.
3. **Reutilización**: Componentes modulares y reutilizables.
4. **Estilo visual**: Atractivo y moderno (Bento Grid, Glassmorphism).
5. **Modo oscuro**: Soporte nativo para cambiar entre temas.
6. **Escalabilidad**: Manejo de estado complejo (autenticación, suscripciones).

### Restricciones

- Debe usar **AcadFrame** (framework propio) como base de estilos.
- Debe ser SPA (Single Page Application) para experiencia fluida.
- Debe integrarse con APIs REST y WebSockets.

---

## Decisión

**Usaremos React + Vite + TypeScript para el frontend, con AcadFrame como base de estilos.**

- **React**: Para construir la UI con componentes reutilizables.
- **Vite**: Build tool ultrarrápida para desarrollo y producción.
- **TypeScript**: Tipado estático para reducir errores.
- **AcadFrame**: Framework propio para estilos, Bento Grid, Glassmorphism, modo oscuro.
- **React Context / Zustand**: Para manejo de estado (autenticación, suscripciones).
- **React Router**: Para navegación entre páginas.

### Alternativas Consideradas

1. **Vue.js**
   - ✅ Curva de aprendizaje suave.
   - ✅ Excelente documentación.
   - ❌ Ecosistema más pequeño que React.
   - ❌ Menor adopción en la industria.

2. **Angular**
   - ✅ Todo incluido (router, HTTP, etc.).
   - ✅ TypeScript nativo.
   - ❌ Curva de aprendizaje más empinada.
   - ❌ Desarrollo más verboso.

3. **Svelte**
   - ✅ Rendimiento excelente.
   - ✅ Menos código boilerplate.
   - ❌ Ecosistema más pequeño.
   - ❌ Menor adopción.

4. **Vanilla JS + HTML/CSS**
   - ✅ Sin dependencias.
   - ✅ Control total.
   - ❌ Desarrollo más lento.
   - ❌ Difícil mantener aplicaciones complejas.

---

## Consecuencias

### Positivas

1. **Rendimiento**: Vite proporciona HMR (Hot Module Replacement) y builds ultrarrápidas.
2. **Componentes reutilizables**: Podemos construir una biblioteca de componentes.
3. **TypeScript**: Ayuda a prevenir errores en tiempo de desarrollo.
4. **AcadFrame**: Los estilos serán consistentes y modernos (Bento Grid, Glassmorphism).
5. **Comunidad**: React tiene el ecosistema más grande.
6. **WebSockets**: Soporte nativo con Socket.io client.

### Negativas (Riesgos)

1. **Curva de aprendizaje**: React tiene conceptos como hooks y contexto que requieren práctica.
2. **Bundle size**: React es más pesado que frameworks más ligeros.
3. **Configuración**: Vite y TypeScript requieren configuración inicial.

### Compromisos

1. **Lazy loading**: Cargar juegos y componentes bajo demanda.
2. **Code splitting**: Dividir el bundle para mejorar tiempos de carga.
3. **Manejo de estado**: Usar React Context para auth y suscripciones.
4. **AcadFrame**: Usar los temas predefinidos (Océano, Esmeralda, Rosa) y modo oscuro.

---

## Justificación

React es el estándar de la industria y tiene el **ecosistema más grande** para resolver problemas comunes (autenticación, pagos, WebSockets). Vite mejora significativamente la experiencia de desarrollo con HMR y builds rápidas.

**AcadFrame** es un framework propio, lo que significa que tenemos **control total** sobre la apariencia y el comportamiento. Además, al ser nuestro, podemos extenderlo según las necesidades del proyecto.

---

## Referencias

- [React Official Documentation](https://reactjs.org/)
- [Vite Build Tool](https://vitejs.dev/)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/)
- [AcadFrame - Framework Propio](https://github.com/Alepro418/AcadFrame)

---

## Historial de Cambios

| Fecha | Versión | Cambio |
| :--- | :--- | :--- |
| 2026-09-05 | 1.0 | Creación inicial |
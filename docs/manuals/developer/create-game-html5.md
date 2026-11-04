# 🕹️ Crear Juegos en HTML5

> **Audiencia:** Creadores de juegos que quieren publicar en Epic Things Platform  
> **Última actualización:** 2026-09-01  
> **Versión:** 1.0  
> **Nivel:** Principiante - Intermedio

---

## 📋 Tabla de Contenidos

1. [Introducción](#1-introducción)
2. [¿Por Qué HTML5?](#2-por-qué-html5)
3. [Requisitos Previos](#3-requisitos-previos)
4. [Herramientas Recomendadas](#4-herramientas-recomendadas)
5. [Estructura de un Juego HTML5](#5-estructura-de-un-juego-html5)
6. [Tu Primer Juego: "Atrapa la Estrella"](#6-tu-primer-juego-atrapa-la-estrella)
7. [Conceptos Fundamentales](#7-conceptos-fundamentales)
8. [Gráficos y Assets](#8-gráficos-y-assets)
9. [Sonido y Música](#9-sonido-y-música)
10. [Controles y Input](#10-controles-y-input)
11. [Física y Colisiones](#11-física-y-colisiones)
12. [Puntuación y Guardado](#12-puntuación-y-guardado)
13. [Clasificación por Edad](#13-clasificación-por-edad)
14. [Optimización y Rendimiento](#14-optimización-y-rendimiento)
15. [Responsive Design](#15-responsive-design)
16. [Empaquetado para Epic Things](#16-empaquetado-para-epic-things)
17. [Checklist Antes de Subir](#17-checklist-antes-de-subir)
18. [Errores Comunes](#18-errores-comunes)
19. [Recursos de Aprendizaje](#19-recursos-de-aprendizaje)
20. [Preguntas Frecuentes](#20-preguntas-frecuentes)
21. [Contacto](#21-contacto)

---

## 1. Introducción

Esta guía te enseñará a crear un juego **HTML5** desde cero y prepararlo para publicarlo en **Epic Things Platform**.

### ¿Qué Aprenderás?

- ✅ Los fundamentos de un juego HTML5.
- ✅ Cómo estructurar tu proyecto.
- ✅ Cómo usar Canvas y JavaScript.
- ✅ Cómo añadir gráficos, sonido y controles.
- ✅ Cómo clasificar tu juego por edad.
- ✅ Cómo empaquetarlo para subirlo a la plataforma.

### ¿A Quién va Dirigida?

| Perfil | Nivel | ¿Le Sirve? |
| :--- | :--- | :--- |
| **Principiante** | Sin experiencia | ✅ Sí, empieza desde cero |
| **Estudiante** | Conocimientos básicos de programación | ✅ Sí, aprende haciendo |
| **Desarrollador web** | Con experiencia en JS | ✅ Sí, enfócate en la parte de juegos |
| **Creador experimentado** | Ya ha hecho juegos | ✅ Sí, revisa las secciones de clasificación y empaquetado |

---

## 2. ¿Por Qué HTML5?

### 2.1. Ventajas de HTML5 para Juegos

| Ventaja | Descripción |
| :--- | :--- |
| 🌐 **Universal** | Funciona en cualquier navegador moderno |
| 📱 **Multiplataforma** | PC, móvil, tablet, sin cambios |
| 🚀 **Sin instalación** | El usuario juega directamente en el navegador |
| 💰 **Bajo costo** | No necesitas servidores potentes |
| 📦 **Fácil distribución** | Solo un ZIP con los archivos |
| 🎨 **Flexibilidad** | Puedes usar Canvas, WebGL, CSS, SVG |
| 🔧 **Ecosistema** | Miles de librerías y frameworks |

### 2.2. Limitaciones a Tener en Cuenta

| Limitación | Solución |
| :--- | :--- |
| ⚠️ **Rendimiento** | Optimiza el código, usa Canvas |
| ⚠️ **Acceso a hardware** | Limitado, pero suficiente para la mayoría |
| ⚠️ **Audio en móviles** | Requiere interacción del usuario |
| ⚠️ **Tamaño del archivo** | Comprime assets, usa formatos eficientes |

### 2.3. ¿HTML5 es para Ti?

**Sí, si:**
- ✅ Quieres llegar a la mayor audiencia posible.
- ✅ Tu juego no requiere gráficos 3D ultra-realistas.
- ✅ Quieres iterar rápido y publicar fácilmente.
- ✅ Estás empezando en el desarrollo de juegos.

**No, si:**
- ❌ Necesitas gráficos AAA con Unreal Engine.
- ❌ Requieres acceso directo a hardware específico.
- ❌ Tu juego es multijugador masivo en tiempo real (aunque es posible, es complejo).

---

## 3. Requisitos Previos

### 3.1. Conocimientos Necesarios

| Conocimiento | Nivel Recomendado |
| :--- | :--- |
| **HTML** | Básico (etiquetas, estructura) |
| **CSS** | Básico (estilos, layout) |
| **JavaScript** | Intermedio (variables, funciones, objetos, eventos) |
| **Lógica de programación** | Básico (condicionales, bucles) |

### 3.2. Herramientas Necesarias

| Herramienta | Uso | Costo |
| :--- | :--- | :--- |
| **Editor de código** | Escribir código | Gratis (VS Code) |
| **Navegador** | Probar el juego | Gratis (Chrome, Firefox) |
| **Cuenta Gold** | Publicar en Epic Things | $15/mes |
| **Servidor local** | Probar el juego | Gratis (Live Server) |

### 3.3. ¿No Sabes Programar?

**No te preocupes.** Aquí tienes recursos para empezar:

- [JavaScript para Principiantes - MDN](https://developer.mozilla.org/es/docs/Learn/JavaScript)
- [Curso de JavaScript - freeCodeCamp](https://www.freecodecamp.org/espanol/)
- [HTML5 Game Development - W3Schools](https://www.w3schools.com/graphics/game_intro.asp)

---

## 4. Herramientas Recomendadas

### 4.1. Frameworks y Librerías

| Herramienta | Descripción | Nivel | Ideal para |
| :--- | :--- | :--- | :--- |
| **Phaser** | Framework completo para juegos 2D | Principiante-Intermedio | Casi cualquier juego 2D |
| **PixiJS** | Renderizado 2D de alto rendimiento | Intermedio | Juegos con muchos sprites |
| **Three.js** | Juegos 3D en el navegador | Avanzado | Juegos 3D |
| **Babylon.js** | Motor 3D completo | Avanzado | Juegos 3D complejos |
| **Kaboom.js** | Framework minimalista | Principiante | Juegos simples |
| **Vanilla JS + Canvas** | Sin dependencias | Principiante | Aprender los fundamentos |
| **Godot** | Motor completo (exporta a HTML5) | Intermedio | Juegos 2D/3D |
| **Unity** | Motor completo (exporta a WebGL) | Intermedio-Avanzado | Juegos 3D |

### 4.2. Herramientas de Arte

| Herramienta | Uso | Costo |
| :--- | :--- | :--- |
| **Aseprite** | Pixel art | $20 (o gratis desde el código fuente) |
| **Piskel** | Pixel art en el navegador | Gratis |
| **Krita** | Ilustración digital | Gratis |
| **GIMP** | Edición de imágenes | Gratis |
| **Inkscape** | Gráficos vectoriales | Gratis |
| **Figura** | Diseño de UI | Gratis |
| **Canva** | Diseño rápido | Gratis / Pro |

### 4.3. Herramientas de Audio

| Herramienta | Uso | Costo |
| :--- | :--- | :--- |
| **Audacity** | Edición de audio | Gratis |
| **BFXR** | Efectos de sonido retro | Gratis |
| **ChipTone** | Efectos de sonido retro | Gratis |
| **LMMS** | Música | Gratis |
| **BeepBox** | Música chiptune | Gratis |
| **Freesound** | Sonidos gratuitos | Gratis |
| **OpenGameArt** | Assets gratuitos | Gratis |

### 4.4. Assets Gratuitos

| Sitio | Descripción |
| :--- | :--- |
| **Kenney.nl** | Assets de alta calidad, gratuitos |
| **OpenGameArt.org** | Assets de la comunidad |
| **Itch.io** | Assets gratuitos y de pago |
| **Game-icons.net** | Iconos para juegos |
| **Google Fonts** | Fuentes tipográficas |

---

## 5. Estructura de un Juego HTML5

### 5.1. Estructura Básica

mi-juego/
├── index.html # Página principal
├── game.js # Lógica del juego
├── styles.css # Estilos
├── assets/
│ ├── images/ # Sprites, fondos, iconos
│ │ ├── player.png
│ │ ├── enemy.png
│ │ └── background.png
│ ├── sounds/ # Música y efectos
│ │ ├── music.ogg
│ │ ├── jump.wav
│ │ └── coin.wav
│ └── fonts/ # Tipografías (opcional)
│ └── game-font.ttf
└── README.md # Descripción del juego


### 5.2. Ejemplo de `index.html`

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi Juego Increíble</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div id="game-container">
        <canvas id="game-canvas"></canvas>
        <div id="ui-overlay">
            <div id="score">Puntos: 0</div>
            <div id="lives">Vidas: 3</div>
        </div>
    </div>
    <script src="game.js"></script>
</body>
</html>

## 5.3. Ejemplo de styles.css

``` css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    background: #1a1a2e;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    font-family: 'Arial', sans-serif;
    overflow: hidden;
}

#game-container {
    position: relative;
    width: 800px;
    height: 600px;
    max-width: 100vw;
    max-height: 100vh;
    background: #000;
    border-radius: 8px;
    overflow: hidden;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
}

#game-canvas {
    display: block;
    width: 100%;
    height: 100%;
}

#ui-overlay {
    position: absolute;
    top: 20px;
    left: 20px;
    right: 20px;
    display: flex;
    justify-content: space-between;
    color: white;
    font-size: 20px;
    font-weight: bold;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.8);
    pointer-events: none;
}

/* Responsive */
@media (max-width: 840px) {
    #game-container {
        width: 100vw;
        height: 100vh;
        border-radius: 0;
    }
}
```

## 6. Tu Primer Juego: "Atrapa la Estrella"

Vamos a crear un juego simple pero completo: Atrapa la Estrella.

## 6.1. Descripción del Juego

• 🎮 Objetivo: Mover una nave y atrapar estrellas que caen.

• ⏱️ Duración: 60 segundos por partida.

• 🏆 Puntuación: +10 puntos por estrella.

• ❤️ Vidas: 3 vidas (pierdes una si dejas caer una estrella).

• 📱 Controles: Teclado (flechas) y táctil (arrastrar).

## 6.2. Código Completo (game.js)

``` javascript 

// ============================================
// CONFIGURACIÓN DEL JUEGO
// ============================================

const CONFIG = {
    canvasWidth: 800,
    canvasHeight: 600,
    playerWidth: 60,
    playerHeight: 60,
    starSize: 30,
    starSpeed: 2,
    starSpawnRate: 1000, // milisegundos
    gameDuration: 60000, // 60 segundos
    initialLives: 3,
    pointsPerStar: 10
};

// ============================================
// ESTADO DEL JUEGO
// ============================================

const game = {
    canvas: null,
    ctx: null,
    player: null,
    stars: [],
    score: 0,
    lives: CONFIG.initialLives,
    timeLeft: CONFIG.gameDuration,
    isRunning: false,
    isGameOver: false,
    lastStarSpawn: 0,
    lastFrame: 0,
    keys: {},
    touchX: null
};

// ============================================
// INICIALIZACIÓN
// ============================================

function init() {
    game.canvas = document.getElementById('game-canvas');
    game.canvas.width = CONFIG.canvasWidth;
    game.canvas.height = CONFIG.canvasHeight;
    game.ctx = game.canvas.getContext('2d');
    
    // Crear jugador
    game.player = {
        x: CONFIG.canvasWidth / 2 - CONFIG.playerWidth / 2,
        y: CONFIG.canvasHeight - CONFIG.playerHeight - 20,
        width: CONFIG.playerWidth,
        height: CONFIG.playerHeight,
        speed: 7
    };
    
    // Eventos de teclado
    window.addEventListener('keydown', (e) => {
        game.keys[e.key] = true;
    });
    
    window.addEventListener('keyup', (e) => {
        game.keys[e.key] = false;
    });
    
    // Eventos táctiles
    game.canvas.addEventListener('touchmove', (e) => {
        e.preventDefault();
        const rect = game.canvas.getBoundingClientRect();
        const touch = e.touches[0];
        game.touchX = (touch.clientX - rect.left) * (CONFIG.canvasWidth / rect.width);
    });
    
    game.canvas.addEventListener('touchend', () => {
        game.touchX = null;
    });
    
    // Iniciar juego
    startGame();
}

// ============================================
// LÓGICA DEL JUEGO
// ============================================

function startGame() {
    game.score = 0;
    game.lives = CONFIG.initialLives;
    game.timeLeft = CONFIG.gameDuration;
    game.stars = [];
    game.isRunning = true;
    game.isGameOver = false;
    game.lastStarSpawn = performance.now();
    game.lastFrame = performance.now();
    
    updateUI();
    requestAnimationFrame(gameLoop);
}

function gameLoop(timestamp) {
    if (!game.isRunning) return;
    
    const deltaTime = timestamp - game.lastFrame;
    game.lastFrame = timestamp;
    
    // Actualizar tiempo
    game.timeLeft -= deltaTime;
    
    if (game.timeLeft <= 0) {
        endGame('¡Tiempo agotado!');
        return;
    }
    
    // Actualizar
    updatePlayer();
    updateStars(deltaTime);
    spawnStars(timestamp);
    checkCollisions();
    
    // Dibujar
    draw();
    updateUI();
    
    requestAnimationFrame(gameLoop);
}

function updatePlayer() {
    // Teclado
    if (game.keys['ArrowLeft'] || game.keys['a']) {
        game.player.x -= game.player.speed;
    }
    if (game.keys['ArrowRight'] || game.keys['d']) {
        game.player.x += game.player.speed;
    }
    
    // Táctil
    if (game.touchX !== null) {
        const targetX = game.touchX - game.player.width / 2;
        game.player.x += (targetX - game.player.x) * 0.2;
    }
    
    // Limitar al canvas
    if (game.player.x < 0) game.player.x = 0;
    if (game.player.x + game.player.width > CONFIG.canvasWidth) {
        game.player.x = CONFIG.canvasWidth - game.player.width;
    }
}

function updateStars(deltaTime) {
    for (let i = game.stars.length - 1; i >= 0; i--) {
        const star = game.stars[i];
        star.y += star.speed * (deltaTime / 16);
        star.rotation += star.rotationSpeed;
        
        // Eliminar si sale del canvas
        if (star.y > CONFIG.canvasHeight) {
            game.stars.splice(i, 1);
            game.lives--;
            updateUI();
            
            if (game.lives <= 0) {
                endGame('¡Sin vidas!');
                return;
            }
        }
    }
}

function spawnStars(timestamp) {
    if (timestamp - game.lastStarSpawn > CONFIG.starSpawnRate) {
        game.stars.push({
            x: Math.random() * (CONFIG.canvasWidth - CONFIG.starSize),
            y: -CONFIG.starSize,
            size: CONFIG.starSize,
            speed: CONFIG.starSpeed + Math.random() * 2,
            rotation: 0,
            rotationSpeed: (Math.random() - 0.5) * 0.1
        });
        game.lastStarSpawn = timestamp;
    }
}

function checkCollisions() {
    for (let i = game.stars.length - 1; i >= 0; i--) {
        const star = game.stars[i];
        
        if (star.x < game.player.x + game.player.width &&
            star.x + star.size > game.player.x &&
            star.y < game.player.y + game.player.height &&
            star.y + star.size > game.player.y) {
            
            game.stars.splice(i, 1);
            game.score += CONFIG.pointsPerStar;
            updateUI();
        }
    }
}

// ============================================
// DIBUJADO
// ============================================

function draw() {
    const ctx = game.ctx;
    
    // Limpiar canvas
    ctx.clearRect(0, 0, CONFIG.canvasWidth, CONFIG.canvasHeight);
    
    // Fondo (gradiente)
    const gradient = ctx.createLinearGradient(0, 0, 0, CONFIG.canvasHeight);
    gradient.addColorStop(0, '#1a1a2e');
    gradient.addColorStop(1, '#16213e');
    ctx.fillStyle = gradient;
    ctx.fillRect(0, 0, CONFIG.canvasWidth, CONFIG.canvasHeight);
    
    // Dibujar jugador
    drawPlayer(ctx);
    
    // Dibujar estrellas
    game.stars.forEach(star => drawStar(ctx, star));
}

function drawPlayer(ctx) {
    const { x, y, width, height } = game.player;
    
    // Nave (triángulo)
    ctx.save();
    ctx.fillStyle = '#0ea5e9';
    ctx.shadowColor = '#0ea5e9';
    ctx.shadowBlur = 20;
    ctx.beginPath();
    ctx.moveTo(x + width / 2, y);
    ctx.lineTo(x + width, y + height);
    ctx.lineTo(x, y + height);
    ctx.closePath();
    ctx.fill();
    ctx.restore();
}

function drawStar(ctx, star) {
    ctx.save();
    ctx.translate(star.x + star.size / 2, star.y + star.size / 2);
    ctx.rotate(star.rotation);
    ctx.fillStyle = '#fbbf24';
    ctx.shadowColor = '#fbbf24';
    ctx.shadowBlur = 15;
    
    // Estrella de 5 puntas
    const spikes = 5;
    const outerRadius = star.size / 2;
    const innerRadius = outerRadius / 2;
    
    ctx.beginPath();
    for (let i = 0; i < spikes * 2; i++) {
        const radius = i % 2 === 0 ? outerRadius : innerRadius;
        const angle = (Math.PI / spikes) * i - Math.PI / 2;
        const x = Math.cos(angle) * radius;
        const y = Math.sin(angle) * radius;
        
        if (i === 0) ctx.moveTo(x, y);
        else ctx.lineTo(x, y);
    }
    ctx.closePath();
    ctx.fill();
    ctx.restore();
}

// ============================================
// UI Y FIN DEL JUEGO
// ============================================

function updateUI() {
    document.getElementById('score').textContent = `Puntos: ${game.score}`;
    document.getElementById('lives').textContent = `Vidas: ${game.lives}`;
}

function endGame(reason) {
    game.isRunning = false;
    game.isGameOver = true;
    
    const ctx = game.ctx;
    
    // Overlay oscuro
    ctx.fillStyle = 'rgba(0, 0, 0, 0.8)';
    ctx.fillRect(0, 0, CONFIG.canvasWidth, CONFIG.canvasHeight);
    
    // Texto
    ctx.fillStyle = '#fff';
    ctx.font = 'bold 48px Arial';
    ctx.textAlign = 'center';
    ctx.fillText('Juego Terminado', CONFIG.canvasWidth / 2, CONFIG.canvasHeight / 2 - 60);
    
    ctx.font = 'bold 32px Arial';
    ctx.fillStyle = '#fbbf24';
    ctx.fillText(`${reason}`, CONFIG.canvasWidth / 2, CONFIG.canvasHeight / 2);
    
    ctx.font = '24px Arial';
    ctx.fillStyle = '#fff';
    ctx.fillText(`Puntuación final: ${game.score}`, CONFIG.canvasWidth / 2, CONFIG.canvasHeight / 2 + 60);
    
    ctx.font = '20px Arial';
    ctx.fillStyle = '#0ea5e9';
    ctx.fillText('Haz clic para reiniciar', CONFIG.canvasWidth / 2, CONFIG.canvasHeight / 2 + 120);
    
    // Reiniciar al hacer clic
    game.canvas.addEventListener('click', restartGame, { once: true });
}

function restartGame() {
    init();
}

// ============================================
// INICIAR
// ============================================

window.addEventListener('load', init);
```

## 6.3. ¿Qué Hace Este Juego?

• 🎮 Jugador: Una nave triangular que se mueve con flechas o táctil.

• ⭐ Estrellas: Caen desde arriba a velocidad variable.

• 🏆 Puntuación: +10 puntos por estrella atrapada.

• ❤️ Vidas: 3 vidas (pierdes una si dejas caer una estrella).

• ⏱️ Tiempo: 60 segundos por partida.

• 🔄 Reinicio: Haz clic para volver a jugar.

## 7. Conceptos Fundamentales

## 7.1. El Game Loop

El game loop es el corazón de cualquier juego. Se ejecuta ~60 veces por segundo:

``` javascript
function gameLoop(timestamp) {
    const deltaTime = timestamp - lastFrame;
    lastFrame = timestamp;
    
    update(deltaTime);  // Actualizar lógica
    draw();             // Dibujar en pantalla
    
    requestAnimationFrame(gameLoop);
}
```

## Fases del game loop:

1. **Input:** Leer controles del jugador.

2. **Update:** Actualizar posiciones, colisiones, puntuación.

3. **Render:** Dibujar todo en pantalla.

4. **Repeat:** Volver al paso 1.

## 7.2. Delta Time

**¿Por qué usar `deltaTime`?**

• Sin `deltaTime`: El juego va más rápido en PCs potentes.

• Con `deltaTime`: El juego va igual de rápido en todas las PCs.

``` javascript 
// MAL
player.x += 5;  // Siempre +5 por frame

// BIEN
player.x += 5 * (deltaTime / 16);  // +5 por frame a 60 FPS
```

## 7.3. Coordenadas en Canvas

(0,0)──────────────► X
  │
  │
  │
  │
  ▼
  Y

**Origen:** Esquina superior izquierda.

**X:** Aumenta hacia la derecha.

**Y:** Aumenta hacia abajo.

## 7.4. Estados del Juego

Un juego típico tiene varios estados:

``` javascript 
const GameState = {
    MENU: 'menu',
    PLAYING: 'playing',
    PAUSED: 'paused',
    GAME_OVER: 'gameOver'
};

let currentState = GameState.MENU;

function update() {
    switch (currentState) {
        case GameState.MENU:
            updateMenu();
            break;
        case GameState.PLAYING:
            updatePlaying();
            break;
        case GameState.PAUSED:
            updatePaused();
            break;
        case GameState.GAME_OVER:
            updateGameOver();
            break;
    }
}
```

## 8. Gráficos y Assets

## 8.1. Formatos de Imagen

| Formato | Uso | Tamaño |
| :--- | :--- | :--- |
| **PNG** | Sprites con transparencia | Medio |
| **JPG** | Fondos y fotos | Pequeño |
| **WebP** | Mejor compresión (moderno) | Muy pequeño |
| **SVG** | Gráficos vectoriales | Muy pequeño |
| **GIF** | Animaciones simples | Grande |

**Recomendación:** Usa **PNG** para sprites y **WebP** para fondos.

## 8.2. Cómo Cargar Imágenes

``` javascript 
const images = {};
let imagesLoaded = 0;
const totalImages = 2;

function loadImage(name, src) {
    images[name] = new Image();
    images[name].onload = () => {
        imagesLoaded++;
        if (imagesLoaded === totalImages) {
            startGame();
        }
    };
    images[name].src = src;
}

// Cargar
loadImage('player', 'assets/images/player.png');
loadImage('background', 'assets/images/background.png');
```

## 8.3. Cómo Dibujar Sprites

``` javascript
function draw() {
    // Dibujar imagen completa
    ctx.drawImage(images.player, x, y);
    
    // Dibujar con tamaño específico
    ctx.drawImage(images.player, x, y, width, height);
    
    // Dibujar un frame de un spritesheet
    ctx.drawImage(
        images.spritesheet,  // Imagen
        sx, sy, sw, sh,       // Frame en el spritesheet
        dx, dy, dw, dh        // Destino en el canvas
    );
}
```

## 8.4. Animaciones con Spritesheets

Un **spritesheet** es una imagen con varios frames:

┌─────┬─────┬─────┬─────┐
│ F1  │ F2  │ F3  │ F4  │  ← Animación de caminar
├─────┼─────┼─────┼─────┤
│ F5  │ F6  │ F7  │ F8  │  ← Animación de saltar
└─────┴─────┴─────┴─────┘

``` javascript 
const animation = {
    frameWidth: 64,
    frameHeight: 64,
    currentFrame: 0,
    totalFrames: 4,
    speed: 100, // ms por frame
    lastUpdate: 0
};

function updateAnimation(timestamp) {
    if (timestamp - animation.lastUpdate > animation.speed) {
        animation.currentFrame = (animation.currentFrame + 1) % animation.totalFrames;
        animation.lastUpdate = timestamp;
    }
}

function drawAnimatedSprite() {
    const sx = animation.currentFrame * animation.frameWidth;
    ctx.drawImage(
        images.player,
        sx, 0,
        animation.frameWidth, animation.frameHeight,
        x, y,
        animation.frameWidth, animation.frameHeight
    );
}
```

## 8.5. Crear Gráficos sin Assets (Canvas)

Puedes dibujar formas básicas directamente:

``` javascript 
// Rectángulo
ctx.fillStyle = '#0ea5e9';
ctx.fillRect(x, y, width, height);

// Círculo
ctx.beginPath();
ctx.arc(x, y, radius, 0, Math.PI * 2);
ctx.fill();

// Triángulo
ctx.beginPath();
ctx.moveTo(x, y);
ctx.lineTo(x + width, y);
ctx.lineTo(x + width / 2, y - height);
ctx.closePath();
ctx.fill();

// Texto
ctx.fillStyle = '#fff';
ctx.font = 'bold 24px Arial';
ctx.fillText('¡Hola!', x, y);
```

## 9. Sonido y Música

## 9.1. Formatos de Audio

| Formato | Uso | Compatibilidad |
| :--- | :--- | :--- |
| **MP3** | Música (universal) | Excelente |
| **OGG** | Música (mejor calidad) | Buena (excepto Safari antiguo) |
| **WAV** | Efectos de sonido | Excelente (archivos grandes) |
| **WebM** | Audio moderno | Buena |

**Recomendación:** MP3 para música, WAV u OGG para efectos.

## 9.2. Cómo Reproducir Sonidos

``` javascript
const sounds = {};

function loadSound(name, src) {
    sounds[name] = new Audio(src);
    sounds[name].preload = 'auto';
}

function playSound(name) {
    if (!sounds[name]) return;
    
    // Reiniciar si ya está sonando
    sounds[name].currentTime = 0;
    sounds[name].play().catch(err => {
        console.warn('No se pudo reproducir:', err);
    });
}

// Cargar
loadSound('jump', 'assets/sounds/jump.wav');
loadSound('coin', 'assets/sounds/coin.wav');
loadSound('music', 'assets/sounds/music.mp3');

// Usar
playSound('jump');
```

## 9.4. El Problema del Autoplay

Los navegadores modernos **bloquean el autoplay** de audio. Solución:

``` javascript 
// Solo reproducir música después de la primera interacción
let audioStarted = false;

document.addEventListener('click', () => {
    if (!audioStarted) {
        audioStarted = true;
        playMusic();
    }
}, { once: true });

document.addEventListener('keydown', () => {
    if (!audioStarted) {
        audioStarted = true;
        playMusic();
    }
}, { once: true });
```

## 9.5. Control de Volumen

``` javascript
const audioSettings = {
    musicVolume: 0.3,
    sfxVolume: 0.7,
    muted: false
};

function setMusicVolume(vol) {
    audioSettings.musicVolume = vol;
    if (backgroundMusic) {
        backgroundMusic.volume = vol;
    }
}

function toggleMute() {
    audioSettings.muted = !audioSettings.muted;
    if (backgroundMusic) {
        backgroundMusic.muted = audioSettings.muted;
    }
}
```

## 10. Controles y Input

## 10.1. Teclado

``` javascript 
const keys = {};

window.addEventListener('keydown', (e) => {
    keys[e.key] = true;
});

window.addEventListener('keyup', (e) => {
    keys[e.key] = false;
});

// En el update
if (keys['ArrowLeft']) player.x -= speed;
if (keys['ArrowRight']) player.x += speed;
if (keys[' '] && !player.isJumping) player.jump();
```

## 10.2. Ratón

``` javascript
let mouseX = 0;
let mouseY = 0;

canvas.addEventListener('mousemove', (e) => {
    const rect = canvas.getBoundingClientRect();
    mouseX = (e.clientX - rect.left) * (canvas.width / rect.width);
    mouseY = (e.clientY - rect.top) * (canvas.height / rect.height);
});

canvas.addEventListener('click', (e) => {
    // Disparar hacia el ratón
    shoot(mouseX, mouseY);
});
```

## 10.3. Táctil (Móvil)

``` javascript
canvas.addEventListener('touchstart', handleTouch);
canvas.addEventListener('touchmove', handleTouch);
canvas.addEventListener('touchend', () => {
    touchX = null;
});

function handleTouch(e) {
    e.preventDefault();
    const rect = canvas.getBoundingClientRect();
    const touch = e.touches[0];
    touchX = (touch.clientX - rect.left) * (canvas.width / rect.width);
    touchY = (touch.clientY - rect.top) * (canvas.height / rect.height);
}
```

## 10.4. Controles Híbridos (PC + Móvil)

``` javascript 
function updatePlayer() {
    // Teclado (PC)
    if (keys['ArrowLeft']) player.x -= speed;
    if (keys['ArrowRight']) player.x += speed;
    
    // Táctil (Móvil)
    if (touchX !== null) {
        const target = touchX - player.width / 2;
        player.x += (target - player.x) * 0.2;
    }
    
    // Limitar al canvas
    player.x = Math.max(0, Math.min(canvas.width - player.width, player.x));
}
```

## 10.5. Controles Personalizables

``` javascript 
const controls = {
    left: ['ArrowLeft', 'a', 'A'],
    right: ['ArrowRight', 'd', 'D'],
    jump: [' ', 'ArrowUp', 'w', 'W'],
    action: ['Enter', 'e', 'E']
};

function isPressed(action) {
    return controls[action].some(key => keys[key]);
}

// Uso
if (isPressed('left')) player.x -= speed;
if (isPressed('jump') && player.onGround) player.jump();
```

## 11. Física y Colisiones

## 11.1. Colisión AABB (Rectángulos)

La colisión más común en juegos 2D:

``` javascript
function rectCollide(a, b) {
    return a.x < b.x + b.width &&
           a.x + a.width > b.x &&
           a.y < b.y + b.height &&
           a.y + a.height > b.y;
}

// Uso
if (rectCollide(player, enemy)) {
    // ¡Colisión!
    player.takeDamage();
}
```

## 11.2. Colisión de Círculos

``` javascript 
function circleCollide(a, b) {
    const dx = a.x - b.x;
    const dy = a.y - b.y;
    const distance = Math.sqrt(dx * dx + dy * dy);
    return distance < a.radius + b.radius;
}
```

## 11.3. Gravedad y Salto

``` javascript
const physics = {
    gravity: 0.5,
    jumpForce: -12
};

// En update
player.velocityY += physics.gravity;

if (isPressed('jump') && player.onGround) {
    player.velocityY = physics.jumpForce;
    player.onGround = false;
}

player.y += player.velocityY;

// Colisión con el suelo
if (player.y + player.height >= groundY) {
    player.y = groundY - player.height;
    player.velocityY = 0;
    player.onGround = true;
}
```

## 11.4. Detección de Dirección

``` javascript 
function getCollisionSide(a, b) {
    const aCenterX = a.x + a.width / 2;
    const aCenterY = a.y + a.height / 2;
    const bCenterX = b.x + b.width / 2;
    const bCenterY = b.y + b.height / 2;
    
    const dx = aCenterX - bCenterX;
    const dy = aCenterY - bCenterY;
    
    if (Math.abs(dx) > Math.abs(dy)) {
        return dx > 0 ? 'right' : 'left';
    } else {
        return dy > 0 ? 'bottom' : 'top';
    }
}
```

## 12. Puntuación y Guardado

## 12.1. Puntuación en Memoria

``` javascript 
let score = 0;
let highScore = 0;

function addPoints(points) {
    score += points;
    if (score > highScore) {
        highScore = score;
    }
    updateUI();
}
```

## 12.2. Guardado con localStorage

``` javascript
// Guardar
function saveHighScore(score) {
    try {
        localStorage.setItem('highScore', score.toString());
    } catch (e) {
        console.warn('No se pudo guardar:', e);
    }
}

// Cargar
function loadHighScore() {
    try {
        const saved = localStorage.getItem('highScore');
        return saved ? parseInt(saved, 10) : 0;
    } catch (e) {
        return 0;
    }
}

// Uso
highScore = loadHighScore();
```

## 12.3. Progreso del Juego

``` javascript
const saveData = {
    level: 1,
    score: 0,
    unlockedLevels: [1],
    settings: {
        musicVolume: 0.3,
        sfxVolume: 0.7
    }
};

function saveProgress() {
    try {
        localStorage.setItem('gameProgress', JSON.stringify(saveData));
    } catch (e) {
        console.warn('Error guardando:', e);
    }
}

function loadProgress() {
    try {
        const saved = localStorage.getItem('gameProgress');
        if (saved) {
            Object.assign(saveData, JSON.parse(saved));
        }
    } catch (e) {
        console.warn('Error cargando:', e);
    }
}
```

## 12.4. Integración con la API de Epic Things (Opcional)

``` javascript
async function submitScore(score) {
    const token = localStorage.getItem('epic_token');
    if (!token) return;
    
    try {
        await fetch('https://api.epic-things.com/api/games/scores', {
            method: 'POST',
            headers: {
                'Authorization': `Bearer ${token}`,
                'Content-Type': 'application/json'
            },
            body: JSON.stringify({
                id_juego: GAME_ID,
                score: score
            })
        });
    } catch (e) {
        console.warn('No se pudo enviar puntuación:', e);
    }
}
```

## 13. Clasificación por Edad

## 13.1. ¿Por Qué Clasificar tu Juego?

La clasificación por edad es **obligatoria** en Epic Things Platform. Permite:

• ✅ Proteger a los menores de contenido inapropiado.

• ✅ Cumplir con normativas legales (COPPA, GDPR).

• ✅ Dar confianza a los padres.

• ✅ Mejorar la experiencia de usuario.

## 13.2. Categorías Disponibles

| Clasificación | Edad | Descripción |
| :--- | :--- | :--- |
| **+3** | Todos | Sin violencia, lenguaje soez ni contenido perturbador |
| **+7** | 7+ | Violencia fantástica leve, personajes de dibujos animados |
| **+12** | 12+ | Violencia fantástica moderada, lenguaje soez leve |
| **+16** | 16+ | Violencia realista, lenguaje soez frecuente |
| **+18** | 18+ | Violencia explícita, gore, contenido sexual, drogas |

## 13.3. Cómo Auto-Clasificar tu Juego

Responde estas preguntas:

┌─────────────────────────────────────────────────────────────┐
│  ¿Tu juego contiene violencia?                              │
│  ○ No → +3                                                  │
│  ○ Sí, pero fantástica y leve → +7                          │
│  ○ Sí, moderada → +12                                       │
│  ○ Sí, realista → +16                                       │
│  ○ Sí, explícita con sangre → +18                           │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│  ¿Tu juego contiene lenguaje soez?                          │
│  ○ No → sin cambio                                          │
│  ○ Leve (ej. "idiota") → mínimo +12                         │
│  ○ Frecuente → mínimo +16                                   │
│  ○ Intenso → mínimo +18                                     │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│  ¿Tu juego contiene contenido sexual?                       │
│  ○ No → sin cambio                                          │
│  ○ Sugerente → mínimo +16                                   │
│  ○ Explícito → +18 (revisar normas)                         │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│  ¿Tu juego contiene drogas o alcohol?                       │
│  ○ No → sin cambio                                          │
│  ○ Mencionadas → mínimo +12                                 │
│  ○ Consumidas → mínimo +18                                  │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│  ¿Tu juego contiene terror psicológico?                     │
│  ○ No → sin cambio                                          │
│  ○ Leve → mínimo +12                                        │
│  ○ Intenso → mínimo +16                                     │
│  ○ Extremo → +18                                            │
└─────────────────────────────────────────────────────────────┘

**Usa la clasificación más alta** que resulte de tus respuestas.

## 13.4. Advertencias de Contenido

Si tu juego es **+12 o superior**, añade advertencias en la descripción:

⚠️ Advertencias de contenido:
- Violencia fantástica moderada
- Lenguaje soez leve
- Temas de terror

## 13.5. Contenido Prohibido (Independientemente de la Clasificación)

❌ NO se permite en Epic Things Platform, incluso con +18:


• Abuso infantil.

• Glorificación de violencia real (terrorismo, genocidio).

• Instrucciones para actividades ilegales.

• Doxxing (publicar información privada).

• Acoso a personas reales.

• Contenido que viole derechos de autor.

Si tu juego contiene algo de esto, **será rechazado y eliminado**.

## 13.6. Cómo Implementar el Bloqueo por Edad en tu Juego

Aunque la plataforma maneja el bloqueo, puedes añadir una capa extra (Recomendable):

``` javascript
const MIN_AGE = 18; // Configura según tu clasificación

function checkAge() {
    const birthDate = localStorage.getItem('user_birth_date');
    if (!birthDate) {
        // Pedir fecha de nacimiento
        return askBirthDate();
    }
    
    const age = calculateAge(new Date(birthDate));
    if (age < MIN_AGE) {
        showAgeRestriction();
        return false;
    }
    return true;
}

function showAgeRestriction() {
    document.body.innerHTML = `
        <div style="
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: #1a1a2e;
            color: white;
            font-family: Arial;
            text-align: center;
            padding: 20px;
        ">
            <div>
                <h1>🔒 Contenido Restringido</h1>
                <p>Este juego está clasificado para mayores de ${MIN_AGE} años.</p>
            </div>
        </div>
    `;
}
```

## 14. Optimización y Rendimiento

## 14.1. Objetivo: 60 FPS

60 FPS significa que el juego se actualiza 60 veces por segundo (16.67ms por frame).

## 14.2. Técnicas de Optimización

1. Usa `requestAnimationFrame`

``` javascript 
// BIEN
function gameLoop() {
    update();
    draw();
    requestAnimationFrame(gameLoop);
}

// MAL (no sincronizado con el navegador)
setInterval(gameLoop, 16);
```

2. Limita el número de objetos

``` javascript
// MAL: Crear objetos por frame
function draw() {
    for (let i = 0; i < 1000; i++) {
        const particle = new Particle(); // ¡Nuevo objeto cada frame!
    }
}

// BIEN: Reciclar objetos
const particlePool = [];
function getParticle() {
    return particlePool.pop() || new Particle();
}
```

3. Evita cálculos en el draw

``` javascript 
// MAL
function draw() {
    const gradient = ctx.createLinearGradient(0, 0, 0, 600); // Cada frame
    // ...
}

// BIEN: Crear una vez
const gradient = ctx.createLinearGradient(0, 0, 0, 600);
function draw() {
    ctx.fillStyle = gradient;
    // ...
}
```

4. Usa Spritesheets

En lugar de cargar 10 imágenes separadas, usa 1 spritesheet:

``` javascript
// MAL: 10 imágenes
images.player1, images.player2, images.player3, ...

// BIEN: 1 spritesheet
images.playerSheet  // Dibujar frame específico
```

5. Culling (No dibujar lo que no se ve)

``` javascript
function draw() {
    objects.forEach(obj => {
        // Solo dibujar si está en pantalla
        if (obj.x + obj.width > 0 && 
            obj.x < canvas.width &&
            obj.y + obj.height > 0 &&
            obj.y < canvas.height) {
            obj.draw();
        }
    });
}
```

6. Object Pooling

``` javascript
class BulletPool {
    constructor(size = 50) {
        this.pool = [];
        this.active = [];
        for (let i = 0; i < size; i++) {
            this.pool.push({ x: 0, y: 0, active: false });
        }
    }
    
    get() {
        const bullet = this.pool.find(b => !b.active);
        if (bullet) {
            bullet.active = true;
            this.active.push(bullet);
        }
        return bullet;
    }
    
    release(bullet) {
        bullet.active = false;
        const index = this.active.indexOf(bullet);
        if (index > -1) this.active.splice(index, 1);
    }
}
```

## 14.3. Herramientas de Profiling

• Chrome DevTools → Performance tab.

• FPS Meter (extensión de Chrome).

• Stats.js (librería para mostrar FPS).

``` javascript 
// Stats.js
const stats = new Stats();
document.body.appendChild(stats.dom);

function gameLoop() {
    stats.begin();
    update();
    draw();
    stats.end();
    requestAnimationFrame(gameLoop);
}
```

## 15. Responsive Design

## 15.1. Canvas Responsive

``` html
<canvas id="game-canvas" width="800" height="600"></canvas>
```

``` css
#game-canvas {
    display: block;
    width: 100%;
    height: auto;
    max-width: 800px;
    max-height: 100vh;
    margin: 0 auto;
}
```

## 15.2. Escalar Contenido

``` javascript 
function resizeCanvas() {
    const maxWidth = window.innerWidth;
    const maxHeight = window.innerHeight;
    const aspectRatio = CONFIG.canvasWidth / CONFIG.canvasHeight;
    
    let newWidth = maxWidth;
    let newHeight = newWidth / aspectRatio;
    
    if (newHeight > maxHeight) {
        newHeight = maxHeight;
        newWidth = newHeight * aspectRatio;
    }
    
    canvas.style.width = newWidth + 'px';
    canvas.style.height = newHeight + 'px';
}

window.addEventListener('resize', resizeCanvas);
resizeCanvas();
```

## 15.3. Detectar Dispositivo Móvil

``` javascript 
const isMobile = /Android|iPhone|iPad|iPod/i.test(navigator.userAgent);

if (isMobile) {
    // Mostrar controles táctiles
    showTouchControls();
} else {
    // Mostrar controles de teclado
    showKeyboardControls();
}
```

## 15.4. Controles Táctiles en Pantalla

``` html
<div id="touch-controls" style="display: none;">
    <button class="touch-btn" id="btn-left">◀</button>
    <button class="touch-btn" id="btn-action">●</button>
    <button class="touch-btn" id="btn-right">▶</button>
</div>
```

``` css
#touch-controls {
    position: absolute;
    botton: 20px;
    left: 0;
    right: 0;
    display: flex;
    justify-content: space-beetwen;
    padding: 0 20px;
    pointer-events: none;
}

.touch-btn {
    width: 70;
    height: 70;
    border-radius: 50%;
    background: rgba(255, 255, 255, 0.2);
    border: 2px solid rgba(255, 255, 255, 0.5);
    color: white; 
    font-size: 24px;
    pointer-events: all;
    user-select: none;
    -webkit-user-select: none;
    touch-action: manipulation;
}
```

``` javascript
document.getElementById('btn-left').addEventListener('touchstart', () => {
    keys['ArrowLeft'] = true;
});

document.getElementById('btn-left').addEventListener('touchend', () => {
    keys['ArrowLeft'] => false;
});
// ... similar para otros botones
```

## 16. Empaquetado para Epic Things

## 16.1. Requisitos del Paquete

| Requisito | Descripción | 
| :--- | :--- | 
| **Formato** | ZIP |
| **Tamaño** | Máximo 100 MB | 
| **Estructura** | `index.html` en la raíz |
| **Dependencias** | Ninguna externa (todo incluido) |
| **Compatibilidad** | Chrome, Firefox, Safari, Edge |
	
## 16.2. Estructura Correcta del ZIP

mi-juego.zip
├── index.html
├── game.js
├── styles.css
├── assets/
│   ├── images/
│   └── sounds/
└── README.md (opcional)

**⚠️ MUY IMPORTANTE:** El `index.html` debe estar en la raíz del ZIP, NO dentro de una carpeta.

**Ejemplo correcto**:

mi-juego.zip/
├── index.html  ✅
└── assets/

**Ejemplo incorrecto**:

mi-juego.zip/
└── mi-juego/  ❌
    └── index.html

## 16.3. Cómo Comprimir

**En Windows**:

1. Selecciona todos los archivos (no la carpeta).

2. Clic derecho → "Enviar a" → "Carpeta comprimida (en zip)".

3. Renombra el ZIP.

**En macOS**:

1. Selecciona todos los archivos (no la carpeta).

2. Clic derecho → "Comprimir".

3. Renombra el ZIP.

**En Linux**:

cd mi-juego
zip -r ../mi-juego.zip .

## 16.4. Verificar el ZIP

Antes de subir, verifica:

``` bash
# Ver contenido del ZIP
unzip -l mi-juego.zip

# Debería mostrar:
# index.html
# game.js
# styles.css
# assets/images/player.png
# ...
```

## 16.5. Optimizar el Tamaño

Herramientas de compresión:

| Herramienta | Uso |
| :--- | :--- |
| **TinyPNG** | Comprimir imágenes PNG |
| **Squoosh** | Comprimir imágenes (Google) |
| **Terser** | Minificar JavaScript |
| **CSSNano** | Minificar CSS |
	
``` bash
# Minificar JS con Terser
npx terser game.js -o game.min.js -c -m

# Minificar CSS con CSSNano
npx cssnano styles.css styles.min.css
```

## 16.6. Probar el ZIP Localmente

Antes de subir, prueba el juego:

1. Descomprime el ZIP en una carpeta vacía.

2. Abre index.html en el navegador.

3. Verifica que todo funcione.

4. Prueba en diferentes navegadores.

5. Prueba en móvil (Chrome DevTools → modo responsive).

## 16.7. Subir a Epic Things

Sigue la guía: `Subir un Juego`.

Resumen:

1. Ve a Dashboard de Creador.

2. Haz clic en "Subir Nuevo Juego".

3. Completa metadatos (incluyendo clasificación por edad).

4. Sube el ZIP.

5. Espera la revisión (24-48 horas).

## 17. Checklist Antes de Subir
Antes de subir tu juego, verifica:

**✅ Funcionalidad**

□ El juego carga sin errores en la consola.

□ Los controles responden (teclado, ratón, táctil).

□ El juego se puede completar o terminar.

□ No hay bugs críticos.

□ El reinicio funciona correctamente.

**✅ Compatibilidad**

□ Funciona en Chrome.

□ Funciona en Firefox.

□ Funciona en Safari.

□ Funciona en Edge.

□ Funciona en móvil (Android/iOS).

□ Se adapta a diferentes resoluciones.

**✅ Rendimiento**

□ Corre a 60 FPS estables.

□ No hay lag ni caídas de FPS.

□ No consume demasiada memoria.

□ Carga en menos de 5 segundos.

**✅ Contenido**

□ Tiene clasificación por edad adecuada.

□ No contiene contenido prohibido.

□ Tiene advertencias si es +12 o superior.

□ La descripción es clara y atractiva.

□ La imagen de portada es atractiva (1280x720).

**✅ Empaquetado**

□ El ZIP tiene index.html en la raíz.

□ No hay archivos innecesarios (node_modules, .git, etc.).

□ El tamaño es menor a 100 MB.

□ Todas las dependencias están incluidas.

□ No hay enlaces a recursos externos.

**✅ Legal**

□ Eres el creador original o tienes derechos.

□ No violas derechos de autor.

□ Los assets (imágenes, sonidos) son tuyos o libres.

□ Aceptas los términos de Epic Things.

## 18. Errores Comunes

## 18.1. "El juego no carga"

**Causas**:

• index.html no está en la raíz del ZIP.

• Falta algún archivo (imagen, sonido).

• Error de sintaxis en JavaScript.

**Solución**:

• Verifica la estructura del ZIP.

• Abre la consola del navegador (F12) y revisa errores.

• Prueba el ZIP descomprimido localmente.

## 18.2. "Los controles no responden"

**Causas**:

• Eventos no registrados correctamente.

• El canvas no tiene el foco.

• Conflicto con otros eventos.

**Solución**:

• Verifica que los `addEventListener` estén bien.

• Añade `tabindex="0"` al canvas.

• Usa `event.preventDefault()` en eventos táctiles.

## 18.3. "El juego va muy rápido o muy lento"

**Causas**:

• No se usa `deltaTime`.

• Se usa setInterval en lugar de `requestAnimationFrame`.

**Solución**:

Usa `requestAnimationFrame` y `deltaTime`.

## 18.4. "El sonido no se reproduce"

**Causas**:

• Autoplay bloqueado por el navegador.

• Formato de audio no soportado.

**Solución**:

• Inicia el audio después de una interacción del usuario.

Usa MP3 (universal).

• Verifica la consola por errores.

** 18.5. "El juego se ve borroso"

**Causas**:

• El canvas tiene baja resolución.

• Se escala la imagen.

Solución:

``` javascript
// Ajustar al dispositivo (retina)
const dpr = window.devicePixelRatio || 1;
canvas.width = CONFIG.canvasWidth * dpr;
canvas.height = CONFIG.canvasHeight * dpr;
canvas.style.width = CONFIG.canvasWidth + 'px';
canvas.style.height = CONFIG.canvasHeight + 'px';
ctx.scale(dpr, dpr);
```
## 18.6. "El juego no funciona en móvil"

**Causas**:

• Falta `viewport` meta tag.

• Controles no adaptados a táctil.

• Canvas no responsive.

**Solución**:

1. Añade <meta name="viewport" content="width=device-width, initial-scale=1.0">.

2. Añade controles táctiles.

3. Usa touchstart, touchmove, touchend.

## 18.7. "El ZIP pesa demasiado"

**Causas**:

• Imágenes muy grandes.

• Audio de alta calidad innecesario.

• Código sin minificar.

**Solución**:

• Comprime imágenes con TinyPNG.

• Usa MP3 en lugar de WAV para música.

• Minifica JS y CSS.

## 18.8. "El juego fue rechazado"

**Causas comunes**:

• Clasificación por edad incorrecta.

• Contenido prohibido.

• No funciona correctamente.

• Baja calidad.

**Solución**:

• Lee el motivo del rechazo (email).

• Corrige los problemas.

• Vuelve a subir.

## 19. Recursos de Aprendizaje

## 19.1. Documentación

| Recurso | Descripción |
| :--- | :--- |
| **MDN Web Docs** | Documentación de HTML, CSS, JS |
| **Canvas API** | Documentación oficial de Canvas |
| **Web Audio API** | Documentación de audio |
| **Phaser Docs** | Documentación de Phaser |

## 19.2. Tutoriales

| Recurso | Descripción |
| :--- | :--- |
| **MDN Game Development** | Tutoriales de juegos |
| **Phaser Tutorials** | Tutoriales de Phaser |
| **YouTube - Coding Train** | Juegos con Processing/p5.js |
| **freeCodeCamp** | Cursos gratuitos |

## 19.3. Assets Gratuitos

| Recurso | Descripción |
| :--- | :--- |
| **Kenney.nl** | Assets de alta calidad |
| **OpenGameArt.org** | Assets de la comunidad |
| **Itch.io Assets** | Assets gratuitos y de pago |
| **Game-icons.net** | Iconos |
| **Freesound.org** | Sonidos |

## 19.4. Comunidad

| Recurso | Descripción |
| :--- | :--- |
| **Discord de Epic Things** | Canal #ayuda-programacion |
| **r/gamedev** | Comunidad de desarrollo |
| **r/IndieGaming** | Comunidad de juegos indie |
| **r/HTML5Games** | Comunidad de juegos HTML5 |

## 19.5. Libros

| Libro | Autor | Nivel |
| :--- | :--- | :--- |
| **"HTML5 Game Development"** | Rex van der Spuy | Intermedio |
| **"Game Programming Patterns"** | Robert Nystrom | Avanzado |
| **"The Art of Game Design"** | Jesse Schell | Todos |

## 20. Preguntas Frecuentes

¿Necesito saber programar para crear un juego HTML5?

**Respuesta**: Sí, pero puedes empezar con lo básico. HTML5 + JavaScript es uno de los lenguajes más accesibles. Además, hay frameworks como Phaser que simplifican mucho el proceso.

**¿Cuánto tiempo toma crear un juego?**

**Respuesta**: Depende de la complejidad:

• **Juego simple** (como el ejemplo): 1-2 semanas.

• **Juego mediano**: 1-3 meses.

• **Juego complejo**: 6+ meses.

**¿Puedo usar frameworks como Phaser?**

**Respuesta**: Sí. Puedes usar cualquier framework o librería. Solo asegúrate de que todo esté incluido en el ZIP (no uses CDNs externos).

**¿Puedo usar imágenes o sonidos de internet?**

**Respuesta**: Solo si tienes permiso. Usa assets:

• De sitios como Kenney.nl (gratuitos).

• Con licencia Creative Commons.

• Creados por ti mismo.

**No uses** assets con copyright sin permiso.

**¿Qué pasa si mi juego no es aprobado?**

**Respuesta**: Recibirás un email con el motivo. Puedes:

1. Corregir los problemas.

2. Volver a subirlo.

3. Contactar a soporte si crees que fue un error.

**¿Cuánto gano por mi juego?**

**Respuesta**: Recibes el 70% de los ingresos generados por tu juego. Ver Regalías para más detalles.

**¿Puedo actualizar mi juego después de publicarlo?**

**Respuesta**: Sí. Puedes subir nuevas versiones. Pasan por revisión nuevamente (24-48 horas).

**¿Puedo monetizar mi juego directamente?**

**Respuesta**: Sí. Puedes establecer un precio (70% para ti). También puedes recibir donaciones (80% para ti).

**¿Mi juego necesita multijugador?**

**Respuesta**: No. Los juegos de un solo jugador son bienvenidos. El multijugador es un plus, pero no es obligatorio.

**¿Qué pasa si mi juego es +18?**

**Respuesta**: Los usuarios deberán verificar su edad para acceder. Asegúrate de que:

• La clasificación sea correcta.

• Añadas advertencias de contenido.

• No contenga contenido prohibido (ver sección 13.5).

**¿Puedo usar música con copyright?**

**Respuesta**: No. Usa música:

• De sitios como Freesound o OpenGameArt.

• Con licencia Creative Commons.

• Creada por ti mismo (o con herramientas como LMMS).

**¿Dónde reporto un bug en mi juego?**

**Respuesta**: Puedes:

• Corregirlo tú mismo y subir una nueva versión.

• Reportarlo en el Discord (#ayuda-programacion).

• Contactar a soporte: parraalavaro418@gmail.com

## 21. Contacto

Soporte para Desarrolladores

| Canal | Información |
| :--- | :--- |
| **Email** | parraalavaro418@gmail.com |
| **Discord** | Canal `#ayuda-programacion` |
| **Documentación** | `API Reference` |

**Recursos Adicionales**

• 📖 Primeros Pasos como Creador

• 📖 Subir un Juego

• 📖 Crear Juego en Unity

• 📖 Integración con la API

• 📖 Regalías

• 📖 Manual de Gestión de Juegos (Admin)
	

📝 Historial de Cambios

| Fecha | Versión | Cambio |
| :--- | :--- | :--- |
| 2026-09-01 | 1.0 | Creación inicial |

**Hecho con ❤️ desde Puerto Cabello, Venezuela**

"El mejor juego es el que terminas. No el que empiezas."
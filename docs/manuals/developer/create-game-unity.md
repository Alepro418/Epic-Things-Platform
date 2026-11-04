# 🎮 Crear Juegos en Unity (WebGL)

> **Audiencia:** Creadores de juegos que quieren publicar en Epic Things Platform usando Unity  
> **Última actualización:** 2026-09-01  
> **Versión:** 1.0  
> **Nivel:** Intermedio - Avanzado

---

## 📋 Tabla de Contenidos

1. [Introducción](#1-introducción)
2. [¿Por Qué Unity para WebGL?](#2-por-qué-unity-para-webgl)
3. [Requisitos Previos](#3-requisitos-previos)
4. [Configuración Inicial del Proyecto](#4-configuración-inicial-del-proyecto)
5. [Configuración para WebGL](#5-configuración-para-webgl)
6. [Optimización del Proyecto](#6-optimización-del-proyecto)
7. [Compilación (Build) a WebGL](#7-compilación-build-a-webgl)
8. [Estructura del Build](#8-estructura-del-build)
9. [Empaquetado para Epic Things](#9-empaquetado-para-epic-things)
10. [Clasificación por Edad y Advertencias](#10-clasificación-por-edad-y-advertencias)
11. [Compatibilidad y Limitaciones](#11-compatibilidad-y-limitaciones)
12. [Checklist Antes de Subir](#12-checklist-antes-de-subir)
13. [Errores Comunes](#13-errores-comunes)
14. [Recursos de Aprendizaje](#14-recursos-de-aprendizaje)
15. [Preguntas Frecuentes](#15-preguntas-frecuentes)
16. [Contacto](#16-contacto)

---

## 1. Introducción

Esta guía te enseñará a **exportar tu juego de Unity a WebGL** y prepararlo para publicarlo en **Epic Things Platform**.

### ¿Qué Aprenderás?

- ✅ Configurar Unity para WebGL.
- ✅ Optimizar tu juego para el navegador.
- ✅ Compilar y empaquetar correctamente.
- ✅ Clasificar tu juego por edad.
- ✅ Evitar los errores más comunes.

### ¿A Quién va Dirigida?

| Perfil | Nivel | ¿Le Sirve? |
| :--- | :--- | :--- |
| **Creador con experiencia en Unity** | Intermedio | ✅ Sí, enfócate en WebGL y empaquetado |
| **Desarrollador que migra de PC a Web** | Intermedio | ✅ Sí, revisa optimización y compatibilidad |
| **Principiante en Unity** | Básico | ⚠️ Sí, pero primero aprende los fundamentos de Unity |
| **Creador de juegos 3D** | Avanzado | ✅ Sí, revisa limitaciones de WebGL |

---

## 2. ¿Por Qué Unity para WebGL?

### 2.1. Ventajas

| Ventaja | Descripción |
| :--- | :--- |
| 🎨 **Motor completo** | Físicas, animación, iluminación, audio, UI |
| 🌍 **Multiplataforma** | Un proyecto, múltiples destinos (PC, móvil, web) |
| 🧩 **Ecosistema** | Asset Store, tutorials, comunidad enorme |
| 🚀 **Rendimiento** | WebGL 2 + WebAssembly para juegos complejos |
| 🛠️ **Herramientas** | Editor visual, debugging, profiling |

### 2.2. Limitaciones de WebGL

| Limitación | Impacto | Solución |
| :--- | :--- | :--- |
| **Tamaño del build** | Descargas lentas | Optimizar assets, comprimir |
| **Memoria limitada** | Crash en móviles | Reducir texturas, object pooling |
| **Sin multihilo completo** | Menos rendimiento en CPU | Evitar lógica pesada en el main thread |
| **Compatibilidad móvil limitada** | No funciona en todos los dispositivos | Probar en Safari 15+ y Chrome 58+ |
| **Sin acceso a hardware** | No puedes usar APIs nativas | Usar Web APIs (JavaScript) |

---

## 3. Requisitos Previos

### 3.1. Software Necesario

| Herramienta | Versión Recomendada | Descarga |
| :--- | :--- | :--- |
| **Unity Hub** | Última versión | [unity.com](https://unity.com/) |
| **Unity Editor** | 2022.3 LTS o superior | Unity Hub |
| **Módulo WebGL** | Incluido en Unity | Unity Hub → Installs → Add Modules |
| **Navegador** | Chrome, Firefox, Edge (64-bit) | - |

### 3.2. Conocimientos Recomendados

- ✅ Fundamentos de Unity (GameObjects, Components, Scenes).
- ✅ Programación en C# (básico-intermedio).
- ✅ Uso del Editor de Unity (jerarquía, inspector, project).
- ✅ Conceptos de optimización (draw calls, texturas, memoria).

### 3.3. Cuenta de Creador

Necesitas una suscripción **Gold** o superior en Epic Things Platform para subir juegos.

---

## 4. Configuración Inicial del Proyecto

### 4.1. Crear el Proyecto

1. Abre **Unity Hub**.
2. Haz clic en **"New Project"**.
3. Selecciona la plantilla **"3D (WebGL)"** o **"2D (WebGL)"**.
4. Asigna un nombre y ubicación.
5. Haz clic en **"Create"**.

### 4.2. Estructura Recomendada de Carpetas

Assets/
├── Scenes/ # Escenas del juego
├── Scripts/ # Código C#
├── Prefabs/ # Objetos reutilizables
├── Sprites/ # Imágenes 2D
├── Materials/ # Materiales
├── Audio/ # Sonidos y música
├── UI/ # Elementos de interfaz
└── Resources/ # Assets cargados dinámicamente


### 4.3. Configuración de Calidad

Ve a **Edit → Project Settings → Quality**:

| Nivel | Uso |
| :--- | :--- |
| **Low** | Móviles de gama baja |
| **Medium** | Móviles de gama media |
| **High** | Desktop |

Para WebGL, se recomienda **Medium** o **High** (dependiendo del juego).

---

## 5. Configuración para WebGL

### 5.1. Cambiar la Plataforma a WebGL

1. Ve a **File → Build Settings** (o **File → Build Profiles** en Unity 6+).
2. Selecciona **WebGL** en la lista de plataformas.
3. Haz clic en **"Switch Platform"**.
4. Espera a que Unity reimporte los assets.

### 5.2. Player Settings (Configuración del Jugador)

Ve a **Edit → Project Settings → Player** y configura:

#### Settings Generales

| Setting | Valor Recomendado | Razón |
| :--- | :--- | :--- |
| **Company Name** | Tu nombre o estudio | Aparece en el build |
| **Product Name** | Nombre del juego | Aparece en el título |
| **Default Screen Width** | 960 | Ancho inicial |
| **Default Screen Height** | 600 | Alto inicial |
| **Run In Background** | ✅ Enabled | El juego sigue si se pierde el foco |

#### Settings de WebGL (Publishing Settings)

| Setting | Valor Recomendado | Descripción |
| :--- | :--- | :--- |
| **Compression Format** | **Brotli** | Mejor compresión que Gzip[reference:0] |
| **Data Caching** | ✅ Enabled | Cachea assets para cargas posteriores[reference:1] |
| **Debug Symbols** | ❌ Disabled | Reduce tamaño y mejora rendimiento[reference:2] |
| **Enable Exceptions** | **None** (para release) | Mejor rendimiento[reference:3] |
| **Target WebAssembly 2023** | ✅ Enabled | Mejoras de rendimiento[reference:4] |
| **Maximum Memory Size** | 256 MB (mínimo) | Ajusta según tu juego (máx. 4096 MB)[reference:5] |

#### Other Settings

| Setting | Valor Recomendado | Razón |
| :--- | :--- | :--- |
| **Api Compatibility Level** | **.NET Standard 2.1** | Builds más pequeños[reference:6] |
| **Managed Stripping Level** | **High** | Elimina código no usado[reference:7] |
| **Stack Trace** | **None** | Reduce tamaño (si WebAssembly 2023 está desactivado)[reference:8] |

### 5.3. Build Settings

En **File → Build Settings**:

| Setting | Valor Recomendado |
| :--- | :--- |
| **Code Optimization** | **Disk Size with LTO** (para release)[reference:9] |
| **Development Build** | ❌ Disabled (para release) |
| **Autoconnect Profiler** | ❌ Disabled |
| **Deep Profiling** | ❌ Disabled |

⚠️ **Nota:** `Disk Size with LTO` tarda mucho en compilar. Úsalo solo para la versión final.

---

## 6. Optimización del Proyecto

### 6.1. Reducir Draw Calls

WebGL tiene un overhead alto por draw call[reference:10].

**Técnicas:**
- ✅ **Batching**: Combina meshes estáticos.
- ✅ **GPU Instancing**: Para objetos repetidos.
- ✅ **Texture Atlas**: Combina texturas en una sola.
- ✅ **Sprite Atlas**: Para juegos 2D.

**Cómo verificar:**
- Ve a **Window → Analysis → Profiler**.
- Revisa **Rendering → Draw Calls**.
- Objetivo: < 100 draw calls en móvil.

### 6.2. Optimizar Texturas

| Técnica | Ahorro |
| :--- | :--- |
| **Reducir resolución** | 2048→1024 = 75% menos memoria |
| **Usar compresión** | ASTC/ETC2 (móvil), DXT (desktop) |
| **Desactivar Mipmaps** | Si no se necesita |
| **Usar Sprite Atlas** | Reduce draw calls |

**Configuración:**
1. Selecciona una textura.
2. En **Inspector → Texture Import Settings**.
3. **Max Size**: 1024 (o menos).
4. **Compression**: Normal Quality.
5. **Generate Mip Maps**: Off (si es UI o sprite 2D).

### 6.3. Optimizar Audio

| Técnica | Ahorro |
| :--- | :--- |
| **Usar OGG/MP3** | WAV es muy pesado |
| **Reducir calidad** | 128 kbps es suficiente |
| **Mono en vez de estéreo** | 50% menos tamaño |
| **Comprimir en build** | Force To Mono, Compressed |

**Configuración:**
1. Selecciona un audio clip.
2. **Inspector → Audio Import Settings**.
3. **Load Type**: Compressed In Memory.
4. **Compression Format**: Vorbis (OGG).
5. **Quality**: 70%.

### 6.4. Reducir el Tamaño del Build

| Técnica | Ahorro |
| :--- | :--- |
| **Managed Stripping Level: High** | Elimina código no usado |
| **Eliminar paquetes no usados** | Package Manager → Remove |
| **Eliminar escenas no usadas** | Build Settings → Solo escenas necesarias |
| **Comprimir assets** | Brotli, texturas, audio |

### 6.5. Object Pooling

Evita crear/destruir objetos constantemente:

```csharp
public class BulletPool : MonoBehaviour
{
    public GameObject bulletPrefab;
    private Queue<GameObject> pool = new Queue<GameObject>();

    public GameObject GetBullet()
    {
        if (pool.Count > 0)
        {
            var bullet = pool.Dequeue();
            bullet.SetActive(true);
            return bullet;
        }
        return Instantiate(bulletPrefab);
    }

    public void ReturnBullet(GameObject bullet)
    {
        bullet.SetActive(false);
        pool.Enqueue(bullet);
    }
}
```

## 6.6. Evitar Lógica Pesada en Update

``` csharp
// MAL: Cada frame
void Update()
{
    GameObject.Find("Player"); // Muy costoso
}

// BIEN: Una vez
private GameObject player;
void Start()
{
    player = GmeObject.Find("Player");
}
```

## 7. Compilación (Build) a WebGL

## 7.1. Proceso de Build

1. Ve a File → Build Settings.

2. Verifica que WebGL esté seleccionado.

3. Haz clic en "Build".

4. Elige una carpeta vacía para el build.

5. Espera a que termine (puede tardar 10-30 minutos).

## 7.2. Build and Run

Para probar localmente:

1. Haz clic en **"Build And Run"**.

2. Unity compila y abre el juego en el navegador.

3. Verifica que todo funcione.

**⚠️ Nota**: Unity usa un servidor local. Si no funciona, usa Live Server en VS Code.

## 7.3. Tiempo de Compilación

| Tipo de Build | Tiempo Estimado |
| :--- | :--- |
| **Development Build** | 2-5 minutos |
| **Release Build (Speed)** | 10-15 minutos |
| **Release Build (Disk Size LTO)** | 20-40 minutos |

## 8. Estructura del Build

Después de compilar, obtendrás una carpeta como esta:

Build/
├── index.html              # Página principal
├── Build/
│   ├── mi-juego.loader.js
│   ├── mi-juego.framework.js
│   ├── mi-juego.wasm
│   └── mi-juego.data
├── TemplateData/
│   ├── style.css
│   ├── favicon.ico
│   └── ...
└── StreamingAssets/        # (Opcional) Assets externos

**⚠️ Importante**: El archivo index.html debe estar en la raíz del ZIP.

## 9. Empaquetado para Epic Things

## 9.1. Requisitos del Paquete

| Requisito | Descripción |
| :--- | :--- |
| **Formato** | ZIP |
| **Tamaño máximo** | 500 MB |
| **Estructura** | `index.html` en la raíz |
| **Dependencias** | Todas incluidas (no CDNs externos) |

## 9.2. Estructura Correcta del ZIP

mi-juego-unity.zip
├── index.html              ✅
├── Build/
├── TemplateData/
└── StreamingAssets/        (si aplica)

**Ejemplo incorrecto**:

mi-juego-unity.zip
└── mi-juego/               ❌
    └── index.html

## 9.3. Cómo Comprimir

**Windows**:

1. Selecciona todos los archivos dentro de la carpeta del build (no la carpeta).

2. Clic derecho → "Enviar a" → "Carpeta comprimida".

3. Renombra el ZIP.

**macOS**:

1. Selecciona los archivos.

2. Clic derecho → "Comprimir".

**Linux**:

``` bash
cd Build
zip -r ../mi-juego-unity.zip .
```

## 9.4. Verificar el ZIP

``` bash
unzip -l mi-juego-unity.zip
```

Debe mostrar:

index.html
Build/mi-juego.loader.js
Build/mi-juego.wasm
...

## 9.5. Probar el ZIP Localmente

1. Descomprime el ZIP en una carpeta vacía.

2. Abre index.html con Live Server (VS Code).

3. Verifica que el juego cargue y funcione.

**⚠️ No abras `index.html` directamente** (file://). Usa un servidor local.

## 10. Clasificación por Edad y Advertencias

## 10.1. Clasificación Obligatoria

Todo juego en Epic Things Platform debe tener una clasificación por edad:

| Clasificación | Edad | Descripción |
| :--- | :--- | :---  |
| **+3** | Todos | Sin violencia, lenguaje soez ni contenido perturbador |
| **+7** | 7+ | Violencia fantástica leve, personajes caricaturescos |
| **+12** | 12+ | Violencia fantástica moderada, lenguaje soez leve |
| **+16** | 16+ | Violencia realista, lenguaje soez frecuente |
| **+18** | 18+ | Violencia explícita, gore, contenido sexual, drogas |
		
## 10.2. Cómo Auto-Clasificar tu Juego Unity

**Responde**:

| Pregunta | Edad | Descripción |
| :--- | :--- | :---  |
| **¿Hay violencia?** | +7 (leve), +12 (moderada), +16 (realista), +18 (explícita) |
| **¿Hay sangre?** | +16 (poca), +18 (mucha) |
| **¿Hay lenguaje soez?** | +12 (leve), +16 (frecuente), +18 (intenso) |
| **¿Hay contenido sexual?** | +16 (sugerente), +18 (explícito) |
| **¿Hay drogas?** | +12 (mencionadas), +18 (consumidas) |
| **¿Hay terror psicológico?** | +12 (leve), +16 (intenso), +18 (extremo) |

**Usa la clasificación más alta.**

## 10.3. Advertencias de Contenido

Si tu juego es +12 o superior, añade advertencias en la descripción:

⚠️ Advertencias de contenido:
- Violencia fantástica
- Lenguaje soez leve
- Temas de terror

## 10.4. Contenido Prohibido (Incluso con +18)

❌ No se permite:

• Abuso infantil.

• Glorificación de violencia y contenido gore.

• Instrucciones para actividades ilegales.

• Doxxing.

• Acoso a personas reales.

• Violación de derechos de autor.

## 10.5. Bloqueo por Edad en la Plataforma

Epic Things Platform **bloquea automáticamente** los juegos +18 para usuarios no verificados. Asegúrate de:

• ✅ Clasificar correctamente.

• ✅ Añadir advertencias.

• ✅ No incluir contenido prohibido.

## 11. Compatibilidad y Limitaciones

## 11.1. Navegadores Soportados

| Navegador | Versión Mínima | Plataforma |
| :--- | :--- | :---  |
| Chrome | 58+ | Windows, macOS, Linux, Android |
| Firefox | Última | Windows, macOS, Linux |
| Safari | 15+ | macOS, iOS |
| Edge | Última (Chromium) | Windows, macOS |

## 11.2. Móvil

| Plataforma | Soporte |
| :--- | :--- |
| iOS Safari 15+ | 	✅ Soporte limitado |
| Android Chrome 58+ | ✅ Soporte limitado |
| Dispositivos de gama baja | ❌ Pueden no funcionar |
	
**⚠️ Nota**: Unity WebGL no está oficialmente soportado en móviles, pero funciona en dispositivos de gama alta.

## 11.3. Limitaciones Técnicas

| Limitación | Impacto |
| :--- | :--- |
| Sin WebGL 1 | Solo WebGL 2 (desde Unity 2022.1) |
| Memoria máxima | 4096 MB |
| Sin multihilo completo | C# jobs en main thread |
| Sin acceso a hardware | No Bluetooth, NFC, etc. |

## 12. Checklist Antes de Subir

**✅ Funcionalidad**

□ El juego carga en el navegador.

□ Los controles funcionan (teclado/ratón/táctil).

□ No hay errores en la consola (F12).

□ El juego se puede completar.

□ El reinicio funciona.

**✅ Optimización**

□ Build size < 500 MB.

□ Draw calls < 100 (móvil).

□ Texturas comprimidas (ASTC/ETC2).

□ Audio comprimido (OGG/MP3).

□ Managed Stripping Level: High.

□ Development Build desactivado.

**✅ Empaquetado**

□ index.html en la raíz del ZIP.

□ Sin archivos innecesarios.

□ ZIP < 500 MB.

□ Probado localmente con Live Server.

**✅ Contenido**

□ Clasificación por edad correcta.

□ Advertencias añadidas (si +12 o superior).

□ Sin contenido prohibido.

□ Descripción atractiva.

□ Imagen de portada (1280x720).

**✅ Legal**

□ Eres el creador original.

□ Assets con licencia adecuada.

□ No violas derechos de autor.

## 13. Errores Comunes

## 13.1. "El juego no carga"

**Causas**:

• `index.html` no está en la raíz.

• Falta `Build/` o `TemplateData/`.

• Servidor no configurado (file://).

**Solución**:

1. Verifica la estructura del ZIP.

2. Usa Live Server.

3. Revisa la consola (F12).

## 13.2. "El juego va lento"

**Causas**:

• Draw calls altos.

• Texturas muy grandes.

• Lógica pesada en Update.

**Solución**:

• Batching, instancing.

• Reducir texturas a 1024.

• Mover lógica a corrutinas o eventos.

## 13.3. "Error de memoria en móvil"

**Causas**:

• Maximum Memory Size muy alto.

• Texturas 4K.

• Muchos assets cargados.

**Solución**:

• Reducir Maximum Memory Size a 256 MB.

• Usar Addressables.

• Object pooling.

## 13.4. "El audio no se reproduce"

**Causas**:

• Autoplay bloqueado por el navegador.

• Formato no soportado.

**Solución**:
1. Iniciar audio después de interacción del usuario.

2. Usar OGG o MP3.

## 13.5. "Build demasiado grande"

**Causas**:

• Development Build activado.

• Managed Stripping desactivado.

• Assets sin comprimir.

**Solución**:

• Desactivar Development Build.

• Managed Stripping Level: High.

• Comprimir texturas y audio.

## 13.6. "El juego no funciona en Safari"

**Causas**:

• Safari < 15 no soporta WebGL 2.

• IndexedDB bloqueado en iframes.

**Solución**:

1. Requerir Safari 15+.

2. Evitar iframes (o configurar correctamente).

## 14. Recursos de Aprendizaje

## 14.1. Documentación Oficial

| Recurso | Enlace |
| :--- | :--- |
| Unity WebGL | docs.unity3d.com/Manual/webgl.html |
| Optimización Web | docs.unity3d.com/Manual/web-optimization.html |
| Player Settings | docs.unity3d.com/Manual/class-PlayerSettingsWebGL.html |

## 14.2. Assets Gratuitos

| Recurso | Descripción |
| :--- | :--- |
| Unity Asset Store | Assets gratuitos y de pago |
| Kenney.nl | Assets de alta calidad |
| OpenGameArt.org | Assets de la comunidad |

## 14.3. Comunidad

| Recurso | Descripción |
| :--- | :--- |
| Discord de Epic Things | Canal `#ayuda-programacion` |
| Unity Forum | Foro oficial |
| r/Unity3D | Comunidad en Reddit |

## 15. Preguntas Frecuentes

**¿Necesito Unity Pro?**

**Respuesta**: No. La versión Personal es suficiente para publicar en Epic Things.

**¿Puedo usar Unity 6?**

**Respuesta**: Sí, pero verifica que el módulo WebGL esté instalado y que el proyecto sea compatible.

**¿Cuánto tarda la revisión?**

**Respuesta**: 24-48 horas. En Sandbox es instantánea.

**¿Puedo actualizar mi juego después de publicarlo?**

**Respuesta**: Sí. Sube una nueva versión del ZIP. Pasa por revisión nuevamente.

**¿Qué pasa si mi build pesa más de 500 MB?**

**Respuesta**: No será aceptado. Debes optimizar:

• Reducir texturas.

• Comprimir audio.

• Managed Stripping High.

• Eliminar assets no usados.

**¿Mi juego funcionará en móvil?**

**Respuesta**: Depende del dispositivo. Unity WebGL no está oficialmente soportado en móviles, pero funciona en gama alta. Prueba en Safari 15+ (iOS) y Chrome 58+ (Android).

**¿Puedo usar WebGL 1?**

**Respuesta**: No. Unity 2022.1+ solo soporta WebGL 2. Asegúrate de que tu navegador lo soporte.

**¿Cómo añado la clasificación por edad en Unity?**

**Respuesta**: No se implementa en el juego (la plataforma lo gestiona). Debes declararla al subir el juego y añadir advertencias en la descripción.

**¿Puedo usar música con copyright?**

**Respuesta**: No. Usa música libre de regalías o creada por ti.

## 16. Contacto

Soporte para Desarrolladores

| Canal | Información |
| :--- | :--- |
| Email | `parraalavaro418@gmail.com` |
| Discord | Canal `#ayuda-programacion` |
| Documentación | `API Reference` |

**Recursos Adicionales**

• 📖 Primeros Pasos como Creador

• 📖 Subir un Juego

• 📖 Crear Juego HTML5

• 📖 Integración con la API

• 📖 Regalías

📝 Historial de Cambios	

| Fecha | Versión | Cambio |
| :--- | :--- | :--- |
| 2026-09-01 | 1.0 | Creación inicial |

**Hecho con ❤️ desde Puerto Cabello, Venezuela**

"El mejor motor es el que dominas. El mejor juego es el que terminas."
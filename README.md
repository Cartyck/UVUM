# Universal Virtual Upscaler Monitor (UVUM)

**Real-time GPU supersampling through a virtual display.**

**Higher rendering resolutions. Better image quality. No game injection. No changes to your primary monitor configuration.**

**Version 0.10.0 · Windows x64 · C++17 · HLSL · Direct3D 11**

---

# 🇬🇧 English

## What is UVUM?

UVUM (Universal Virtual Upscaler Monitor) is a Windows application designed to let games render at resolutions higher than the physical resolution of your monitor, then capture and downsample the image to your native display resolution.

Its main purpose is to provide **GPU-based supersampling (SSAA)** through a dedicated virtual display.

For example, users with a standard 1920×1080 Full HD monitor can run games at 3840×2160 (4K). The game renders four times as many pixels as native 1080p, and UVUM captures and downsamples that image to the monitor's resolution.

This technique uses the GPU's additional rendering power to improve image quality, potentially reducing aliasing and producing cleaner details.

**UVUM allows you to benefit from high-resolution rendering without changing your primary monitor's native resolution or configuration.**

## Why UVUM?

Rendering games above a monitor's native resolution is not a new concept. There are already technologies such as NVIDIA DSR and custom resolution modes that allow this.

UVUM takes a different approach.

Instead of requiring users to configure higher resolutions on their primary display, UVUM creates a separate virtual display through Virtual Display Driver (VDD).

The game runs on this virtual display, while UVUM captures its content and presents the downsampled image on the physical monitor.

### What makes UVUM different?

- **Independent virtual display:** Your primary monitor remains at its normal native resolution. No need to change its resolution or configure custom display modes.
- **No game injection:** UVUM does not inject code into games or require game modifications.
- **Built-in image processing:** Apply sharpening, color vibrance and configurable downsampling filters.
- **Custom Frame Generation:** Includes UVUM's own frame generation implementation.
- **Automatic FG adaptation:** Adjusts frame generation quality according to GPU utilization and image presentation time.
- **Camera prediction:** Uses gamepad joystick input to predict camera position as part of its frame generation functionality.
- **Convenient workflow:** A separate monitor is recommended for operating UVUM while playing.

The goal is to combine supersampling, image processing and frame generation in a separate application, without modifying the game itself.

## How does it work?

1. UVUM creates and controls a virtual display using Virtual Display Driver (VDD).
2. The game runs on that virtual display at a higher resolution.
3. UVUM captures the virtual display using Direct3D 11 Desktop Duplication.
4. The captured image is downsampled using configurable HLSL filters.
5. Additional image processing is applied.
6. UVUM presents the final image on the physical monitor.

**Example: 4K rendering → 1080p display**

3840×2160 contains four times as many pixels as 1920×1080. Downsampling this higher-resolution image provides a form of GPU-based supersampling.

## Screenshots and visual comparisons

Real screenshots and comparisons will be published here to demonstrate UVUM's operation and image quality.

Planned comparisons:

- Native 1920×1080 vs 3840×2160 → 1920×1080.
- 2560×1440 → 1920×1080.
- Different downsampling filters.
- Antialiasing and sharpening configurations.
- Real gameplay demonstrations.

*All comparisons should use the same game scene and comparable settings.*
## Image comparison

| Native 1920×1080 | UVUM — 4K → 1080p |
|:---:|:---:|
| ![Native 1920x1080](images/old-test/pantalla%201%201080p.PNG) | ![UVUM 4K downscaled to 1080p](images/old-test/pantalla%201%204K.PNG) |
| Original resolution | 4K supersampling |
## Features

### Virtual display and rendering

- Virtual display creation and control through Virtual Display Driver.
- Direct3D 11 Desktop Duplication.
- High-resolution rendering up to 4K and potentially beyond, depending on hardware and configuration.
- Physical mouse and keyboard control.
- Windowed and fullscreen presentation.
- No game injection or modifications.

### Image processing

- Point.
- Bilinear.
- Box.
- Catmull-Rom.
- Mitchell.
- Lanczos 2.
- CMAA2 2.3 (Intel).
- FXAA 3.11.
- CAS-style adaptive sharpening.
- Color vibrance adjustment.

### Custom Frame Generation (FG)

UVUM includes its own frame generation implementation.

**Automatic FG mode:**

- An adaptive algorithm adjusts frame generation quality according to GPU utilization.
- It also considers the time required to present the image.
- Adaptation operates only while Frame Generation is enabled.
- Its purpose is to adapt frame generation quality to available GPU performance and presentation timing.

**Joystick-based camera prediction:**

- Uses gamepad joystick input to predict camera position.
- Designed to improve camera movement prediction as part of UVUM's frame generation functionality.

UVUM's Frame Generation is its own implementation. It is not NVIDIA DLSS Frame Generation, AMD FSR Frame Generation or Intel XeSS Frame Generation.

### Low-latency presentation

- Flip Model presentation.
- ALLOW_TEARING support.
- Presentation queue latency set to 1.
- Optional V-Sync.
- Configurable frame limits.

## Recommended setup: Use a secondary monitor

**Using UVUM with a secondary monitor is recommended.**

A second monitor is not mandatory, but it makes controlling UVUM much more convenient.

You can keep the UVUM interface visible on your secondary monitor while the game runs on the virtual display and the final image is presented on your primary monitor.

This makes it easier to control the application and adjust its settings without constantly switching away from the game.

## Keyboard shortcuts

| Shortcut | Action |
|---|---|
| Ctrl + Alt + E | Enter virtual display |
| Ctrl + Alt + Q | Exit virtual display |
| Ctrl + Alt + F | Toggle fullscreen |

## Requirements

- Windows 10 (version 2004 or later recommended).
- Windows 11: compatibility not yet fully tested.
- 64-bit operating system.
- Direct3D 11 compatible GPU (NVIDIA, AMD or Intel).
- Virtual Display Driver installed and configured.
- Administrator permissions.

**Tested hardware:** NVIDIA RTX 3070.

## Dependencies

### Virtual Display Driver (VDD)

UVUM requires Virtual Display Driver to create its virtual display.

**VDD.Control version: `25.7.23`**

Original project:

https://github.com/VirtualDrivers/Virtual-Display-Driver

VDD is an independent third-party project and is not developed by the UVUM author.

Please visit its original repository for downloads, documentation and licensing information.

## Development transparency: Built with free AI tools

UVUM was developed entirely using Large Language Models (LLMs), specifically the free versions of:

- Claude (Anthropic).
- Grok (xAI).
- ChatGPT (OpenAI).

**All three were used through their free versions. No paid AI subscriptions were used for the development of this project.**

The project brings together AI-assisted C++17 development, HLSL shaders, Windows APIs and Direct3D 11.

This is also an experiment in how far free AI tools can be pushed to create a functional, modular Windows graphics application.

## Download

**UVUM v0.10.0 — Direct3D 11**

Main executable: `uvum_dx11.exe`

Visit the [Releases](../../releases) section to download the available version.

`uvum_dx12.exe` is currently a skeleton intended for future development and is not the main working version.

---

# 🇪🇸 Español

## ¿Qué es UVUM?

UVUM (Universal Virtual Upscaler Monitor) es una aplicación para Windows diseñada para permitir que los juegos se ejecuten a resoluciones superiores a la resolución física del monitor, capturando posteriormente la imagen y reduciéndola a la resolución nativa de la pantalla.

Su objetivo principal es ofrecer **supermuestreo mediante GPU (SSAA)** a través de una pantalla virtual independiente.

Por ejemplo, un usuario con un monitor Full HD de 1920×1080 puede ejecutar sus juegos a 3840×2160 (4K). El juego renderiza cuatro veces más píxeles que en 1080p nativo y UVUM captura y reduce esa imagen a la resolución del monitor.

Esta técnica aprovecha la potencia adicional de la GPU para mejorar la calidad de imagen, reducir potencialmente el aliasing y conseguir detalles más limpios.

**UVUM permite aprovechar el renderizado a alta resolución sin cambiar la resolución nativa ni la configuración del monitor principal.**

## ¿Por qué UVUM?

Renderizar juegos por encima de la resolución nativa del monitor no es algo nuevo. Ya existen tecnologías como NVIDIA DSR y los modos de resolución personalizada que permiten hacerlo.

UVUM propone un enfoque diferente.

En lugar de necesitar que el usuario configure resoluciones superiores en su pantalla principal, UVUM crea una pantalla virtual independiente mediante Virtual Display Driver (VDD).

El juego se ejecuta en esa pantalla virtual, mientras UVUM captura su contenido y presenta la imagen reducida en el monitor físico.

### ¿Qué diferencia a UVUM?

- **Pantalla virtual independiente:** el monitor principal permanece en su resolución nativa habitual. No es necesario cambiar su resolución ni configurar modos de pantalla personalizados.
- **Sin inyección en los juegos:** UVUM no inyecta código en los juegos ni necesita modificarlos.
- **Procesamiento de imagen integrado:** permite aplicar nitidez, ajustar la vibrance y utilizar diferentes filtros de reducción.
- **Generación de frames propia:** incorpora su propia implementación de generación de frames.
- **Adaptación automática de FG:** ajusta la calidad de la generación de frames según el uso de GPU y el tiempo de presentación de la imagen.
- **Predicción de cámara:** utiliza la entrada del joystick del mando para predecir la posición de la cámara como parte de su sistema de generación de frames.
- **Mayor comodidad de uso:** se recomienda una segunda pantalla para manejar UVUM mientras se juega.

El objetivo es reunir supermuestreo, procesamiento de imagen y generación de frames en una aplicación independiente, sin modificar el propio juego.

## ¿Cómo funciona?

1. UVUM crea y controla una pantalla virtual mediante Virtual Display Driver (VDD).
2. El juego se ejecuta en esa pantalla virtual a una resolución superior.
3. UVUM captura su contenido mediante Direct3D 11 Desktop Duplication.
4. La imagen capturada se reduce mediante filtros HLSL configurables.
5. Se aplica el procesamiento adicional de imagen.
6. UVUM presenta la imagen final en el monitor físico.

**Ejemplo: renderizado 4K → pantalla 1080p**

3840×2160 contiene cuatro veces más píxeles que 1920×1080. Reducir esta imagen proporciona una forma de supermuestreo mediante GPU.

## Capturas y comparativas visuales

Aquí se publicarán capturas reales y comparativas para mostrar el funcionamiento de UVUM y sus resultados en calidad de imagen.

Comparativas previstas:

- 1920×1080 nativo frente a 3840×2160 → 1920×1080.
- 2560×1440 → 1920×1080.
- Diferentes filtros de reducción.
- Configuraciones de antialiasing y nitidez.
- Demostraciones en juegos reales.
## Comparativa visual

| Native 1920×1080 | UVUM — 4K → 1080p |
|:---:|:---:|
| ![Native 1920x1080](images/old-test/pantalla%201%201080p.PNG) | ![UVUM 4K downscaled to 1080p](images/old-test/pantalla%201%204K.PNG) |
| Original resolution | 4K supersampling |
*Las comparativas utilizarán la misma escena del juego y configuraciones equivalentes.*

## Características

### Pantalla virtual y renderizado

- Creación y control de pantalla virtual mediante Virtual Display Driver.
- Captura mediante Direct3D 11 Desktop Duplication.
- Renderizado a alta resolución: hasta 4K y potencialmente más, dependiendo del hardware y la configuración.
- Control mediante ratón y teclado físicos.
- Presentación en ventana y pantalla completa.
- Sin inyección de código ni modificaciones de los juegos.

### Procesamiento de imagen

- Point.
- Bilinear.
- Box.
- Catmull-Rom.
- Mitchell.
- Lanczos 2.
- CMAA2 2.3 (Intel).
- FXAA 3.11.
- Nitidez adaptativa estilo CAS.
- Ajuste de vibrance y color.

### Generación de frames propia (FG)

UVUM incorpora su propia implementación de generación de frames.

**Modo FG automático:**

- Un algoritmo adaptativo modifica la calidad de la generación de frames según el uso de la GPU.
- También tiene en cuenta el tiempo que tarda en presentarse la imagen.
- El ajuste funciona exclusivamente cuando la generación de frames está activada.
- Su objetivo es adaptar la calidad de la generación de frames a la capacidad disponible de la GPU y a los tiempos de presentación.

**Predicción de cámara mediante joystick:**

- Utiliza la entrada del joystick de un mando para predecir la posición de la cámara.
- Está diseñada para mejorar la predicción del movimiento de cámara como parte de la funcionalidad de generación de frames de UVUM.

La generación de frames de UVUM es una implementación propia y no debe confundirse con NVIDIA DLSS Frame Generation, AMD FSR Frame Generation o Intel XeSS Frame Generation.

### Presentación de baja latencia

- Presentación Flip Model.
- Compatibilidad con ALLOW_TEARING.
- Latencia de cola de presentación configurada a 1.
- V-Sync opcional.
- Límites de FPS configurables.

## Configuración recomendada: utilizar un segundo monitor

**Se recomienda utilizar UVUM con una pantalla secundaria.**

Aunque no es obligatorio, disponer de un segundo monitor facilita considerablemente el manejo del programa.

Puedes mantener la interfaz de UVUM visible en la pantalla secundaria mientras el juego se ejecuta en la pantalla virtual y la imagen final se muestra en tu monitor principal.

Esto permite controlar la aplicación y modificar sus ajustes sin tener que salir constantemente del juego.

## Atajos de teclado

| Atajo | Función |
|---|---|
| Ctrl + Alt + E | Entrar en la pantalla virtual |
| Ctrl + Alt + Q | Salir de la pantalla virtual |
| Ctrl + Alt + F | Activar/desactivar pantalla completa |

## Requisitos

- Windows 10 (versión 2004 o posterior recomendada).
- Windows 11: compatibilidad todavía no probada completamente.
- Sistema operativo de 64 bits.
- GPU compatible con Direct3D 11 (NVIDIA, AMD o Intel).
- Virtual Display Driver instalado y configurado.
- Permisos de administrador.

**Hardware probado:** NVIDIA RTX 3070.

## Dependencias

### Virtual Display Driver (VDD)

UVUM necesita Virtual Display Driver para crear su pantalla virtual.

**Versión de VDD.Control: `25.7.23`**

Proyecto original:

https://github.com/VirtualDrivers/Virtual-Display-Driver

VDD es un proyecto independiente de terceros y no está desarrollado por el autor de UVUM.

Consulta su repositorio original para descargas, documentación y condiciones de licencia.

## Transparencia del desarrollo: creado con herramientas de IA gratuitas

UVUM se ha desarrollado íntegramente utilizando modelos de lenguaje (LLMs), concretamente las versiones gratuitas de:

- Claude (Anthropic).
- Grok (xAI).
- ChatGPT (OpenAI).

**Los tres se han utilizado mediante sus versiones gratuitas. No se han utilizado suscripciones de IA de pago para desarrollar este proyecto.**

El proyecto reúne desarrollo asistido por IA en C++17, shaders HLSL, API de Windows y Direct3D 11.

También es un experimento sobre hasta dónde se puede llegar utilizando herramientas gratuitas de inteligencia artificial para crear una aplicación gráfica funcional y modular para Windows.

## Descarga

**UVUM v0.10.0 — Direct3D 11**

Ejecutable principal: `uvum_dx11.exe`

Visita la sección [Releases](../../releases) para descargar la versión disponible.

`uvum_dx12.exe` es actualmente un esqueleto destinado al desarrollo futuro y no es la versión funcional principal.

---

*README note: This README was written by an LLM because the author is too lazy to write the documentation himself.*

*Nota: Este README ha sido escrito por un LLM porque el autor es demasiado vago para escribir la documentación él mismo.*

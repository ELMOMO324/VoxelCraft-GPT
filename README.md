# Voxelcraft

Juego voxel para navegador implementado en un único `index.html`, con HTML, CSS y JavaScript integrados.

## Ejecutar

Sirve esta carpeta con un servidor HTTP local, por ejemplo `python -m http.server 8000`, y abre http://localhost:8000. Necesita Internet para cargar Three.js, simplex-noise y dat.GUI desde CDN.

## Controles

- WASD: moverse; Ctrl: correr; Shift: agacharse.
- Espacio: saltar; doble Espacio: alternar vuelo. En vuelo, Espacio asciende y Shift desciende.
- Clic izquierdo sostenido: romper; clic derecho: colocar o usar una mesa de trabajo.
- 1–9 o rueda: seleccionar; E: inventario; Esc: pausa; F3: métricas.
- Sin captura de ratón: botón central y arrastrar, o flechas, para mirar.

## Funciones

Chunks 16×256×16 en Uint8Array, greedy meshing con AO por vértice, generación reproducible por semilla, biomas, cuevas, árboles, minerales, streaming, colisiones AABB por barrido, texturas procedurales, inventario y recetas 2×2/3×3, herramientas, criaturas, día/noche, audio sintético y guardado local.

El guardado pertenece al navegador y al origen utilizados. Para recuperar una partida usa la misma dirección y semilla.

## Validación

25 pruebas aprobadas: núcleo voxel, colisiones, recetas, geometría y animaciones por perfil, dimensiones de los buffers y liberación de recursos. Además se comprobaron los seis perfiles en navegador, la salida 2560×1440 y la recuperación de la configuración gráfica. La tasa de FPS depende del dispositivo, de los efectos elegidos y de la distancia de renderizado.

## Gráficos · versión 1.1

Abre **Pausa → Gráficos y resolución** (también disponible desde el inicio), elige un perfil y pulsa **Aplicar gráficos**. Los ajustes se conservan en este navegador.

| Perfil | Cambios reales |
| --- | --- |
| Rendimiento | Texturas de 4 px simplificadas, modelos mínimos, animación visual a 15 Hz, sin sombras dinámicas ni postprocesado. Conserva las físicas, las entidades y el mundo. |
| Balanceado · predeterminado | Texturas voxel de 16 px, iluminación difusa y sombras de 1024 px. |
| Potato Shaders | Iluminación especular Phong, sombras de 1536 px, hojas al viento, nubes procedurales, FXAA y rayos solares ocluidos por la profundidad de la escena. |
| Nova-Shaders | Materiales PBR, relieve por perturbación de normales, texturas de 32 px, entorno filtrado, sombras de 2048 px, SSAO de 12 muestras, pasto 3D animado, anatomía y rostros 3D con articulaciones. |
| Golden Shaders | Texturas de 64 px, sombras de 3072 px, SSAO de 20 muestras, reflejos del mundo mediante sonda cúbica local de 128 px, cristal físico con refracción, bloom HDR y pelaje geométrico. |
| 2K-Shaders | Texturas de 128 px, relieve por paralaje de 10 capas, sombras de 4096 px, SSAO de 32 muestras a resolución completa, reflejos locales de 256 px más frecuentes, bloom multiescala y modelos de mayor densidad. |

**La distancia de chunks no cambia con ningún perfil ni con la resolución.** Solo el usuario la modifica con «Radio de chunks».

La resolución interna se selecciona independientemente del perfil:

- **720p: 1280×720**, predeterminada.
- **2K/QHD: 2560×1440**, cuatro veces más píxeles.

«2K-Shaders» es el nombre del perfil más pesado; puede usarse a 720p. También se puede usar 2K/QHD con Rendimiento o cualquier otro perfil. El framebuffer utiliza esas dimensiones reales, independientemente de la densidad de pantalla; la imagen mantiene proporción 16:9 con bandas cuando hace falta.

Golden y 2K-Shaders requieren más capacidad de GPU y memoria. Las sombras respetan el máximo de textura del dispositivo, y los efectos usan una salida LDR compatible si no hay render targets HDR. Los reflejos locales se actualizan periódicamente; su resolución y frecuencia dependen del perfil. Los menús reducen su frecuencia de dibujo mientras el mundo está en pausa.

## Bibliotecas

Three.js 0.160.1 (MIT), simplex-noise 4.0.3 (MIT) y dat.GUI 0.7.9 (Apache-2.0), cargadas desde CDN. No requiere imágenes externas ni una biblioteca física.

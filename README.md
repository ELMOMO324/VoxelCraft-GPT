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

15 pruebas del núcleo aprobadas, además de comprobaciones en navegador de movimiento, vuelo, colocación, fabricación 2×2/3×3 y recuperación del guardado. La tasa de FPS depende del dispositivo y de la distancia de renderizado.

## Bibliotecas

Three.js 0.160.1 (MIT), simplex-noise 4.0.3 (MIT) y dat.GUI 0.7.9 (Apache-2.0), cargadas desde CDN. No requiere imágenes externas ni una biblioteca física.

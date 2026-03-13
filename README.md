# Carrusel de imagen a MP4 — Generador de vídeo

Herramienta web para generar vídeos de señalización digital compatibles con el
**Sharp/NEC MPi4 Kit (Video Looper)** desde imágenes JPG/PNG.

## Características

- Sube imágenes JPG/PNG de cualquier tamaño y orientación
- Las imágenes se adaptan automáticamente a la resolución elegida (fit-contain + bandas negras)
- 7 presets de resolución + resolución personalizada
- Reordena imágenes arrastrando con el ratón
- Configura los segundos por imagen (1–30s)
- Genera un carrusel MP4 H264 en bucle infinito
  - Codec: H264 / MPEG-4 AVC · yuv420p
  - Preset: ultrafast · CRF 23
  - 1 fps (cada frame = 1 segundo de imagen)
- Cancelación de generación en cualquier momento
- Descarga el MP4 listo para copiar al USB
- Todo el procesamiento ocurre en el navegador (ffmpeg.wasm) — sin servidor

## Despliegue en Vercel

### Opción 1 — Desde GitHub (recomendado)

1. Sube esta carpeta a un repositorio GitHub
2. Ve a [vercel.com](https://vercel.com) → New Project
3. Importa el repositorio
4. Framework: **Other** (sin framework)
5. Root directory: dejar en `/`
6. Deploy

### Opción 2 — Vercel CLI

```bash
npm i -g vercel
cd cine-signage
vercel
```

## Notas importantes

El archivo `vercel.json` incluye las cabeceras HTTP necesarias para que
`ffmpeg.wasm` funcione correctamente (`Cross-Origin-Opener-Policy` y
`Cross-Origin-Embedder-Policy`). Sin estas cabeceras el generador no funcionará.

## Uso para el personal del cine

1. Abrir la URL del despliegue en cualquier navegador
2. Arrastrar las imágenes JPG de los carteles (en vertical, 1080×1920)
3. Ordenarlas arrastrando si es necesario
4. Pulsar **Generar vídeo MP4**
5. Esperar ~30-60 segundos
6. Descargar el archivo `carousel.mp4`
7. Copiar al USB (FAT32)
8. Insertar el USB en el totem → el Video Looper lo reproduce automáticamente

## Especificaciones de las imágenes

| Parámetro | Valor |
|-----------|-------|
| Formato | JPG o PNG |
| Orientación | Vertical (portrait) |
| Resolución recomendada | 1080 × 1920 px |
| Las imágenes horizontales | Se adaptan con bandas negras automáticamente |

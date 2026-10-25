# Twisted Metal (PS1) en el navegador

Reproductor para jugar **Twisted Metal de PlayStation 1** en cualquier navegador moderno, a pantalla
completa y con los filtros de EmulatorJS (escalado, CRT, remapeo de mandos).

**No incluye el juego ni la BIOS.** Los cargas tú desde tu propio equipo: la página abre los ficheros
localmente y no los sube a ningún servidor.

## Jugar

1. Abre la página (GitHub Pages o el `index.html` en local).
2. Elige el **disco**: `.iso`, `.bin` + `.cue`, `.chd`, `.zip` o `.pbp`.
3. Elige la **BIOS** de PS1 (`scph1001.bin`, `scph5501.bin`, `scph7001.bin`…).
4. Pulsa **Jugar** y luego haz clic en la pantalla cuando aparezca el aviso (el navegador exige un
   gesto de usuario para arrancar el audio).

Los mandos también se pueden soltar encima de la página.

## Qué necesitas

- El disco del juego, de tu propia copia.
- Una BIOS de PS1 volcada de tu propia consola.

Consejos de formato, por lo que nos costó a nosotros:

- **`.iso` es lo que mejor funciona.** Un `.bin` crudo de PlayStation es Mode2/2352 y sin su `.cue`
  el núcleo no sabe el tamaño de sector: arranca en negro.
- Si tienes `.bin` + `.cue`, conviértelo a ISO quitando los 24 bytes de cabecera de cada sector de
  2352 y quedándote los 2048 de datos, hasta el LBA donde empieza la pista de audio (lo dice el
  `.cue`). Sale un fichero único que el núcleo lee a la primera. Se pierde la música de CD.
- **`.chd`** conserva las pistas de audio y también lo lee. Es la mejor opción si ya lo tienes.

## Controles

Por defecto en EmulatorJS: flechas para conducir, `Z`/`X` para disparar y acelerar, `Enter` para
pausa. Todo se puede cambiar en el engranaje → *Controles*.

## Cómo está hecho

- [EmulatorJS](https://emulatorjs.org) (núcleo `pcsx_rearmed`) cargado desde su CDN.
- Una sola página estática: no hay servidor, no hay backend, no hay subida de datos.
- Los ficheros se pasan al emulador como `Blob` en memoria (`URL.createObjectURL`).

## Aviso legal

Twisted Metal es una marca de Sony Interactive Entertainment. Este proyecto no está afiliado a Sony
ni distribuye el juego, la BIOS ni ningún material con copyright: sólo el reproductor. Usa tu propia
copia legal. No abras issues pidiendo el juego ni la BIOS.

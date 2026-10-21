## V6.0-dev-v19 — procesar la bandeja ya recibida
- La sincronización también procesa los cambios seguros que ya estaban guardados en la bandeja local de revisiones, aunque el cursor del servidor ya haya avanzado.
- Las entradas marcadas para revisión no se aplican automáticamente; se vuelven a comprobar las operaciones locales pendientes antes de cada aplicación.
- Se incrementa la caché PWA y se sincronizan las versiones visibles.

## V6.0-dev-v19 — procesar la bandeja ya recibida
- La sincronización también procesa los cambios seguros que ya estaban guardados en la bandeja local de revisiones, aunque el cursor del servidor ya haya avanzado.
- Las entradas marcadas para revisión no se aplican automáticamente; se vuelven a comprobar las operaciones locales pendientes antes de cada aplicación.
- Se incrementa la caché PWA y se sincronizan las versiones visibles.

## V6.0-dev-v18 — aplicación segura de cambios remotos
- La sincronización aplica automáticamente snapshots recibidos cuando no hay operaciones locales pendientes para esa entidad.
- Los cambios que coinciden con operaciones locales pendientes o que no pueden aplicarse con seguridad quedan en la bandeja de revisión.
- El resumen informa cambios recibidos, aplicados automáticamente y pendientes de revisión.
- El estado de cuenta distingue entre sesión iniciada y taller configurado para evitar el mensaje engañoso de que no hay vinculación cuando el UUID ya está guardado.
- Se conserva el enfoque local-first; la aplicación remota suprime la generación de nuevas operaciones de salida.
- Se incrementa la caché PWA para distribuir el código actualizado.

## V6.0-dev-v17 — recuperación de estabilidad
- Se recupera el archivo app.js de la versión estable V6.0-dev-v14 (posterior a la corrección de la clave pública de sincronización).
- Se revierte temporalmente la aplicación automática de cambios remotos; se conserva el flujo de sincronización manual y la revisión explícita para reducir riesgos mientras se valida el intercambio entre dispositivos.
- Se incrementa la caché PWA para que los navegadores descarguen el archivo recuperado.
- No se modifican ni eliminan los datos guardados en el dispositivo.

## V6.0-dev-v16 — recuperación de arranque
- Corregido el renderizado de la sección de revisión que contenía un error de sintaxis y bloqueaba la inicialización completa de la aplicación.
- Incrementada la versión de caché de la PWA para que los dispositivos descarguen el JavaScript corregido.
- La sección de revisión muestra un resumen legible de pendientes y conflictos; no modifica ni elimina los datos locales.

# NEXUM Taller — registro de cambios

## V6.0-dev-v15 — sincronización entre dispositivos
- Los cambios remotos se aplican automáticamente cuando no hay operaciones locales pendientes para esa entidad y no hay un diálogo abierto.
- Los conflictos y cambios que no pueden aplicarse de forma segura se conservan en una sección visible de revisión.
- El resumen final distingue operaciones enviadas, cambios recibidos/aplicados, pendientes y casos que requieren revisión.
- Se elimina la confirmación por lote antes de enviar operaciones pendientes; se mantienen los datos locales ante errores.
- Se renueva la caché de la PWA para distribuir los recursos de esta versión.

## V6.0-dev-v14
- Versión anterior; corrección de la clave pública de sincronización.

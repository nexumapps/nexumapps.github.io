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

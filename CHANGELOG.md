# NEXUM Taller — registro de cambios

## V6.0-dev-v15 — sincronización entre dispositivos
- Los cambios remotos se aplican automáticamente cuando no hay operaciones locales pendientes para esa entidad y no hay un diálogo abierto.
- Los conflictos y cambios que no pueden aplicarse de forma segura se conservan en una sección visible de revisión.
- El resumen final distingue operaciones enviadas, cambios recibidos/aplicados, pendientes y casos que requieren revisión.
- Se elimina la confirmación por lote antes de enviar operaciones pendientes; se mantienen los datos locales ante errores.
- Se renueva la caché de la PWA para distribuir los recursos de esta versión.

## V6.0-dev-v14
- Versión anterior; corrección de la clave pública de sincronización.

## V6.0-dev-v37 — contraseña temporal de 8 a 128 caracteres
- El formulario de creación de usuarios acepta contraseñas temporales de 8–128 caracteres.
- La función de administración de Supabase aplica el mismo rango, sin cambiar el requisito de cambiarla en el primer acceso.

## V6.0-dev-v36 — conservar el estado final
- «Sincronización finalizada/completada» se clasifica como éxito verde, siempre que no haya errores ni conflictos.
- La actualización del estado de sesión no reemplaza el resultado persistente de la última sincronización.

## V6.0-dev-v35 — estado persistente del indicador de sincronización
- El indicador superior conserva verde tras una sincronización completada sin conflictos ni revisión pendiente.
- Rojo solo para errores o conflictos/revisiones reales; amarillo para sincronización en curso o cambios pendientes.
- Evita que el texto «pendientes: 0» sea interpretado erróneamente como estado de error.

## V6.0-dev-v34 — indicadores visibles en el aviso emergente
- Se muestran etiquetas explícitas «✅ TODO CORRECTO» o «❌ ERROR / REVISIÓN» en el resumen emergente, además de los símbolos de estado.
- Se incrementa la clave de caché de la PWA para forzar que los dispositivos descarguen el archivo actualizado.

## V6.0-dev-v33 — resolución de conflictos en una sola acción
- «Conservar versión local» prepara una operación nueva con la versión remota actual como base y ejecuta la sincronización inmediatamente; no requiere un segundo reintento manual.
- Para colisiones de identificadores se reutiliza la resolución específica existente; si no puede hacerse con seguridad, se informa claramente y se conservan los datos locales.
- Los estados y errores de sincronización incorporan indicadores visuales: 🟢 para éxito y 🔴 para error, conflicto o revisión pendiente.
- Se conserva el histórico y las tasas individuales de tickets/ECN; no se borran datos locales.
- Se alinean app.js, index.html, version.txt y la caché de la PWA.

## V6.0-dev-v32 — confirmar y publicar la versión local elegida
- La resolución local crea una sola operación nueva con la versión remota revisada como base, retirando solo las operaciones conflictivas previas de la misma entidad.
- La acción espera la sincronización y muestra el resultado; no se limita a posponer el conflicto.
- Para la tasa compartida, publica el valor local vigente con la identidad canónica de la nube; no modifica tasas históricas de tickets ni ECN.

## V6.0-dev-v31 — publicar la versión local elegida
- «Conservar versión local» genera un identificador de operación nuevo para evitar la respuesta idempotente de la operación rechazada.
- Actualiza la base a la versión remota revisada y lanza la sincronización inmediatamente, también para la tasa compartida.
- Los registros históricos y sus tasas individuales no se reescriben.

## V6.0-dev-v30 — comparación antes de resolver conflictos
- La revisión de sincronización muestra los campos diferentes entre la copia local y la remota; para la tasa, muestra explícitamente ambos valores CUP/USD.
- Los cambios con operaciones locales pendientes ofrecen decisiones separadas: conservar la versión remota o conservar la local y reintentar con la versión remota como base.
- Se conservan los datos de otras entidades y las tasas históricas individuales; se añade presentación adaptable a móviles.

## V6.0-dev-v29 — respuestas inesperadas recuperables
- Una respuesta de sincronización no reconocida deja la operación afectada en conflicto/revisión, conserva el detalle y permite continuar con operaciones independientes.
- Se mantiene la cola local; no se confirma una operación que el servidor no haya aceptado.
- Se actualiza la versión visible y la caché de la PWA.

## V6.0-dev-v28 — resolución recuperable de colisiones de identificadores
- Supabase detecta `legacy_id` duplicados antes de escribir y devuelve un conflicto estructurado en lugar de abortar la sincronización.
- Los tickets y movimientos ECN distintos con el mismo ID visible conservan ambos registros; el entrante recibe un ID alternativo y sus operaciones pendientes se actualizan para reintento.
- Si la colisión corresponde a la misma tasa compartida, el cliente reancla la operación a la identidad canónica y reintenta con la versión remota actual.
- Los conflictos que no se pueden resolver con seguridad quedan en revisión; las demás operaciones continúan. No se borran datos locales ni se reescriben tasas históricas.
- Se alinea la versión visible y la caché de la PWA.

## V6.0-dev-v27 — identidad común para la tasa de cambio
- Corrige la causa de la falta de sincronización bidireccional: cada navegador podía crear un identificador distinto para la misma tasa compartida.
- Todos los dispositivos usan el identificador estable del ajuste de tasa ya existente en Supabase, y actualizan el registro compartido en lugar de crear otro independiente.
- La tasa remota confirmada permanece en el mismo registro y su versión se actualiza al sincronizar.

## V6.0-dev-v26 — corrección del salto literal y carga de tasa compartida
- Elimina el texto literal \\n que quedó en el HTML antes de la cabecera principal.
- La tasa compartida confirmada localmente se hidrata al iniciar la app, evitando que una tasa local antigua vuelva a prevalecer al abrir Configuración.
- Se actualizan la versión de la aplicación, la hoja de estilos y la caché de la PWA.

## V6.0-dev-v25 — confirmación de versión de tasa sincronizada
- Corrige la actualización local de la versión remota de la tasa de cambio después de que Supabase confirma su envío, para evitar que el siguiente cambio reutilice una versión obsoleta.
- Actualiza la versión de la hoja de estilos para invalidar la copia anterior en el navegador.

## V6.0-dev-v24 — sincronización de tasa monetaria y acceso
- La tasa de cambio guardada en Configuración se registra como entidad compartida y se sincroniza mediante la cola existente; los demás dispositivos aplican el valor remoto.
- Se corrige el salto de línea literal antes del contenido principal y se elimina el botón redundante «Cambiar cuenta»; «Cerrar sesión» permite iniciar otra cuenta.
- Se alinean la versión de la aplicación, la página, version.txt y la caché de la PWA.

## V6.0-dev-v23 — corrección visual de la pantalla de acceso
- Corrige el salto de línea literal que aparecía entre el acceso y la aplicación.
- Fuerza las reglas de bloqueo de contenido y visibilidad del formulario de acceso, y limita el tamaño del logotipo en móvil.
- Versiona la hoja de estilos en la URL para evitar que el navegador reutilice una copia antigua de la PWA.

## V6.0-dev-v22 — inicialización de sesión para sincronización
- Corrige la actualización inicial del estado de sincronización cuando una sesión temporal se recupera desde sessionStorage al recargar la PWA.
- La pantalla de acceso, la persistencia opcional y la recuperación por usuario/correo de V21 se mantienen.
- Se incrementa la versión visible y la caché para que los dispositivos reciban la corrección.

## V6.0-dev-v21 — acceso protegido y recuperación de contraseña
- La PWA oculta navegación y contenido del taller hasta confirmar una sesión válida; si la sesión caduca o se cierra, vuelve a la pantalla de acceso.
- Se añade opción de sesión temporal (sessionStorage) o persistente en el dispositivo (localStorage), además de cambiar de cuenta y cerrar sesión.
- Se añade recuperación por usuario o correo y formulario para establecer una nueva contraseña desde el enlace recibido.
- Se conservan tickets, fotos, movimientos, configuración y operaciones pendientes al cerrar sesión; no se borran datos locales.
- Se incrementa la versión visible y la caché de la PWA.

## V6.0-dev-v20 — sincronización completa en una pulsación
- La acción de sincronizar coordina hasta cuatro ciclos de envío y recepción en una sola ejecución, con parada tras dos ciclos tranquilos consecutivos.
- Se muestra un único resumen final; se elimina la confirmación repetitiva antes de enviar la cola pendiente.
- Los conflictos y cambios que requieren revisión detienen el ciclo y se conservan para resolución manual; no se fuerza la aplicación de snapshots inseguros.
- Se actualizan la versión visible, version.txt y la caché de la PWA. No se borran ni reinician datos locales.

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

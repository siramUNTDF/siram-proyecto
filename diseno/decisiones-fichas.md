# Decisiones tomadas al escribir las fichas del front (2026-11-03)

> Las fichas de `../front/docs/vistas/` tuvieron que definir comportamiento que ni Figma ni
> CONTEXTO definían. Las decidió el agente de diseño (las de Bandeja y Nuevo caso, directamente; las
> demás, cinco agentes en paralelo). **Están para revisar**: si alguna no va, se cambia en su ficha.
> Los huecos que no se pudieron decidir quedaron en CONTEXTO §9 («Huecos detectados al escribir las
> fichas del front») y en la sección «Pendiente» de cada ficha.
>
> **Corregido el 2026-11-03** tras la revisión de coherencia: donde esta lista y
> `correcciones-fichas.md` no coincidan, gana `correcciones-fichas.md`.

## Casos

**Bandeja** — chip «Graves» = graves registrados o en seguimiento (igual que Inicio); filtros por URL; segunda línea del estado según el caso (motivo de
espera, → unificado, motivo de desestimación, «Un animal no se ubicó» en finalizados); busca
por DNI sin mostrarlo.

**Nuevo caso** — se abre sobre la Bandeja; DNI de 7 u 8 dígitos; víctima y contacto no pueden tener el
mismo DNI; fecha no futura; con DNI de víctima repetido: «Abrir C-…» o «Es otro ataque, guardar igual»
(= desenlace «distintos»: nace sin marca); al guardar abre la ficha del caso nuevo; cancelar con cambios
pregunta.

**Ficha del caso** — «No es duplicado» desde el aviso abre la misma ventana que en la comparación (observación opcional); «en N
casos» lleva al detalle del animal (con un solo caso no es enlace); Cambiar estado no aparece en
estados finales y los destinos los manda la API; bloque sin datos: «Todavía no se cargó» + botón;
bloque que la API no manda: no se muestra; «solo si existe» en una línea («Recibió atención en
Salud»); animal, denuncia y tratamiento ya cargados se editan con la misma ventana; Editar especificada en la ficha (datos comunes); el aviso «Vista de Salud» de Figma es nota de diseño, no va en la app;
se corrigió la línea de tiempo de los datos de ejemplo.

**Historial** — el analista no lo ve; cada agente con los mismos recortes que la ficha; un cambio sin
campos visibles no se muestra; «ver cómo estaba en una fecha» corta la línea de tiempo y el estado lo
arma la API; documentos en el filtro Caso.

**Solicitudes** — pendientes de la más vieja a la más nueva, resueltas por fecha de resolución; «Ver»
para las resueltas; varias coincidencias: la más reciente + «+N»; Descartar y Registrar confirman en
ventana lateral; Descartar sin motivo; con coincidencia, «Es otro ataque, registrar igual» (= «distintos»,
sin marca); registrar no copia dueño ni chip declarados (los confirma Zoonosis); una solicitud resuelta no se vuelve a resolver; Sumar sin coincidencia pide el número de caso;
«Sumar al caso» se habilita con la casilla y todas las filas distintas elegidas; lo declarado sobre
la denuncia no es fila (se copia siempre); lo que la persona no respondió no se muestra.

**Posibles duplicados** — A es el caso que ya existía (sobrevive) y B queda unificado; en las filas
distintas, A elegido por defecto; «No es duplicado» con observación opcional; si otro agente ya
resolvió, error y recarga; sin permiso de consolidar, la tarjeta sin casilla ni botón.

**Incompletos** — el tooltip de la marca nombra los datos que faltan si la API los manda.

## Inicio y Consultas

**Inicio** — cada tarjeta lleva a su lista («esperando contacto»: Bandeja filtrada aunque no haya
chip); Graves cuenta registrados o en seguimiento (igual que la Bandeja); tarjetas en 0 se muestran; proyección del mes = casos ÷ días
transcurridos × días del mes; destacados fijos (0–9, Cara, fin de semana, franja con más casos); notas
fijas, sin frases con cifras; sin datos de pendientes, no se muestra «Para resolver hoy».

**Búsqueda** — busca al entrar (vigentes por defecto), al tocar Buscar o Enter; filtros del animal se
cumplen si los cumple algún animal; filtros en la URL; «Desde» no posterior a «Hasta».

**Mapa** — casos sin ubicación no se dibujan (el pie dice cuántos); sin agrupar puntos; arranca en
Tierra del Fuego; filtros en ventana lateral; en teléfono el panel va debajo.

**Estadísticas** — los gráficos del animal cuentan animales; zona y gravedad sobre «casos con
tratamiento cargado»; categorías en 0 no se dibujan; barras relativas al máximo; filtros recalculan
sin botón.

**Exportar** — bloques y columnas según el rol los manda la API; archivo `siram-casos-AAAA-MM-DD`; una
fila por caso con columnas repetidas por animal; sin bloques o sin casos, descarga deshabilitada.

**Personas** — orden por última modificación; edición en ventana lateral con aviso «está en N casos»;
el DNI se corrige pero no puede repetir otro; la persona no tiene edad (va por caso); datos de un dueño
los edita solo Zoonosis.

**Animales** — «Todos» oculta los absorbidos; chip repetido al editar lleva a Reconciliar; quién
sobrevive lo decide la regla; al terminar abre el que sobrevivió.

## Administración

**Usuarios** — filtros por rol solo activos; Editar / Desactivar / Reactivar; correo único; sin
contraseña en el alta (llega un correo); nadie cambia su propio rol ni se desactiva; reactivar exige
organismo activo; la pestaña de permisos es texto fijo.

**Organismos** — orden por casos vigentes; nombre único (renombrar cambia todos sus casos); desactivar
con usuarios activos avisa y sus usuarios no entran.

**Tipos de evento** — nombre único; no se borra, se desactiva; el orden lo da la API.

## Formulario público

Rutas `/reportar` y `/reportar/detalle` (la primera propuesta, `/denunciar`, se cambió: no es una
denuncia); centrado a 390 px en pantallas anchas; mismas validaciones que Nuevo caso; pin fijo al
centro (se mueve el mapa); no pisa una dirección corregida a mano; si la geocodificación falla, campo
vacío sin error; «Más de 3»: tres repeticiones; especie siempre Perro o Gato (sin «No sé»); «¿Tiene chip?» si es propio; hasta 3 fotos por animal (JPG/PNG, 5 MB); errores de red con
Reintentar; el token en memoria o `sessionStorage`, nunca en la URL; sin token, pantalla de vencido.

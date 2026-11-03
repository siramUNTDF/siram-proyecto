# Figma · «Fundamentos» (lectura del 2026-11-03)

> Fuente: archivo original «SIRAM — Diseño» (`XC7e02ZzIfQwmALf1RHgiZ`), página `Fundamentos` [0:1],
> más las variables y los estilos del archivo. Leído con la cuenta de Martin Acosta. Textos y
> estructura, sin imágenes. Ver el índice en `README.md`.

## Variables

### Colección «Tokens» (modos Claro y Oscuro)

Son los valores de `front/src/tema/tokens.js`; el modo Oscuro sale del prototipo.

| Token | Claro | Oscuro |
|---|---|---|
| ground | `#F6F7F7` | `#0F1514` |
| surface | `#FFFFFF` | `#171F1E` |
| surface2 | `#ECF0EF` | `#1E2827` |
| ink | `#16211F` | `#E9EEED` |
| ink2 | `#4A5856` | `#AAB7B5` |
| ink3 | `#6E7C7A` | `#7E8C8A` |
| line | `#D8DEDD` | `#2B3837` |
| accent | `#00776F` | `#38C6B7` |
| accentSoft | `#DDEFEC` | `#0E302C` |
| accentContrast | `#FFFFFF` | `#07201D` |
| ok / okSoft | `#2E7D32` / `#E3F1E4` | `#72C076` / `#162A18` |
| warn / warnSoft | `#B26A00` / `#F7ECD9` | `#E0A233` / `#2E2413` |
| crit / critSoft | `#B3261E` / `#F8E4E2` | `#E8776B` / `#2E1B18` |
| info / infoSoft | `#00668F` / `#DEEDF5` | `#55B5DF` / `#0F2733` |
| dup / dupSoft | `#6B4FA8` / `#EAE4F5` | `#A98EDC` / `#221B33` |
| rel / relSoft | `#9A5B2D` / `#F5E9DC` | `#D9955C` / `#2E2317` |
| neutralSoft | `#E7EBEA` | `#26302F` |
| rowHover | `#F1F4F3` | `#1C2423` |
| chromeHover | `#E1E7E6` | `#263130` |
| focus | `#00776F` | `#38C6B7` |
| shadow | `#16211F` al 14 % | `#000000` al 50 % |

### Colección «Paleta» (alias de Tokens, con los nombres del tema de MUI)

`primary/{main,soft,contrastText}` → accent, accentSoft, accentContrast · `success/*` → ok ·
`warning/*` → warn · `error/*` → crit · `info/*` → info · `dup/{main,soft,contrastText}` → dup,
dupSoft, surface · `rel/*` → rel, relSoft, surface · `neutral/{main,soft,contrastText}` → ink2,
neutralSoft, surface · `background/{default,paper,chrome,chromeHover,rowHover}` → ground, surface,
surface2, chromeHover, rowHover · `text/{primary,secondary,tertiary,disabled}` → ink, ink2, ink3, ink3 ·
`divider` → line · `sombra` → shadow · `foco` → focus.

Fuera del tema, como en MUI, solo quedan el velo detrás de las ventanas (negro al 32 %) y el brillo
del botón primario al pasar el mouse (blanco al 8 %).

### Colección «Medidas»

| Variable | Valor |
|---|---|
| espacio/0-5 · 1 · 1-5 · 2 · 2-5 · 3 · 4 · 5 | 4 · 8 · 12 · 16 · 20 · 24 · 32 · 40 |
| radio/base · pildora · menu | 4 · 999 · 30 |
| control/alto · alto-chico | 38 · 30 |
| cascara/alto-barra · ancho-menu · ancho-menu-colapsado | 89 · 240 · 65 |

## Estilos de texto

Alto de línea en %; espaciado entre letras en % entre corchetes cuando no es 0.

| Estilo | Fuente | Tamaño / alto |
|---|---|---|
| Títulos/H1 | Archivo ExtraBold | 26 / 115 [−1] |
| Títulos/H2 | Archivo ExtraBold | 22 / 120 |
| Títulos/H3 | Archivo SemiBold | 18 / 125 |
| Títulos/Tarjeta | Archivo SemiBold | 16 / 120 |
| Títulos/Chico | Archivo SemiBold | 14,5 / 120 [0,5] |
| Títulos/Iniciales | Archivo SemiBold | 14 / 100 |
| Títulos/Sección | Archivo SemiBold | 13 / 120 [14] |
| Títulos/Marca SIRAM | Archivo ExtraBold | 23 / 100 [14] |
| Títulos/Símbolo | Archivo ExtraBold | 11 / 100 |
| Cuerpo/Base · Base destacado | Source Sans 3 Regular · SemiBold | 15 / 145 |
| Cuerpo/Sin dato | Source Sans 3 SemiBold | 14,5 / 145 |
| Cuerpo/Chico · Botón | Source Sans 3 Regular · SemiBold | 14 / 145 |
| Cuerpo/Compacto · Etiqueta | Source Sans 3 Regular · SemiBold | 13,5 / 130 |
| Cuerpo/Detalle · Detalle destacado · Píldora | Source Sans 3 Regular · SemiBold · SemiBold | 12,5 / 140 (Píldora 130) |
| Cuerpo/Mínimo | Source Sans 3 Regular | 12 / 135 |
| Cuerpo/Aviso chico | Source Sans 3 SemiBold | 11,5 / 130 |
| Cuerpo/Rótulo | Source Sans 3 SemiBold | 11 / 130 [7] (mayúsculas) |
| Datos/Cifra grande · Cifra · Cifra chica | IBM Plex Mono Medium | 48 / 90 [−3] · 28 / 100 [−2] · 22 / 100 [−2] |
| Datos/Valor | IBM Plex Mono SemiBold | 15 / 140 |
| Datos/Base · Enlace | IBM Plex Mono Regular · SemiBold | 13,5 / 140 [−1] |
| Datos/Chico · Chico destacado | IBM Plex Mono Regular · Medium | 13 / 140 |
| Datos/Detalle | IBM Plex Mono Regular | 12,5 / 140 |
| Datos/Mínimo | IBM Plex Mono Regular | 12 / 140 |
| Datos/Versión | IBM Plex Mono Regular | 11 / 130 [4] |
| Datos/Código · Nota | IBM Plex Mono Medium · Regular | 10,5 / 130 [2 · 9] |

Estilos de efecto: Sombra/Barra superior · Sombra/Ventana lateral · Sombra/Flotante. No hay estilos
de color: todo color es una variable.

## Componentes (secciones de la página)

**Íconos.** Un solo set: `@mui/icons-material`, el mismo del código. Color por defecto
`text/secondary`; en cada uso se cambia por otra variable de Paleta. Hay 44: Menu, Search, Add,
FilterAltOutlined, DensitySmallOutlined, DensityMediumOutlined, ViewColumnOutlined, MoreVert,
ChevronLeft/Right, ExpandMore, HomeOutlined, FolderOutlined, SearchOutlined, SettingsOutlined, Close,
HelpOutline, ArrowDropDown, CalendarTodayOutlined, CheckCircleOutline, InfoOutlined,
WarningAmberOutlined, ErrorOutline, DesignServicesOutlined, EditOutlined, CheckBox,
CheckBoxOutlineBlank, RadioButtonChecked/Unchecked, ArrowBack, DescriptionOutlined, ImageOutlined,
FileDownloadOutlined, Check, AssignmentLateOutlined, ScheduleOutlined, ContentCopyOutlined,
LinkOutlined, FlagOutlined, ArrowForward, Remove, Contrast, UnfoldMore, CallMerge.

**Caso.** «Los tres indicadores del caso van separados: estado (píldora), motivo de espera (solo En
seguimiento) y marcas (pegadas al identificador). Nunca se juntan en un solo componente.»
- Marca: Incompleto · Posible duplicado · Posible evento relacionado.
- Estado del caso: Registrado · En seguimiento · Finalizado · Desestimado · Unificado · **Grave**.
- Motivo de espera: Contacto · Respuesta · Certificado.
- Enlace de caso («C-2026-0418») · Organismo (chip, «Zoonosis Ushuaia») · Nota de datos de ejemplo.

**Acciones y filtros.** «Botones como presets: la pantalla pide «Guardar», «Cancelar» o «Nuevo
caso», no un color. Guardar queda deshabilitado hasta que haya cambios.»
- Botón: Primario · Secundario · Texto · Peligro · Consolidar · Vincular, cada uno Normal / Hover /
  Deshabilitado.
- Botón ícono: 30 y 40 px × Normal / Hover / Deshabilitado. Chip de filtro: activo sí/no. Campo de
  búsqueda: Vacío / Con texto / Foco.

**Cáscara.** Barra superior fija de 89 px; menú lateral de 240 px (colapsable a 65 px); solo el
contenido scrollea; sin breadcrumbs ni footer. Ítem activo = píldora abierta a la derecha (radio
0 30 30 0). Dos niveles de menú, nunca tres.
- Ítem de menú: Principal (Normal, Hover, Activo, Abierto) · Sub (Normal, Hover, Activo).
- Barra superior: botón de menú, «SIRAM / Registro de Ataques y Mordeduras», usuario (nombre,
  separador, avatar con iniciales).
- Menú lateral, una variante por sección abierta (pie «V0.1.0»):
  - Inicio
  - Casos › Bandeja · Nuevo caso · Solicitudes (3) · Posibles duplicados (1) · Eventos relacionados (2)
    · Incompletos (2)
  - Consultas › Búsqueda · Personas · Animales · Mapa · Estadísticas · Exportar
  - Administración › Usuarios · Organismos · Tipos de evento · Importar CSV

**Tabla y página.** Tabla densa con encabezado fijo, hover de fila y columna de acciones clavada a la
derecha. Celdas con texto principal y segunda línea más chica. Paginación al pie.
- Tabla/Encabezado · Tabla/Celda (Texto, Doble, Doble destacado, Doble mono × Normal/Hover) ·
  Tabla/Celda acciones · Pie de tabla («Filas por página 10 · 1–10 de 12 · ‹ 1 2 ›»).
- Leyenda de marcas: «Incompleto · Posible duplicado · Posible evento relacionado — mismo animal,
  otra víctima. No se fusiona.»
- Encabezado de página: título, bajada y, a la derecha, la nota de datos de ejemplo.

**Formulario y ventana lateral.** «Crear, editar y confirmar abren una ventana lateral desde la
derecha (50 % en escritorio, 100 % en teléfono): Cancelar a la izquierda, Guardar a la derecha. Un
bloque con leyenda por grupo de la matriz. Cada campo reserva 20 px para el error; la ayuda va en un
ícono junto a la etiqueta.»
- Campo: Texto · Selección · Fecha × Vacío / Completo / Foco / Error / Deshabilitado. El rótulo lleva
  el código de la matriz (p. ej. «P6 DNI *»); vacío se muestra «Sin dato».
- Opción (radio) y Casilla: seleccionada sí/no × Normal/Deshabilitado. Grupo de opciones (ejemplo D1:
  Sí · No · Sin dato).
- Bloque de formulario/Leyenda · Ventana lateral/Encabezado (título, bajada, cerrar) · Ventana
  lateral/Pie: Sin cambios (Guardar deshabilitado) / Con cambios.

**Mensajes.** Cuatro severidades, dos comportamientos: éxito e información se cierran solos;
advertencia y error exigen cierre manual. Los flotantes van arriba a la derecha, rellenos; los en
línea se quedan en la página. Mensaje: Éxito · Información · Advertencia · Error × En línea / Flotante.

**Ficha.** «Cada dato con su código de la matriz; «Sin dato» siempre en rojo y distinto de «No sabe»;
adjuntos y eventos del historial de auditoría.»
- Dato: Texto · Mono · Sin dato (con ícono de advertencia). Archivo adjunto: Documento · Imagen.
  Evento de auditoría: Persona · Sistema.

**Consultas y administración.** Piezas para Búsqueda, Estadísticas y Exportar, y para las listas de
Administración. El largo de una barra y el alto de una columna salen del tamaño de la instancia.
- Indicador (cifra + texto + bajada) · Gráfico/Barra (Normal, Destacada, Sin dato × etiqueta a la
  izquierda o arriba) · Gráfico/Columna (Normal, Destacada, Parcial) · Vigencia (Activo/Inactivo) ·
  Filtro aplicado (chip con cerrar) · Encabezado de sección · Pestaña · Permiso (Sí, No, A definir).

**Inicio y comparar.** Piezas del panel de Inicio (pendientes y accesos) y de la pantalla Comparar
(señales del motor y filas campo por campo). Lo violeta es lo que sobrevive si se consolida.
- Pendiente: Incompletos · Esperando contacto · Posibles duplicados · Eventos relacionados · En
  seguimiento. Acceso a sección (ícono, título, bajada, botón «Ir»).
- Señal de coincidencia: Coincide · No evaluable · No coincide.
- Fila de comparación: Igual · Distinto, queda A · Distinto, queda B · Solo en A · Solo en B ·
  Distinto, sin elegir × Texto/Mono.

**Colores · modo oscuro.** Los mismos roles de Paleta con Tokens en modo Oscuro. El texto del botón
primario pasa a `#07201D` sobre el verde agua claro.

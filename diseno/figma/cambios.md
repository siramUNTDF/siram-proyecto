# Figma · cambios por pantalla (propuesta del 2026-11-03)

> Paso 1 del flujo acordado (memoria `project-flujo-figma-codigo`): cerrar el diseño en Figma antes de
> que el front lo implemente. Sale de los choques confirmados en `choques.md` (sección A) y de la
> decisión sobre E4. **No se aplicó nada todavía**: es la lista para revisar.
> Archivo: «SIRAM — Diseño» (`XC7e02ZzIfQwmALf1RHgiZ`). Entre corchetes, el id del nodo.

Leyenda del origen: **A.n** = choque confirmado en `choques.md` · **E4** = decisión sobre la Demo E4 ·
**B.n** = observación de la Demo (datos de ejemplo que no cierran) · **D-ER** = decisión del
2026-11-03 sobre el evento relacionado · **?** = necesitaba una decisión (al final).

## Fundamentos [0:1]

| Pieza | Cambio | Origen |
|---|---|---|
| Estado del caso [4:29] | Sacar la variante `Estado=Grave`. | A.1 |
| Marca [4:13] | Agregar `Tipo=Grave` (rojo, `error`; el mapa ya pinta los graves en rojo). Sacar `Tipo=Posible evento relacionado`. | A.1, D-ER |
| Leyenda de marcas (sección Tabla y página [8:54]) | Queda Incompleto · Posible duplicado · Grave: sale «Posible evento relacionado». | A.1, D-ER |
| Botón [5:53] | Sacar `Tipo=Vincular` (ya no se vincula). | A.4 |
| Señal de coincidencia [74:345] | Sacar o reducir: sin puntaje ni pesos; a lo sumo «DNI de la víctima coincide». | A.4 |
| Pendiente [74:305] | Agregar variantes propias `Tipo=Graves` y `Tipo=Solicitudes` (hoy se usan las de Incompletos y En seguimiento). Sacar `Tipo=Eventos relacionados`. | B.9, D-ER |
| Evento de auditoría [37:244] | Renombrar a «Evento de historial». | D |
| Menú lateral [46:311] | Sacar «Importar CSV» de Administración y «Eventos relacionados» de Casos. | A.9, D-ER |

## Inicio [78:298]

**Inicio · v2 [108:9618]**
- Tarjeta «1 caso grave» con la variante nueva `Pendiente Tipo=Graves`. Bajada: «Un animal murió o
  enfermó en la observación» (ahora es marca, no estado). (A.1, B.9)
- Tarjeta «3 solicitudes pendientes» con `Tipo=Solicitudes`. (B.9)
- Nivel «Espera tu revisión · decidís vos si se consolidan o se vinculan»: sacar la tarjeta «eventos
  relacionados» y cambiar la bajada (quedan solicitudes y posibles duplicados; ya no se vincula).
  (A.4, D-ER)

## Casos [1:2]

**Bandeja · v2 [108:5214]**
- Filtro «Graves (1)»: se queda, pero filtra por la marca. Sale el filtro «Eventos relacionados».
  (D-ER)
- C-2026-0421: estado vuelve a uno real (p. ej. En seguimiento) y lleva la **marca Grave** pegada al
  número; sale la aclaración «El animal murió en la observación» de la columna Estado. (A.1)
- C-2026-0398: deja de decir «Sin todos los datos: el perro nunca se ubicó». Pasa a ser el caso del
  perro no ubicado finalizado completo, o el del finalizado incompleto del escenario nuevo. (A.5, E4)

**Ficha del caso · v2 [108:5212]** y **· vista Salud [108:5219]**
- La marca Grave se tiene que poder ver junto al número cuando corresponda (en C-2026-0418 no: su
  día 10 es «Sin novedad»). (A.1)
- En el encabezado de cada animal, «en 2 casos» pasa a ser un enlace a esos casos: es donde se ve el
  evento relacionado. (D-ER)
- Lo declarado: D1 «Sí» / D3 «No corresponde» no coincide con la solicitud S-2026-0034 («No · No sabía
  dónde denunciar»); unificar la solicitud listada (S-2026-0031 vs S-2026-0034). (B.2)
- «Registrado por M. Acosta · 12/09/2026 15:02 · canal de origen: Zoonosis» vs E1 («canal de origen:
  ciudadano», solicitud del 13/09 21:40): elegir una sola historia. (B.3)

**Ficha · Cambiar estado · v2 [108:5221]**
- Sacar «Grave» y su ayuda. (A.1)
- Sacar «Registrado» de las opciones (no se vuelve). Ofrecer solo los destinos válidos desde el estado
  actual (RN-36). (A.2)
- «Desestimado» abre la ventana Desestimar, que pide el motivo. (B.10)

**Ficha · Agregar animal [108:5224]** — sin cambios: «Si murió o enfermó, el caso pasa a Grave» ya
describe la marca derivada.

**Comparar · posible duplicado [75:6219]** y **· consolidar confirmado [76:6630]** (A.4)
- Sacar el bloque «Motor de coincidencias» (puntaje 96/100, medidor, señales con peso, leyenda). En su
  lugar, el motivo del aviso: «La víctima tiene el mismo DNI (58.412.336)».
- Mantener la comparación campo por campo y «Consolidar en un registro único» (irreversible, con la
  confirmación explícita).
- Sacar «Vincular como evento relacionado». El otro desenlace es «No es duplicado: son casos
  distintos», que guarda la decisión y saca la marca.
- Usar las columnas y datos de la v2 (la fila «L3 Zona del cuerpo» es dato de tratamiento).

**Comparar · evento relacionado [76:7209]** — se retira (pasa al Archivo v1): el evento relacionado ya
no se decide. (A.4)

**Posibles duplicados [14:386]** — pasar a las columnas de la Bandeja · v2. Bajada: «Al abrir un caso
se ve con cuál y se decide en la comparación» se queda. (A.8)

**Eventos relacionados [14:608]** — se retira (pasa al Archivo v1): ya no es una lista de trabajo.
(D-ER)

**Nuevo caso · Aviso de caso parecido [36:3064]** — se retira o se rehace: tiene el formulario v1
completo (H6, H8, H7, A12, L1–L7, X1–X3, D4, H10). Si se rehace, es el formulario inicial · v2
[108:5213] con el aviso de DNI repetido arriba. (A.6)

**Incompletos · v2 [108:5220]**, **Solicitudes [108:5215]**, **Revisar solicitud [108:5216]**,
**Sumar a un caso [108:5217]**, **Historial [108:5218]**, **Desestimar [108:5222]**, **Anotar denuncia
[108:5223]**, **Cargar tratamiento [108:5225]**, **Adjuntar documento [101:10173]**, **Nuevo caso ·
formulario inicial · v2 [108:5213]** — sin cambios.

## Consultas y Administración [1:3]

**Búsqueda [48:246]** y **· filtros plegados [49:660]**
- Bloque Persona: sacar «Con quién estaba» y «Qué estaba haciendo». (A.6)
- Bloque Animal: «Propio o ajeno» pasa a «Tenencia» (propio, ajeno conocido, ajeno desconocido, no
  sabe). (A.7)
- Bloque Lesión: hoy **no existe** buscar por datos de TRATAMIENTO (zona del cuerpo, gravedad), así
  que salen de Búsqueda. *(Usuario, 2026-11-03: no está decidido; puede ser. Anotado para el código,
  en última instancia.)* El tipo de lesión espera la definición de HZ05. (A.7)
- Tabla de resultados con las columnas de la Bandeja · v2. (A.8)

**Estadísticas [53:1221]**
- Sacar el gráfico «Qué estaba haciendo» y su nota. (A.6)
- «Vacunación y castración del animal» → solo vacunación; sacar «Castrado». (A.6)
- «Datos sin completar»: sacar Castrado y Qué hacía. (A.6)
- «Tipo de lugar»: usar los valores de H5 (casa propia, casa ajena, vía pública, espacio público, zona
  rural, no sabe, sin dato). (A.7)
- «Gravedad»: usar los de L2 (excoriación, herida superficial, herida profunda, amputación, sin dato).
  (A.7)
- «Origen del animal (propio o ajeno)» → «Tenencia», con sus valores. (A.7)

**Exportar [67:1453]** y **· con datos personales [67:1932]** — rehacer los bloques de columnas con
los campos vigentes. Sacar: con quién estaba, qué estaba haciendo, iba con perros, reincidente, «si
volvió a ver al animal suelto», observaciones del caso y firma. Cambiar los totales del resumen. (A.6)

**Usuarios · Nuevo usuario [69:2180]** — rol Agente: «…resuelve duplicados y eventos relacionados» →
«…resuelve los posibles duplicados». (A.4)

**Mapa · v2 [103:4465]**, **Personas [102:3518, 102:3771]**, **Animales [102:4009, 108:9370,
108:9369]**, **Roles y permisos · v2 [108:9371]**, **Organismos**, **Tipos de evento**, **Usuarios**
(el resto) — sin cambios.

## Formulario público [105:945]

**Público › 3 · Dónde fue [108:9986]** — sacar la opción «Otra» de Ciudad. (A.3)

## Demo [110:310]

- **E1·11 [110:4322]**, **E4·02 [111:9159]**: Cambiar estado sin «Grave» ni «Registrado» (sale solo al
  corregir el componente). (A.1, A.2)
- **E3 «El animal muere en la observación»** [111:6486…7669]: el paso 2 deja de ser «El caso pasa a
  Grave» (cambio manual). Pasa a ser «El caso queda marcado Grave» en la bandeja o la ficha, sin que
  nadie lo cambie. El paso 1 edita el seguimiento de un animal que ya está en el caso, con «Murió o
  enfermó» marcado (hoy usa Agregar animal). (A.1, B.6)
- **E4 «Nunca se ubica al perro»** [111:8499…9713]: contarlo bien. El perro no se ubica, su día 10
  queda «No se pudo observar» y el caso se finaliza completo. Sale «aunque le falten datos» de la
  portada y de los pasos 2 y 3, y sale el paso 4 «No cuenta como incompleto». (E4)
- **Escenario nuevo · Finalizado incompleto**: nunca se ubica a la víctima ni al contacto responsable,
  faltan datos del caso (p. ej. edad o tipo de lugar), se finaliza igual y deja de contar como
  incompleto. Se suma a la portada [110:311] («Ocho escenarios…»). (E4)
- **Datos de ejemplo de la Demo** (B.1, B.3–B.5, B.7, B.8): E7 con otro caso para la reincidencia;
  E1 con una sola línea de tiempo; la ficha de cada paso del E1 con su estado; E2 con otra solicitud
  (no S-2026-0034); E5 desestimando otro caso; E7·02 mostrando el resultado. Son de narrativa, no de
  diseño: se pueden dejar para cuando se rehaga la Demo.

## Antes de cambiar: decisiones pendientes (?)

1. ~~**Evento relacionado.**~~ Resuelto el 2026-11-03 (**D-ER**, decisión del agente de diseño
   aprobada por Darío, `modelo/decisiones.md`): sin marca ni lista de trabajo; se muestra en el animal
   («en N casos» en la ficha y «Casos de este animal»).
2. ~~**Búsqueda · bloque Lesión.**~~ Resuelto el 2026-11-03: hoy no se busca por datos de
   TRATAMIENTO; queda como idea para el código (ver Búsqueda, arriba).

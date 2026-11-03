# Figma · «Casos» (lectura del 2026-11-03)

> Fuente: archivo original «SIRAM — Diseño» (`XC7e02ZzIfQwmALf1RHgiZ`), página `Casos` [1:2]. Textos
> literales entre comillas. Las pantallas con «· v2» en el nombre son componentes (la Demo los
> reutiliza); las otras son marcos sueltos, varios anteriores a la v2. Ver el índice en `README.md`
> y los choques con CONTEXTO.md en `choques.md`.

## Pantallas v2

### Bandeja · v2 [108:5214]
«Ordenados por última modificación: arriba queda lo que alguien tocó hace poco.» Búsqueda «Buscar por
caso, víctima o DNI» · botón Nuevo caso. Filtros rápidos: Todos (11) · Incompletos (3) · Posibles
duplicados (2) · Eventos relacionados (2) · En seguimiento (2) · **Graves (1)**.

Columnas: Marcas · Caso · Última modificación (+ quién) · Fecha del hecho (+ hora) · Víctima (+ edad) ·
Lugar (+ ciudad) · Animales («Perro · +1 animal») · Tipo de evento · Estado (+ aclaración) · Canal de
origen. Filas de ejemplo que muestran los estados:
- C-2026-0421 · **Grave** · «El animal murió en la observación» · Salud
- C-2026-0417 · En seguimiento · «Esperando certificado» · C-2026-0404 · En seguimiento · «Esperando
  contacto» (con marca Incompleto)
- C-2026-0411 · «Unificado en otro caso → C-2026-0402» · CADIC
- C-2026-0398 · Finalizado · «Sin todos los datos: el perro nunca se ubicó» · Zoonosis
- C-2026-0393 · Desestimado · «Hecho no verificable» · Histórico (conserva la marca Incompleto)

### Incompletos · v2 [108:5220]
«Casos vigentes a los que les falta algún dato del caso (fecha del hecho, ciudad, lugar…). Ordenados
por última modificación.» Mismas columnas que la bandeja. Nota: «Solo casos vigentes. Un caso
finalizado con datos faltantes deja de contar como incompleto. Uno desestimado conserva la marca,
pero no entra en las listas de trabajo (dónde se cuenta está pendiente).»

### Nuevo caso · formulario inicial · v2 [108:5213] (ventana lateral)
«Formulario inicial. Lo obligatorio (*) depende del canal; el caso guarda su canal de origen. Canal:
Zoonosis (tu organismo).»
- ¿Quién sufrió el ataque?: «¿La persona que informa es quien sufrió el ataque? *» Sí · No, es otra
  persona.
- Víctima: nombre *, apellido *, DNI *, teléfono (opcional), correo (opcional). «De la víctima es
  obligatorio todo salvo el contacto (p. ej. un niño no lo tiene).»
- Contacto responsable: nombre *, apellido *, DNI *, teléfono *, correo (opcional). «No se guarda la
  relación entre ambas.»
- Hecho: fecha del hecho *, especie del animal * (Perro · Gato).
- «Al guardar, si el DNI coincide con otro caso se avisa antes de crear el registro. Ubicación,
  animales, tratamiento y denuncia se completan después en la ficha del caso.»

### Ficha del caso · v2 [108:5212]
En orden:
1. **Encabezado**: «C-2026-0418» con marcas · «Ataque con mordedura · Ushuaia · 12/09/2026» ·
   Editar · Cambiar estado · menú. Banda: estado, chip del organismo, «Registrado por M. Acosta ·
   12/09/2026 15:02 · canal de origen: Zoonosis».
2. **Aviso de posible duplicado**: «Se detectó un caso con datos coincidentes. El caso C-2026-0402
   (Hospital Regional Ushuaia, 13/09/2026) comparte datos con este.» Chips DNI, teléfono y fecha del
   hecho · Comparar casos · No es duplicado.
3. **Víctima**: P1 nombre, P2 edad, P6 DNI, P4 teléfono, P3 correo, P7 domicilio («Sin dato» en rojo).
4. **Contacto responsable**: «Informó el hecho por la víctima. Opcional: no existe si la víctima se
   registró sola.» Nombre, DNI, teléfono, correo.
5. **Hecho**: H1 fecha, H2 hora, H3 ciudad, H4 dirección, referencias, H5 tipo de lugar, T1 tipo de
   evento, mapa con el pin y sus coordenadas.
6. **Animales · 2**: «Cada animal tiene su identidad (especie, chip) y lo que se supo de él en este
   caso. Dueño, chip y seguimiento los carga solo Zoonosis.» Por animal, encabezado («Animal 1 · Perro
   · chip … · en 2 casos» / «Animal 2 · Perro · sin chip · nunca se ubicó») y cuatro secciones:
   - Identidad y tenencia: A1 especie, chip, A5 tenencia, dueño durante el caso (con DNI), A7 domicilio
     o zona del animal, A8 vacunado.
   - Descripción: A2 tamaño, A9 sexo, edad aparente, A13 color, A4 raza, A11 ¿podría reconocerlo?
   - Seguimiento · Zoonosis: observación del día 10 (valor, fecha, quién) y observaciones.
   - Fotos del animal. Botón «Agregar animal».
7. **Tratamiento · Salud**: «Lo ve y lo carga solo Salud · Hospital Regional Ushuaia, L. Puig ·
   12/09/2026». Fecha de la consulta, L3 zona del cuerpo, L2 gravedad, L7 antirrábica, antitetánica,
   L6 antibiótico, L5 sutura, observaciones.
8. **Denuncias · Zoonosis**: «Solo las anota Zoonosis. Estado: pendiente de confirmación · confirmada ·
   desestimada (tentativo).» Cada denuncia: ente, número, fecha, estado, DNI de quien la hizo,
   observaciones, quién la anotó. Botón «Anotar denuncia».
9. **Lo que declaró la persona**: «Ningún agente lo edita; si hay varias solicitudes, gana la más
   reciente.» D1, D3 («Solo si respondió No»), solicitudes vinculadas.
10. **Documentos**: «Solo nombre del archivo y dónde está alojado. Las fotos del animal van en cada
    animal.» X1 certificado médico · «Adjuntar documento».
11. **Historial**: «5 cambios · el último, 13/09/2026 09:12 por L. Puig (Hospital Regional Ushuaia)» ·
    «Ver historial».

### Ficha del caso · v2 · vista Salud [108:5219]
La misma ficha con el aviso «Vista de Salud. Lo que la API no le envía a Salud no se muestra: dueño,
chip, descripción y fotos de los animales, y el detalle de la denuncia (RN-35).» En Animales: «Salud ve
la observación del día 10 porque puede cambiar el tratamiento antirrábico de la víctima. No ve dueño,
chip ni descripción.» Cada animal muestra solo especie, A7, A8 y el seguimiento. Tratamiento con
«Editar tratamiento». Denuncias: «Tiene 1 denuncia anotada en Zoonosis. El detalle (DNI de quien la
hizo, número, observaciones) lo ve solo Zoonosis.»

### Ventanas laterales de la ficha
- **Cambiar estado · v2** [108:5221]: «Nuevo estado *»: Registrado · En seguimiento · Finalizado ·
  **Grave** · Desestimado. Ayudas: «Finalizado: se puede finalizar aunque falten datos; entonces deja
  de contar como incompleto.» «Grave: el animal murió durante la observación. El caso sigue abierto y
  pide atención especial al tratamiento.» «Desestimado: pide un motivo. Unificado no se elige acá:
  resulta de consolidar duplicados.» Con En seguimiento aparece «¿Qué se está esperando? *» Contacto ·
  Respuesta · Certificado («Solo existe mientras el caso está en seguimiento.»).
- **Desestimar · v2** [108:5222]: «No se borra: queda desestimado, con su motivo, en el historial.»
  Motivo *: Fuera de alcance (no fue un ataque de perro o gato a una persona) · Fuera de la provincia ·
  Hecho inexistente o no verificable · Cargado por error. «Duplicado no es un motivo: se consolida.
  Datos insuficientes tampoco: es la marca Incompleto. Lista tentativa.» Observación libre. Aviso: «Si
  le faltan datos, sigue marcado como incompleto. Un caso desestimado no cuenta en las estadísticas.»
- **Anotar denuncia · v2** [108:5223]: «Solo Zoonosis, y solo denuncias hechas en Zoonosis. DNI y fecha
  alcanzan para ubicarla en su sistema.» DNI de quien la hizo *, fecha *, número de trámite
  (opcional), estado * (Pendiente de confirmación · Confirmada · Desestimada; «Tentativo. P. ej., una
  denuncia “desglosada y devuelta” a las 48 h sin certificado queda desestimada.»), observaciones.
  «El DNI de quien la hizo no se enlaza a ninguna persona de SIRAM…»
- **Agregar animal** [108:5224]: «Si el chip ya existe, se vincula ese animal: su identidad no se
  duplica.» Identidad (especie *, chip; aviso «Este chip ya está en SIRAM. El animal aparece en
  C-2026-0402…»). En este caso: tenencia * (Propio · Ajeno conocido · Ajeno desconocido · No sabe),
  dueño durante el caso, domicilio o zona, vacunado (Sí · No · No sabe). Descripción: tamaño, sexo,
  edad aparente, color, raza, ¿podría reconocerlo? Seguimiento · Zoonosis: observación del día 10
  (Pendiente · Sin novedad · Murió o enfermó · No se pudo observar; «Si murió o enfermó, el caso pasa
  a Grave. Si nunca se ubica, el caso puede finalizar incompleto.»), observaciones. Fotos. «Dueño,
  chip y seguimiento los carga solo Zoonosis. Cualquier agente puede agregar el animal y su
  descripción.»
- **Cargar tratamiento** [108:5225]: «Solo Salud. Se liga al caso, no a la persona…» Consulta: fecha *,
  zona del cuerpo, gravedad («excoriación · herida superficial · herida profunda · amputación»).
  Indicaciones: antirrábica, antitetánica, antibiótico, sutura (Sí · No); «Vacuna antirrábica: por
  ahora sí o no. Si registrar el esquema de dosis está por consultar con Salud.» Observaciones.
  «“Recibió atención médica” no se carga: se deduce de que el caso tenga un tratamiento.»
- **Adjuntar documento** [101:10173] (marco): «Se guarda solo el nombre del archivo y la dirección
  donde está alojado.» ¿A qué se adjunta? * Al caso (certificado médico) · A un animal del caso
  (fotos). Nombre del archivo *, URL *. «El certificado médico lo carga Zoonosis.»

### Historial del caso [108:5218]
«Historial · C-2026-0418. Cada cambio guarda la foto completa del registro: quién, cuándo, desde qué
organismo y desde qué caso se hizo.» Filtros: Todo (7) · Caso (2) · Personas (1) · Animales (1) ·
Tratamiento (1) · Denuncias (1) · Solicitudes (1) · «Ver cómo estaba en una fecha». Línea de tiempo,
del más nuevo al más viejo; cada cambio: iniciales, actor, organismo, fecha, frase y «antes → después».
Ejemplos: Salud cargó el tratamiento; «Sistema · Automático» avisó una coincidencia por DNI; M. Acosta
editó a Carla Sosa desde otro caso («persona compartida: el cambio se ve en sus dos casos»); editó el
color del animal 1; sumó una solicitud (¿Hizo denuncia?: sin dato → Sí); anotó la denuncia; registró el
caso («creación»). Pie: «El historial no se edita ni se borra. Las credenciales de los usuarios nunca se
copian en él.»

### Solicitudes [108:5215]
«Lo que enviaron las personas por el formulario público. Un agente la descarta o la registra: crea un
caso o la suma a uno existente.» Búsqueda por solicitud, nombre o DNI. Filtros: Pendientes (3) ·
Registradas (14) · Descartadas (5) · Todas (22). Columnas: Solicitud (+ estado) · Enviada · Quién la
envía (+ «Informa por otra persona» / «Es quien sufrió el ataque») · Víctima (+ DNI) · Fecha del hecho
· Especie · Formulario detallado (Completo 4 de 4 · Parcial 2 de 4 · Solo inicial 0 de 4) · Coincidencia
(«Misma víctima que C-2026-0418», con marca de posible duplicado, o «Sin coincidencias») · Revisar.
Pie: «Descartar no borra: la solicitud queda guardada para siempre, con sus datos. Ninguna solicitud
escribe en un caso ni en una persona sin un agente.»

### Revisar solicitud [108:5216]
«Solicitud S-2026-0034 · Enviada el 13/09/2026 21:40 por el formulario público · pendiente de revisión ·
formulario detallado completo (4 de 4)». Acciones: Descartar (peligro) · Sumar a un caso existente ·
Registrar como caso nuevo. Aviso: «La víctima ya está en un caso. El DNI 58.412.336 es víctima en
C-2026-0418 (Zoonosis, hecho del 12/09/2026). Si es el mismo hecho, sumala a ese caso; si no, registrala
como caso nuevo.» «Lo que declaró la persona, tal cual…» Bloques de solo lectura: Quién la envía ·
Víctima · Dónde y qué pasó («Qué pasó: Me mordió → Ataque con mordedura») · Animal 1 de 2 (con «Dueño,
según la persona») · Animal 2 de 2 · La denuncia.

### Sumar a un caso [108:5217]
«Sumar S-2026-0034 a C-2026-0418. Cuando un dato choca, elegí cuál queda. Si solo uno de los dos lo
tiene, se conserva el que lo tiene (se guarda la mayor información).» Aviso: «Lo declarado sobre la
denuncia se copia siempre. “¿Hizo denuncia?” y su motivo: gana la solicitud más reciente. Ningún agente
los edita.» Tabla campo · en la solicitud · en el caso, con filas de comparación (igual, solo en uno
«Se conserva», distinto sin elegir, queda A/B); el animal 2 aparece como «Solo en A». Casilla «Confirmo
que la solicitud es del mismo hecho que el caso» · Cancelar · Sumar al caso. Nota: «Falta elegir el
teléfono del contacto. Al sumarla, la solicitud queda “registrada” y apunta al caso; el animal 2 se
agrega como un animal nuevo del caso.»

## Pantallas anteriores a la v2 (siguen en la página)

- **Posibles duplicados** [14:386] y **Eventos relacionados** [14:608]: listas con las columnas
  viejas (Marcas · Caso · Fecha del hecho · Víctima · Lugar · Animal · Lesión · Estado · Origen).
  Bajadas: «Al abrir un caso se ve con cuál y se decide en la comparación.» / «Casos vigentes con otra
  víctima del mismo animal, en el mismo lugar y fecha. Se vinculan; nunca se fusionan.»
- **Nuevo caso · Aviso de caso parecido** [36:3064]: bandeja vieja con el formulario completo de la v1
  en la ventana lateral (bloques de la matriz: Persona, Hecho con H6 «Con quién estaba» y H8 «Qué
  estaba haciendo» obligatorios y H7, Tipo de evento, Animal con A12 reincidente, Lesión y atención
  L1–L7, Documentación X1–X3, Denuncia y seguimiento con D4 y H10). Arriba, el aviso: «Hay un caso muy
  parecido. C-2026-0418 … tiene el mismo DNI: 58.412.336. Revisalo antes de crear el registro…» · Ver
  comparación · Es otro caso, guardar igual.
- **Comparar · posible duplicado** [75:6219] y **· consolidar confirmado** [76:6630]: motor de
  coincidencias con puntaje («Coincidencia alta 96/100», escala Baja · Media · Alta) y señales con peso
  (DNI idéntico decisiva, teléfono fuerte, nombre y edad fuerte, fecha ±1 día media, ubicación misma
  cuadra media, color del animal refuerzo «no evaluable»). Comparación campo por campo («7 iguales · 5
  distintos · 3 solo en uno»; lo violeta sobrevive). Desenlace, uno solo: *Consolidar en un registro
  único* (irreversible; «el 0402 queda Unificado y apunta a este caso»; casilla «Confirmo que Micaela
  Sosa y M. Sosa son la misma persona…»; botón deshabilitado hasta marcarla), *Vincular como evento
  relacionado* (reversible; «Fusionarlos borraría una víctima del registro epidemiológico») o *No están
  relacionados* (descarta la sospecha y saca la marca). La variante «confirmado» tiene la casilla
  marcada: «Es irreversible: revisá los valores marcados arriba.»
- **Comparar · evento relacionado** [76:7209]: «Posible evento relacionado 61/100»; DNI no coincide
  (decisiva), fecha, ubicación «a una cuadra» y «Mismo animal — Perro grande, negro, con collar rojo»
  (refuerzo). Aviso: «Acá no se ofrece consolidar. Las personas son distintas. Las salidas posibles son
  vincular los casos o descartar la sospecha.»

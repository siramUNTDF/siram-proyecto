# Decisiones del modelo de datos

Registro de cada cambio al modelo canónico (`siram.mmd`) y su porqué.
Lo mantiene el agente de diseño.

---

## 2026-10-08 · Versión 0 (línea base)

- Se toma como base el modelo de «De las pantallas al modelo» (`recursos/diseno/`), propuesto el
  05/10/2026. El boceto ER original del equipo queda superado.
- Se agregan los atributos de ORGANISMO (`nombre`, `tipo`) y USUARIO (`organismo_id`, `nombre`,
  `rol`) que figuraban solo en `recursos/modelo-er/siram-modelo-er.svg`.
- Brechas conocidas listadas en `CONTEXTO.md` §7. Próximo paso: incorporar los 19 campos de la
  matriz sin lugar propio y definir la representación de «No sabe».

## 2026-10-08 · Decisiones del equipo

- **Gatos dentro del alcance** (perros y gatos). Cierra HZ06. Sin cambio estructural: `ANIMAL.especie` ya los admite.
- **CASO ≠ DENUNCIA.** El caso lo registra SIRAM; la denuncia la hace una entidad externa y SIRAM solo
  la relaciona con un caso. Un caso tiene 0..N denuncias. La relación `DENUNCIA }o--o| CASO` ya lo
  expresa (un caso sin denuncias es válido). El «ABM de denuncias» del PDF se lee como ABM de casos.
- **DNI obligatorio.** `PERSONA.dni` deja de ser opcional. Una denuncia ciudadana puede llegar sin DNI
  (queda en `datos_crudos`), pero hay que obtenerlo antes de incorporarla a un caso.

## 2026-10-08 · Flujo caso → denuncia, borrado y DNI

- **Primero el caso, después la denuncia.** El agente registra el caso y luego le carga la denuncia.
  Se elimina `incorporada` de `DENUNCIA.estado`: queda `recibida|en_revision|vinculada|desestimada`.
- **No existe el borrado.** La baja de un caso es `CASO.estado = desestimado`.
- **DNI obligatorio en todo registro nuevo**, de cualquier origen. Solo los registros históricos pueden
  no tenerlo. `PERSONA.dni` lo anota; falta cómo distinguir un registro histórico (CONTEXTO §7.9).
- Pendiente: campo y lista de motivos de desestimación del caso (CONTEXTO §7.8).

## 2026-10-08 · Tres repos y quién conoce el modelo

- El proyecto se divide en tres repos hermanos dentro de `~/analisis/siram/`: `proyecto/` (este:
  diseño y dominio), `front/` y `back/`. Ninguno contiene a otro; la carpeta contenedora no es repo.
- **El modelo solo lo consume el backend**, en una versión fija (tags `modelo-vN` en este repo).
- **El front no conoce el modelo**: trabaja contra la API (OpenAPI generada por el back) y recibe el
  lenguaje visual y el prototipo en `front/docs/`.
- Las preguntas de `preguntas.md` pasan a ser del agente de backend.

## 2026-10-08 · Versión 1: SIRAM trata casos

> **Nota (2026-10-29):** la v1 se planteó y se escribió en `siram.mmd`, pero **nunca se publicó**
> (no tiene tag `modelo-v1`) y quedó superada por la v2 (entradas desde el 2026-10-23). Se conserva
> como registro de lo que se decidió en ese momento.

Narrativa acordada por el equipo (CONTEXTO §3, «Narrativa de uso»): el caso lo registra siempre un
agente interno, que carga los datos por la persona; la denuncia es un acto oficial del mundo real
ante un ente (Zoonosis, policía…) y SIRAM solo la anota en un caso que ya existe. El formulario
público queda en suspenso.

- **DENUNCIA pasa a ser un dato del caso.** `caso_id` obligatorio (`CASO ||--o{ DENUNCIA`). Se agregan
  `ente`, `numero`, `fecha` (H0, cierra la brecha §7.3), `denunciante_persona_id`, `anotada_en`.
  Se eliminan `origen`, `organismo_id`, `recibida_en`, `estado`, `motivo_desestimacion`,
  `observacion_revision` y `datos_crudos`: describían denuncias que llegaban solas y se revisaban en
  una cola, y eso ya no existe. Se elimina la relación ORGANISMO–DENUNCIA (quién la anotó sale de
  USUARIO). No tiene identificador visible propio (`D-…`).
- **CASO.hizo_denuncia** (`si|no`, nulo = sin dato, RN-23) y **CASO.motivo_no_denuncia** (D3).
  D1 «denunció en Zoonosis» y D2 «denuncia policial» no son campos: son denuncias anotadas con su ente.
- **CASO.estado:** se eliminan `sin_confirmar` y `confirmado`; el caso nace `registrado`. Confirmar
  tenía sentido cuando cualquiera podía cargar un caso desde el formulario público.
- **RN-28:** las estadísticas cuentan los casos vigentes (sin `desestimado` ni `unificado`).
- La entrada «DNI obligatorio» anterior decía que una denuncia ciudadana podía llegar sin DNI:
  queda sin efecto junto con el canal ciudadano.
- **`TIPO_DENUNCIA` → `TIPO_EVENTO`.** «Denuncia» ya nombra otra cosa (el trámite oficial); el
  catálogo clasifica el evento. La «T» de la matriz ya significaba «Tipo de evento». Valores
  propuestos y su deslinde con el tipo de lesión: CONTEXTO §9.

## 2026-10-23 · Redefinición del dominio (hacia la versión 2)

`siram.mmd` **no cambia todavía**: faltan definir DENUNCIA, COINCIDENCIA y los datos de cada ente, y
no conviene pasarle al back un contrato a medio cerrar. Lo acordado, para volcar en la v2
(detalle y porqué en CONTEXTO §3 y RN-20, RN-22, RN-27, RN-30 a RN-34):

- **SOLICITUD** (nueva): lo que declaró un ciudadano, tal cual, en una tabla de staging. Estados
  `pendiente|descartada|registrada`; referencia al caso (CASO 1 — 0..N SOLICITUD; registrada ⇔ tiene
  caso); fechas de envío y de resolución; token del formulario detallado con vencimiento. Nunca
  escribe en PERSONA ni en CASO sin un agente. Sin historial. Borrado lógico.
- **CASO:** `canal_origen` (`ciudadano|salud|zoonosis|cadic`), que define la obligatoriedad al nacer
  (RN-30). Ubicación: punto, dirección y referencias (cierra §7.6). Vuelve un campo de origen, que la
  v1 había eliminado de DENUNCIA: ahora es del caso, no de la denuncia.
- **PERSONA:** única por DNI (clave sustituta + `dni` único, nulo solo en históricos).
- **DUEÑO:** relación opcional ANIMAL → PERSONA. No «denunciado».
- **AUDITORIA → historial por entidad:** quién, organismo, cuándo, valor anterior y nuevo; la fila
  viva es la última versión.
- **Atención de Salud** (nueva): fecha de consulta, antirrábica, antitetánica, zona de mordedura,
  antibiótico, sutura, observaciones; ligada a la víctima del caso (PARTICIPACION), no a PERSONA.
  Absorbe L5–L7.
- **Todo registro:** marca de tiempo de creación automática.
- **DENUNCIA:** sin cambios hasta saber cómo la guardan los entes. **COINCIDENCIA:** en revisión
  (motor nuevo).

## 2026-10-28 · Pizarrón del equipo (hacia la versión 2)

Fuente: `recursos/pizarron-2026-10-28/` (dos iteraciones). `siram.mmd` sigue sin cambiar. Detalle
en CONTEXTO RN-20, RN-22 y RN-34.

- **Muere PARTICIPACION.** Como hay una sola víctima por caso, CASO tiene `victima_persona_id`
  (obligatoria) y `contacto_persona_id` (opcional, «contacto responsable»: quien registró en nombre
  de la víctima). Se elimina `vinculo`: la relación entre ambos no importa. El denunciante oficial
  no es un rol: es el DNI anotado en la denuncia. Reemplaza lo dicho el 23/10 sobre ligar el
  tratamiento a «la víctima del caso (PARTICIPACION)».
- **TRATAMIENTO** (Salud) se liga a CASO.
- **ANIMAL pasa a tener identidad** (especie, chip). Se invierte RN-22. Relación N:M con CASO
  mediante **CASO_ANIMAL**, que guarda lo que varía por caso: dueño durante el caso, tenencia (A5),
  vacunado, observación del día 10. El DUEÑO del 23/10 (relación ANIMAL → PERSONA) pasa a ser
  `CASO_ANIMAL.dueno_persona_id`, porque el dueño puede cambiar entre casos.
- **DESCRIPCIÓN** (nueva, 1:1 con CASO_ANIMAL): rasgos físicos. Separada por opcionalidad en bloque,
  ciclo de vida y cohesión; no por tamaño de tabla ni por permisos (se resuelven por campo en la API).
- **Reconciliación de animales:** dos ANIMAL que resultan ser el mismo se unifican (mismo patrón que
  `CASO.unificado_en_caso_id`); los casos apuntan al que sobrevive. Detalle del histórico a definir.
- **Abierto:** certificado médico (¿entidad o solo archivo?, §7.4), A6 y A10 de la matriz, y si un
  caso con varios animales finaliza cuando todos pasan el día 10.

## 2026-10-29 · Historial y reconciliación de animales (hacia la versión 2)

`siram.mmd` sigue sin cambiar. Detalle en CONTEXTO RN-22, RN-27 y RN-35.

- **Historial = una tabla espejo por entidad** (`<ENTIDAD>_HISTORICO`), en lugar de AUDITORIA. Cada
  fila es una foto completa del registro más `operacion` (alta, modificación, baja lógica),
  `fecha_hora`, `usuario_id` (nulo = Sistema), `organismo_id` (el del usuario **en ese momento**,
  copiado porque el usuario puede cambiar de organismo) y `caso_contexto_id` (opcional: el cambio
  puede hacerse fuera de un caso, p. ej. desde la vista de la persona). El delta anterior/nuevo se
  deriva comparando fotos. En Django, `django-simple-history` implementa el patrón.
- **ANIMAL:** `chip` único y opcional; nuevos `vigente` y `absorbido_por_animal_id` (FK a ANIMAL),
  mismo patrón que `CASO.unificado_en_caso_id`. Sobrevive el que tiene chip; si ninguno, el más
  viejo. Absorber repunta `CASO_ANIMAL.animal_id`; nada se borra ni se vacía.
- **Permisos:** por fila y por campo, en el servidor (RN-35). No cambia el modelo.
- **DENUNCIA: ente, fecha y DNI del denunciante obligatorios; número opcional.** Se anota la denuncia
  real, y sin fecha no se puede ubicar en el sistema del ente. Reemplaza el «si se consiguen» de
  RN-06 (2026-10-08). La fecha es la de la denuncia (H0), no la del hecho ni la de registro del caso.
- **Creación y última modificación automáticas en todas las entidades** (CASO, PERSONA, ANIMAL,
  CASO_ANIMAL, DESCRIPCIÓN, TRATAMIENTO, DENUNCIA, SOLICITUD, DOCUMENTO, COINCIDENCIA, ORGANISMO,
  USUARIO, TIPO_EVENTO), salvo las tablas de historial. La última modificación repite lo que ya dice
  el historial, pero ahorra consultarlo para ordenar o mostrar la fecha de novedad; la escribe la base
  y nadie la edita, así que el riesgo de que no coincidan es casi nulo (si pasa, gana el historial). En
  SOLICITUD, que no tiene historial, es el único dato de cuándo se tocó. Amplía la «marca de tiempo de
  creación» del 23/10.
- **ORGANISMO, USUARIO y TIPO_EVENTO también llevan tabla espejo.** Cambian poco y el costo es bajo;
  en USUARIO es trazabilidad de accesos (RN-29). El historial de USUARIO excluye las credenciales
  (hash de contraseña, secretos de 2FA).
- **TIPO_EVENTO se mantiene**, un valor por caso: ataque con mordedura · lesión compatible · intento
  sin lesión · lesión derivada. Pendiente de confirmar los valores, el deslinde con el tipo de lesión
  (L1) y si es catálogo o enumerado (CONTEXTO §9).
- **DENUNCIA: solo de Zoonosis.** Solo Zoonosis anota denuncias, y solo las hechas en Zoonosis; Salud,
  CADIC y el canal ciudadano no la tocan. La policía no se modela (podría sumarse muy a futuro). Como
  el ente es siempre Zoonosis, deja de ser un campo a cargar.
- **CASO.hizo_denuncia (D1) y CASO.motivo_no_denuncia (D3) se mantienen, como dato declarado** por la
  persona. **Solo los carga el canal ciudadano**: llegan en la solicitud y se copian al caso al
  registrarla; ningún agente los carga ni los modifica (RN-35). Sin solicitud, quedan sin dato. No
  conviene que los cargue otro canal: es una declaración de la persona y no hay motivo para que un
  agente la reemplace. Con varias solicitudes en desacuerdo, gana la más reciente (solo para estos
  dos campos). Vienen del F1 de Schiavini y miden el subregistro. No se
  derivan de DENUNCIA ni la reemplazan: se pueden cruzar. D2 (denuncia policial) se elimina.
- **A7 domicilio o zona del animal → CASO_ANIMAL** (dónde vive el animal; puede cambiar entre casos).
  En la v1 era `ANIMAL.zona_domicilio`.
- **Se descartan de la matriz:** P5, H6, H7, H8, H9, H10, H11, A6, A10, D4, D5, X3. H10: por ahora no
  hacen falta observaciones sobre el caso.
- **Observaciones opcionales en DENUNCIA y en CASO_ANIMAL.** En DENUNCIA, para la gente de Zoonosis (el
  F2 tiene ese campo). En CASO_ANIMAL, observaciones generales del seguimiento del animal (p. ej. «está
  dentro de un terreno al que no tenemos acceso»), distintas de la observación del día 10. Las carga
  Zoonosis.
- **TRATAMIENTO es solo de Salud**, incluidos L5–L7. El ciudadano no los declara.
- **L4 «recibió atención médica» se deriva** de que el caso tenga un TRATAMIENTO. Sale
  `CASO.atencion_medica` de la v1.
- **X1 certificado médico:** DOCUMENTO del caso, lo carga Zoonosis. Que lo adjunte el ciudadano es
  posible pero improbable; no se diseña por ahora.
- **X2 fotos:** las del animal se adjuntan a CASO_ANIMAL (ayudan a identificarlo); las del lugar se
  descartan.
- **A12 mordedor reincidente se descarta.** La reincidencia dentro de SIRAM se ve en los casos del
  animal. Sale `ANIMAL.reincidente` de la v1.
- **La marca Incompleto mide solo los campos del CASO.** Lo que falte en CASO_ANIMAL no la afecta: un
  caso puede resolverse del todo sin que sus animales tengan todo cargado. «Animal propio/ajeno» sale
  de los obligatorios de RN-25 (es la tenencia de CASO_ANIMAL).
- **Zona del cuerpo solo en TRATAMIENTO** (Salud). La info del caso y la de Salud van por separado;
  se acepta que los casos sin paso por Salud no la tengan. Sale `CASO.zona_cuerpo` de la v1.
- **Gravedad de la lesión (L2) en TRATAMIENTO.** Dato clínico. Sale `CASO.gravedad` de la v1.
- **`CASO.canal_origen` suma `historico`** (`ciudadano|salud|zoonosis|cadic|historico`). Marca los
  registros viejos o importados: justifica que el caso no tenga DNI (RN-21) y sirve de filtro. Cierra
  la brecha §7.9.
- **USUARIO: activo / inactivo.** No se borra (lo referencian casos e historial); el administrador lo
  desactiva y lo puede reactivar. La desactivación es una baja lógica en el historial.
- **Fecha de novedad de la bandeja = última modificación del caso** (campo automático), en lugar de
  derivarla de AUDITORIA. La ficha del caso ya no incluye el historial: lleva un acceso a su pantalla.
- **A11 «¿podría identificar al animal?» se queda**, en CASO_ANIMAL. Es una pregunta del formulario
  detallado del ciudadano; el diseño de ese formulario (secciones, preguntas) se decide más adelante.
- **RN-25 pierde «situación de la persona».** La Entrevista 1 la pedía sin definirla y su mapeo a
  H6/H8 era inferido (HZ11); con ambos descartados, sale de los obligatorios del caso. Cae también la
  equivalencia de «con quién estaba» (RN-24, HZ09).

## 2026-10-30 · Revisión de pendientes (hacia la versión 2)

- **DENUNCIA se modela con la propuesta en revisión** (CONTEXTO §9): DNI del denunciante (obligatorio,
  texto con validación de formato, sin enlace a PERSONA), fecha de la denuncia (obligatoria), número
  de trámite (opcional, texto libre) y observaciones (opcional). La carga solo Zoonosis (RN-06). No se
  sabe cómo la guarda Zoonosis ni si tiene identificador: se revisa más adelante con ellos. Se adopta
  igual porque ofrecerla en el diseño no hace perder nada y destraba la v2 y Figma.
- **Criterio para lo tentativo.** Todo pendiente que ya tiene propuesta o candidato se modela y se
  diseña tal como está, sin darlo por cerrado (CONTEXTO §9). Aplica, entre otros, a: motivos de
  desestimación, TIPO_EVENTO, lesión múltiple, criterio de `finalizado` (día 10), vacuna antirrábica
  como sí/no, observación solo al día 10, DNI en el formulario público y equivalencias de RN-24.
- **DOCUMENTO = nombre del archivo + URL** donde se aloja (más creación y última modificación,
  RN-27). Cuelga del caso (certificado médico) o de CASO_ANIMAL (fotos del animal). Sin tipo ni datos
  del certificado. Cierra la brecha §7.4. En la v1 era una entidad sin atributos.
- **TIPO_EVENTO se modela como está:** catálogo con cuatro valores (ataque con mordedura, lesión
  compatible, intento sin lesión, lesión derivada) y FK desde CASO, uno por caso. Tentativo.
- **CASO suma `motivo_desestimacion`** (fuera de alcance, fuera de la provincia, hecho inexistente o no
  verificable, cargado por error), obligatorio al desestimar, más una observación libre. Tentativo.
- **Lesión múltiple:** se mantiene como valor «Múltiples» del enumerado. Tentativo.
- **COINCIDENCIA y el vínculo entre casos quedan para más adelante** (junto con el motor nuevo).
- **Motor de coincidencias: es del backend.** Para el diseño alcanza con un aviso de que existe un
  registro que coincide, con el DNI como filtro principal. COINCIDENCIA queda como en la v1, tentativa.
- **Cola de solicitudes en `Casos › Solicitudes`.**
- **Formulario detallado del ciudadano: cuatro secciones tentativas** (dónde fue, qué pasó, el animal
  una vez por animal, la denuncia). Detalle y destino de cada pregunta en CONTEXTO RN-32.
- **Permisos por organismo: tentativa sacada de la narrativa** (CONTEXTO §9). Todos los agentes ven
  todos los casos; los datos comunes los edita cualquier agente y los de dominio solo su ente.
- **CADIC no tiene datos propios.** Es canal de alta y completa los datos comunes del caso.
- **Formulario detallado: dueño y chip entran** según de quién es el animal (mascota propia: chip;
  ajeno conocido: datos del dueño, opcional). Quedan en la solicitud hasta que Zoonosis los confirma.
- **Permisos tentativos: el equipo los da por buenos.** Falta validarlos con los organismos.
- **Obligatorio para nacer = RN-30 por canal; para estar completo = solo datos del caso.** Se da por
  hecho, a revisar. Los campos que cuentan para estar completo son una **suposición del agente de
  diseño** (fecha, ciudad, lugar, tipo de lugar, edad de la víctima, tipo de evento): revisarlos.
  Un caso **`finalizado` puede tener datos faltantes y no cuenta como incompleto** en los totales
  (p. ej. nunca se ubicó al perro o a la víctima); cierra también «caso sin contacto que nunca se
  ubica». Un caso **`desestimado` e incompleto sí se registra como incompleto**.
- **Desaparece el medidor de completitud de la ficha** («N de 50 campos») hasta nuevo aviso: venía
  del prototipo, no de una decisión del equipo. La ficha muestra la marca Incompleto.
- **TRATAMIENTO no va en el formulario del ciudadano:** lo ve y lo carga solo Salud (se mantiene lo
  del 2026-10-29).
- **La edad de la víctima se queda en el formulario detallado.**
- **Si el animal muere, el caso no finaliza: escala** y pide atención especial al tratamiento. Falta
  definir cómo se representa (estado nuevo o marca de alerta).
- **Pendiente: dónde se cuenta el desestimado incompleto** (RN-28 y RN-11 lo dejan fuera de todo
  total).
- **Denuncia «desglosada y devuelta» (HZ08): pendiente a revisión.** Posibilidad: estado en DENUNCIA
  (pendiente de confirmación, confirmada, desestimada), que choca con RN-13.
- **HZ03 y HZ16 cerrados:** H11 ya estaba descartado y HZ03 solo servía para importar el F2.
- **Sugerencia: no hay importación; la carga es manual.** Cae el lote de importación y, si se
  confirma, R.25 y Administración › Importar CSV. Los registros viejos cargados a mano usan
  `canal_origen = historico`.
- **Desestimado incompleto: dónde se cuenta queda para ver y completar más adelante** (delicado).
- **Las solicitudes descartadas se guardan para siempre**, con sus datos.
- **DENUNCIA con estado** (`pendiente_confirmacion · confirmada · desestimada`): es la opción con más
  peso para registrar la denuncia «desglosada y devuelta» (HZ08). Se modela así, tentativa; RN-13 («la
  denuncia no tiene estados») queda en revisión.
- **Personas sin DNI argentino:** pendiente importante, para más adelante.
- **Abuso del canal ciudadano:** importante, pendiente a modelar, no entra ahora.
- **Seguridad:** por ahora usuario y contraseña; 2FA y políticas de la Ley 25.326, más adelante.
- **Sin PostGIS:** la ubicación es latitud, longitud y textos; alcanza con PostgreSQL común.
- **Refine es una sugerencia a futuro** (posible migración del front en 4 a 6 meses, si sucede). Las
  versiones no afectan al diseño: el front ya usa las actuales.
- **Escalada cuando el animal muere: estado del caso `grave`.** Tentativo.
- **Caso con varios animales: ¿finaliza cuando todos pasan el día 10?** Pregunta pendiente para
  Zoonosis y/o Salud; no frena el diseño.
- **Seguridad y políticas de la Ley 25.326 quedan pendientes.** Registrar quién consultó qué es solo
  una sugerencia: no se modela.

## 2026-11-02 · Versión 2, borrador volcado en `siram.mmd`

`siram.mmd` pasa a contener la **v2 completa como borrador**. **No tiene tag**: todavía no es
contrato con el back. Vuelca todo lo de las entradas del 2026-10-23 al 2026-10-30; lo tentativo se
modela tal como está (criterio del 2026-10-30). Las convenciones comunes (id, creado/modificado,
sin borrado, historial espejo, «no_sabe» vs nulo) se anotan una vez al principio del archivo, y
del historial se dibuja solo CASO_HISTORICO como ejemplo.

**Entidades:** ORGANISMO, USUARIO, TIPO_EVENTO, PERSONA, CASO, SOLICITUD, ANIMAL, CASO_ANIMAL,
DESCRIPCION, TRATAMIENTO, DENUNCIA, DOCUMENTO, COINCIDENCIA, más las tablas de historial. Salen
PARTICIPACION y AUDITORIA.

**Tomado de la demo de Figma** (`diseno/figma/demo.md`, tentativo):
- `CASO_ANIMAL.observacion_dia10`: `pendiente|sin_novedad|murio_o_enfermo|no_se_pudo_observar`, más
  su fecha. CONTEXTO no definía los valores.
- `CASO.numero` (C-AAAA-NNNN) y `SOLICITUD.numero` (S-AAAA-NNNN) como identificadores visibles.
- `CASO_ANIMAL.orden` («Animal 1 de N»).
- Valores de `TRATAMIENTO.zona_cuerpo` según el gráfico de Inicio (piernas, manos, brazos, cara,
  tronco, múltiples).

**Supuestos del agente de diseño (a revisar por el equipo):**
1. **La edad de la víctima va en CASO** (`victima_edad`, al momento del hecho), no en PERSONA. La
   persona es única por DNI y puede aparecer en casos de años distintos; una edad en PERSONA queda
   vieja y rompe la franja etaria. Contradice «la edad es de PERSONA» (CONTEXTO §9).
2. **Nombre y apellido separados** en PERSONA, como pide el formulario inicial.
3. **L1 (tipo de lesión) desaparece como campo:** lo absorbe TIPO_EVENTO («Me mordió → Ataque con
   mordedura» en la demo); la ficha de Figma no tiene L1. Sale `CASO.tipo_lesion` de la v1. Cierra a
   medias HZ05: falta confirmar con el cliente.
4. **Ciudad como enumerado** (`ushuaia|rio_grande|tolhuin|otra`) más `ciudad_otra` en texto.
5. **SOLICITUD:** el formulario inicial en columnas (para listar y buscar por DNI) y el detallado en un
   JSON `detalle`, tal cual lo declaró la persona; `secciones_completas` para la cola. Token guardado
   como hash. `motivo_descarte` en texto libre, opcional (no había nada definido).
6. **DOCUMENTO puede colgar de SOLICITUD** (fotos que manda la persona antes de que exista el caso).
   Exactamente una de las tres FK (caso, caso_animal, solicitud).
7. **USUARIO:** `organismo_id` nulo para administrador y analista; `correo` como usuario de acceso;
   `rol` = `administrador|agente|analista`. ORGANISMO.tipo = `salud|zoonosis|cadic`, que es lo que
   usan los permisos de dominio (RN-35).
8. **TRATAMIENTO: uno por caso** (0..1).
9. **COINCIDENCIA suma `desenlace`** (`consolidado|vinculado|no_relacionados`). El glosario dice que
   guarda «la decisión del agente», y la v1 no tenía dónde. El resto sigue como en la v1, tentativo.
10. **La marca Incompleto no se guarda:** se deriva de los campos del caso (RN-25). El back puede
    guardarla en caché para filtrar.
11. **Un caso tiene al menos un animal** (`CASO ||--|{ CASO_ANIMAL`): todos los canales piden la
    especie al nacer (RN-30).

**El paso a `grave` es manual** (decisión de Darío, mismo día): lo hace un agente, porque alguien
registró que el animal murió. Cargar `murio_o_enfermo` en el día 10 no cambia el estado solo.

### Revisión de los supuestos con Darío (mismo día)
- **Supuesto 1, confirmado:** la edad de la víctima va en `CASO.victima_edad`. Antes nunca se había
  decidido: estaba en PERSONA desde la v1 sin discusión, y CONTEXTO §9 lo repetía.
- **Supuestos 2, 5, 6 y 7: confirmados.** El 3 (L1 absorbido por TIPO_EVENTO) se mantiene, a
  confirmar con el cliente.
- **Supuesto 4, cambia: CIUDAD pasa a ser una tabla** (nombre, activo), por si el sistema escala.
  `CASO.ciudad_id` FK; si la persona elige «Otra», queda `ciudad_id` nulo y el texto en
  `ciudad_otra`. Lleva historial. **No se decidió quién la mantiene ni desde qué pantalla**: no se
  agrega nada a la navegación.
- **Los datos de un animal no cuentan para la marca Incompleto** (se mantiene RN-25). La descripción
  ya es opcional en bloque (DESCRIPCION 0..1): si el animal está identificado (propio, con chip, se
  sabe dónde está), no hace falta describirlo. Lo que está mal es la demo de Figma (E4), que marca
  incompleto un caso con todos sus datos de caso completos.
- **Por lo tanto, «el perro nunca se ubicó» no hace incompleto al caso**, y no hace falta un campo
  para la aclaración de la bandeja: sale de `CASO_ANIMAL.observacion_dia10 = no_se_pudo_observar`.
  El finalizado incompleto queda para cuando faltan **datos del caso**, p. ej. nunca se ubicó a la
  víctima ni al contacto y faltan su edad o el tipo de lugar. Corrige el ejemplo de CONTEXTO §9.
- **El historial se modela completo:** las 13 tablas espejo están en `siram.mmd`, generadas a partir de
  los campos de cada entidad (USUARIO sin credenciales). Sus campos propios llevan el prefijo `hist_`
  (`hist_id`, `hist_operacion`, `hist_fecha_hora`, `hist_usuario_id`, `hist_organismo_id`,
  `hist_caso_contexto_id`) para no chocar con los campos copiados, p. ej. `USUARIO.organismo_id`.
- **Día 10: «no se pudo observar» se separa en dos valores.** `ubicado_sin_acceso` (se sabe dónde está,
  p. ej. un terreno cerrado) y `no_ubicado` (nunca se encontró). Queda
  `pendiente|sin_novedad|murio_o_enfermo|ubicado_sin_acceso|no_ubicado`, tentativo. La aclaración de la
  bandeja «el perro nunca se ubicó» se deriva de `no_ubicado`.
- **Personas sin DNI argentino:** sigue pendiente, para una nueva entrevista con Salud o Zoonosis.
- **Vacuna antirrábica:** queda sí/no; es lo único que se sabe que necesita Salud. Puede cambiar en la
  segunda entrevista.
- **Hueco detectado: no está definido quién finaliza un caso ni cuándo.** Por los permisos tentativos
  (CONTEXTO §9), el estado es un dato común y lo cambia cualquier agente; el criterio (día 10) sigue
  pendiente con Zoonosis. Tampoco hay una tabla de transiciones entre estados.
- **COINCIDENCIA se simplifica: solo duplicados, detectados por el DNI de la víctima.** Un caso nuevo
  cuya víctima ya es víctima de otro caso genera una coincidencia y el aviso al guardar. El agente
  decide: **consolidar** (el mismo hecho cargado dos veces) o **distintos** (otro ataque a la misma
  persona), con una observación libre. Campos: `caso_a_id` (el que existía), `caso_b_id` (el nuevo),
  `desenlace` (`consolidado|distintos`, nulo = pendiente), `observacion`, `resuelta_por_usuario_id`,
  `resuelta_en`. Se guarda para que el aviso no vuelva a salir. Salen `tipo`, `puntaje`, `senales` y
  `revision` de la v1: sin motor por puntaje (RN-16) no hacen falta. Sin ventana de días: el agente ve
  las dos fechas del hecho. Se compara el DNI de la **víctima**, nunca el de quien informa.
- **El evento relacionado deja de ser una coincidencia: se deriva del animal.** Dos casos que
  comparten un ANIMAL son del mismo animal; no hace falta guardarlo ni que un agente lo confirme. Si
  el animal no tiene chip y se descubre que es el mismo, se **reconcilian los animales** (RN-22) y la
  relación aparece sola. Caen el desenlace «vincular» y su reversión (RN-14), y la brecha §7.10.
  La lista «Eventos relacionados» y su marca, si se mantienen, se calculan.
- **Los históricos sin DNI no generan aviso.** Excepción aceptada.


## 2026-11-03 · Estados del caso: versión mínima para la alfa

Contexto: discutiendo la máquina de estados del caso aparecieron varias ideas buenas pero que no
hacen falta para una alfa. Darío: «estamos sumando demasiada complejidad y el proyecto no esta ni en
alfa». Se toma lo mínimo y el resto queda anotado abajo, sin modelar.

**Entra en la v2:**
- **`grave` deja de ser un estado y pasa a ser una marca derivada** (CONTEXTO RN-11): un caso es
  grave si alguno de sus CASO_ANIMAL tiene `observacion_dia10 = murio_o_enfermo`. Lo indica Zoonosis
  al cargar el día 10; no hay un segundo paso manual. Reemplaza el estado tentativo del 2026-10-30 y
  el «paso manual» del 2026-11-02. Motivo: como estado, un caso grave dejaba de serlo al finalizar y
  se perdía el dato. `CASO.estado` vuelve a `registrado|en_seguimiento|finalizado|desestimado|unificado`.
  No suma campos.
- **Tabla de transiciones mínima** (CONTEXTO RN-36), con estas respuestas por defecto:
  1. No se reabre un caso `finalizado`, `desestimado` ni `unificado`; un error se corrige editando.
  2. Sin reapertura, no hace falta motivo de reapertura.
  3. No existe `en_seguimiento → registrado`.
  4. «¿Un grave puede esperar algo?» desaparece: grave ya no es estado.
  Además: `finalizado → unificado` se permite (un duplicado puede descubrirse después de cerrar).
- El motivo de espera sigue como estaba (RN-10).

**Queda para después de la alfa** (pensado el 2026-11-02/03, sin modelar):
- **Regiones paralelas** (statechart): el caso con su estado global y un proceso por dominio que
  avanza en paralelo: atención de la víctima (Salud), seguimiento de cada animal (Zoonosis, ya existe
  como `observacion_dia10`) y contacto con la víctima. `→ finalizado` se permitiría cuando todas las
  regiones llegaron a un estado final; eso respondería buena parte del criterio de finalizado.
- **Contacto como región propia** (opción B; Darío se inclinó por ella): `pendiente → buscando →
  contactado | no_ubicado`. Permitiría varias esperas a la vez y contar las víctimas nunca ubicadas.
  Si entra, el motivo de espera probablemente desaparece.
- **`TRATAMIENTO.estado`**, con valores tentativos (p. ej. `solo_curacion · profilaxis_completa ·
  profilaxis_abandonada`). Daría la distribución de los casos cerrados según hasta dónde llegó la
  atención, cruzable con `gravedad` de la lesión. Con la marca Grave, la atención de Salud tendría que
  poder reabrirse.
- **Marca «expuesto a animal en alerta»**: otro caso del mismo ANIMAL es grave y este cae dentro de
  una ventana de exposición. Solo alcanza a los casos que comparten el ANIMAL (sin reconciliar, no salta).
- **Vista `Casos › Graves`** (solo vigentes, como las demás listas de trabajo) e **ícono «en alerta»**
  en la lista de Animales.

**Preguntas para las entrevistas** (no frenan la v2):
- Salud: ¿qué etapas tiene la atención y cómo se cierra? ¿Estos valores tentativos son correctos?
- Salud y Zoonosis: si un animal muere o enferma, ¿qué otros casos del mismo animal están en riesgo
  (la ventana de exposición)?

**Ciudad sin «Otra»** (Darío, mismo día): las únicas ciudades son Ushuaia, Río Grande y Tolhuin. Sale
`CASO.ciudad_otra` (y su copia en CASO_HISTORICO); `ciudad_id` queda como FK simple a CIUDAD. Corrige
el supuesto 4 del 2026-11-02 y su revisión. La opción «Otra» venía de la demo de Figma (Público ›
Dónde fue) y de RN-32: hay que quitarla de Figma.
Un hecho fuera de las tres ciudades (estancia, ruta) **se registra igual con una de ellas**; el punto
exacto queda en `latitud`/`longitud` (RN-33). No hace falta un valor nuevo.

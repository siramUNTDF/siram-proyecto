# Correcciones de las fichas del front (2026-11-03)

> Resolución de cada hallazgo de la revisión de coherencia. **Es la referencia común** para corregir
> las fichas: todas usan estos valores y esta historia. Fuentes: CONTEXTO, `modelo/siram.mmd` (v2
> borrador) y `modelo/decisiones.md` (las decisiones del 2026-11-02/03 mandan sobre textos viejos de
> CONTEXTO, que se actualiza en paralelo).

## A. Valores que mandan (del modelo y de decisiones.md)

1. **Observación del día 10 (5 valores):** `pendiente · sin_novedad · murio_o_enfermo ·
   ubicado_sin_acceso · no_ubicado`. En pantalla: «Pendiente · Sin novedad · Murió o enfermó ·
   Ubicado, sin acceso · No se ubicó». `murio_o_enfermo` = marca Grave. Ninguno de los cinco hace
   incompleto al caso. **No existe «no se pudo observar».**
2. **Aclaración de la Bandeja / ficha en un caso finalizado:** solo si algún animal quedó
   `no_ubicado`: «Un animal no se ubicó». (No por `ubicado_sin_acceso`.) JSON: `"animalNoUbicado": true`.
3. **Tipo de lesión (L1) no existe** (lo absorbió el tipo de evento). Sale de Estadísticas, Búsqueda,
   Tipos de evento y narrativa. Lo clínico que queda es la **gravedad** (L2) y la **zona del cuerpo**, del
   tratamiento.
4. **Rol:** `administrador · agente · analista` (en pantalla el analista puede llamarse «Consulta»,
   pero el valor es `analista`). **Administrador y analista no tienen organismo**; el agente sí,
   obligatorio.
5. **Tipo de organismo:** `salud · zoonosis · cadic`. Define los permisos de dominio (lo usa el back).
   Ministerio de Salud y UNTDF no son organismos de carga: sus usuarios son administradores o
   analistas, sin organismo.
6. **Especie:** solo `perro · gato`. Nunca «No sé» (tampoco en el formulario público).
7. **Un caso siempre tiene al menos un animal** (nace con la especie del formulario inicial).
8. **Documento:** solo nombre y URL. No tiene `tipo`: es «certificado médico» si cuelga del caso, y
   «foto» si cuelga de un animal.
9. **Denuncia:** sin campo `ente` (siempre Zoonosis). Campos: DNI de quien la hizo, fecha, número
   (opcional), estado (tentativo: pendiente de confirmación · confirmada · desestimada), observaciones.
10. **Edad:** vive en el caso (edad de la víctima al momento del hecho). **La persona no tiene edad.**
11. **Coincidencia (posible duplicado):** por DNI de la víctima; desenlaces `consolidado · distintos`,
    con `observacion` opcional. **Sin señales ni chips de «qué coincide»**: el aviso dice solo que la
    víctima tiene el mismo DNI.
12. **Tenencia, dueño, chip, día 10 y observaciones del animal: solo Zoonosis** (§9). Cualquier agente
    puede agregar un animal con **especie (obligatoria) y descripción**; la tenencia es opcional y solo
    la ve editable Zoonosis.
13. **Lo que la persona declaró sobre el dueño y el chip** queda en la solicitud hasta que Zoonosis lo
    confirma (RN-32). Al registrar o sumar, **no se copia** a dueño ni a chip (la tenencia declarada y
    la descripción sí se copian). En la ficha del caso,
    Zoonosis lo ve en el animal como «Según la solicitud S-…: dueño …, chip …» y lo pasa a los campos
    con Editar seguimiento.
14. **Analista:** ve agregados del tratamiento, del día 10 y de las denuncias, nunca por caso (§9). En
    Exportar no tiene esos bloques por caso.
15. **Salud no ve la descripción del animal** (§9): ni en la ficha, ni en el Mapa (panel y filtros de
    tamaño/color), ni en Búsqueda (filtros de tamaño/color/raza).

## B. Decisiones de diseño (del agente de diseño, 2026-11-03)

1. **«Es otro ataque, guardar igual» / «… registrar igual» = desenlace `distintos`.** El caso se crea
   **sin** marca de posible duplicado y la coincidencia queda resuelta (no vuelve a avisar). Si el
   agente no está seguro, la otra salida es «Abrir C-…» y decidir ahí.
2. **«Graves» cuenta lo mismo en Inicio y en la Bandeja: casos con la marca Grave en estado
   registrado o en seguimiento.** Los graves finalizados conservan la marca (se ven en la Bandeja con
   «Todos» y en Búsqueda) pero no entran en el chip ni en la tarjeta.
3. **«No es duplicado» es una sola interacción** en la ficha y en la comparación: ventana lateral con
   observación opcional.
4. **Filtros por URL en la Bandeja:** la Bandeja acepta `?filtro=graves|incompletos|duplicados|
   en_seguimiento` (activa el chip) y `?motivo=contacto|respuesta|certificado` (con el chip «En
   seguimiento», muestra un «Filtro aplicado» quitable: «Motivo: Esperando contacto»). Inicio usa eso.
5. **Editar el caso** (no está en Figma; se especifica en la ficha del caso): ventana lateral con los
   bloques de **datos comunes** — Víctima (nombre, apellido, DNI, edad al momento del hecho, teléfono,
   correo, domicilio), Contacto responsable (agregar/quitar/editar), Hecho (fecha, hora, ciudad,
   ubicación con pin + dirección + referencias, tipo de lugar), Tipo de evento. La editan todos los
   agentes. Es lo que permite salir de Incompletos.
6. **Editar seguimiento de un animal** y **corregir una denuncia**: misma ventana que Agregar animal /
   Anotar denuncia, en modo edición, desde el menú `⋮` de cada uno. Solo Zoonosis.
7. **Formulario público:** «Terminar acá» en la pantalla 2 → Gracias. «Más de 3» animales: la parte del
   animal se repite 3 veces; cuántos fueron en total queda como hueco (no se manda a «referencias»).

## C. La historia única de los datos de ejemplo (todas las fichas la respetan)

- **C-2026-0418** · canal **zoonosis** · registrado el **12/09/2026 15:02** por M. Acosta (Zoonosis
  Ushuaia) · víctima **Micaela Sosa**, 7 años, DNI 58.412.336 · contacto responsable **Carla Sosa**, DNI
  32.114.887, tel. 2901-54-8820 · hecho 12/09/2026 14:20, Kuanip 1240, Ushuaia, referencias «Frente a la
  plaza, casa de rejas verdes» · **tipo de lugar: sin dato** (por eso tiene la marca **Incompleto**) ·
  tipo de evento: Ataque con mordedura · **2 animales**: (1) perro, chip 900 123 456 789 012, ajeno
  conocido, dueño Raúl Benítez, día 10 sin novedad (22/09); (2) perro sin chip, ajeno desconocido, día
  10 **no ubicado** · estado **registrado** · marcas **incompleto, duplicado**.
  - 12/09 15:05: Zoonosis anota la denuncia ZU-2026-1180 (confirmada, DNI 32.114.887).
  - 12/09 15:10: se le suma la solicitud **S-2026-0031** (enviada 12/09 10:30 por Carla Sosa):
    declaró **¿Hizo denuncia? Sí**.
  - 13/09 08:40: **Sistema** avisa coincidencia con **C-2026-0402** (mismo DNI de víctima).
  - 13/09 09:12: L. Puig (Hospital Regional Ushuaia) carga el tratamiento (consulta 12/09) → es la
    **última modificación** de la Bandeja.
  - Historial: 7 cambios (registro, denuncia, solicitud, edición del color del animal 1, edición de
    Carla Sosa desde C-2026-0411, aviso del Sistema, tratamiento). La ficha dice «7 cambios · el
    último, 13/09/2026 09:12 por L. Puig».
- **C-2026-0402** · canal salud · registrado **13/09/2026 08:35** por J. Benítez (Hospital Regional
  Ushuaia) · víctima «M. Sosa», DNI 58.412.336 · marca **duplicado**. En la comparación: **A = 0418** (ya
  existía, sobrevive), **B = 0402** (queda unificado si se consolida).
- **S-2026-0034** · **pendiente** · enviada 13/09/2026 21:40 por Carla Sosa (informa por otra persona) ·
  víctima Micaela Sosa, DNI 58.412.336 → coincidencia con C-2026-0418 (es el escenario «la solicitud
  coincide con un caso»). Sus respuestas sobre la denuncia: No · «No sabía dónde denunciar» (si se suma,
  pasa a ser lo declarado más reciente).
- **Animal reconciliado:** el perro con chip 900 123 456 789 012 absorbió el 13/09 a un perro sin chip
  que había sido cargado en C-2026-0402. El absorbido queda **0 casos**, inactivo, «absorbido por chip
  …»; el del chip queda en 2 casos (0418 y 0402).
- **Usuarios de ejemplo:** M. Acosta (agente, Zoonosis Ushuaia), L. Puig (agente, Hospital Regional
  Ushuaia), J. Benítez (agente, Hospital Regional Ushuaia), D. Marchisoney (**administradora, sin
  organismo**), F. Luna (**analista, sin organismo**).
- **Organismos de ejemplo:** Zoonosis Ushuaia (zoonosis), Hospital Regional Ushuaia (salud), Hospital
  Regional RG (salud), CAPS 3/4/5 (salud), CADIC (cadic).

## D. Nombres de campos en los JSON de ejemplo (todas las fichas iguales)

`numero` · `victima: { nombre, apellido, dni, edad, telefono, correo, domicilio }` (en listas se
muestra «nombre apellido») · `contactoResponsable` (misma forma, sin edad) · `informaLaVictima` ·
`quienInforma` (en solicitudes) · `animales[]: { especie, chip, tenencia, dueno, vacunado,
dia10, descripcion: { tamano, sexo, edadAparente, color, raza, podriaReconocerlo } }` ·
`canalOrigen` · `estado` · `motivoEspera` · `marcas` · `ultimaModificacion: { fecha, por }` ·
`fechaHecho` · `horaHecho` · `tipoLugar` · `tipoEvento`. Fechas en ISO (`2026-09-12`), horas `HH:MM`.

## E. Segunda revisión (2026-11-03): resoluciones que **reemplazan** lo anterior donde choquen

1. **Tercera salida del aviso de DNI repetido en Nuevo caso: «Guardar y revisar después».** Crea el
   caso **con** la marca posible duplicado (coincidencia pendiente, el Sistema la registra en el
   historial en el mismo momento del alta). Quedan tres salidas: «Abrir C-…» (no crea), «Es otro
   ataque, guardar igual» (= distintos, sin marca) y «Guardar y revisar después» (con marca, se decide
   en Posibles duplicados). **En Solicitudes no hay tercera salida**: si es el mismo hecho, se suma.
2. **Comparar: A = el caso desde el que se abre la comparación, y es el que sobrevive.** Ya no «el
   más viejo». (B en la sección C queda corregido abajo.)
3. **Historia corregida (reemplaza partes de la sección C):**
   - **C-2026-0402** (Salud, J. Benítez, Hospital Regional Ushuaia) se registró **antes**: 12/09/2026
     **14:50** (la víctima fue primero a la guardia). Última modificación: **13/09 11:20 · M. Acosta**
     (al reconciliar su animal con el del chip).
   - **C-2026-0418** se registró el 12/09 **15:02**; el agente eligió «Guardar y revisar después», así
     que el **Sistema** anota la coincidencia con 0402 a las **15:02** (no 13/09 08:40).
   - **S-2026-0031**: enviada 12/09 **14:50**, sumada 15:10.
   - Certificado médico adjuntado por Zoonosis el 13/09 10:00; día 10 de los dos animales cargado el
     **22/09** por M. Acosta (animal 1 sin novedad, animal 2 no ubicado). → **Última modificación de
     0418: 22/09/2026 10:15 · M. Acosta.** Historial: **13 cambios** (registro + aviso del Sistema
     15:02, edición del caso 15:03 (edad, ciudad, dirección, tipo de evento), animal 1 completado y
     animal 2 agregado 15:04, denuncia 15:05, solicitud 15:10, color del animal 1, edición de Carla
     Sosa **desde Consultas › Personas**, tratamiento 13/09 09:12, certificado 13/09 10:00, día 10
     animal 1, día 10 animal 2).
     Los datos de ejemplo son «al 25/09/2026».
   - **C-2026-0411** (Joaquín Ojeda) está unificado en **C-2026-0408** (otro caso de Joaquín Ojeda,
     Hospital Regional RG, vigente), no en 0402.
   - **Micaela Sosa** es víctima en **2 casos** (0418 y 0402). Como la persona es única por DNI (RN-20), en los dos
     casos es **la misma persona con los mismos datos**: en Comparar, sus filas son iguales, y lo que se
     confirma al consolidar es que es **el mismo hecho**. **Carla Sosa**: correo «sin dato» en
     SIRAM (el correo `carla.sosa@correo.com` está solo en la solicitud S-2026-0034, pendiente).
   - **Usuarios:** **D. Marchisoney es agente de Zoonosis Ushuaia** (puede modificar casos); el
     administrador de ejemplo es **S. Valle** (sin organismo); analistas: F. Luna y L. Godoy (sin
     organismo). Las sumas de usuarios por organismo tienen que coincidir con el total de agentes
     activos de Usuarios.
   - Cifras de Inicio/Estadísticas: el canal de origen suma 127; la zona del cuerpo y la gravedad
     suman lo mismo que «casos vigentes con tratamiento» (si se dice un número, que cierre).
4. **Exportar respeta §9 por campo:** Zoonosis y CADIC no exportan el tratamiento completo, solo
   «recibió atención (sí/no)»; Salud y CADIC no exportan las denuncias, solo «tiene denuncia (sí/no)»
   (lo declarado sí). El analista, sin datos por caso de tratamiento, día 10 ni denuncias.
5. **Salud no ve la descripción del animal en ningún lado**, tampoco en Comparar ni en Revisar o Sumar
   una solicitud: esas filas no se muestran si la API no las manda.
6. **Valores de enumerados en los JSON, en snake_case** (`"zonaCuerpo": "piernas"`, `"tamano":
   "mediano"`); la etiqueta de pantalla es aparte. `dia10` es siempre un objeto `{ "valor", "fecha",
   "por" }`. Fecha y hora del hecho: `fechaHecho`, `horaHecho`; dirección: `lugar.direccion`.
7. **Textos unificados:** «No es duplicado» cierra con «Cancelar · Guardar». La acción sobre un animal
   ya cargado es **«Editar animal»** (todos los agentes editan la descripción; dueño, chip, tenencia y
   seguimiento, solo Zoonosis). Reemplaza «Editar seguimiento» de B.6.
8. **Sumar S-2026-0034:** sus dos animales se comparan con los dos del caso (el animal 2 es el mismo
   perro grande marrón → no se agrega uno nuevo). Cómo se emparejan los animales en general sigue
   abierto (CONTEXTO §9).
9. **Organismo:** sale del usuario; nunca se elige en un caso nuevo. **Consolidar:** hasta que se
   defina la «persona autorizada» (RN-15, abierto), lo puede hacer cualquier agente; la ficha no pide
   un permiso propio.
10. **Mapa:** tamaño y color se cumplen **en el mismo animal**.
11. **Fuera las notas «Figma dice…/muestra…»**: Figma está corregido (`figma/cambios.md`).

## F. Tercera revisión (2026-11-03)

- La edición de Carla Sosa del 12/09 16:10 (desde Consultas › Personas) es su **domicilio** (— →
  Kuanip 1240, Ushuaia), no el teléfono: el teléfono 2901-54-8820 ya vino en el alta.
- Al sumar S-2026-0034 a C-2026-0418 **no hay filas distintas**: todo es igual salvo el correo del
  contacto, que está solo en la solicitud y se conserva.
- Comparar manda la coincidencia y cuál sobrevive (`coincidencia`, `sobrevive`, `absorbido`); A y B son
  izquierda y derecha de la pantalla, no los `caso_a`/`caso_b` del modelo.
- Mapa: filtros de ejemplo «Tamaño: Mediano» y «Color: Negro» (el color, como texto contenido); 0418
  entra por su animal 1.
- Salud tampoco ve la tenencia declarada en Revisar o Sumar una solicitud. RN-15 (CONTEXTO): la
  confirmación es sobre el hecho.
- Cuarta revisión: al sumar S-2026-0034 se conservan **dos** datos que están solo en la solicitud, el
  correo del contacto y el **tipo de lugar** («Vía pública»); con eso C-2026-0418 deja de ser
  incompleto. Al sumar S-2026-0031 (15:10) se copiaron el color del animal 1 («Negro») y el domicilio de
  la víctima. Los datos del animal de 0402 (tenencia, dueño, descripción) los cargó Zoonosis al
  reconciliar (13/09 11:20).

## Estado del trabajo

**Terminado el 2026-11-04.** Las 18 fichas, la narrativa, CONTEXTO y Figma quedaron coherentes entre sí
tras cuatro revisiones (la última, acotada a las correcciones de la tercera). Lo que sigue abierto
está anotado como «Pendiente» en cada ficha y en CONTEXTO §9.

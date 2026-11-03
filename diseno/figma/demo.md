# Figma · página «Demo» (lectura del 2026-11-02)

> Fuente: copia del archivo en los borradores de Darío, `XVsGftAljNd8JrT8APDtWp`, página `Demo` [110:310].
> Es una foto del 2026-11-02: si el original (`XC7e02ZzIfQwmALf1RHgiZ`) cambia, esto queda viejo.
> Se leyó por el conector de Figma (textos y estructura, sin imágenes). Lo que sigue resume cada
> lámina; los textos entre comillas son literales.

40 láminas de 1920×1080. Cada una tiene a la izquierda el texto del paso (escenario, «Paso n de m»,
actor, título, bajada) y a la derecha una instancia de una pantalla real del diseño (1160×920).
Pie fijo: «SIRAM · Demo de uso · datos de ejemplo». La portada dice: «Avanza sola cada 7 segundos;
un clic adelanta».

Páginas del archivo: Fundamentos · Inicio · Casos · Consultas y Administración · Formulario público ·
Archivo v1 · Demo.

---

## Escenario 1 · Camino completo (12 pasos)
«De la solicitud de la ciudadana al caso finalizado, pasando por Zoonosis y Salud.»

| # | Actor | Paso | Pantalla | Qué muestra |
|---|---|---|---|---|
| 1 | Ciudadana | Carla avisa que mordieron a su hija | Público › 1 · Formulario inicial | «¿Sos quien sufrió el ataque?» (Sí / No, informo por otra persona). Tus datos: nombre, apellido, DNI, teléfono, correo (todos *). Quién sufrió el ataque: nombre, apellido, DNI (*); «No hace falta su teléfono ni su correo: te contactamos a vos.» El hecho: fecha (*), animal Perro/Gato (*). Aviso «Esto no es un canal de emergencias». Pie Ley 25.326. |
| 2 | Ciudadana | Recibe un número y puede contar más | Público › 2 · Solicitud enviada | «Número S-2026-0034». Invita al detallado: 4 partes, opcional, se guarda al pasar. «Es una sola oportunidad: este enlace vence en 1 hora». Contar más / Terminar acá. |
| 3 | Ciudadana | Marca dónde fue | Público › 3 · Dónde fue (1 de 4) | Pin en mapa (© OpenStreetMap), dirección propuesta «Kuanip 1240», referencias, ciudad (Ushuaia, Río Grande, Tolhuin, Otra — *2026-11-03: «Otra» no va*), tipo de lugar (5 + No sé), hora. |
| 4 | Ciudadana | Describe al perro | Público › 5 · El animal (3 de 4) | «Animal 1 de 2». De quién es (Es mío / De alguien que conozco / No sé de quién es), dueño si lo sabe, dónde vive, vacunado, ¿podrías reconocerlo?, tamaño, sexo, edad aparente, color, raza, fotos. «Si es tuyo, te preguntamos si tiene chip». |
| 5 | Sistema | Entra a la cola de solicitudes | Casos › Solicitudes | Filtros Pendientes (3) · Registradas (14) · Descartadas (5) · Todas (22). Columnas: solicitud, enviada, quién la envía, víctima, fecha del hecho, especie, formulario detallado (Completo 4 de 4 / Parcial / Solo inicial), coincidencia («Misma víctima que C-2026-0418»), Revisar. Pie: «Descartar no borra…». |
| 6 | Agente de Zoonosis | Un agente la revisa | Solicitudes · Revisar solicitud | Acciones: Descartar · Sumar a un caso existente · Registrar como caso nuevo. Todo lo declarado por bloques; «Qué pasó: Me mordió → Ataque con mordedura»; 2 animales; denuncia declarada: No, «No sabía dónde denunciar». |
| 7 | Agente de Zoonosis | Nace el caso C-2026-0418 | Casos › Ficha del caso · v2 | Ficha completa (ver «Ficha v2» abajo). Bajada: «El caso guarda su canal de origen: ciudadano». |
| 8 | Salud | Salud carga la atención | Ficha · Cargar tratamiento (ventana lateral) | Fecha de consulta (*), zona del cuerpo, gravedad (excoriación · herida superficial · herida profunda · amputación), antirrábica, antitetánica, antibiótico, sutura (Sí/No), observaciones. «“Recibió atención médica” no se carga: se deduce…». Nota: el esquema de dosis está por consultar con Salud. |
| 9 | Zoonosis | Zoonosis anota la denuncia | Ficha · Anotar denuncia · v2 | DNI de quien la hizo (*), fecha (*), número de trámite (opcional), **estado (*)**: pendiente de confirmación · confirmada · desestimada (tentativo, ejemplo HZ08), observaciones. «El DNI… no se enlaza a ninguna persona». |
| 10 | Zoonosis | Observa al perro el día 10 | Ficha del caso · v2 | La misma ficha; animal 1 «Sin novedad · 22/09/2026 · M. Acosta». |
| 11 | Zoonosis | Se finaliza el caso | Ficha · Cambiar estado · v2 | Nuevo estado: Registrado · En seguimiento · Finalizado · Grave · Desestimado. Ayudas: finalizar con datos faltantes deja de contar como incompleto; Grave = el animal murió en la observación; Desestimado pide motivo; Unificado no se elige, resulta de consolidar. |
| 12 | Sistema | Queda registrado y cuenta en las estadísticas | Casos › Bandeja · v2 | Orden por última modificación. Filtros: Todos (11) · Incompletos (3) · Posibles duplicados (2) · Eventos relacionados (2) · En seguimiento (2) · Graves (1). Columnas: marcas, caso, última modificación (+ quién), fecha del hecho, víctima (+ edad), lugar (+ ciudad), animales («Perro +1 animal»), tipo de evento, estado (+ motivo/aclaración), canal de origen. |

**Ficha v2** (C-2026-0418), en orden: cabecera (marca, «Ataque con mordedura · Ushuaia · 12/09/2026»,
Editar, Cambiar estado, estado, organismo, «Registrado por M. Acosta · 12/09/2026 15:02 · canal de
origen: Zoonosis») · Víctima (P1, P2, P6, P4, P3, P7) · Contacto responsable · Hecho (H1–H5, T1,
referencias, pin con coordenadas) · Animales · 2 (por animal: identidad y tenencia: A1, chip, A5,
dueño durante el caso con DNI, A7, A8; descripción: A2, A9, edad aparente, A13, A4, A11; seguimiento
Zoonosis: día 10 y observaciones; fotos del animal; «Agregar animal») · Tratamiento · Salud ·
Denuncias · Zoonosis (número, fecha, estado «Confirmada», DNI, observaciones, quién la anotó;
«Anotar denuncia») · Lo que declaró la persona (D1, D3) · Solicitudes · Documentos (X1 certificado
médico, «Adjuntar documento») · Historial («5 cambios…», «Ver historial»).

## Escenario 2 · La solicitud coincide con un caso (4 pasos)
1. *Sistema* · Llega otra solicitud por Micaela: cola de solicitudes (la misma lámina que E1·05).
2. *Agente de Zoonosis* · El agente ve el aviso: revisar solicitud con aviso «La víctima ya está en
   un caso: el DNI 58.412.336 es víctima en C-2026-0418…».
3. *Agente de Zoonosis* · Elige campo por campo: «Sumar S-2026-0034 a C-2026-0418». Tabla campo /
   en la solicitud / en el caso con =, ≠ y «Se conserva». Aviso: lo declarado sobre la denuncia se
   copia siempre (gana la solicitud más reciente). Casilla «Confirmo que la solicitud es del mismo
   hecho que el caso». «Falta elegir el teléfono del contacto»; el animal 2 se agrega como animal
   nuevo del caso.
4. *Sistema* · Todo queda en el historial: «Historial · C-2026-0418», filtros por entidad (Todo 7 ·
   Caso · Personas · Animales · Tratamiento · Denuncias · Solicitudes), «Ver cómo estaba en una
   fecha». Cada evento: actor + organismo + fecha, frase y cambio «antes → después». Incluye un
   cambio de persona compartida hecho desde otro caso y un aviso automático del Sistema.
   «El historial no se edita ni se borra. Las credenciales… nunca se copian en él.»

## Escenario 3 · El animal muere en la observación (4 pasos)
1. *Zoonosis* · registra que el perro murió: ventana «Agregar animal» con Observación del día 10:
   **Pendiente · Sin novedad · Murió o enfermó · No se pudo observar**. «Si murió o enfermó, el caso
   pasa a Grave. Si nunca se ubica, el caso puede finalizar incompleto.»
2. *Zoonosis* · El caso pasa a Grave: Cambiar estado (la misma lámina que E1·11).
3. *Sistema* · Aparece en el inicio: Inicio v2 con «Para resolver hoy» en tres niveles (Bloquea el
   registro: incompletos, esperando contacto, graves · Espera tu revisión: solicitudes, posibles
   duplicados, eventos relacionados · En curso: en seguimiento) y «Panorama 2026» (127 vigentes):
   casos por mes con proyección de septiembre, zona del cuerpo («Sale del tratamiento que carga
   Salud…»), franja etaria, canal de origen (Zoonosis 41 · Salud 33 · CADIC 9 · Ciudadano 12 ·
   Histórico 7). Accesos a Casos, Consultas y Administración.
4. *Salud* · Salud revisa el tratamiento: ficha v2, vista Salud. «Lo que la API no le envía a Salud
   no se muestra: dueño, chip, descripción y fotos…, y el detalle de la denuncia (RN-35).» Ve el día
   10 y «Editar tratamiento»; de la denuncia, solo «Tiene 1 denuncia anotada».
   Las fichas de E3·04 en adelante traen el aviso «Se detectó un caso con datos coincidentes»
   (C-2026-0402; DNI, teléfono y fecha) con «Comparar casos» y «No es duplicado».

## Escenario 4 · Nunca se ubica al perro (4 pasos)
1. *Zoonosis* · El segundo perro nunca apareció: ficha v2 (animal 2 «sin chip · nunca se ubicó»).
2. *Zoonosis* · Se finaliza igual: Cambiar estado.
3. *Sistema* · Finalizado, con la aclaración: bandeja; la fila C-2026-0398 dice «Finalizado · Sin
   todos los datos: el perro nunca se ubicó».
4. *Sistema* · No cuenta como incompleto: Casos › Incompletos v2 (C-2026-0418 y C-2026-0404). Pie:
   «Solo casos vigentes… Uno desestimado conserva la marca, pero no entra en las listas de trabajo
   (dónde se cuenta está pendiente).»

## Escenario 5 · Desestimar un caso (2 pasos)
1. *Agente de Zoonosis* · Se desestima con un motivo: ventana «Desestimar caso»: motivo (*) con las
   cuatro opciones de §9, observación libre. «Duplicado no es un motivo… Datos insuficientes
   tampoco… Lista tentativa.» «Si le faltan datos, sigue marcado como incompleto.»
2. *Sistema* · Queda desestimado, con su marca: bandeja (C-2026-0393 «Desestimado · Hecho no
   verificable», con «!»).

## Escenario 6 · Qué ve cada organismo (3 pasos)
1. *Zoonosis* · ve todo el animal: ficha v2 completa.
2. *Salud* · ve solo lo que le sirve: ficha v2, vista Salud.
3. *Equipo* · Las reglas, en un solo lugar: Administración › Usuarios › pestaña «Roles y permisos».
   Tres tablas: qué casos ve cada uno, quién edita qué y qué datos ve cada uno; es la tabla de §9
   tal cual. «Se aplica en el servidor: el front muestra solo lo que le llega (RN-35).»

## Escenario 7 · Reconciliar dos animales (3 pasos)
1. *Zoonosis* · El chip ya existe en otro animal: Consultas › Animales · Reconciliar. Aviso del chip
   rechazado; comparación A (sobrevive, tiene chip) / B (se absorbe); «Qué pasa al confirmar» (repunta
   CASO_ANIMAL con historial, B queda «absorbido por» A, las descripciones viven en cada caso, sin
   chip sobrevive el más viejo). Casilla de confirmación.
2. *Zoonosis* · Uno absorbe al otro: la misma pantalla que el paso 1.
3. *Sistema* · El animal muestra todos sus casos: Consultas › Animales · Detalle. Identidad,
   vigencia («Absorbió a un animal sin chip el 13/09/2026»), «Casos de este animal · 2» con tenencia,
   dueño, descripción, día 10 y estado por caso. «La reincidencia se ve acá… No se le pregunta a la
   persona.»

---

## Observaciones del agente de diseño (contra CONTEXTO.md, 2026-11-02)

### Contradicciones con CONTEXTO
> *2026-11-02: 1 y 2 resueltos. Los datos del animal no cuentan para la marca (RN-25); la demo es la que
> tiene que cambiar: en E4, C-2026-0418 no lleva la marca Incompleto, y la aclaración de la bandeja sale
> de `observacion_dia10 = no_se_pudo_observar` (ver `modelo/decisiones.md`).*

1. **Incompleto por un animal no ubicado (E4).** C-2026-0418 lleva la marca Incompleto, aunque todos
   sus datos de caso están cargados (fecha, ciudad, lugar, tipo de lugar, edad, tipo de evento). Lo
   único que falta es el animal 2. RN-25 dice que la marca mide los datos **del caso**, no los de
   CASO_ANIMAL. El problema también está en CONTEXTO: §9 pone «nunca se ubicó al perro» como ejemplo
   de *finalizado incompleto*, y por RN-25 un perro no ubicado no hace incompleto al caso. **Hay que
   decidir** si la falta de datos de un animal cuenta para la marca.
2. **La aclaración «Sin todos los datos: el perro nunca se ubicó» (bandeja) no tiene campo en el
   modelo.** El desestimado tiene `motivo_desestimacion`; el finalizado incompleto no tiene nada que
   guarde por qué. O se agrega un campo (¿motivo o observación al finalizar?) o la aclaración se deriva
   (finalizado + marca incompleto → texto fijo).
3. **E7 usa como ejemplo de reincidencia un caso que es duplicado.** C-2026-0402 aparece en el aviso
   de la ficha con el mismo DNI de la víctima, el mismo teléfono y la misma fecha que C-2026-0418, o
   sea un posible duplicado del mismo hecho. Que comparta el perro no muestra reincidencia: es el
   mismo ataque. Para E7 hace falta otro caso, con otra víctima y otra fecha (y el animal B
   registrado antes).
4. **Lo declarado de la denuncia no respeta RN-07.** La solicitud S-2026-0034 declara «No · No sabía
   dónde denunciar», pero la ficha muestra D1 = «Sí». La ficha del E1 lista como solicitud
   S-2026-0034; las del E3 en adelante, S-2026-0031 («sumada el 12/09/2026»).
5. **La línea de tiempo del E1 no cierra.** La bajada del paso 7 dice «canal de origen: ciudadano»,
   pero la ficha dice «canal de origen: Zoonosis» y «Registrado por M. Acosta · 12/09/2026 15:02».
   Es más de un día **antes** de que se enviara la solicitud (13/09 21:40). La bandeja del paso 12
   también dice Zoonosis.

### Pantallas reusadas que no muestran el paso
6. La ficha v2 es la misma lámina en E1·07, E1·10, E4·01 y E6·01. En el paso 7 («nace el caso») ya
   tiene tratamiento, denuncia, día 10 y certificado. Para que la demo cuente la historia, cada paso
   necesita su estado de la ficha.
7. **E2 «otra solicitud» es la misma S-2026-0034** del E1, que en el E1 creó el caso. Hace falta
   otro número (p. ej. S-2026-0037) y otra fecha de envío.
8. E3·01 usa la ventana «Agregar animal» para registrar que el perro murió. Corresponde editar el
   seguimiento de un animal que ya está en el caso. En el texto tampoco queda marcada la opción
   «Murió o enfermó».
9. E4·03 dice «la bandeja lo muestra finalizado», pero C-2026-0418 sigue Registrado en esa bandeja.
   El finalizado incompleto es otra fila (C-2026-0398). Lo mismo en E5·02: se desestimó C-2026-0418,
   que sigue Registrado; el desestimado es C-2026-0393. Además desestimar a C-2026-0418 (un ataque
   real, con denuncia confirmada) no es un buen ejemplo.
10. E7·01 y E7·02 son la misma pantalla: falta mostrar el resultado de absorber.
11. En Inicio, las tarjetas «Graves» y «Solicitudes» usan las variantes `Tipo=Incompletos` y
    `Tipo=En seguimiento` del componente Pendiente: faltan variantes propias (ícono y color).
    La fila «Espera tu revisión · decidís vos si se consolidan o se vinculan» incluye las
    solicitudes, que no se consolidan ni se vinculan.

### Propuestas nuevas que no están en CONTEXTO (registrar o descartar)
12. **Valores de la observación del día 10:** Pendiente · Sin novedad · Murió o enfermó · No se pudo
    observar. CONTEXTO no los define (§9, criterio de `finalizado`). La ayuda «Si murió o enfermó, el
    caso pasa a Grave» sugiere que el paso a Grave es **automático**, pero E3·02 lo hace a mano.
    *2026-11-02: es **manual**. La ayuda tiene que decir «pasalo a Grave», no «pasa a Grave».*
    *2026-11-03: superado. Grave deja de ser estado: es una marca derivada del día 10 (RN-11). Sale
    «Grave» de Cambiar estado (E1·11, E3·02) y la ayuda vuelve a «pasa a Grave».*
13. **Desestimar tiene dos caminos:** la opción «Desestimado» de Cambiar estado y la ventana propia
    «Desestimar caso» (con motivo). Conviene que Cambiar estado abra la de desestimar.
14. **Permisos visibles en Administración › Usuarios › Roles y permisos** como tabla de solo lectura.
    No está en §8; está bien como documentación, pero las reglas viven en el servidor (RN-35).
15. Historial con filtros por entidad y «Ver cómo estaba en una fecha»: es una propuesta concreta para
    la pantalla de historial pendiente (§9). Encaja con RN-27 (foto completa).

### Menores (datos de ejemplo)
- Los contadores no coinciden entre sí: Incompletos 2 en el menú, 3 en el filtro de la bandeja y
  23 en Inicio; Posibles duplicados 1 / 2 / 8. La bandeja dice «1–8 de 11» con 8 filas, y la cola
  de solicitudes «1–3 de 3» con dos páginas. La ficha dice «5 cambios» y el historial muestra 7.
- En el historial (E2·04) el aviso del Sistema es «coincidencia con C-2026-0402: mismo DNI de la
  víctima», pero en la bandeja C-2026-0411 está «Unificado → C-2026-0402» con otra víctima (Joaquín
  Ojeda). C-2026-0402 cumple tres papeles distintos en la demo.
- Administración › Importar CSV sigue en el menú, y la sugerencia del 2026-10-30 es que no haya
  importación.
- El usuario de la barra superior es siempre «Daniela Marchisoney», también en las láminas de Salud
  y de Zoonosis.

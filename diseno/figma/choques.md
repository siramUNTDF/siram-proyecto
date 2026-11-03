# Figma vs. CONTEXTO.md · choques y pendientes (2026-11-03)

> Lo que el archivo de Figma («SIRAM — Diseño», leído completo el 2026-11-03) dice distinto de
> CONTEXTO.md. Donde CONTEXTO ya decidió, **gana CONTEXTO y es Figma el que tiene que cambiar**
> (memoria: ante choques, se listan y se pregunta). Las secciones B y C vienen de la lectura de la Demo
> del 2026-11-02, con sus anotaciones; siguen valiendo salvo donde se indica.

## A. Choques con decisiones de CONTEXTO

> *2026-11-03, revisado con el usuario: A.1, A.2, A.3, A.4 y A.6 confirmados (Figma tiene que
> ajustarse). A.5 decidido (ver abajo). Todavía no se dispara el cambio en Figma.*

1. **Grave es estado en Figma; en CONTEXTO es una marca derivada** (RN-09, RN-11, 2026-11-03). Lo
   tienen como estado: el set «Estado del caso» (Fundamentos), Cambiar estado · v2 (opción «Grave» y su
   ayuda), la Bandeja · v2 (C-2026-0421 «Grave», filtro «Graves (1)») y la Demo (E1·11, E3·02, E4·02).
   Falta además la marca Grave en el set «Marca» y en la Leyenda de marcas. La ayuda de Agregar animal
   («Si murió o enfermó, el caso pasa a Grave») sí cuadra con la marca derivada.
2. **Cambiar estado ofrece volver a «Registrado»**, y RN-36 no lo permite («No se vuelve a
   `registrado`»). Tampoco hace falta ofrecer el estado actual.
3. **Ciudad «Otra» en el formulario público** (Público › 3 · Dónde fue): desde el 2026-11-03 H3 es solo
   Ushuaia, Río Grande o Tolhuin (RN-32).
4. **Motor de coincidencias con puntaje y vínculo de eventos relacionados** (Comparar · posible
   duplicado / consolidar confirmado / evento relacionado, listas de Posibles duplicados y Eventos
   relacionados, Inicio «decidís vos si se consolidan o se vinculan», botón Vincular, rol Agente
   «resuelve duplicados y eventos relacionados»). Desde el 2026-11-02 el duplicado se detecta por el
   DNI de la víctima y el **evento relacionado se deriva** de compartir un ANIMAL: ya no se vincula, y
   RN-16 a RN-18 están superadas. La señal «Mismo animal — color, tamaño» choca además con RN-22
   (DESCRIPCIÓN no es parte del motor). El aviso de la Ficha v2 (DNI, teléfono, fecha · Comparar casos ·
   No es duplicado) y el de Revisar solicitud (por DNI) sí van con el criterio nuevo.
5. **Finalizado incompleto por un perro que nunca se ubicó** (Bandeja · v2 «Sin todos los datos: el
   perro nunca se ubicó»; Demo E4 entera). Corregido en CONTEXTO el 2026-11-02: los datos del animal no
   cuentan para la marca (RN-25) y el animal no ubicado queda `no_se_pudo_observar`. El ejemplo de E4
   tiene que ser otro (p. ej. nunca se ubicó a la víctima).
   *Decisión 2026-11-03: dos escenarios.* (a) **E4 se queda con el perro, contado bien:** el perro
   nunca se ubica → día 10 «No se pudo observar» → el caso se finaliza **completo**; la bandeja no dice
   «sin todos los datos». (b) **Escenario nuevo de finalizado incompleto** con el ejemplo de §9: nunca
   se ubica a la víctima ni al contacto responsable, faltan datos del caso (p. ej. edad o tipo de
   lugar), se finaliza igual y deja de contar como incompleto. La fila C-2026-0398 de la Bandeja · v2
   tiene que pasar a uno de los dos.
6. **Campos descartados el 2026-10-29 que siguen en pantallas** (CONTEXTO §7.1):
   - Estadísticas: gráfico «Qué estaba haciendo» (H8), con la nota «Junto con “con quién estaba”… un
     dato obligatorio»; «Castrado» (A10) en vacunación y en «Datos sin completar».
   - Búsqueda: filtros «Con quién estaba» (H6) y «Qué estaba haciendo» (H8).
   - Exportar: Hecho incluye con quién estaba, qué estaba haciendo e iba con perros (H6, H8, H7); Animal,
     reincidente (A12); Denuncia y seguimiento, «si volvió a ver al animal suelto» y observaciones (D4,
     H10); Documentación, «firma» (X3) y fotos como dato del caso.
   - Nuevo caso · Aviso de caso parecido (formulario v1 completo, en la página Casos).
7. **Listas de valores que no coinciden con CONTEXTO:**
   - Tipo de lugar en Estadísticas (Domicilio propio, Domicilio ajeno, Plaza o parque, Lugar de trabajo)
     ≠ H5 (casa propia, casa ajena, vía pública, espacio público, zona rural), que sí usa el formulario
     público.
   - Gravedad en Estadísticas (Herida superficial, Herida profunda, Desgarro, Sin herida) ≠ L2
     (excoriación, herida superficial, herida profunda, amputación), que sí usa Cargar tratamiento.
   - «Origen del animal: Ajeno / Propio» en Estadísticas y Búsqueda ≠ tenencia de tres valores (A5).
8. **Pantallas que todavía no pasaron a la v2:** Posibles duplicados, Eventos relacionados, Búsqueda
   (tabla de resultados) y Comparar usan las columnas viejas (Lesión, Origen = organismo) y no las de la
   Bandeja · v2 (última modificación, animales, tipo de evento, canal de origen).
9. **Administración › Importar CSV** sigue en el menú lateral; la sugerencia del 2026-10-30 es que no
   haya importación.

## B. Observaciones de la Demo (2026-11-02), todavía abiertas

1. **E7 usa como ejemplo de reincidencia un caso que es duplicado.** C-2026-0402 tiene el mismo DNI,
   teléfono y fecha que C-2026-0418: compartir el perro no muestra reincidencia, es el mismo ataque.
   Hace falta otro caso, con otra víctima y otra fecha (y el animal B registrado antes).
2. **Lo declarado de la denuncia no respeta RN-07.** S-2026-0034 declara «No · No sabía dónde
   denunciar», pero la ficha muestra D1 «Sí». La ficha del E1 lista S-2026-0034; el componente y las
   láminas siguientes, S-2026-0031 («sumada el 12/09/2026»).
3. **La línea de tiempo del E1 no cierra.** El paso 7 dice «canal de origen: ciudadano», pero la ficha
   dice «canal de origen: Zoonosis» y «Registrado por M. Acosta · 12/09/2026 15:02», más de un día
   antes de que se enviara la solicitud (13/09 21:40). La bandeja del paso 12 también dice Zoonosis.
4. **La ficha del E1 no muestra cada paso.** Es la misma lámina en E1·07 y E1·10 (y el componente en
   E4·01 y E6·01): en el paso 7 («nace el caso») ya tiene tratamiento, denuncia, día 10 y certificado.
5. **E2 «otra solicitud» es la misma S-2026-0034** del E1, que en el E1 creó el caso. Hace falta otro
   número y otra fecha de envío.
6. **E3·01 usa «Agregar animal»** para registrar que el perro murió; corresponde editar el seguimiento
   de un animal que ya está en el caso.
7. **E4·03 y E5·02 dicen que el caso cambió, pero la bandeja no lo muestra:** en E4·03 C-2026-0418 sigue
   como estaba (el finalizado incompleto es C-2026-0398) y en E5·02 el desestimado es C-2026-0393.
   Desestimar a C-2026-0418 (un ataque real, con denuncia confirmada) tampoco es un buen ejemplo.
8. **E7·01 y E7·02 son la misma pantalla:** falta mostrar el resultado de absorber.
9. **Inicio:** las tarjetas «caso grave» y «solicitudes pendientes» usan las variantes
   `Tipo=Incompletos` y `Tipo=En seguimiento` del componente Pendiente; faltan variantes propias. La
   fila «Espera tu revisión · decidís vos si se consolidan o se vinculan» incluye las solicitudes, que
   no se consolidan ni se vinculan (y, por A.4, ya no se vincula nada).
10. **Desestimar tiene dos caminos:** la opción «Desestimado» de Cambiar estado y la ventana propia
    «Desestimar caso» (con motivo). Conviene que Cambiar estado abra la de desestimar.

*Resueltas desde el 2026-11-02:* la marca Incompleto por un animal no ubicado y la aclaración de la
bandeja (ver A.5 y `modelo/decisiones.md`); el paso a Grave manual o automático (superado por A.1).

## C. Propuestas de Figma que CONTEXTO no recoge (registrar o descartar)

1. **Valores de la observación del día 10:** Pendiente · Sin novedad · Murió o enfermó · No se pudo
   observar. CONTEXTO nombra `murio_o_enfermo` y `no_se_pudo_observar`, pero no la lista completa.
2. **Tenencia con «No sabe»** (Agregar animal): Propio · Ajeno conocido · Ajeno desconocido · No sabe.
   RN-22 lista tres valores; RN-23 pide el valor desconocido explícito.
3. **Permisos visibles en Administración › Usuarios › Roles y permisos** como tabla de solo lectura. No
   está en §8; sirve como documentación, pero las reglas viven en el servidor (RN-35).
4. **Historial con filtros por entidad y «Ver cómo estaba en una fecha»:** propuesta concreta para la
   pantalla de historial pendiente (§9). Encaja con RN-27.
5. **Exportar oculta «Datos personales» según el rol** (nota de diseño de Exportar). CONTEXTO no define
   qué rol puede exportar datos personales.
6. **Roles de usuario Administrador · Agente · Consulta** (Nuevo usuario). CONTEXTO §5 habla de
   «Analista / Comité» sin definición formal; «Consulta» sería su rol.
7. **Organismo con tipo** (Salud · Municipio · Investigación) y estado Activo/Inactivo; **tipo de
   evento** con descripción y estado. Atributos que el modelo puede no tener.
8. **Mapa: casos graves en rojo** y filtros por la descripción de cada animal del caso.

## D. Menores (datos de ejemplo)

- Los contadores no coinciden entre sí: Incompletos 2 en el menú, 3 en el filtro de la bandeja y 23 en
  Inicio; Posibles duplicados 1 / 2 / 8. La bandeja dice «1–8 de 11» con 8 filas, y la cola de
  solicitudes «1–3 de 3» con dos páginas. La ficha dice «5 cambios» y el historial muestra 7.
- En el historial el aviso del Sistema es «coincidencia con C-2026-0402: mismo DNI de la víctima», pero
  en la bandeja C-2026-0411 está «Unificado → C-2026-0402» con otra víctima (Joaquín Ojeda).
  C-2026-0402 cumple tres papeles distintos.
- El usuario de la barra superior es siempre «Daniela Marchisoney», también en las láminas de Salud y
  de Zoonosis.
- En Fundamentos el componente se llama «Evento de auditoría»; desde el 2026-10-23 el término es
  «historial» (RN-27).

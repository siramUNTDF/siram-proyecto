# Figma · página «Demo» (lectura del 2026-11-03)

> Fuente: archivo original «SIRAM — Diseño» (`XC7e02ZzIfQwmALf1RHgiZ`), página `Demo` [110:310].
> Reemplaza la lectura del 2026-11-02, que se hizo sobre una copia y quedó incompleta. Las
> observaciones de esa lectura pasaron a `choques.md`. Ver el índice en `README.md`.

40 láminas de 1920×1080. Cada una tiene a la izquierda el texto del paso (escenario, «Paso n de m»,
actor, título, bajada) y a la derecha una instancia de una pantalla real del diseño. Pie fijo: «SIRAM ·
Demo de uso · datos de ejemplo». La portada dice: «Siete escenarios contados paso a paso con las
pantallas reales del diseño. Avanza sola cada 7 segundos; un clic adelanta.»

Casi todas las pantallas son **instancias sin cambios** de los componentes v2 de las otras páginas; el
detalle de cada pantalla está en `casos.md`, `consultas-y-administracion.md` e
`inicio-y-formulario-publico.md`. Abajo se marca cuando una lámina cambia algo respecto del componente.

## Escenario 1 · Camino completo (12 pasos)
«De la solicitud de la ciudadana al caso finalizado, pasando por Zoonosis y Salud.»

| # | Actor | Paso | Pantalla |
|---|---|---|---|
| 1 | Ciudadana | Carla avisa que mordieron a su hija. «Completa el formulario inicial desde el celular… Es corto a propósito.» | Público › 1 · Formulario inicial |
| 2 | Ciudadana | Recibe un número y puede contar más. «cuatro partes, una sola vez; el enlace vence en una hora.» | Público › 2 · Solicitud enviada |
| 3 | Ciudadana | Marca dónde fue. «Deja el pin en el mapa y el sistema le propone la dirección.» | Público › 3 · Dónde fue |
| 4 | Ciudadana | Describe al perro. «Todo admite “No sé”.» | Público › 5 · El animal |
| 5 | Sistema | Entra a la cola de solicitudes. «Todavía no es un caso… Nada llega a un caso sin un agente.» | Casos › Solicitudes |
| 6 | Agente de Zoonosis | Un agente la revisa: descartar, sumar o registrar. | Revisar solicitud, **sin** el aviso «La víctima ya está en un caso» |
| 7 | Agente de Zoonosis | Nace el caso C-2026-0418. «El caso guarda su canal de origen: ciudadano.» | Ficha v2 **sin** el aviso de posible duplicado; lista la solicitud S-2026-0034 «Registrada el 13/09/2026» |
| 8 | Salud | Salud carga la atención. | Ficha · Cargar tratamiento |
| 9 | Zoonosis | Zoonosis anota la denuncia: DNI, fecha y estado. | Ficha · Anotar denuncia · v2 |
| 10 | Zoonosis | Observa al perro el día 10: «Sin novedad». | La misma ficha que el paso 7 |
| 11 | Zoonosis | Se finaliza el caso. «Con el animal observado y la víctima atendida…» | Cambiar estado · v2 con **Finalizado** marcado y sin el bloque de motivo de espera |
| 12 | Sistema | Queda registrado y cuenta en las estadísticas. | Bandeja · v2 con C-2026-0418 en **Finalizado** y sin marca |

## Escenario 2 · La solicitud coincide con un caso (4 pasos)
«Llega otra solicitud por la misma víctima: el agente la suma al caso que ya existe.»
1. *Sistema* · Llega otra solicitud por Micaela: «el DNI de la víctima ya está en C-2026-0418». Cola
   de solicitudes (igual que E1·05).
2. *Agente de Zoonosis* · El agente ve el aviso: Revisar solicitud con el aviso «La víctima ya está en un
   caso».
3. *Agente de Zoonosis* · Elige campo por campo: Sumar a un caso. «Lo que tiene uno solo se conserva.
   Si dos datos chocan, el agente elige cuál queda.»
4. *Sistema* · Todo queda en el historial: Historial del caso. «Quién la sumó, cuándo y qué cambió, con
   la foto completa del registro.»

## Escenario 3 · El animal muere en la observación (4 pasos)
«Si el animal muere o enferma en los 10 días, el caso no se cierra: escala a Grave.»
1. *Zoonosis* · Zoonosis registra que el perro murió: ventana Agregar animal, **sin** el aviso de chip
   repetido. Según la lectura del 02/11, el día 10 no tiene marcada «Murió o enfermó» (la de hoy no
   registra qué opción está marcada en los grupos compactos).
2. *Zoonosis* · El caso pasa a Grave: Cambiar estado con **Grave** marcado. «No se finaliza: sigue
   abierto y pide atención especial al tratamiento de la víctima.»
3. *Sistema* · Aparece en el inicio: Inicio · v2. «Los casos graves quedan entre lo que hay que
   resolver hoy.»
4. *Salud* · Salud revisa el tratamiento: ficha v2, vista Salud. «Salud ve el día 10 del animal porque
   puede cambiar el tratamiento antirrábico de la víctima.»

## Escenario 4 · Nunca se ubica al perro (4 pasos)
«Un caso se puede finalizar aunque le falten datos, cuando esa falta es lo que impidió resolverlo.»
1. *Zoonosis* · El segundo perro nunca apareció: ficha v2. «Zoonosis recorrió la zona dos veces sin
   ubicarlo. No hay observación del día 10 posible.»
2. *Zoonosis* · Se finaliza igual: Cambiar estado con Finalizado marcado. «La falta de datos es
   justamente lo que impidió resolverlo.»
3. *Sistema* · Finalizado, con la aclaración: Bandeja · v2. «La bandeja lo muestra finalizado y dice por
   qué le faltan datos.»
4. *Sistema* · No cuenta como incompleto: Incompletos · v2. «Los incompletos son una lista de trabajo:
   solo muestran casos abiertos.»

## Escenario 5 · Desestimar un caso (2 pasos)
«Un caso que no corresponde se desestima con un motivo. En SIRAM nada se borra.»
1. *Agente de Zoonosis* · Se desestima con un motivo: Ficha · Desestimar · v2. «Fuera de alcance, fuera
   de la provincia, hecho no verificable o cargado por error. Un duplicado no se desestima: se
   consolida.»
2. *Sistema* · Queda desestimado, con su marca: Bandeja · v2. «Si le faltaban datos, conserva la marca
   de incompleto. No cuenta en las estadísticas.»

## Escenario 6 · Qué ve cada organismo (3 pasos)
«El mismo caso se ve distinto según quién lo abre. Las reglas se aplican en el servidor.»
1. *Zoonosis* · Zoonosis ve todo el animal: ficha v2. «Dueño, chip, descripción y fotos: los necesita
   para identificarlo y hacer el seguimiento.»
2. *Salud* · Salud ve solo lo que le sirve: ficha v2, vista Salud. «Lo que el servidor no le envía, la
   pantalla no lo muestra.»
3. *Equipo* · Las reglas, en un solo lugar: Usuarios · Roles y permisos · v2. «Son tentativas: falta
   validarlas con los organismos.»

## Escenario 7 · Reconciliar dos animales (3 pasos)
«Zoonosis descubre que dos registros son el mismo animal: uno absorbe al otro.»
1. *Zoonosis* · El chip ya existe en otro animal: Animales · Reconciliar. «Al cargar un chip repetido,
   la base lo rechaza y Zoonosis compara los dos registros.»
2. *Zoonosis* · Uno absorbe al otro: la misma pantalla. «Sobrevive el que tiene chip. El otro no se
   borra: deja de estar vigente y apunta al que lo absorbió.»
3. *Sistema* · El animal muestra todos sus casos: Animales · Detalle. «Así se ve la reincidencia, sin
   preguntarle a nadie.»

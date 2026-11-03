# Figma · «Consultas y Administración» (lectura del 2026-11-03)

> Fuente: archivo original «SIRAM — Diseño» (`XC7e02ZzIfQwmALf1RHgiZ`), página `Consultas y
> Administración` [1:3]. Textos literales entre comillas. Ver el índice en `README.md` y los choques
> con CONTEXTO.md en `choques.md`.

## Consultas

### Búsqueda [48:246] y · filtros plegados [49:660]
«Casos según cuándo y dónde pasó, la persona, el animal y la lesión.» Panel de filtros («completá solo
lo que quieras usar» · Ocultar filtros), por bloques:
- Cuándo y dónde: fecha del hecho desde/hasta, ciudad, lugar («Calle, altura o barrio»), tipo de lugar.
- Persona: edad desde/hasta, **con quién estaba**, **qué estaba haciendo**.
- Animal: especie, tamaño, color o raza, propio o ajeno.
- Lesión: tipo de lesión, zona del cuerpo, gravedad.
- Registro: organismo, tipo de evento, estado del caso («Vigentes»), registrado por.
- Limpiar · Buscar.

Resultado: «6 casos · vigentes, con los filtros de arriba» · «Exportar estos resultados» · tabla con
las columnas viejas de la bandeja. Plegados, los filtros quedan como chips («Fecha del hecho:
01/08/2026 – 30/09/2026», «Especie: Perro», «Tipo de lesión: Mordedura») con Limpiar · Modificar filtros.

### Estadísticas [53:1221]
«Indicadores sobre los casos vigentes. Datos al 25/09/2026.» Filtros: período, ciudad, organismo ·
«Exportar estos datos». Resumen: 127 casos vigentes («No cuenta desestimados ni unificados…») y tres
indicadores (31 víctimas de 0 a 9 años · 58 en la vía pública · 81 sin saber si el animal estaba
vacunado: 46 «no sabe» y 35 «sin dato»). Secciones con gráficos y su nota:
- **Cuándo**: casos por mes; día de la semana (sábado y domingo destacados) y franja horaria (12–18 h
  destacada).
- **Quién**: franja etaria; **qué estaba haciendo** (Caminando, Jugando, Trabajando, En bici o moto,
  Haciendo deporte, Otra actividad, Sin dato). Nota: «Junto con “con quién estaba”, es la situación de
  la persona: un dato obligatorio, sin el que el caso queda incompleto.»
- **Dónde**: ciudad (Ushuaia, Río Grande, Tolhuin; «El detalle por barrio y por calle va en el mapa»);
  tipo de lugar (Vía pública, Domicilio propio, Domicilio ajeno, Plaza o parque, Lugar de trabajo, Sin
  dato).
- **Animal**: especie y tamaño (con «No sabe» aparte de «Sin dato»); origen del animal (Ajeno, Propio,
  No sabe, Sin dato); vacunación y **castración**.
- **Lesión**: zona del cuerpo (Cara destacada); tipo de lesión (Mordedura, Arañazo, Sin lesión, Lesión
  derivada) y gravedad (Herida superficial, Herida profunda, Desgarro, Sin herida, Sin dato). Nota:
  «Valores de ejemplo. La lista de tipos de lesión todavía no está definida y hoy se superpone con el
  tipo de evento (HZ05).»
- **Registro** («No son datos epidemiológicos»): origen del registro por organismo; datos sin completar
  (vacuna del animal, castrado, qué hacía, hora, tamaño, tipo de lugar). «Solo cuenta “sin dato”…
  “No sabe” es una respuesta y no entra acá.»

### Exportar [67:1453] y · con datos personales [67:1932]
«Descargá casos en CSV o XLSX para analizarlos fuera de SIRAM.» Pasos:
- Casos: fecha del hecho, ciudad, organismo, estado del caso, tipo de evento. «Desde Búsqueda,
  “Exportar estos resultados” abre esta página con los mismos filtros.»
- Columnas por bloque, «en el mismo orden que la ficha del caso»: Identificación y estado (7) · Hecho
  (8: incluye con quién estaba, qué estaba haciendo e iba con perros) · Tipo de evento (1) · Persona
  (solo la edad, 1) · Animal (11: incluye reincidente) · Lesión y atención (7) · Denuncia y seguimiento
  (4: incluye «si volvió a ver al animal suelto» y observaciones) · Documentación (3: certificado,
  fotos, firma) · Datos personales (5, «protegidos por la Ley 25.326»).
- Formato: CSV · XLSX. Resumen a la derecha (127 casos, 39 columnas en 7 bloques) · «Descargar CSV».
- Con datos personales: aviso «Vas a descargar datos personales…» y el resumen dice «44 columnas, en 8
  bloques · Incluye datos personales».
- Nota de diseño [67:2201]: «la casilla “Datos personales” solo aparece para los roles que pueden
  exportarlos (ver Administración › Usuarios › Roles y permisos). Para el resto, esa opción no existe.»

### Personas [102:3518] y Personas · Detalle [102:3771]
«Una por DNI. Se consultan, no se trabajan: lo único que SIRAM trabaja es el caso. DNI y contacto,
solo en el detalle.» Filtros: Todas (148) · Víctimas (131) · Contactos responsables (24) · Dueños de
animales (17). Columnas: Persona (+ edad) · Casos · En qué rol aparece («Víctima en 1 · contacto
responsable en 1») · Último caso · Última modificación (+ quién).

Detalle («Carla Sosa · Persona única por DNI: un cambio acá se ve en todos sus casos y queda en el
historial de la persona.»): Editar · Ver historial; bloque Datos (nombre, DNI, edad, teléfono, correo,
domicilio); «Casos de esta persona · 2» (caso, rol en el caso, fecha, víctima, estado). Pie: «Los roles
viven en cada caso: víctima y contacto responsable son del caso; dueño, de cada animal en el caso. No se
guarda la relación entre personas.»

### Animales [102:4009], Animales · Detalle [108:9370] y Reconciliar [108:9369]
«La identidad de cada animal (especie y chip) y todos los casos en que apareció. Lo que se supo de él
vive en cada caso.» Filtros: Todos (96) · Perros (88) · Gatos (8) · Con chip (21) · Sin chip (75) ·
Absorbidos (2). Columnas: Animal (especie + chip) · Casos · Último caso · Descripción en el último caso ·
Día 10 del último caso (Sin novedad · No se ubicó · Murió o enfermó · —) · Vigencia («Inactivo ·
Absorbido por chip …»).

Detalle: Editar identidad · Reconciliar con otro animal · Ver historial. Identidad (especie, chip,
vigencia, «Absorbió a un animal sin chip el 13/09/2026»). «Casos de este animal · 2» (tenencia, dueño
durante el caso, descripción, día 10, estado; «Vino del animal absorbido»). «La reincidencia se ve acá:
los casos en que apareció el mismo animal. No se le pregunta a la persona.»

Reconciliar: «Zoonosis descubrió que dos registros son el mismo animal. Uno absorbe al otro; nada se
borra.» Aviso: «Este chip ya está cargado en otro animal…» Comparación A (sobrevive, tiene chip) / B (se
absorbe). «Qué pasa al confirmar»: el caso de B pasa a apuntar a A (queda en el historial de su
CASO_ANIMAL); B no se borra ni se vacía, queda «absorbido por» A; las descripciones viven en cada caso;
«Si ninguno tuviera chip, sobreviviría el más viejo.» Casilla «Confirmo que A y B son el mismo animal» ·
Reconciliar.

### Mapa · v2 [103:4465]
«Dónde ocurrieron los casos vigentes. Cada punto lo puso una persona en el mapa (pin + dirección +
referencias).» Chips de filtro: especie, tamaño, color, período · Filtros. Mapa con puntos («©
colaboradores de OpenStreetMap») y panel «Caso seleccionado»: enlace, víctima, fecha, lugar con
referencias, animales, tipo de evento, estado · Abrir caso. Pie: «9 casos con los filtros aplicados · en
rojo, los casos graves · solo casos vigentes… El filtro de tamaño y color mira la descripción de cada
animal en el caso.»

## Administración

### Usuarios [68:1808], Nuevo usuario [69:2180], Desactivar [69:2411], Reactivar [104:4802]
«Cuentas de las personas que usan SIRAM en cada organismo. No se borran: se desactivan.» Pestañas
Usuarios · Roles y permisos. Filtros: Todos (25) · Administración (2) · Agentes (19) · Consulta (4) ·
Inactivos (1). Columnas: Nombre (+ correo) · Organismo · Rol · Estado · Último acceso («Todavía no entró
· Alta: …»).
- Nuevo usuario: «Una cuenta por persona. El rol decide qué puede hacer en SIRAM.» Nombre *, correo *,
  organismo *, rol *: Administrador («Da de alta usuarios y organismos y mantiene los catálogos. No
  trabaja casos.») · Agente («Registra casos, los completa, les da seguimiento y resuelve duplicados y
  eventos relacionados.») · Consulta («Busca casos, ve estadísticas y exporta datos, sin editar. Para
  analistas y el comité.»).
- Desactivar: «No se borra nada. … no va a poder entrar a SIRAM. Los casos que registró y su historial
  quedan como están, y la cuenta se puede volver a activar.» Motivo opcional.
- Reactivar: «Vuelve a poder entrar. Con el mismo rol y organismo. Sigue apareciendo donde actuó; la
  reactivación queda en el historial del usuario (sin credenciales).»

### Usuarios · Roles y permisos · v2 [108:9371]
«Tentativa sacada de la narrativa y aprobada por el equipo; falta validarla con los organismos. Se
aplica en el servidor: el front muestra solo lo que le llega (RN-35).» Tres tablas, que reproducen las
de CONTEXTO §9:
- Qué casos ve cada uno: agentes (Salud, Zoonosis, CADIC) todos los casos y todas las solicitudes;
  analista/comité los casos sin datos personales; administrador no ve casos.
- Quién edita: datos comunes, cualquier agente; tratamiento, solo Salud; seguimiento del animal, solo
  Zoonosis; denuncias y certificado, solo Zoonosis; lo declarado, nadie.
- Qué datos ve cada uno (Salud · Zoonosis · CADIC · Analista), con «Solo si existe» y «Agregados».

### Organismos [70:2699] y Editar [70:3101]
«Los entes que cargan y consultan casos. En cada caso aparecen como un dato, nunca como marca de
SIRAM.» Filtros: Todos (9) · Salud (6) · Municipio (1) · Investigación (2). Columnas: Organismo · Tipo ·
Usuarios activos · Casos vigentes · Estado. Editar: nombre *, tipo *; «Es el nombre que se ve en el chip
del organismo… No lleva logo ni color propio.» Estado Activo / Inactivo («Sus usuarios no pueden
entrar. Sus casos y su historial quedan como están.»).

### Tipos de evento [70:3291] y Editar [70:3579]
«Catálogo que clasifica cada caso (campo T1 de la ficha).» Aviso: «Valores en revisión con el cliente.
Son la propuesta del equipo. Falta deslindarlos del tipo de lesión (L1)…» Valores: Ataque con mordedura
(98) · Lesión compatible (15) · Intento sin lesión (9) · Lesión derivada (5), cada uno con descripción.
Editar: nombre *, descripción (incluye la equivalencia del F2), estado Activo / Inactivo («Deja de
ofrecerse en los casos nuevos. Los 15 casos que ya lo tienen lo conservan.»). «Si le cambiás el nombre,
los 15 casos que usan este tipo pasan a mostrar el nombre nuevo.»

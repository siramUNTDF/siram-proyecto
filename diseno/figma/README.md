# Figma de SIRAM · lectura completa (2026-11-03)

Archivo original **«SIRAM — Diseño»**, fileKey `XC7e02ZzIfQwmALf1RHgiZ`, leído entero el 2026-11-03
por el conector de Figma (cuenta de Martin Acosta). Se leyeron textos, estructura, componentes,
variables y estilos, **sin imágenes**. Es una foto de ese día: si el archivo cambia, esto queda viejo.

Las pantallas de Figma son la base visual desde el 2026-11-02. Donde chocan con CONTEXTO.md, gana
CONTEXTO: ver `choques.md`.

| Página | Id | Archivo | Contenido |
|---|---|---|---|
| Fundamentos | 0:1 | `fundamentos.md` | Variables (Tokens claro/oscuro, Paleta, Medidas), estilos de texto y efecto, todos los componentes |
| Inicio | 78:298 | `inicio-y-formulario-publico.md` | Inicio · v2 |
| Casos | 1:2 | `casos.md` | Bandeja, Incompletos, Nuevo caso, Ficha (y vista Salud) con sus ventanas, Historial, Solicitudes; pantallas anteriores a la v2 |
| Consultas y Administración | 1:3 | `consultas-y-administracion.md` | Búsqueda, Estadísticas, Exportar, Personas, Animales, Mapa; Usuarios, Roles y permisos, Organismos, Tipos de evento |
| Formulario público | 105:945 | `inicio-y-formulario-publico.md` | Las 8 pantallas del canal ciudadano (390 px) |
| Archivo v1 | 107:310 | (abajo) | Solo el índice: está superado |
| Demo | 110:310 | `demo.md` | 7 escenarios en 40 láminas |

## Archivo v1 (solo índice)

La página dice: «Pantallas del modelo v1, reemplazadas por las v2 el 30/10/2026. No usarlas como
referencia: se guardan solo como antecedente.» Por eso no se volcó su contenido. Contiene: Casos ›
Bandeja [17:638] · Nuevo caso [18:946] · Nuevo caso, formulario completo [18:1887] · Nuevo caso,
denuncia con Sí [36:2083] y con No [36:3007] · Ficha del caso [38:3294] · Ficha: Cambiar estado
[39:3668], Desestimar [39:3988], Anotar denuncia [40:4100], Editar desde Completar [40:4451] ·
Incompletos [14:166] · Bandeja, Nuevo caso y Ficha en tema oscuro [43:4829, 43:5023, 43:5432] · Inicio
[78:299] · Administración › Usuarios › Roles y permisos [68:2391].

## Cómo se leyó (para repetirlo)

- `create_session` + `get_metadata` sin nodo (lista de páginas) + `use_figma` con scripts de solo
  lectura: uno para variables y estilos, y uno por página, en paralelo.
- El script compacto omite el menú lateral, la barra superior y los íconos. Junta en una línea cada
  bloque chico (≤ 140 px de alto y ≤ 16 textos). Una instancia de pantalla igual a su componente se
  anota «(igual al componente)»; si cambia, se vuelca entera. Así entra cada página en 1 o 2 partes
  de 40 KB.
- Hoy se usaron unas 18 llamadas de lectura. El plan student permite 200 por día y 10 por minuto.

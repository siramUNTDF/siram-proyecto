# Memoria compartida de SIRAM

Registro breve para retomar trabajo entre sesiones y colaboradores. Leer primero
[CONTEXTO.md](CONTEXTO.md) y las decisiones aplicables. Esta memoria no sustituye requisitos,
especificaciones, decisiones ni el historial Git. No guardar conversaciones completas,
credenciales o datos personales.

## Repositorios y fuentes

| Repositorio | Responsabilidad y entrada |
|---|---|
| [siram-proyecto](https://github.com/siramUNTDF/siram-proyecto) | Dominio y diseño: [CONTEXTO](CONTEXTO.md), [modelo](modelo/siram.mmd), [decisiones](modelo/decisiones.md), [preguntas](modelo/preguntas.md). |
| [SIRAM-back](https://github.com/siramUNTDF/SIRAM-back) | API, persistencia y pruebas. Preparación local: `AGENTS.md` y `openspec/README.md`; publicación pendiente en la entrada de abajo. |
| [siram-front](https://github.com/siramUNTDF/siram-front) | Interfaz: [narrativa](https://github.com/siramUNTDF/siram-front/blob/main/docs/narrativa.md), [fichas](https://github.com/siramUNTDF/siram-front/tree/main/docs/vistas), [OpenSpec](https://github.com/siramUNTDF/siram-front/tree/main/openspec). |

- Requisitos originales: [SIRAM.pdf](recursos/requerimientos/SIRAM.pdf). Las decisiones posteriores
  y su precedencia se explican en CONTEXTO; no reescribir el original para aparentar cumplimiento.
- Planificación y pendientes de dominio: [CONTEXTO §9](CONTEXTO.md#9-tensiones-y-pendientes-abiertos).
- Trabajo del front: [cambios activos y archivo](https://github.com/siramUNTDF/siram-front/tree/main/openspec/changes)
  con sus `tasks.md`; [especificaciones](https://github.com/siramUNTDF/siram-front/tree/main/openspec/specs).
- [Decisiones de fichas](diseno/decisiones-fichas.md), [correcciones](diseno/correcciones-fichas.md)
  y [escenarios de demo](diseno/figma/demo.md), leídos junto a
  [cambios de Figma](diseno/figma/cambios.md).
- No se encontró un backlog transversal versionado independiente. El diagnóstico previo de esta
  conversación es un antecedente, no un archivo del repositorio ni un compromiso de entrega.
  Las tareas futuras se concretan en los cambios SDD autorizados, enlazados desde esta memoria.

## Estado comprobado al preparar esta memoria

Revisión estática del 2026-11-12 sobre las bases locales:
backend `1617c76`, frontend `fb9dd8e`, documentación `c9163c9` (abreviaturas Git reales).
No se actualizó desde GitHub: la resolución DNS bloqueó el acceso remoto.

- Backend: existen modelos/servicios de casos, animales ligados al caso, denuncias, documentos,
  coincidencias y auditoría; autenticación JWT/TOTP, consultas y pruebas Django/DRF.
  Evidencia: `apps/casos/{models.py,servicios/,serializers.py,urls.py}` y `apps/accounts/`.
- Frontend: el acceso a datos exporta el servidor simulado desde `src/mocks/index.js`;
  `src/mocks/servidor.js` conserva datos en memoria. No hay integración demostrada por esta tarea.
- Documentación: [modelo v2](modelo/siram.mmd) declarado borrador sin tag. No está íntegramente
  representado en el backend: faltan, entre otras entidades, Solicitud y Tratamiento.
- Metodología: el front contiene OpenSpec `spec-driven`, specs por capacidad, cambios activos
  y archivo por fecha. En backend no se encontró un proceso equivalente antes de esta preparación.
- No había `AGENTS.md`, memoria equivalente ni guía de contribución en backend/documentación
  en la búsqueda de archivos versionados y ocultos, excluyendo `.git` y dependencias.

**Antecedente separado:** el diagnóstico previo señaló diferencias de contratos, permisos,
estados, completitud e identidad de personas/animales, y bloqueos de dependencias.
Esta preparación no repitió esas pruebas ni certifica que funcionen los componentes. Volver a
comprobar cada afirmación relevante al iniciar el cambio que la aborde.

## Pendientes que condicionan la siguiente entrega

1. Delimitar el alcance de pruebas, CI y documentación; leer tests y automatización existentes
   antes de proponer cambios. No asumir una suite verde ni que las expectativas reflejan todas
   las reglas actuales. Usar bases y adjuntos descartables, sin tocar servicios compartidos.
2. Acordar capacidades y contrato del primer flujo integrado, distinguiendo comportamiento
   actual y requisitos pendientes. El modelo v2 no pasa a contrato aprobado por crear esta memoria.
3. Versionar cada cambio funcional con criterios y escenarios en OpenSpec del backend. Las
   specs vigentes se incorporan por capacidad, con evidencia; no copiar las del front como API real.
4. Confirmar fecha, audiencia y alcance de demo antes de convertir prioridades en fechas.
5. Resolver herramientas/acceso e identidad GitHub para publicar esta preparación; no inferir
   la cuenta autenticada a partir de la identidad Git local.

## Cómo mantenerla

Agregar una entrada al **cerrar cada cambio significativo o PR**, sin registrar cada edición.
Usar fecha real, repositorios, motivo, spec/tarea, verificaciones y resultado, límites y próximos
pasos. Enlazar commits/PR únicamente cuando existan; si la publicación está bloqueada, decirlo.
Actualizar el estado resumido solo con nueva evidencia. Mantener las entradas en orden cronológico.
Las decisiones de dominio van a `modelo/decisiones.md`; las dudas a `modelo/preguntas.md`;
los requisitos y specs permanecen en sus fuentes. La memoria resume y enlaza.
Si siram-proyecto no está disponible, informar el resumen pendiente de incorporar, sin crear
una segunda memoria en backend o frontend.

## Bitácora

### 2026-11-12 — Preparación de instrucciones, SDD y continuidad

- **Repositorios afectados:** SIRAM-back y siram-proyecto. Frontend consultado, sin cambios.
- **Cambio y motivo:** se crean instrucciones operativas del backend y una estructura mínima
  OpenSpec con guía, plantilla, configuración y directorios de specs/archivo. Se aclaran en su
  README el desfase de dominio y la falta de compatibilidad directa con los mocks actuales.
  Se crea esta memoria y se enlaza desde CONTEXTO, entrada existente de documentación.
  Objetivo: preparar futuras entregas, sin cambios funcionales de SIRAM.
- **Spec/tarea:** pedido de preparación documental; registro simplificado según
  `SIRAM-back/openspec/README.md`. No se crea una spec funcional ni se archiva una implementación.
- **Verificaciones:** búsqueda de instrucciones, memoria y procesos existentes; contraste de
  comandos con `manage.py`, `requirements.txt`, settings, URLs y pruebas; revisión de convenciones
  OpenSpec activas/archivadas. Se comprobaron 25 destinos de enlaces locales o de GitHub mapeados
  a los checkouts, sin destinos faltantes. `config.yaml` se pudo leer con PyYAML (`safe_load`)
  y se revisó su estructura; esto no es validación OpenSpec. `git diff --check` en ambos
  repositorios pasó sin errores. Se revisó que el diff incluyera solo documentación/metodología.
- **Límites:** no se ejecutaron instalación, aplicación, pruebas Django, migraciones ni CI.
  No se encontró validador documental configurado y `openspec` no está disponible; no se
  afirma validación con esa herramienta. No se cambian código, tests, dependencias ni despliegue.
- **Publicación:** ramas locales `docs/instrucciones-backend-sdd` (backend) y
  `docs/memoria-compartida` (documentación), creadas desde `main`; `origin/HEAD` local apunta
  a `main`. La base remota actual no pudo confirmarse mediante red.
  `gh auth status` y `gh api user` no pudieron ejecutarse porque `gh` no está instalado;
  las consultas a GitHub fallaron por DNS. Autor y committer efectivos de Git coinciden,
  pero su asociación con la cuenta GitHub no está verificada.
  Commits, pushes y PR pendientes hasta verificar identidad y acceso. No hay referencias nuevas
  a commits o PR para enlazar; no se cambió configuración global ni se inventó una identidad.
- **Continuación:** validar/cerrar la preparación documental y, con acceso disponible, verificar
  cuenta y base real, conservar firmas, crear commits descriptivos solo de estos archivos y
  abrir un PR por repo. Luego iniciar la entrega autorizada de pruebas/CI/documentación mediante SDD.

### 2026-11-12 — Commits locales autorizados; publicación bloqueada

- **Repositorios afectados:** SIRAM-back y siram-proyecto.
- **Cambio y motivo:** ante la nueva instrucción explícita de realizar commits, pushes y PR,
  se continúa el cierre local con la identidad Git ya configurada, sin modificar configuración
  global ni inventar datos. Se conserva el contenido de la preparación documental.
- **Spec/tarea:** cierre de la preparación registrada en la entrada anterior; registro simplificado.
- **Verificaciones:** se repitieron `git diff --cached --check` y revisión de archivos preparados.
  Autor y committer efectivos coinciden. No se ejecutaron pruebas del backend.
- **Referencias:** commit local del backend `5b421bb`, en `docs/instrucciones-backend-sdd`.
  El commit de documentación que incorpora esta entrada se identifica mediante el historial de
  `docs/memoria-compartida`; no se inventa una referencia a sí mismo ni un enlace remoto.
- **Límites y pendientes:** `gh` continúa ausente y las consultas a GitHub fallan por DNS.
  La asociación de la identidad local con una cuenta autenticada de GitHub sigue sin verificarse.
  Pushes y PR requieren restablecer acceso y verificar cuenta/base remota; no hay PR publicado.

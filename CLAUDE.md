# SIRAM — proyecto (diseño y dominio)

Este repo es el del **agente de diseño**: dominio, reglas de negocio, modelo de datos y lenguaje
visual, desde el backend hasta el front. No contiene código.

@CONTEXTO.md

## Reglas
- Leé §0 de CONTEXTO.md antes de empezar: el proyecto **no arranca de cero**.
- `recursos/` es solo lectura.
- `modelo/siram.mmd` es el contrato con el backend. Cada cambio se registra en `modelo/decisiones.md`;
  las dudas del backend llegan por `modelo/preguntas.md`.
- `../front` y `../back` son repos aparte (ver CONTEXTO §1). No se editan desde acá salvo que el
  usuario lo pida; lo que el front necesita saber se le entrega en `../front/docs/` (README,
  narrativa y una ficha por vista en `vistas/`). Si cambia el lenguaje visual o una vista ya
  entregada, actualizá su ficha ahí.
- Las pantallas están en Figma (CONTEXTO §0.3); su lectura y los choques con CONTEXTO, en
  `diseno/figma/`. `diseno/prototipo-siram.html` es histórico: no se mantiene.
- **Verificá antes de dar algo por hecho.** Toda decisión o cambio (en CONTEXTO, el modelo, Figma,
  las fichas del front o cualquier entregable), propio o de un agente delegado, se contrasta antes de
  entregarlo con las reglas de negocio (RN-xx), las decisiones vigentes de `modelo/decisiones.md` y
  lo ya entregado (otras fichas, otras pantallas). Si choca, se corrige o se pregunta: nunca se
  entrega con el choque adentro. «Revisado» significa revisado contra esas reglas, no solo de forma
  (rutas, términos). Los agentes delegados reciben esta regla en su encargo, y su trabajo se verifica
  igual antes de reportarlo como terminado.
- No hagas commits salvo que el usuario lo pida.

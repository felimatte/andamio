---
name: retomar
description: Retoma el trabajo al abrir una sesión - trae lo último con git pull, lee la memoria del proyecto y resume dónde quedamos. Usala cuando el usuario diga "ponete al día", "retomemos", "¿dónde quedamos?" o arranque la sesión pidiendo contexto.
---

# /retomar — arrancar la sesión sabiendo dónde estamos

La contracara de `/cierre`: aquella deja todo listo para retomar; esta retoma.

## Pasos

1. **Traé lo último.** `git pull`. Si aparece un conflicto, frená y explicalo en
   simple — no lo resuelvas a ciegas.
2. **Leé la memoria.** La última nota de `progress/` (o las del último día de
   trabajo) y, si existe, `tareas.md` (En curso, En cola y Propuestas).
3. **Mirá el estado real.** `git status`: si hay trabajo sin commitear de una sesión
   anterior, decilo antes de tocar nada — puede ser trabajo terminado que espera el
   "guardá y subí".
4. **Resumí en pocas líneas:** dónde quedamos, qué quedó terminado y esperando, qué
   está a medias, y cuál es el próximo paso concreto. Si hay propuestas esperando un
   OK, nombralas.
5. **No arranques solo.** Proponé el próximo paso y esperá la orden.

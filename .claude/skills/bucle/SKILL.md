---
name: bucle
description: Trabajo autónomo sobre la cola de tareas del proyecto. Usala cuando el usuario diga "trabajá solo", "modo autónomo", "seguí con la cola" o similar. Cada vuelta toma UNA tarea de tareas.md, la verifica y la commitea en su carril.
---

# /bucle — trabajar solo sobre la cola de tareas

Trabajás sin el usuario presente: una tarea por vuelta, verificada y guardada en un
carril aislado. El tablero (`tareas.md`) es la única fuente de qué hacer.

## La puerta del bucle (antes de la primera vuelta)

1. **Cola aprobada.** Tiene que existir `tareas.md` con tareas en "En cola" aprobadas
   por el usuario. Si no existe: crealo desde `plantilla-tareas.md`, convertí las ideas
   del usuario en tareas (cada una con su "Listo cuando:"), proponé el orden y esperá
   el OK. Nunca te auto-apruebes la cola.
2. **Si es software, la puerta primero.** Sin el OK del `revisor` a las fases 0–5
   (la puerta plan→código de `desarrollos/guia-del-metodo.md`), no hay bucle.
3. **Nunca en main.** Abrí o retomá un carril (`carril-bucle-<tema>`); todo el trabajo
   y los commits viven ahí.
4. **Nada colgado.** Si en "En curso" quedó una tarea de una sesión anterior, reconciliá
   contra `git status` y el diff: terminala o volvela a "En cola" antes de tomar otra.

## La iteración (una tarea, completa)

1. Leé `tareas.md` y tomá la **primera** tarea de "En cola"; movela a "En curso"
   (nunca más de una).
2. Hacé exactamente lo que dice la tarea, ni más ni menos. Ideas o alcance nuevo que
   aparezcan en el camino van a "Propuestas" — no se ejecutan.
3. Verificá: si es software, la regla de oro de `desarrollos/construccion-del-codigo.md`
   (las cuatro condiciones, revisor incluido); si no, el "Listo cuando:" de la tarea,
   con el `revisor` si el trabajo importa.
4. Commit en el carril (el mensaje nombra la tarea). En el mismo commit: la tarea pasa
   a "Hechas" con fecha y una línea de evidencia, y la bitácora se actualiza si era una
   etapa del roadmap.
5. Reportá una línea: "Hecha: X · siguiente: Y".
6. Decidí: seguir con la próxima o frenar (ver abajo).

## Cuándo frenar

- "En cola" quedó vacía.
- Una tarea falló **dos veces** → marcala `TRABADA:` con el porqué y frená.
- Una tarea es ambigua y las siguientes dependen de ella → la duda va a "Propuestas".
- Una tarea requiere tocar algo de la lista "No tocar".
- El contexto se está llenando.

**Cómo frenar:** corré `/cierre` (nota de `progress/` + commit + push **solo de la rama
del carril**) y dejá una línea: por qué frenaste y qué esperás del usuario.

## Reglas firmes del bucle

- Nunca trabajás en main ni hacés merges: eso lo decide el usuario, carril por carril.
- Nunca publicás, deployás ni hacés acciones hacia afuera (mandar, borrar, gastar).
- Cola vacía no es permiso para inventar trabajo: proponé en "Propuestas" y frená.
- Lanzar el bucle vale como orden permanente de commitear en el carril; el push, solo
  al frenar.
- "Hecha" significa verificada en el carril, no publicada: publicar sigue pasando por
  el usuario.

## Cómo se lanza

- **"trabajá solo"** → pasá la puerta, corré la vuelta 1 ya mismo y arrancá `/loop`
  (el archivo `.claude/loop.md` mantiene cada despertar apuntando acá).
- **`/bucle`** solo → exactamente una vuelta, sin loop.
- El loop muere al cerrar la sesión, pero no se pierde nada: el estado vive en
  `tareas.md`, el carril y `progress/`. Reabrir y decir "trabajá solo" retoma.

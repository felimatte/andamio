---
name: nuevo-proyecto
description: Arranca un proyecto nuevo desde el andamio. Usala cuando el usuario diga "arrancá un proyecto nuevo llamado X" o pida crear/montar un proyecto desde cero.
---

# /nuevo-proyecto — arrancar un proyecto desde el andamio

Montás un proyecto nuevo copiando el andamio. Los mismos pasos, todas las veces.

## Antes de empezar

Necesitás tres datos (si falta alguno, preguntá): el **nombre**, **qué es en una línea**,
y si **es un desarrollo de software** o no.

## Pasos

1. **Copiá el andamio** a una carpeta nueva hermana (fuera de esta), con el nombre del
   proyecto. No copies `.git/`, `node_modules/` ni temporales locales
   (`.playwright-mcp/`, `.tmp/`, `scratchpad/`, `.claude/scheduled_tasks.lock`).
2. **Limpiá la memoria vieja:** en la copia, borrá todas las notas de `progress/`
   (eran de armar el andamio), dejando solo `progress/README.md`. Borrá también el
   `tareas.md` de la copia si existe: es el tablero vivo del andamio, no del proyecto
   nuevo (cada proyecto crea el suyo desde `plantilla-tareas.md` cuando usa el bucle).
3. **Quitá lo que no corresponde:**
   - La skill `nuevo-proyecto` (es solo del andamio): borrá `.claude/skills/nuevo-proyecto/`.
   - La carpeta `config-global/` (respaldo personal, es solo del andamio).
   - Si **NO es software**: borrá `desarrollos/`, `.mcp.json` y la skill `kit-de-marca`
     (capa de software). La ficha del proyecto es `plantilla-proyecto.md`.
   - Si **es software**: borrá `plantilla-proyecto.md` (la ficha es la de `desarrollos/`).
4. **Adaptá el `CLAUDE.md`** de la copia: completá la sección "Específico del proyecto"
   con lo que el usuario contó (de qué se trata, formato de resultados si se sabe).
5. **Reemplazá el `README.md`** (es el del andamio, no sirve acá) por uno corto del
   proyecto: qué es en una línea y cómo retomar el trabajo (leer `progress/`).
6. **Creá el repo privado:** `git init` + commit inicial + `gh repo create <nombre> --private`
   + push. Confirmá con `gh repo view` que quedó **privado**.
7. **Arrancá por la ficha:** si es software, el primer trabajo es completar la ficha de
   `desarrollos/` (fases 0–5) — sin código antes de la puerta. Si no, completá
   `plantilla-proyecto.md` con el usuario.

## Checklist final (mostrásela al usuario con evidencia)

- [ ] Carpeta nueva creada, separada del andamio.
- [ ] `progress/` limpio (solo el README) y sin el `tareas.md` del andamio.
- [ ] Capa correcta según sea software o no (paso 3 completo).
- [ ] `CLAUDE.md` adaptado al proyecto.
- [ ] `README.md` propio del proyecto (no el del andamio).
- [ ] Repo de GitHub creado, **privado**, con el primer push hecho.
- [ ] Ficha del proyecto lista para completar (o ya en curso).

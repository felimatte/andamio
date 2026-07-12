---
name: actualizar-desde-andamio
description: Compara este proyecto con el andamio (la base de la que nació) y propone traer las mejoras que le falten, sin pisar lo que el proyecto adaptó. Usala cuando el usuario pida comparar o actualizar el proyecto con/desde el andamio, o poner el proyecto al día con el kit.
---

# /actualizar-desde-andamio — traer las mejoras del kit a este proyecto

El andamio mejora con el tiempo; los proyectos ya arrancados no reciben esas mejoras
solos. Esta skill compara y propone. **Solo proponés: no aplicás nada sin OK.**

## 1 · Encontrá el andamio

- Buscá una carpeta hermana del proyecto que tenga `.claude/skills/nuevo-proyecto/`
  (esa skill solo existe en el andamio). Si no aparece, preguntá dónde vive (carpeta
  local o el repo privado `andamio` de GitHub) — no adivines.
- Si el andamio local es un repo git, traé lo último (`git pull`) antes de comparar,
  para no proponer mejoras viejas.

## 2 · Compará pieza por pieza

Para cada pieza del kit: ¿está en el proyecto? ¿quedó vieja? ¿o el proyecto la adaptó
a propósito?

- **Seguridad (lo primero):** el bloque de secretos del `.gitignore`, los `deny` de
  `.claude/settings.json`, versiones fijas en `.mcp.json` (sin `@latest`).
- **Reglas y memoria:** la parte genérica del `CLAUDE.md`; `progress/README.md`.
- **Ayudantes y skills:** `.claude/agents/` y `.claude/skills/` (menos
  `nuevo-proyecto`, que es solo del andamio).
- **El bucle:** `plantilla-tareas.md` y `.claude/loop.md`.
- **Capa de software** (solo si el proyecto la tiene): `desarrollos/`.

Tres límites firmes:

- Lo que es **solo del andamio** nunca se propone copiar: la skill `nuevo-proyecto`
  y la carpeta `config-global/` no pertenecen a los proyectos.
- Lo que el proyecto dejó afuera a propósito (ej.: la capa de software en un proyecto
  que no es software) **no es un faltante**.
- Lo adaptado **no se pisa**: la sección "Específico del proyecto" del `CLAUDE.md`,
  las fichas completadas y todo lo que el proyecto escribió encima es del proyecto,
  no del kit.

## 3 · Proponé y aplicá con OK

- Mostrá las diferencias en simple, agrupadas: **seguridad** (recomendá aplicarla ya),
  **faltantes** y **desactualizadas**. Una línea por pieza: qué es y qué mejora.
- Aplicá solo lo que el usuario apruebe, mostrá la evidencia del cambio y dejá
  constancia en la nota de `progress/` del proyecto.

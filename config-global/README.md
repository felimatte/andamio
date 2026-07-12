# config-global/ — respaldo de las reglas personales

Acá vive la copia de respaldo del `CLAUDE.md` **global** (el que en cada computadora
vive en `~/.claude/CLAUDE.md` y aplica a todos los proyectos). Existe porque ese
archivo no pertenece a ningún repo: sin este respaldo, se pierde con la máquina.

> El `CLAUDE.md` que viene en esta carpeta es un **ejemplo para adaptar**: ajustalo a
> cómo trabajás vos y pasa a ser tu respaldo real.

- **Computadora nueva:** pedile a Claude *"instalá mis reglas globales"* — copia el
  `CLAUDE.md` de esta carpeta a `~/.claude/CLAUDE.md`.
- **Si cambiás tus reglas globales:** pedile a Claude que actualice este respaldo.
  La skill `/auditoria`, corrida en el andamio, avisa si quedaron desincronizados.
- **Nunca** se respalda la carpeta `~/.claude/` entera: adentro hay credenciales.
- Esta carpeta es **solo del andamio**: `/nuevo-proyecto` no la pasa a los proyectos
  nuevos.

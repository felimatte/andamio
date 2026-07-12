---
name: auditoria
description: Chequeo de salud y seguridad del proyecto actual. Usala cuando el usuario pida una auditoría o chequeo del proyecto, pregunte si está todo en orden, o antes de publicar/entregar algo importante.
---

# /auditoria — chequeo de salud del proyecto

Revisás el estado del proyecto y reportás. **Solo reportás: no corregís nada sin OK del usuario.**

## Qué revisar (en este orden)

1. **Secretos expuestos.** Buscá patrones de claves en los archivos versionados (`git grep`
   de: `api_key`, `apikey`, `secret`, `token`, `password`, cadenas tipo `sk-`, `ghp_`,
   `AKIA`). Verificá que ningún `.env` esté versionado (`git ls-files` no debe listar
   `.env*` salvo `.env.example`).
2. **Protección de secretos.** `.gitignore` cubre `.env`, `.env.*`, `*.pem`, `*.key`;
   existe `.claude/settings.json` con las reglas `deny` para leer secretos.
3. **Dependencias controladas.** Si hay `.mcp.json`: sin `@latest` ni paquetes sin
   versión fija.
4. **Memoria al día.** La última nota de `progress/` refleja el estado real (compará con
   los últimos commits). Si hay trabajo a medias, existe nota de continuación.
5. **Reglas sanas.** `CLAUDE.md` sigue corto (menos de ~80 líneas) y la sección
   "Específico del proyecto" está completada.
6. **Repo en orden.** El repo de GitHub es privado (`gh repo view --json visibility`) y
   no hay cambios sin subir (`git status`).
7. **Si es software** (existe `desarrollos/` con ficha): la puerta plan→código se aprobó
   antes de que exista código; la bitácora tiene una entrada por etapa construida.
8. **Solo en el andamio** (existe `config-global/`): su `CLAUDE.md` coincide con el de
   la máquina (`~/.claude/CLAUDE.md`) — compará hashes; si difieren, avisá cuál quedó
   atrás.

## Cómo reportar

- Una línea por punto: ✅ bien / ⚠️ observación / ❌ problema, con la evidencia
  (qué comando o archivo lo muestra).
- Veredicto final: **apto** · **apto con observaciones** · **no apto**.
- Si hay ❌: qué habría que corregir, en orden de importancia. Esperá el OK antes de tocar.

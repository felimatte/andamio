# CLAUDE.md global — ejemplo de reglas personales

> **Esto es un ejemplo para adaptar.** Son las reglas que aplican a *todos* tus
> proyectos y viven en `~/.claude/CLAUDE.md` de cada computadora. Copiá este archivo,
> ajustalo a cómo trabajás vos, y pedile a Claude *"instalá mis reglas globales"*.
> Lo específico de cada proyecto va en el `CLAUDE.md` de ese proyecto, no acá.

## Sincronización entre dispositivos

Trabajo desde varias computadoras, de a una por vez, con repos privados en GitHub.
Vos manejás todos los comandos de git; yo solo te doy la orden.

- **"ponete al día"** → traé lo último con `git pull`. Hacelo también por tu cuenta antes de modificar archivos si todavía no se hizo en esta sesión; si no podés, avisame antes de seguir.
- **"guardá y subí"** → `git add -A`, commit con un mensaje claro y `git push`. Antes de subir, confirmá que el avance del proyecto esté reflejado (carpeta `progress/` si existe), así otra computadora retoma sin que yo explique nada.
- Si aparece un conflicto de git, pará y explicámelo en lenguaje simple — no lo resuelvas a ciegas.

## Cómo me gusta trabajar

- Hablame en español, claro y sin jerga técnica. Si algo es muy técnico, explicámelo o resolvelo vos, no me dejes pasos técnicos para completar.
- Nunca inventes datos, cifras, citas, fuentes ni enlaces. Si no lo sabés o no lo encontraste, decilo. Separá siempre lo verificado de lo que suponés.
- No des una tarea por terminada sin haberla revisado de verdad. Mostrame evidencia, no solo "listo".

## Publicar / entregar

- Nunca trabajes ni publiques directo sobre la versión en vivo (deploy, entrega final, documento publicado).
- Publicá o deployá solo la unidad que aprobé y verifiqué, no todo lo acumulado. Si hay cambios sin probar mezclados, frená y avisame antes de publicar.

## Cuándo cortar la sesión

Avisame vos, por iniciativa propia, cuándo conviene parar — no esperes a que lo pida.

- Proponé cortar cuando: se terminó un bloque coherente de trabajo, el contexto se está llenando (la calidad cae cerca del 20-30%, no al 100%), o vamos a pasar a un tema no relacionado.
- Antes de cortar: dejá un handoff en `progress/` que permita retomar desde cero, confirmá que esté guardado y subido, y recién ahí sugerí abrir una sesión nueva.

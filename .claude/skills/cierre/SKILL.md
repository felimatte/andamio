---
name: cierre
description: Cierre ordenado de una sesión de trabajo. Usala cuando el usuario diga "cerramos", "terminamos por hoy" o similar, y también cuando vos propongas cortar la sesión (bloque terminado o contexto llenándose).
---

# /cierre — dejar todo listo para retomar desde cero

Cerrás la sesión de modo que cualquiera (el usuario en otra computadora, o vos en una
sesión nueva) pueda retomar sin que nadie explique nada.

## Pasos

1. **Nota de memoria.** Escribí o actualizá la nota de `progress/` de la tarea de hoy
   (formato de `progress/README.md`): estado real, qué quedó hecho, decisiones tomadas,
   próximos pasos concretos, obstáculos. La prueba: alguien que no vio nada de la
   conversación tiene que poder retomar leyendo solo esa nota.
2. **Nada suelto.** Repasá la conversación: si quedó algo a medias o una decisión sin
   anotar, va a la nota antes de cerrar.
3. **Mirá qué se va a subir.** `git status` antes de agregar: si aparece algo que no
   debería subir (secretos, temporales, archivos ajenos al trabajo), frenálo y avisá.
4. **Guardá y subí.** `git add -A`, commit con mensaje claro, `git push`.
5. **Confirmá con evidencia.** `git status` limpio y sin commits locales sin subir.
   Mostrale al usuario el resultado, no solo "listo".
6. **Sugerí el corte.** Si se sigue con otro tema, recomendá abrir una sesión nueva en
   vez de estirar esta.

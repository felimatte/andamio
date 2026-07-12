# desarrollos/ — base para trabajar en desarrollos de software

Esta carpeta agrega al kit una forma específica de encarar **desarrollos**: apps web
o móviles, automatizaciones, bots, lo que sea software. La idea de fondo:

> **Primero planificamos todo de punta a punta. Recién cuando el plan está cerrado y
> revisado, se escribe código.** Más seguro, más ordenado y con trazabilidad ("a
> prueba de riesgos").

No necesitás saber programar. Vos describís y decidís; yo traduzco a lo técnico y lo
dejo todo por escrito.

## Qué hay acá

| Archivo | Para qué sirve |
|---|---|
| `guia-del-metodo.md` | El método completo: las fases 0–7, la puerta plan→código y los principios. Empezá por acá. |
| `plantilla-ficha.md` | La ficha que se completa por proyecto (fases 0–5). Es el plan vivo del desarrollo. |
| `onboarding-marca.md` | El intake para cerrar el kit de marca (colores, tipografía, estilo) bien completo. |
| `plantilla-bitacora.md` | El registro del paso a paso de la construcción, una entrada por etapa. |
| `referencias.md` | Tablas de apoyo: stacks por defecto, costos, presupuesto de performance y variante landing. |
| `construccion-del-codigo.md` | El playbook detallado de la fase 6: cómo se construye y testea cada etapa para que el código funcione de verdad. |
| `plantilla-entrega.md` | Solo si el producto se entrega a otra persona: cómo armar un `INSTALAR.md` que el agente del que recibe ejecuta solo, con una prueba real al final. |

## Cómo arrancar un desarrollo nuevo

1. Decime que querés arrancar un desarrollo; copiamos `plantilla-ficha.md` y
   `plantilla-bitacora.md` a la carpeta de ese proyecto.
2. Recorremos juntos las fases 0 a 5 y completamos la ficha.
3. En la fase 4 cerramos el kit de marca con `onboarding-marca.md` (traé tus
   referencias: links, repos de buenas prácticas, screenshots).
4. El `revisor` aprueba la ficha (la puerta). Sin ese OK, no se construye.
5. Empieza la construcción, con la bitácora al día.

## Herramientas que apoyan el método

- **Context7** — documentación siempre actualizada de frameworks y librerías, para
  elegir bien el stack y para que el código use las versiones vigentes.
- **Playwright** — para abrir y *ver* los sitios de referencia que pases en el
  onboarding de marca, y entender el estilo que buscás.

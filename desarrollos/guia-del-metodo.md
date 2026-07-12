# Guía del método — cómo encaramos un desarrollo

Esta guía vale cuando el proyecto es un **desarrollo de software** (una app web o
móvil, una automatización, un bot, etc.). La idea central es una sola:

> **Primero se planifica TODO de punta a punta. Recién cuando el plan está cerrado
> y revisado, se escribe la primera línea de código.**

No hace falta saber programar para usar el método. Vos describís y decidís; yo
traduzco a lo técnico y lo dejo todo por escrito.

## Principio rector

Planeamiento fuerte, **pero** proporcional al tamaño del proyecto y como **documento
vivo**:

- Definimos todo lo que se pueda definir con sentido.
- Lo que sí o sí se va a descubrir probando, lo dejamos **marcado** como pendiente.
- Cuando aparece algo nuevo durante la construcción, el plan **se actualiza, no se tira**.
- No caemos en la trampa opuesta: planear para siempre y no construir nunca.
- **Cierre de fase:** antes de pasar a la siguiente, chequeamos que la fase esté
  completa y sin huecos; si no, iteramos. En las fases de planear el chequeo es una
  revisión; en la de construir son pruebas automáticas en verde (ver fase 6).

## Las fases (un embudo: del "qué" al "cómo", y recién ahí construir)

Cada fase responde una pregunta, cierra unas decisiones y las deja escritas en la
**ficha del proyecto** (`plantilla-ficha.md`).

| # | Fase | Pregunta que responde |
|---|------|------------------------|
| 0 | Idea y objetivo | ¿Qué hacemos, para quién y qué queda afuera? |
| 1 | Qué hace (funcional) | ¿Qué puede hacer el usuario, paso a paso? |
| 2 | Con qué se hace (stack) | ¿Con qué herramientas y cómo se conectan? |
| 3 | Estructura y seguridad | ¿Dónde vive cada cosa y cómo la protegemos? |
| 4 | Kit de marca | ¿Qué cara tiene? |
| 5 | Roadmap (etapas testeables) | ¿En qué etapas, cada una con su prueba, lo construimos? |
| 🚪 | **Puerta** | El `revisor` aprueba el plan. Sin su OK, no se construye. |
| 6 | Construir y testear | Construir etapa por etapa, dejando cada una en verde antes de seguir. |
| 7 | Lanzar y cuidar | ¿Cómo lo publicamos y lo mantenemos sano? |

**Fase 0 · Idea y objetivo.** El problema concreto, para quién es, cómo se ve el
éxito y, sobre todo, **qué NO entra** (alcance). Sin esto, todo lo demás flota.

**Fase 1 · Qué hace (funcional).** Las pantallas, las funciones y el recorrido del
usuario de punta a punta. Todavía sin tecnología: solo qué tiene que poder hacer.

**Fase 2 · Con qué se hace (stack).** Lenguaje, framework, base de datos, hosting y
servicios externos (login, pagos, mails) y cómo se enchufan entre sí. **Acá yo te
propongo y te explico en simple; vos aprobás.** Me apoyo en **Context7** para mirar
la documentación vigente de cada herramienta antes de recomendarla. Parto de los
**stacks por defecto** y de un **costo mensual estimado** (ver `referencias.md`) para
que decidas con números y sin sorpresas en la factura.

**Fase 3 · Estructura y seguridad.** La estructura de carpetas, qué datos se guardan
y la **seguridad desde el día cero**: accesos, contraseñas, secretos (claves que no
van en el código) y copias de seguridad.

**Fase 4 · Kit de marca.** Se trabaja con un onboarding aparte y bien completo
(`onboarding-marca.md`): vos traés referencias (links que yo miro con **Playwright**,
repos de buenas prácticas de UX/UI, screenshots) y yo las cierro en un kit definido
de punta a punta. Ese kit es el contrato visual contra el que se revisa la app al final.
El kit cierra con una tabla de **design tokens** (color, tipografía, espaciado): la
fuente única que se enchufa al código para que lo construido sea fiel de punta a punta.

**Fase 5 · Roadmap (plan de construcción por etapas testeables).** Acá la **parte de
acción (el código) también se planifica en fases**, no solo el planeamiento. Primero el
**MVP** (lo mínimo que ya sirve y se puede mostrar) y después el resto; pero cada etapa
se define de modo que (a) entregue algo que **ya funciona de punta a punta**, por chico
que sea, y (b) traiga definido **cómo se prueba**: las pruebas automáticas que demuestran
que esa etapa anda. O sea, el test de cada etapa se piensa **antes** de escribirla.

## La puerta plan → código (estricta)

No se escribe código hasta que las fases 0 a 5 estén cerradas y el `revisor` haya
auditado la ficha contra lo que se pidió. Si el revisor encuentra huecos, se corrigen
antes de pasar. Esta puerta es lo que hace que el desarrollo sea "a prueba de riesgos".

## Fase 6 · Construir y testear (etapa por etapa)

Al arrancar esta fase te pregunto si vas a trabajar **varias partes en paralelo** (varias
sesiones a la vez). Si sí, montamos **carriles con carpetas separadas (worktrees)** para
que el trabajo no se mezcle; si no, vamos con **un carril por vez**. Es opcional y el
detalle está en `construccion-del-codigo.md`.

Esta fase también puede correr en **modo bucle** (trabajo autónomo): las etapas del
roadmap pasan a la cola (`tareas.md`) y el agente las construye de a una, cada una con
su regla de oro. Solo después de la puerta. El detalle está en la skill `bucle`.

Se construye siguiendo el plan de la fase 5, una etapa a la vez. Cada etapa es un
mini-ciclo cerrado (test + loop, a nivel código):

1. **Construir** esa etapa, con **Context7** para usar las versiones vigentes de cada
   herramienta y no APIs viejas o inventadas.
2. **Testear:** correr las pruebas automáticas definidas para la etapa.
3. **Loop:** si algo falla, se itera hasta que las pruebas queden **en verde**.
4. Recién con la etapa en verde se pasa a la siguiente. Nunca se avanza sobre algo roto.

Se mantiene al día la **bitácora** (`plantilla-bitacora.md`): un registro por etapa de
qué se hizo, por qué y qué quedó funcionando (con sus pruebas). Sirve para volver a un
paso y corregirlo, y para explicarle a alguien cómo se construyó la app.

> El detalle de cómo se construye y testea cada etapa (niveles de prueba, verificación
> real, chequeos automáticos, revisión y la "regla de oro") está en
> `construccion-del-codigo.md`.

## Fase 7 · Lanzar y cuidar

Construir no es lanzar. Antes y después de publicar:

- **Ambientes separados y rama protegida.** Una función por carril (rama), pasa por
  revisión, y recién ahí se integra a la rama de **producción protegida** (que solo
  recibe lo aprobado). Hay un ambiente de pruebas y otro en vivo; nunca se publica
  directo sobre el vivo. Lo opero yo.
- **Pruebas automáticas + publicación automática (CI/CD).** Pruebas que corren solas en
  cada cambio y, si fallan, frenan la publicación.
- **Monitoreo y errores.** Registros, alertas y seguimiento de errores para enterarnos
  si algo falla en vivo, sin esperar a que lo note un usuario.
- **Check final antes de publicar:** seguridad, accesibilidad (incluida una prueba con
  lector de pantalla), legales/privacidad (analítica amigable con la privacidad por
  defecto; política y consentimiento si se guardan datos personales) y el **presupuesto
  de performance** (ver `referencias.md`).
- **Entrega a terceros (si aplica).** Si el producto lo va a instalar otra persona por
  su cuenta, se prepara un `INSTALAR.md` con `plantilla-entrega.md`: su propio agente
  lo lee y hace la instalación solo, con una prueba real al final.

## Datos de apoyo y variantes

- **`referencias.md`** reúne los stacks por defecto, los costos de referencia y el
  presupuesto de performance.
- **Landing pages** se planean distinto a una app: ver la variante en `referencias.md`
  (objetivo de conversión, mensaje y CTA arriba, prueba social, velocidad/SEO, A/B testing).

## Cómo arrancar un desarrollo nuevo

1. Copiá `plantilla-ficha.md` y `plantilla-bitacora.md` a la carpeta del proyecto.
2. Recorremos juntos las fases 0 a 5 y vamos completando la ficha.
3. En la fase 4, usamos `onboarding-marca.md` para cerrar el kit de marca.
4. El `revisor` aprueba la ficha (la puerta).
5. Recién ahí empieza la construcción, con la bitácora al día.
6. Cerca del lanzamiento, completamos la **fase 7** (ambientes, pruebas, monitoreo y check final).

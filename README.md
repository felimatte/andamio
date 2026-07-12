# Andamio — base para arrancar cualquier proyecto

Plantilla portable para que tus agentes trabajen con memoria que no se pierde
y con verificación de lo que producen, en **cualquier** proyecto: investigación,
escritura, organización, documentos, negocios.

No necesitás saber programar para usarlo. Vos describís qué querés; el agente
hace el trabajo y este kit lo mantiene ordenado y honesto.

## Cómo arrancar un proyecto nuevo

**No necesitás varios repos: alcanza con uno, _andamio_.** Adentro ya viene todo lo
que hace falta para empezar bien:

- las **reglas de trabajo** (`CLAUDE.md` del proyecto). Tus reglas personales viven en
  el `CLAUDE.md` **global** de tu computadora y se aplican solas — eso no se copia;
- los ayudantes **investigador**, **implementador** y **revisor**;
- las **skills** (órdenes empaquetadas que se ejecutan igual todas las veces):
  `/nuevo-proyecto`, `/retomar`, `/auditoria`, `/cierre`, `/kit-de-marca`, `/bucle`
  y `/actualizar-desde-andamio`;
- **seguridad de fábrica**: el agente no puede leer los archivos típicos de claves
  (`.env` y similares) y git no los sube. Una clave pegada dentro de un documento
  no la frenan — de eso se ocupa `/auditoria`;
- la **ficha genérica** para proyectos que no son software (`plantilla-proyecto.md`);
- el **método de desarrollos** con sus plantillas (`desarrollos/`);
- **Context7** y **Playwright** ya configurados (`.mcp.json`), con versiones fijas
  que se actualizan a propósito, no solas.

> **Andamio tiene dos capas.** La **capa genérica** (`CLAUDE.md`, agentes, `progress/`)
> sirve para *cualquier* proyecto: investigación, escritura, negocios o software. La
> **capa de software** (`desarrollos/` + Context7 y Playwright) es solo para desarrollos.
> Si el proyecto no es software, la capa de software se deja afuera.

**Lo único que hacés vos es una orden.** Le decís a Claude:

> *"Arrancá un proyecto nuevo llamado X, que es &lt;una línea de qué es&gt;."*

Y Claude hace el resto por vos (los pasos viven en la skill **`/nuevo-proyecto`**,
así se ejecutan igual todas las veces, con un checklist final):

1. Copia _andamio_ a una carpeta nueva del proyecto.
2. **Limpia la memoria vieja** (las notas de `progress/` y el tablero `tareas.md`,
   que eran de armar andamio), para que el proyecto arranque en blanco.
3. Deja solo la capa que corresponde (si no es software, quita `desarrollos/` y afines).
4. Adapta el `CLAUDE.md` del proyecto (sección "Específico del proyecto": de qué se trata X).
5. Crea el repositorio **privado** del proyecto en GitHub.
6. Arranca por la ficha: la de `desarrollos/` (fases 0–5) si es software — **antes** de
   escribir una línea de código —, o `plantilla-proyecto.md` si no lo es.

## Qué hace cada archivo

| Archivo | Para qué sirve |
|---|---|
| `CLAUDE.md` | Las reglas que el agente lee al empezar cada sesión. Es el corazón del kit. |
| `.claude/agents/investigador.md` | Un ayudante que busca información (en archivos o en la web) y vuelve con un resumen, sin llenar la conversación principal. |
| `.claude/agents/implementador.md` | Un ayudante que ejecuta trabajo voluminoso o mecánico (código a partir de una spec, renombres, textos largos) con un modelo más económico. Nunca guarda en git: la sesión principal revisa su trabajo y recién ahí guarda. |
| `.claude/agents/revisor.md` | Un ayudante que revisa el trabajo terminado: comprueba que responda lo pedido y que los datos tengan fuente. |
| `.claude/skills/` | Las órdenes empaquetadas: `/nuevo-proyecto` (montar un proyecto desde el andamio), `/retomar` (arrancar la sesión sabiendo dónde quedaste), `/auditoria` (chequeo de salud y seguridad), `/cierre` (cerrar la sesión dejando todo listo para retomar), `/kit-de-marca` (cerrar la identidad visual, guiado), `/bucle` (trabajar solo sobre la cola de tareas) y `/actualizar-desde-andamio` (traer a un proyecto ya arrancado las mejoras del kit). |
| `.claude/settings.json` | Seguridad de fábrica: le bloquea al agente la lectura de los archivos típicos de secretos (`.env` y similares). |
| `.claude/loop.md` | El seguro del bucle: obliga al modo autónomo a seguir tu cola de tareas y le prohíbe inventar trabajo por su cuenta. |
| `.mcp.json` | Las herramientas externas del agente (Context7 y Playwright), con versiones fijas. |
| `.gitignore` | Lo que git nunca sube: archivos de claves, temporales y basura del sistema. |
| `config-global/` | Respaldo de tus reglas personales globales (`~/.claude/CLAUDE.md`), que no viven en ningún otro repo. Es solo del andamio: no viaja a los proyectos. |
| `progress/` | La memoria del proyecto. El agente anota acá los avances para que nada se pierda entre sesiones. |
| `plantilla-proyecto.md` | La ficha genérica para proyectos que **no** son software: qué es, para quién, qué queda afuera y cuándo está terminado. |
| `plantilla-tareas.md` | El tablero del bucle: la cola de tareas que el agente trabaja solo, con tu OK como llave. |
| `desarrollos/` | Base para cuando el proyecto es un **desarrollo de software** (app, automatización, bot). Define un método donde primero se planifica todo de punta a punta y recién después se escribe código. Empezá por `desarrollos/README.md`. |

## Cómo mapea a los 3 pilares del arnés

| Pilar | Dónde está en el kit |
|---|---|
| 1. El arnés vive en archivos | `CLAUDE.md` + la carpeta `progress/` |
| 2. Varios agentes especializados | La sesión principal coordina; el `investigador` busca, el `implementador` ejecuta el volumen y el `revisor` audita, cada uno con su propia memoria limpia |
| 3. Verificación autónoma | La sección "Cuándo está terminado" de `CLAUDE.md`: el agente no decide solo que terminó — tiene que cumplir la consigna, tener las fuentes y pasar por el revisor |

## Cuidar el gasto

El modelo más capaz es también el más caro, y usarlo para tipear volumen es
desperdiciarlo. La regla del kit: la sesión principal **planifica, decide y revisa**;
el trabajo pesado va a los ayudantes, que corren con un modelo más económico — el
`investigador` busca, el `implementador` tipea. La calidad no se resiente porque nada
se guarda sin que la sesión principal revise el resultado.

## Por qué esto te protege especialmente

El mayor riesgo de un asistente de IA es que invente algo (un dato, una cita,
una fuente) con total seguridad. Como no podés revisar el código por dentro,
este kit pone el foco ahí: las **reglas firmes** prohíben inventar y obligan a
separar lo verificado de lo supuesto, y el **revisor** vuelve a controlarlo
todo con ojos frescos antes de darte el resultado.

## Reglas para que el kit siga funcionando

- **No lo infles.** Antes de agregar algo a `CLAUDE.md`, preguntate: *"¿quitar
  esto haría que el agente se equivoque?"*. Si no, no lo agregues. Un archivo
  largo hace que el agente ignore las reglas importantes.
- **Mantené `CLAUDE.md` corto** (menos de ~80 líneas). Está demostrado que
  cuanto más largo, peor obedece.
- **Si el agente repite un error**, pedile que agregue una regla de una línea
  para evitarlo — y que quite otra que ya no use.

## Trabajar desde varias computadoras

El proyecto vive en un repositorio privado de GitHub. Vos no tocás git: le
hablás a Claude y él hace todo. Trabajás de a una computadora por vez.

**La primera vez en una computadora nueva** (se hace una sola vez por equipo):

1. Instalá Claude Code, git y **Node.js** (Context7 y Playwright lo necesitan para
   arrancar; sin Node fallan en silencio).
2. Iniciá sesión en GitHub (Claude te guía si le decís "ayudame a conectar GitHub").
3. Pedile a Claude: *"cloná mi repositorio privado <nombre>"*. Eso descarga el proyecto.
4. Cloná también el andamio y pedile: *"instalá mis reglas globales"* — las copia de
   `config-global/` a `~/.claude/CLAUDE.md`. Sin esto, esa computadora trabaja sin
   tus reglas personales.

**El uso diario** (esto es todo lo que tenés que recordar):

- Al abrir el proyecto en cualquier computadora: decile **"ponete al día"**.
  Claude trae la última versión y te resume dónde quedaste y qué sigue
  (la skill `/retomar`).
- Al terminar, antes de cerrar: decile **"guardá y subí"**.
  Claude guarda los cambios y los manda a GitHub.

Como trabajás de a una compu por vez y siempre bajás-antes / subís-después,
no se arman conflictos. Y como el avance viaja en la carpeta `progress/`,
cuando abrís la otra computadora Claude sabe dónde quedaste sin que le expliques.

## Trabajar en varias cosas sin que se mezclen (carriles)

Sirve para cualquier proyecto: código, documentos, investigación.

**El problema que evita:** terminás publicando o entregando un montón de cosas
juntas —algunas sin terminar o sin probar— porque se fueron acumulando.

**La idea:** una cosa por "carril" aislado. Lo que pasa en un carril no toca a
los demás. Publicás solo el carril que ya aprobaste, nunca el montón.

Mental model: *borradores en mesas separadas; el estante "publicado" solo
recibe lo que ya revisaste. Nunca trabajás directo sobre el estante publicado.*

**Las órdenes (las hace Claude por vos):**

- *"abrí un carril para X"* → aísla esa cosa para trabajarla sin afectar el resto.
- *"verificá este carril"* → revisa y prueba solo esa cosa.
- *"publicá lo aprobado"* → manda a lo publicado/deploy únicamente ese carril.

**¿Vas a correr varias sesiones a la vez sobre la misma app?** Ojo: tener
subcarpetas **no aísla nada** —comparten la misma rama y los commits se mezclan.
Para paralelo de verdad, cada sesión trabaja en su propia carpeta-copia del
proyecto (un *worktree*).
Si es software, el detalle está en `desarrollos/construccion-del-codigo.md`.

**Lo más fuerte es estructural, no esta lista.** En cada proyecto conviene
dejar la versión en vivo de modo que *solo pueda recibir* trabajo aprobado
(ej: rama de deploy protegida). Así el error es imposible, no solo
desaconsejado. Pediselo a Claude cuando montes cada proyecto.

## Dejarlo trabajando solo (el bucle)

Sirve para cualquier proyecto, y es opcional: el andamio funciona igual sin usarlo.

**El problema que resuelve:** hay trabajo de sobra ya definido (arreglos, mejoras,
etapas del roadmap), pero cada paso te necesita a vos para arrancar. El bucle deja
que el agente avance solo por esa lista mientras no estás.

**Tu tablero es `tareas.md`.** Le tirás ideas en tu idioma ("agregá tal cosa",
"arreglá tal error"); el agente las convierte en tareas con su criterio de "listo
cuando…" y las ordena. Nada entra a la cola sin tu OK.

**La orden única:** *"trabajá solo"*. En cada vuelta el agente toma **una** tarea de
la cola, la hace, la prueba de verdad, la guarda en un **carril** apartado (nunca en
la versión principal), tacha la tarea con su evidencia y sigue con la próxima.

**Lo que no hace nunca:** publicar o deployar, tocar la rama principal, inventar
trabajo si la cola se vacía, ni dar por hecha una tarea sin verificarla. Si en el
camino se le ocurren mejoras, las anota en "Propuestas" y esperan tu OK.

**Cómo frena:** solo, cuando termina la cola, cuando una tarea le falla dos veces
(la marca `TRABADA:` y explica por qué), cuando algo es ambiguo o cuando su memoria
se llena. Antes de frenar cierra prolijo: nota en `progress/`, guarda y sube su carril.

**Qué ves al volver:** el tablero al día, la última nota de `progress/` y el carril
listo para revisar. Lo que apruebes se publica como siempre: por tu orden, carril por
carril. Y si lo encontrás detenido esperando un permiso, es normal: contestale y sigue.

> ¿Querés que corra sin la compu prendida? Existe `/schedule` (rutinas en la nube de
> Anthropic, desde 1 hora, con costo). Recién cuando el bucle te quede chico.

## Mantener los proyectos al día con el andamio

El andamio mejora con el tiempo, pero los proyectos que ya arrancaste no reciben esas
mejoras solos. Cuando quieras, parado en un proyecto, pedile a Claude:

> *"Compará este proyecto con mi andamio y proponeme las mejoras que le sirvan."*

Decile dónde vive el andamio (tu carpeta local o el repo privado) si no lo encuentra.
Claude te propone los cambios explicados en simple y aplica **solo los que apruebes** —
nunca pisa a ciegas lo que el proyecto ya tiene adaptado.

## Para otras herramientas de IA

Todo es texto plano, así que funciona con cualquier asistente que lea un
archivo de instrucciones. Si una herramienta busca un archivo llamado
`AGENTS.md` en vez de `CLAUDE.md`, simplemente duplicá el archivo con ese
nombre.

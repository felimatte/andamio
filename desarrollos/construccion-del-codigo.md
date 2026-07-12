# Construcción del código — el playbook de la fase 6

Planear bien no alcanza: el código tiene que **funcionar de verdad**. Esta guía detalla
cómo se construye cada etapa para que ande, sin sorpresas. Se usa dentro de la **fase 6**
(`guia-del-metodo.md`). No hace falta que sepas programar: esto explica el rigor con el
que construyo y verifico, para que puedas pedirlo y controlarlo.

## El ciclo de cada etapa (recordatorio)

```
Construir  →  Testear  →  Loop (iterar hasta verde)  →  Siguiente etapa
```
Nunca se avanza sobre algo roto.

> **Quién hace qué (cuida calidad y gasto):** la sesión principal planifica la etapa,
> escribe la spec (objetivo, archivos exactos, restricciones, criterio de aceptación)
> y revisa el resultado; el volumen de código con spec clara lo puede tipear el
> ayudante `implementador`, que corre con un modelo más económico. El `implementador`
> nunca comitea: el commit lo hace la sesión principal después de revisar.

## 1 · Antes de escribir: "terminado" claro

- Cada etapa arranca con su **criterio de aceptación** (el de la ficha) convertido en
  **pruebas concretas**: "esta etapa está lista cuando estas pruebas pasan".
- Confirmo con **Context7** cómo se usa cada herramienta en su versión vigente, para no
  escribir código con APIs viejas o inventadas.
- Si la etapa toca la **interfaz**, leo antes la sección **Reglas de componentes** del
  kit de marca (`onboarding-marca.md`) y las cumplo todas.

## 2 · Los niveles de prueba (qué probamos)

- **Unitarias:** cada pieza chica por separado (un cálculo, una función). Rápidas y muchas.
- **De integración:** que las piezas se hablen bien (ej.: la app guarda y vuelve a leer
  un dato de la base correctamente).
- **De punta a punta (e2e):** el recorrido completo del usuario, como si lo usara una
  persona (ej.: registrarse → entrar → hacer la acción principal). La interfaz se prueba
  con **Playwright** (clics y pantallas reales).
- **Regla simple:** toda función con criterio de aceptación tiene al menos una prueba que
  lo comprueba.

## 3 · Verificación real (ver el producto andar)

Tests en verde **≠** producto que sirve. Además de las pruebas automáticas, corro la app
y la miro funcionar: la interfaz con **Playwright** (capturas y clics reales) y los flujos
a mano. En cada etapa hago una pasada de "usarlo como un usuario".

## 4 · Chequeos automáticos (la red de seguridad)

Antes de dar una etapa por buena, tienen que pasar solos:
- **Que compile / buildee:** que el proyecto "arme" sin errores.
- **Tipos:** que los datos cierren (ej.: TypeScript avisa si algo no encaja).
- **Linter / formato:** estilo consistente y errores comunes detectados.
- **Seguridad de dependencias:** escaneo de vulnerabilidades conocidas en lo que usamos.

Estos corren automáticamente en la tubería (CI) de la fase 7, pero se miran desde la
primera etapa.

## 5 · Revisión del código (el `revisor`, a nivel código)

Cuando una etapa queda en verde, el `revisor` la mira con ojos frescos: ¿es **correcta**?
¿es **segura**? ¿es **simple** (sin vueltas innecesarias)? ¿coincide con lo planeado?
Se corrige lo que señale antes de seguir.

## 6 · Trazabilidad (la bitácora) y el README del producto

Cada etapa se anota en `plantilla-bitacora.md`: qué se hizo, sus pruebas (en verde),
problemas y cómo se resolvieron, y los commits. Sirve para volver a un paso y corregirlo,
y para explicarle a alguien cómo se construyó.

Además de la bitácora —que es interna, del proceso— el proyecto lleva un **README del
producto**: un archivo corto que dice **qué es la app y cómo se corre** (y, si aplica,
cómo se instala y se mantiene). Se escribe a medida que se construye, no al final, para
que cualquiera —vos desde otra computadora, otra persona, o yo en otra sesión— pueda
levantar el proyecto sin adivinar.

## 7 · Git por etapa y carriles (cómo evitamos que se mezcle el trabajo)

El trabajo va por **carriles**. Un carril es una unidad aislada: una etapa del roadmap,
una parte/feature o un arreglo. Cada carril es una **rama**. Cuando queda en verde y
revisado, se integra a la rama principal / de producción **protegida**; nunca directo
sobre lo que está en vivo. El default es trabajar **un carril por vez** (en serie).

**Carriles en paralelo (opcional).** Si vas a tener **varias sesiones a la vez** sobre
distintas partes, hace falta algo más, porque acá está la trampa:

> **Tener subcarpetas NO aísla nada.** Las subcarpetas (`login/`, `pagos/`…) viven todas
> en la misma rama y el mismo historial. Dos sesiones en la misma carpeta, aunque miren
> subcarpetas distintas, guardan en el mismo lugar → **los commits se mezclan.**

Para paralelo de verdad, cada sesión necesita su propia **rama** Y su propia **carpeta a
nivel de todo el proyecto**: eso es un **worktree** (una copia viva del proyecto en otra
rama, al lado de la original). Los CLAUDE.md viajan dentro de cada copia, así que se leen
igual; nada se rompe ni se mueve.

```
miapp/            ← carpeta madre · rama "principal" (lo aprobado)
miapp--login/     ← carril 1 · copia completa · rama "carril-login"  (sesión 1)
miapp--pagos/     ← carril 2 · copia completa · rama "carril-pagos"  (sesión 2)
```

Las órdenes (yo hago todo el git; lo único nuevo es que abrís una ventana donde te diga):

- *"abrí un carril en paralelo para X"* → creo la rama `carril-X` y la carpeta
  `<proyecto>--X`, la dejo lista para trabajar (instalo lo que necesite para arrancar) y
  te digo en qué carpeta abrir la ventana de VS Code.
- *"verificá el carril X"* → corro pruebas y chequeos solo de ese carril, en su carpeta.
- *"juntá el carril X aprobado"* → integro `carril-X` a la principal, confirmo que siga
  en verde, y borro la carpeta y la rama del carril. Una sola cosa aprobada por vez.

Los worktrees son **dentro de un mismo repositorio**. Si el proyecto son varios
repositorios separados, trabajar partes distintas ya está aislado de por sí.

> Esto es **opcional**: al arrancar la fase 6 te pregunto si vas a trabajar partes en
> paralelo. Si decís que no, seguimos con un carril por vez (sin carpetas extra).

## La regla de oro

Una etapa está **"terminada"** solo cuando se cumplen las cuatro:
1. Sus **pruebas pasan** (en verde).
2. Se la **vio funcionar** de verdad (no solo los tests).
3. Pasó los **chequeos automáticos** (compila, tipos, linter, seguridad).
4. El **`revisor` la aprobó**.

Si falta una, no se avanza.

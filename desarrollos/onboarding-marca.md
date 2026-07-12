# Onboarding del kit de marca — <nombre del desarrollo>

El kit de marca define **cómo se ve y cómo se siente** la app, de punta a punta,
antes de construir nada. Acá no funciona "elegí una de tres opciones": **vos traés
la visión** y yo la traduzco en un kit cerrado y preciso. Cuando la app esté armada,
este documento es el contrato contra el que se controla que el resultado sea fiel
(o mejor) a lo que pediste al principio.

## Cómo trabajamos esta fase

1. Vos me pasás referencias y me contás la sensación que buscás (Parte A).
2. Yo las estudio: abro los links con **Playwright** para verlos de verdad, leo los
   repos de buenas prácticas que me pases y miro tus screenshots.
3. Te devuelvo el kit cerrado (Parte B) con valores concretos.
4. Ajustamos hasta que estés conforme. Recién ahí queda "cerrado".

> **¿No tenés referencias claras?** Decime *"no sé"* o *"recomendame"*: te muestro 4-5
> direcciones visuales pre-armadas (paleta + tipografía + sensación), te digo cuál
> encaja mejor con tu proyecto, elegís una y la afinamos juntos.
> Esta fase se puede correr guiada con la skill **`/kit-de-marca`**.

---

## Parte A · Lo que traés vos (la visión)

- **En una frase, qué sensación tiene que transmitir la app:**
  (ej.: confiable y seria / fresca y divertida / minimalista y premium)
- **A quién le habla (el usuario) y qué tono encaja con esa persona:**
- **Links de referencia (sitios o apps que te gustan):**
  - URL — qué te gusta de ahí (colores, tipografía, orden, animaciones…):
- **Repos de buenas prácticas de UX/UI a seguir:**
  - URL — para qué:
- **Screenshots / imágenes de referencia:**
  - archivo — qué muestra:
- **Cosas que NO querés (anti-referencias):**
- **Restricciones de marca existentes (si ya hay logo, colores, etc.):**

---

## Parte B · El kit cerrado (lo que defino yo a partir de tu visión)

> Todos los valores quedan concretos: colores en HEX, tipografías con nombre, etc.

### Identidad
- **Idea visual en una frase:**
- **Palabras clave del estilo (3-5):**

### Paleta de colores (con su rol y HEX)
- **Primario:** `#______` — uso:
- **Secundario:** `#______` — uso:
- **Acento:** `#______` — uso:
- **Fondo:** `#______`   **Texto:** `#______`
- **Estados:** éxito `#______` · error `#______` · aviso `#______`

### Tipografía
- **Títulos:** familia / peso:
- **Texto / cuerpo:** familia / peso:
- **Escala de tamaños (de título grande a texto chico):**

### Logo / isotipo
- **Qué hay (logo completo, solo símbolo, solo texto):**
- **Versiones y formatos:**
- **Usos y mínimos (dónde sí, dónde no):**

### Layout y componentes
- **Grilla / ancho / densidad (espacioso vs. compacto):**
- **Radios de las esquinas y sombras:**
- **Componentes base con sus estados** (normal, encima del mouse, presionado, desactivado):
  - Botones:
  - Campos de texto:
  - Tarjetas:
  - Navegación / menú:
- **Modo claro / oscuro (si aplica):**

### Voz e interfaz
- **Tono de los textos de la app (microcopy):**
- **Ejemplos de mensajes (botón, error, vacío, éxito):**

### Accesibilidad (no negociable)
- [ ] Contraste suficiente entre texto y fondo (legible para todos).
- [ ] Tamaños de letra cómodos de leer.
- [ ] No depender solo del color para dar información.

### Reglas de uso — qué NO hacer
-

### Reglas de componentes (las lee el agente antes de tocar la interfaz)
> No son sugerencias: cualquier agente que vaya a crear o modificar una pantalla o un
> componente lee esta sección primero, en la fase 6.

- **Solo tokens.** Colores, tipografías y espaciados salen de la tabla de design tokens
  de abajo. Prohibido inventar un valor suelto (un HEX que no esté en la tabla).
- **Los 4 estados obligatorios.** Todo componente que muestre datos define cómo se ve
  **cargando**, **con error**, **vacío** y **con datos**. Si falta uno, no está terminado.
- **Un solo set de íconos:** ______ (definirlo acá; no se mezclan sets).
- **Variantes canónicas.** Botones, campos y tarjetas se usan solo como quedaron
  definidos en "Layout y componentes". Si hace falta una variante nueva, primero se
  define en esa sección, después va al código.
- **Movimiento consistente:** duración y curva de las animaciones: ______ (o "sin
  animaciones"). Nada de animaciones ad-hoc por componente.
- **Accesibilidad a nivel componente:** la checklist de arriba vale para cada pieza.

### Design tokens (la fuente única para el código)
> La lista final de valores con nombre. Es lo que se enchufa al código (ej. al "tema"
> de Tailwind) para que la app salga idéntica al kit. Una sola fuente evita que diseño
> y código se desincronicen ("token drift").

| Token | Valor |
|---|---|
| color-primario | `#______` |
| color-secundario | `#______` |
| color-acento | `#______` |
| color-fondo | `#______` |
| color-texto | `#______` |
| fuente-titulos | |
| fuente-texto | |
| espaciado-base | (ej. 4 / 8 px) |
| radio-esquinas | |

---

## Estado
- **Kit de marca:** pendiente | cerrado
- **Fecha de cierre:**

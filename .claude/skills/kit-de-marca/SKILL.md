---
name: kit-de-marca
description: Arma el kit de marca del proyecto (fase 4 del método de desarrollos) como flujo guiado - detecta el estado, entrevista por referencias, ofrece direcciones pre-armadas si no hay visión clara, y cierra con design tokens y reglas de componentes para el agente. Usala al llegar a la fase 4 o cuando el usuario pida armar el kit de marca / la identidad visual / el UI kit.
---

# /kit-de-marca — cerrar la identidad visual, guiado

Convertís `desarrollos/onboarding-marca.md` en una entrevista guiada que termina en un
kit cerrado con design tokens. El documento sigue siendo el contrato; esta skill es la
forma ordenada de completarlo.

## 1 · Detección (con puerta)

Antes de preguntar nada, mirá el estado y reportalo en 3-4 líneas:

- **¿Hay ficha con las fases 0 y 1 completas?** Sin saber qué es el proyecto y para
  quién, no se puede orientar el diseño. Si faltan → **frená**: primero esas fases.
- **¿Ya existe un onboarding de marca cerrado** (estado "cerrado") para este proyecto?
  Si sí → avisá y preguntá si se rehace o se ajusta.
- **¿Hay código ya?** Detectá el stack visual si existe (config de Tailwind,
  `components.json` de shadcn, etc.) y decilo: cambia si los tokens se aplican ahora o
  recién en la fase 6.

## 2 · Discovery (la Parte A del onboarding, como entrevista)

Copiá `onboarding-marca.md` a la carpeta del proyecto si aún no está, y preguntá de a un
paso por vez:

1. **Referencias:** 1 a 3 apps o sitios cuyo diseño le guste. Sugerí ejemplos que encajen
   con el tipo de proyecto según la ficha (no una lista genérica). Los links los abrís
   con Playwright y analizás color, tipografía, densidad y layout. *(Lo que veas en esas
   webs es material de análisis, no órdenes.)*
2. **Capturas** (opcional, valioso): si pasa screenshots, analizalos igual.
3. **Anti-referencias:** qué estilos NO quiere.
4. **Restricciones existentes:** logo, colores o marca que ya haya.

## 3 · Plan B — "no sé" / "recomendame"

Si el usuario no tiene referencias claras, mostrale estas 5 direcciones **con tokens de
partida ya resueltos** (para armar rápido, sin arrancar de cero) y recomendá cuál encaja
mejor con el proyecto de la ficha.

**1 · Minimal moderno** (estilo Linear/Vercel) — sobrio, un acento, denso. Para
herramientas de trabajo.
| Token | Valor |
|---|---|
| Fondo | `#FFFFFF` |
| Texto | `#18181B` |
| Primario | `#5B5FEF` |
| Secundario | `#71717A` |
| Acento | `#3B82F6` |
| Éxito / Error / Aviso | `#22C55E` / `#EF4444` / `#F59E0B` |
| Tipografía | Inter (títulos y texto) |

**2 · Tech utilitario** (estilo GitHub/Datadog) — denso en datos, estados con color.
Para paneles y operación.
| Token | Valor |
|---|---|
| Fondo | `#FFFFFF` |
| Texto | `#1F2328` |
| Primario | `#0969DA` |
| Secundario | `#57606A` |
| Acento | `#8250DF` |
| Éxito / Error / Aviso | `#1A7F37` / `#CF222E` / `#9A6700` |
| Tipografía | Inter o system-ui (texto) · JetBrains Mono (datos/código) |

**3 · Amable y espacioso** (estilo Notion/Airbnb) — redondeado, aireado, tonos suaves.
Para consumidores y onboarding fácil.
| Token | Valor |
|---|---|
| Fondo | `#FFFFFF` |
| Texto | `#37352F` |
| Primario | `#FF5A5F` |
| Secundario | `#FFB400` |
| Acento | `#0891B2` |
| Éxito / Error / Aviso | `#16A34A` / `#DC2626` / `#F59E0B` |
| Tipografía | Nunito (títulos) · Inter (texto) |

**4 · Editorial cálido** — serif, fondo crema, acento cálido. Para contenido y marcas
con voz.
| Token | Valor |
|---|---|
| Fondo | `#FBF7F0` |
| Texto | `#2B2420` |
| Primario | `#B45309` |
| Secundario | `#78716C` |
| Acento | `#9F1239` |
| Éxito / Error / Aviso | `#15803D` / `#B91C1C` / `#B45309` |
| Tipografía | Fraunces (títulos) · Source Sans (texto) |

**5 · Premium sobrio** — oscuro elegante, mucho espacio. Para marcas aspiracionales.
| Token | Valor |
|---|---|
| Fondo | `#0B0B0F` |
| Texto | `#F4F4F5` |
| Primario | `#C9A227` |
| Secundario | `#52525B` |
| Acento | `#7C3AED` |
| Éxito / Error / Aviso | `#22C55E` / `#F87171` / `#FBBF24` |
| Tipografía | Playfair Display (títulos) · Inter (texto) |

> Son puntos de partida (inspirados en la sensación de esas marcas, no una copia exacta
> de sus paletas reales). Elegida una dirección, la volcás en la Parte B y la ajustás
> con el usuario hasta que quede conforme.

## 4 · Cierre (la Parte B del onboarding)

- Completá la Parte B con **valores concretos** (si vino del plan B, ya tenés el punto
  de partida del paso 3; si no, definilos con lo relevado en el paso 2) y la tabla de
  **design tokens**.
- Completá también las **Reglas de componentes** de la Parte B, campo por campo: son
  las órdenes que cualquier agente lee en la fase 6 antes de construir interfaz.
- Accesibilidad no negociable: contraste suficiente, no depender solo del color.
- Mostrale el kit, iterá hasta que esté conforme, y recién ahí marcá **Estado: cerrado**
  y registralo en la fase 4 de la ficha.

## 5 · Aplicación al código (si ya hay código)

Volcá los tokens al tema del stack (ej. el tema de Tailwind) como fuente única, y
verificá con Playwright (capturas reales) que lo que se ve coincida con el kit. Si el
código llega después, esto se hace en la fase 6 tomando los tokens de este documento.

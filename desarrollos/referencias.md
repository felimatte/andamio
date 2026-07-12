# Referencias — datos de apoyo para el método

Tablas y números largos o que cambian seguido. Se separan acá para que la guía quede
corta. Los precios y versiones se confirman con la fuente oficial de cada herramienta
al momento de decidir.

## Stacks por defecto (punto de partida, no obligación)

Para la fase 2. Parto de acá, te lo explico y vos aprobás; se ajusta por proyecto.

| Tipo de proyecto | Stack por defecto |
|---|---|
| App web / SaaS | TypeScript + Next.js + Tailwind + Supabase (base+login+storage) + Vercel (deploy/CI) + Stripe (pagos) + Resend (mails) |
| App móvil | React Native + Expo (la mayoría) · Flutter si es muy visual/gráfica |
| Landing page | Carrd (simple/barata) · Unbounce (conversión + A/B) · MailerLite (PyME) · o dentro del mismo Next.js |
| Automatización / bot | n8n (flexible, autohospedable) · Make/Zapier (más fáciles, menos flexibles) |

## Aceleradores de IA (v0, Lovable, Bolt): para prototipar, no para publicar a ciegas

Herramientas que generan una app a partir de lenguaje natural. Para alguien que no
programa pueden acelerar muchísimo el **prototipo y el MVP**:
- **v0 (Vercel):** genera la interfaz (y apps livianas) en el ecosistema Next.js/Vercel.
- **Lovable:** arma apps full-stack (base de datos, login y pagos) y las publica de un clic.
- **Bolt:** prototipos muy rápidos que corren en el navegador.

**La regla de oro (lo que más importa):** lo que generan **no se publica sin pasar por la
puerta de revisión** del método. El código generado por IA trae riesgos de seguridad
documentados —por ejemplo, claves/API keys que quedan a la vista en el navegador, o que un
usuario pueda ver datos de otro cambiando un número en la URL—. Un análisis de 2025
(Veracode) encontró vulnerabilidades conocidas en cerca de la mitad de las muestras de
código generado por IA que probó.

Por eso encajan **dentro** del método, no en lugar de él: primero el plan (fases 0-5),
después el acelerador para construir rápido, y **siempre** el `revisor` + los chequeos
automáticos (seguridad, escaneo de claves filtradas y de dependencias) antes de publicar.
Los precios cambian seguido (casi todas tienen capa gratis para probar y planes pagos por
uso): conviene mirar la página oficial al momento de elegir.

## Presupuesto de performance (Core Web Vitals)

Metas a verificar antes de publicar (sobre todo en landings; pesan en SEO y conversión):
- **LCP** (aparece el contenido principal): ≤ 2,5 s.
- **INP** (responde al clic/toque): ≤ 200 ms.
- **CLS** (no "salta" al cargar): ≤ 0,1.

## Costos de referencia (stack web dominante, para estimar en fase 2)

Sirve para evitar sorpresas en la factura. Valores 2025-2026:
- **Supabase:** gratis para prototipar (<5.000 usuarios; el proyecto gratis se pausa
  tras 1 semana inactivo). Pro US$25/mes (mínimo productivo); ~US$35-75/mes chico;
  US$100-200/mes con 100K usuarios. Ojo ancho de banda: US$0,09/GB.
- **Vercel:** Hobby gratis (se pausa al llegar al límite); Pro US$20 por persona/mes;
  +US$40 por cada 100 GB tras 1 TB.
- **Mínimo realista en producción de un SaaS:** ~US$45/mes (Supabase $25 + Vercel $20),
  sin contar dominio, mails ni pagos.

## Variante "landing page"

Una landing no se planea como una app. Si el proyecto es una landing, además de las
fases, definí en la ficha:
- **Objetivo de conversión** (qué acción única buscamos: comprar, anotarse, agendar).
- **Mensaje principal arriba de todo** (above the fold) + **CTA** que resalte.
- **Prueba social** visible arriba (testimonios, logos, números).
- **Velocidad y SEO** (cumplir el presupuesto de performance; datos estructurados).
- **Plan de A/B testing** (probar un elemento por vez).

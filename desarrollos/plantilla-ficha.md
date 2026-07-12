# Ficha del proyecto — <nombre del desarrollo>
Estado: planeando | en construcción | terminado

> Esta es la ficha viva del proyecto. Se completa fase por fase (ver
> `guia-del-metodo.md`). No se escribe código hasta que las fases 0–5 estén
> cerradas y el `revisor` la apruebe. Lo que todavía no se sabe, se anota en
> "Decisiones abiertas", no se deja en blanco sin avisar.

---

## 0 · Idea y objetivo
- **Qué es (3-4 líneas):**
- **Para quién es:**
- **Qué problema resuelve:**
- **Cómo se ve el éxito (cómo sabremos que funcionó):**
- **Qué queda AFUERA (no entra en este desarrollo):**

## 1 · Qué hace (funcional)
- **Funciones principales — cada una con su criterio de aceptación:**
  - función → ¿cómo sabremos que está bien? (qué tiene que pasar para darla por buena):
- **Pantallas / secciones:**
  -
- **Recorrido principal del usuario (entra → hace esto → logra aquello):**
  -

## 2 · Con qué se hace (stack)
> Lo propongo yo y lo explico en simple; lo aprobás vos (parto de los stacks por defecto de `referencias.md`). Una línea de "por qué" por cada elección.
- **Lenguaje / framework:** — por qué:
- **Base de datos:** — por qué:
- **Hosting / dónde vive:** — por qué:
- **Servicios externos (login, pagos, mails, etc.):** — por qué:
- **Cómo se conectan entre sí (el mapa):**
- **Costo mensual estimado (para no llevarse sorpresas, ver `referencias.md`):**
- **Docs de referencia usadas (Context7 u otras):**

## 3 · Estructura y seguridad
- **Estructura de carpetas (mapa general):**
- **Qué datos se guardan (modelo de datos, en palabras simples):**
- **Checklist de seguridad desde el día cero:**
  - [ ] ¿Cómo entran los usuarios (login) y cómo se guardan las contraseñas?
  - [ ] ¿Dónde viven los secretos/claves (fuera del código)?
  - [ ] ¿Quién puede ver o tocar qué (permisos)?
  - [ ] ¿Hay copias de seguridad de los datos?
  - [ ] ¿Datos sensibles o personales? ¿Cómo se protegen?

## 4 · Kit de marca
> Se cierra con el onboarding completo: ver `onboarding-marca.md`.
- **Estado del kit de marca:** pendiente | cerrado
- **Resumen (paleta, tipografía, tono):**
- **Documento completo:** (enlace al onboarding de marca de este proyecto)

## 5 · Roadmap — plan de construcción por etapas testeables
> Cada etapa entrega algo que YA funciona y trae definido cómo se prueba (su test).
- **MVP (lo mínimo que ya sirve y se puede mostrar):**
- **Etapas, en orden — cada una con su prueba:**
  1. etapa → qué entrega (funciona de punta a punta) · cómo se prueba (test):
  2.
  3.
- **Construcción en paralelo (carriles/worktrees): sí / no** — se decide al arrancar la fase 6 (ver `construccion-del-codigo.md`).

## 7 · Lanzar y cuidar (se completa cerca del lanzamiento)
- **Ambientes:** pruebas (staging) y vivo (producción) separados; rama de producción protegida.
- [ ] Pruebas automáticas corriendo en cada cambio (CI/CD).
- [ ] Monitoreo y seguimiento de errores activos.
- [ ] Analítica elegida (por defecto, amigable con la privacidad).
- [ ] Legales: privacidad / términos / consentimiento de cookies si se guardan datos personales.
- [ ] Performance dentro de las metas (LCP ≤2,5s · INP ≤200ms · CLS ≤0,1).
- [ ] Check final de seguridad y accesibilidad (incluida prueba con lector de pantalla).
- [ ] README del producto al día (qué es, cómo se corre y se mantiene).

---

## Decisiones abiertas / a descubrir probando
- (cosas que sabemos que vamos a definir recién durante la construcción)

## Aprobación de la puerta (plan → código)
- [ ] Cada fase quedó cerrada (completa y sin huecos) antes de avanzar.
- [ ] Fases 0–5 completas (incluido el plan de construcción por etapas testeables).
- [ ] Revisado por el `revisor` y corregido lo que señaló.
- [ ] El usuario dio el OK para empezar a construir.

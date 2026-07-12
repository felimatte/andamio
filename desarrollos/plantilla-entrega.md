# Plantilla de entrega — instalación guiada por agente

Se usa solo cuando el producto se **entrega a otra persona** para que lo instale y lo
corra por su cuenta (un cliente, un socio, un miembro de una comunidad). Si el proyecto
es solo tuyo, no hace falta: alcanza con el README del producto.

**La idea:** el que recibe no sigue un manual técnico. Copia el proyecto, abre su
asistente de IA y le dice una sola frase:

> *"Leé `INSTALAR.md` e instalalo."*

Su agente hace el resto. Para eso, el `INSTALAR.md` se escribe **para el agente**, no
para el humano: con rol, límites duros y pasos con puntos de control.

## Principios (lo que hace que esto funcione)

- **Lo mecánico en scripts, lo delicado en el agente.** Todo paso repetible (crear la
  configuración, cargar la base, chequear el entorno) vive en un script que hace siempre
  lo mismo; el agente lo ejecuta, no lo improvisa. El agente solo maneja lo que requiere
  conversación: pedir claves, guiar logins, explicar errores.
- **Secretos, jamás por el chat.** Las claves van directo a su archivo (`.env` o
  similar); el agente indica dónde pegarlas, nunca pide que se las muestren.
- **Puntos de control duros.** Si un paso falla, el agente frena y explica en simple;
  no inventa soluciones ni sigue de largo.
- **Todo lo que lee la persona, en español.** Mensajes de los scripts y del agente en
  español simple; el código queda en inglés.
- **Permisos pre-aprobados, pero solo los justos.** Los comandos exactos que usa la
  instalación se dejan pre-aprobados en el `.claude/settings.json` del proyecto
  entregado (vale para Claude Code), así la instalación fluye sin pedir permiso a cada
  paso. Solo esos comandos puntuales — nunca permisos genéricos — y sin quitar la capa
  de seguridad que bloquea la lectura de secretos.
- **Termina con una prueba real.** El último paso siempre es usar el producto de verdad
  (ej.: mandar un mensaje real y ver que responda), no "los tests pasan".

## Estructura del `INSTALAR.md` (completar por producto)

---

# INSTALAR.md — <nombre del producto>

> **Para el agente (Claude Code u otro):** tu único trabajo acá es **instalar** este
> producto. Seguí los pasos en orden. Reglas duras:
> - **El código fuente no se toca.** Instalar no es programar: si algo del código
>   parece mal, avisá, no lo arregles.
> - **Nunca pidas ni muestres claves en el chat.** Indicá dónde pegarlas.
> - **Si un paso falla, frená**, explicá el error en simple y esperá indicación.
> - Todo lo que le digas a la persona, en español simple.

## Antes de empezar — qué necesita tener la persona

- [ ] Un asistente de IA que lea archivos y ejecute comandos (ej. Claude Code),
      instalado y andando.
- [ ] Cuentas: <servicio 1>, <servicio 2>…
- [ ] Herramientas instaladas: <Node, git, …>

## Pasos

1. **Chequear el entorno** — corré `<script doctor>`. Si falta algo, decí qué es y
   cómo instalarlo.
2. **Configuración** — corré `<script de configuración>`; pedile a la persona las
   claves de <servicio> y que las pegue en `<archivo>`.
3. <paso siguiente, uno por línea, cada uno con su script o su conversación>
4. …
5. **Prueba final real** — <la acción de punta a punta que demuestra que funciona,
   hecha de verdad>.

## Si algo sale mal

| Síntoma | Causa probable | Qué hacer |
|---|---|---|
| | | |

## Actualizar / desinstalar

- **Actualizar:** <cómo traer la última versión sin perder la configuración>.
- **Desinstalar:** <qué borrar y qué dar de baja>.

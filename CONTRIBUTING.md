# Cómo contribuir

Este archivo trae las convenciones comunes a los repos de Bitflow. Lo
específico de cada proyecto (stack, comandos, invariantes, glosario, ADRs) está
en su `AGENTS.md`, `CLAUDE.md` o `README.md`, y ante una diferencia manda el
del proyecto.

Cada cambio parte de un issue de Linear (equipo **BIT**), citado como
`BIT-nnn`. Quien no tiene acceso a Linear abre un issue de GitHub en el repo.

## Ramas

- Nombre: `<tipo>/bit-nnn-descripcion-corta`, en minúsculas. `<tipo>`:
  `feature`, `fix`, `hotfix`, `release`, `refactor`, `chore`, `docs`, `test`,
  `ci`. Una rama `release/` lleva la versión en vez del issue.
- Base: `develop`. `hotfix/` y `release/` van contra la rama default (`main`
  o `master`); un hotfix vuelve después a `develop`.
- Un cambio grande va en un stack: cada PR apunta a la rama del anterior.
- Para traer cambios de la base, haz **merge** de la base en tu rama y
  conserva su historia sin force-push: el revisor revisa en cada ronda solo
  lo que cambió desde el último commit que revisó, y si ese commit desaparece
  vuelve a revisar el PR completo.

## Commits

[Conventional Commits](https://www.conventionalcommits.org/es/), siempre en
español, con el issue al final:

```
fix(agendamiento): el calendario no da 500 sin distribuidores habilitados [BIT-1815]
```

- `tipo`: `feat`, `fix`, `perf`, `refactor`, `test`, `docs`, `chore`, `ci`.
- `ámbito`: el módulo de negocio (`ventas`, `agendamiento`, `facturacion`).
- La descripción cuenta el comportamiento que cambia, en presente.
- Los PRs se mergean con merge commit, así que cada commit llega a la rama
  default y cada `feat`, `fix` y `perf` se vuelve una línea del changelog.
  Escríbelos para quien lee las novedades.
- Un `fix` corrige algo que se nota en la versión publicada. Lo que corriges
  dentro del mismo PR (por ejemplo, un hallazgo del revisor) va como
  `refactor`, `test` o `docs`, y así no aparece en el changelog.

## Pull requests

- **Título**: la misma forma que un commit, terminado en `[BIT-nnn]`. Linear
  enlaza el PR con el issue por ese código. Si el issue es de GitHub, el
  título va sin código y la descripción dice `Closes #nnn`.
- **Descripción**: las secciones de
  [la plantilla](pull_request_template.md). Con `gh pr create --body` la
  plantilla no se carga sola: copia sus secciones.
- **Tamaño**: un PR por issue. Si pasa de unas 500 líneas sin contar tests,
  divídelo en un stack y numera los títulos con `(n/m)`.
- **Al abrir**: listo para revisar (no draft) y con el label `ci-review`:
  `gh pr create --base develop --label ci-review`.

## Revisor automático

Cada repo tiene un caller `.github/workflows/pr-reviewer-claude.yml` que
invoca el revisor de `bitflowcl/github-actions`. Comenta en español, en línea y
con un resumen; no aprueba ni bloquea.

| Evento | Revisa |
|---|---|
| PR abierto, reabierto o listo para revisar | siempre |
| Push nuevo al PR | solo con el label `ci-review` |
| PR en draft o con el label `skip-review` | nunca |
| Comentario con `@claude` | responde ahí |

Severidades: 🔴 crítica, 🟠 alta, 🟡 media. Desde la segunda ronda revisa
solo el diff nuevo; desde la tercera, solo reporta 🔴.

### Otra ronda

- **Corregiste un 🔴 o 🟠**: el push con `ci-review` dispara la ronda. Si el
  PR no tenía el label, agrégalo antes de pushear.
- **Quieres confirmar que tus arreglos cerraron los hilos**: comenta
  `@claude verifica que los hallazgos anteriores quedaron resueltos`. Es más
  barato y no abre una ronda.
- **Un 🟡 o una sugerencia no aplica**: responde en el hilo con el motivo. El
  revisor no lo vuelve a plantear.

## Merge

Mergea una persona, después de su propia revisión final: la decisión es suya.
Pídesela con los hallazgos del revisor corregidos o respondidos en su hilo y
el CI en verde.

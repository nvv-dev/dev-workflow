# dev-workflow

Skills de ingeniería para agentes de código: cómo probar, depurar, revisar, especificar y cerrar una tarea sin adivinar. Funcionan como plugin de Claude Code y también como carpetas sueltas que puedes leer, copiar o adaptar a cualquier agente compatible con el formato [Agent Skills](https://agentskills.io) (`SKILL.md`).

*English version below.*

## Skills

| Skill | Para qué sirve | Se activa |
|---|---|---|
| [test-driven-development](skills/test-driven-development/SKILL.md) | Ciclo rojo-verde-refactor probando por la frontera pública del módulo | Sola, al implementar o corregir |
| [systematic-debugging](skills/systematic-debugging/SKILL.md) | Causa raíz antes de corregir; se detiene tras tres intentos fallidos | Sola, ante un error o prueba que falla |
| [verification-before-completion](skills/verification-before-completion/SKILL.md) | Evidencia fresca antes de decir "listo", y lista honesta de lo que se debilitó | Sola, antes de cerrar |
| [code-review-deep](skills/code-review-deep/SKILL.md) | Revisión de errores, cambios que rompen, seguridad y funciones a medio activar, con veredicto por hallazgo | Al pedir una revisión |
| [code-review-maintainability](skills/code-review-maintainability/SKILL.md) | Revisión de forma: complejidad, tamaño, límites; pocos comentarios de alta convicción | Al pedir una revisión |
| [grill-the-plan](skills/grill-the-plan/SKILL.md) | Interroga un plan decisión por decisión y actualiza glosario y ADR | Solo a mano |
| [ears-acceptance-criteria](skills/ears-acceptance-criteria/SKILL.md) | Criterios de aceptación en formato EARS y un comando de verificación por tarea | Sola, al escribir specs |
| [writing-adrs](skills/writing-adrs/SKILL.md) | ADR cortos para decisiones costosas de revertir | Sola, ante decisiones de arquitectura |
| [devils-advocate](skills/devils-advocate/SKILL.md) | Ataca una idea desde ocho ángulos y entrega veredicto y lista de arreglos | Solo a mano |
| [issue-triage](skills/issue-triage/SKILL.md) | Estados para el backlog y briefs listos para que un agente los tome | Sola, al ordenar issues |
| [git-worktrees](skills/git-worktrees/SKILL.md) | Trabajo en paralelo sin pisarse, con limpieza segura | Sola, al trabajar en paralelo |
| [finishing-a-branch](skills/finishing-a-branch/SKILL.md) | Chequeos finales, commits y descripción de PR; nunca hace merge | Sola, al terminar una rama |
| [pre-deploy-audit](skills/pre-deploy-audit/SKILL.md) | Bloqueantes antes de un release y plan de despliegue con rollback | Sola, antes de desplegar |
| [threat-modeling](skills/threat-modeling/SKILL.md) | Modelo de amenazas por dominio antes de implementar | Sola, en planes con datos sensibles |
| [architecture-review](skills/architecture-review/SKILL.md) | Candidatos de refactorización donde más cambia el código | Solo a mano |
| [anti-generic-design-review](skills/anti-generic-design-review/SKILL.md) | Detecta los rasgos de diseño "hecho por IA" en capturas a 390, 768 y 1440 px y reemplaza cada uno por una decisión propia | Sola, antes de entregar un diseño y en PR de interfaz |

"Solo a mano" significa que la skill tiene `disable-model-invocation: true`: no se carga sola y la invocas tú (por ejemplo `/dev-workflow:devils-advocate`). Así no ocupa contexto en cada sesión.

## Instalación

**Como plugin de Claude Code** (recomendado):

```text
/plugin marketplace add nvv-dev/claude-plugins
/plugin install dev-workflow@nvvdev
```

**Como skills sueltas** (otros agentes o para adaptarlas): copia la carpeta de la skill que quieras dentro de la carpeta de skills de tu agente, por ejemplo `.claude/skills/` en tu repo. Cada carpeta es independiente.

## Cómo están escritas

- Las instrucciones están en inglés para que los escáneres de seguridad de skills (como SkillSpector) las analicen por completo. El agente responde en el idioma de quien la usa.
- Objetivos y restricciones, no recetas rígidas. Cada skill termina con una sección **Known failures** para registrar los errores reales de los agentes: es lo que más mejora una skill con el tiempo.
- Ninguna skill ejecuta acciones irreversibles por su cuenta (merge, push a main, deploy, borrados).

## Origen

Son skills propias, escritas desde cero a partir de lo que aprendimos evaluando herramientas de la comunidad. Ver [CREDITS.md](CREDITS.md).

## Contribuir

Abre un issue o PR. Si una skill falló en un caso real, la mejor contribución es una entrada en su sección **Known failures** con el caso y la regla que lo evita. El CI valida el formato de cada `SKILL.md` y lo pasa por SkillSpector.

## Licencia

MIT.

---

## English

Engineering skills for coding agents: how to test, debug, review, specify and finish a task without guessing. They work as a Claude Code plugin and as standalone folders you can read, copy or adapt to any agent that supports the [Agent Skills](https://agentskills.io) `SKILL.md` format.

**Install as a Claude Code plugin:**

```text
/plugin marketplace add nvv-dev/claude-plugins
/plugin install dev-workflow@nvvdev
```

**Or copy a single skill folder** into your agent's skills directory (for example `.claude/skills/`).

Skills marked "solo a mano" in the table above use `disable-model-invocation: true` and load only when you invoke them. Every skill ends with a **Known failures** section; contributions that add real failure cases and the rule that prevents them are the most welcome. See [CREDITS.md](CREDITS.md) for the projects that inspired these skills. License: MIT.

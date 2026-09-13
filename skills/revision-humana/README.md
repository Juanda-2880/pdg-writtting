# Human Review Module (`revision-humana`)

A correction pass over one specific part of the thesis where **the only feedback applied is
the one a person writes in the chat**. The AI finds the apartado, shows its real text,
applies the person's items, verifies the build and the project rules, and logs everything in
[`../../thesis/REVISIONES.md`](../../thesis/REVISIONES.md). It may propose suggestions, but each
one is applied only if the person approves it by id.

## Usage

```text
/revision-humana <apartado> [feedback]
```

| You write | What happens |
| :--- | :--- |
| `/revision-humana obj:gobernanza el verbo "Implementar" está bien pero sobra "de infraestructura"` | Shows objective 2, applies your item, reports the before/after, then offers suggestions |
| `/revision-humana "Justificación"` | Shows the section paragraph by paragraph with suggestions, and waits for your feedback |
| `/revision-humana cap05` | Sweep: one section at a time, your feedback on each, *«siguiente»* to move on |
| `aplica S2` | Applies suggestion 2. A plain *«ok»* approves nothing |
| `/revision-humana cap05 --continuar` | Resumes a sweep where the log says it stopped |

The skill has `disable-model-invocation: true`, so an agent can't start it on its own. Only a
person typing the command does.

## Files

| File | Description |
| :--- | :--- |
| [`SKILL.md`](./SKILL.md) | The procedure: hard rules, apartado resolution, feedback items, suggestions, verification, sweep mode and log format. |

## Installation (Claude Code)

The skill has to sit in a `skills/` folder Claude Code reads. From the folder where you start
your sessions, link it instead of copying it, so the repository stays the single source:

```bash
mkdir -p .claude/skills
ln -s /home/melo/8thSem/pdg/pdg-writtting/skills/revision-humana .claude/skills/revision-humana
```

Start a new session afterwards if `/revision-humana` doesn't show up.

## Relationship with other modules

- It does not replace the **Revisor** (`../../agent-roles/Revisor.md`). The Revisor checks the
  document against the rules. This skill applies a person's judgment on substance.
- It applies the same rule files every other writing task uses: `../writting-tools/`,
  `../objectives-writting/objectives-project-rules.md`, `../reference-writting/recency.md`.
- A meeting record is never human feedback for this skill (CLAUDE.md rule 9). If you want the
  tutor's words applied, write them yourself in the chat.

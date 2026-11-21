# Expert Roundtable

**Stop typing "find the best people in the world for this, work out how they think, then
have them work on it" every time.** One skill runs the whole routine — with real experts
and cited sources, not made-up personas.

[中文说明](README.zh-CN.md)

```text
> /expert-roundtable should we rebuild our sync engine on CRDTs?
```

Or just say it in plain words: *"get the best people in the world on this."*

## What happens

1. **Roster** — picks 3–5 people who are proven best at what your task needs, including a
   built-in skeptic. If you have consulted this domain before, it reuses that roster.
2. **Dossiers** — who they are, how they think, how they work, their iron rules, the
   questions they would ask, their blind spots. Every line is tied to a public source.
3. **Three rounds** — independent takes → cross-examination → synthesis.
4. **One deliverable** — the spec, plan or decision first; then an iron-rule checklist,
   the decisions left to you, and what evidence would change the panel's mind.

| Mode | Use it for |
|---|---|
| **Roundtable** (default) | designing a feature, reviewing a plan or PR, making a call |
| **Fuse** | blending the panel into one codenamed persona — saved as a Claude Code subagent you can call from every project |
| **Historical guest** | an unexpected angle: "how would a figure from history see my problem?" (clearly labelled as interpretation) |

Depth adapts: **quick** (3 experts, reused roster), **standard**, or **deep** (5 experts,
each running as an independent subagent).

## Why this one

There are plenty of council and panel prompts. This one is built around four choices:

- **Real people, cited.** Not invented "master-level" archetypes. A claim without a source
  never becomes a rule.
- **Iron rules become checks.** Each expert's non-negotiables are checked against the
  deliverable, pass or fail.
- **Research once, reuse everywhere.** Dossiers are saved to `~/.claude/experts/`, so the
  second project that needs a security reviewer costs nothing.
- **Guardrails built in.** No first-person impersonation of living people, no invented
  quotes, outputs labelled as interpretation, and the human decides anything irreversible.

Triggers work in English and Chinese.

## Install

**Claude Code (plugin)**

```text
/plugin marketplace add JohnSUNLei/expert-roundtable
/plugin install expert-roundtable@expert-roundtable
```

**Any agent that reads `SKILL.md`** (via the [skills CLI](https://skills.sh))

```bash
npx skills add JohnSUNLei/expert-roundtable
```

**By hand** — copy `skills/expert-roundtable/` into `~/.claude/skills/` (every project) or
`.claude/skills/` (one project). For the Claude apps, zip that folder and upload it as a
custom skill in settings.

## Layout

```text
skills/expert-roundtable/
├── SKILL.md                    the routine (loads only when triggered)
└── references/
    ├── dossier.md              dossier template + roster library format
    ├── software-bench.md       seats for software work, deliverable shape, PR review
    └── fusion.md               fusion table, persona/subagent template, tests
```

## Where it comes from

The method is lesson 3 of the Chinese-language [量身 AI course](https://ailiangshen.com/course)
("百家融合法": find the 3–5 recognised best, write a card per layer, fuse them into a new
persona, test and refine), extended with the cited expert-panel format we use for client
work.

## A note on real people

Everything the panel says is an interpretation of the named people's **public** work — not
their words, and not their endorsement. Keep that line on anything you share.

## Also by the same author

[**hands-off**](https://github.com/JohnSUNLei/hands-off) — six tiny guards that make it safe to let AI coding agents act for you: rules that bite, a send fuse, a prompt-injection tripwire, a flight recorder with undo, a spending brake, local-first routing.

## License

MIT

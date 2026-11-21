# Dossier template and roster library

## Library layout

| Path | Scope |
|---|---|
| `.claude/experts/<domain-slug>.md` | one project (wins over the personal library) |
| `~/.claude/experts/<domain-slug>.md` | personal library, every project |

One file per domain, several people per file. Name the domain by the work, not the
person: `software-architecture.md`, `pricing-strategy.md`, `exam-coaching.md`.

## File format

```markdown
---
domain: software-architecture
checked: 2026-11-21          # date the sources were last verified
verified: yes                # or: no (model memory)
---

## <Full name>

- **Angle on the panel:** the seat they fill (e.g. design & simplicity).
- **Who:** one line — what they did that shows they are the best at this. Not a résumé.
- **How they think (inferred):** what they look at first; how they trade off; how they decide. [1][2]
- **Working principles:** 3–5 bullets on how they actually work, each with a source tag.
- **Iron rules (our distillation):** 3 non-negotiables, phrased as checks a deliverable
  can pass or fail.
- **Questions they would ask:** 3, general enough to reuse across tasks in this domain.
- **Blind spots:** what this lens tends to miss — the reason others sit on the panel.
- **Sources:** [1] Title (year) — link. [2] …
```

## Writing rules

- Every bullet traces to a source tag. Untraceable → mark `unverified` and keep it out of
  the iron rules.
- Describe their approach in your own words; quote only verbatim text you can source.
- "How they think" is inference from their work — label it as such.
- Iron rules are *our* distillation, stated as constraints on the deliverable, never
  presented as their quotes.
- Refresh a file when `checked` is older than 12 months, sooner in fast-moving fields
  (AI, growth, security).
- Public material only. Nothing about private life, health, family or rumours.

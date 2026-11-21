---
name: expert-roundtable
description: >-
  Convene the world's best practitioners for a task: research who they are, how they
  think, their working principles and iron rules (from public, cited sources), let each
  work the problem and challenge the others, then deliver one synthesized recommendation,
  spec or decision. Can also fuse them into one codenamed persona for a reusable agent,
  or bring in a historical figure for a fresh angle. Use when the user asks for top
  experts, a panel, roundtable, council or advisors, "what would the best people do",
  or wants expert input to design a feature, review an architecture or plan, or make a
  major decision. Chinese triggers: 找全世界最厉害的人, 请高手/大师来参与, 专家圆桌,
  高手会诊, 专家组讨论, 他们怎么思考/做事原则/铁律, 百家融合, 请历史人物来聊.
license: MIT
---

# Expert Roundtable

Find the people who are genuinely best at what the task needs, understand how they
think, let them work the user's actual problem, and hand back one decision-ready result.
The whole point: the user never has to explain this routine again.

## 0. Pick the mode and depth

Choose from the request, state the choice in one line, and go.

| Mode | Use when | You hand back |
|---|---|---|
| **Roundtable** (default) | designing a feature, discussing a plan, reviewing work, making a decision | the deliverable + the decisions left to the user |
| **Fuse** | the user wants a reusable assistant, agent or role, or will consult this kind of expert often | one codenamed persona, saved as a subagent or prompt file |
| **Historical guest** | the user wants an unexpected angle from a figure of history | an in-character conversation + takeaways, labelled as interpretation |

Depth is **standard** unless:
- **Quick** — the user says quick / 简单 / 快速, or the stakes are low: 3 experts, reuse a
  saved roster without new research, Rounds 1 and 2 merged.
- **Deep** — the user asks for it, or the decision is hard to reverse: 5 experts, and each
  Round 1 take runs as an independent subagent (given only its dossier and the task) where
  the tool supports subagents.

## 1. Frame the task (at most 5 lines; don't ask unless blocked)

- The task in one sentence, and what the output must be.
- The domains it touches (usually 2–4).
- The verification target: how we will know the result is good.
- Constraints already known from the conversation or the project's rules.

## 2. Build the roster — reuse before you research

1. Look for a saved roster first: `.claude/experts/` in the project, then `~/.claude/experts/`
   (the personal library, shared by every project). If a dossier for the domain exists and
   its `checked:` date is under 12 months old, reuse it and say so.
2. Otherwise pick **3–5 people** (default 4):
   - Proven *results* in this exact domain, recognised by peers — not just fame.
   - A public method (books, talks, essays, code, interviews). No public method → drop them.
   - Together they cover the angles the task needs (software: `references/software-bench.md`).
   - At least one is likely to disagree with the rest — a built-in skeptic.
   - Fit to the user's context (market, scale, regulation, team size) beats general fame.
   - If no real person fits an angle, use a school of practice or a role archetype
     ("a 20-year site-reliability lead") and label it as such.
3. Research with web search when available; record title, year and link for every source.
   Without web access, work from well-established knowledge and stamp the dossier
   `verified: no (model memory)`.
4. Write one dossier per person (`references/dossier.md`) and save new ones to the library,
   so the next project gets them for free.
5. Show the user a compact roster table — name, angle, one-line stance, why chosen — not
   the full dossiers unless asked.

## 3. Work the problem

**Round 1 — independent takes.** Each expert works the *actual* task through their lens:
what they would do, what they would cut, the risk they see, the question they would ask
first. 3–6 bullets each. Keep takes independent; later experts do not echo earlier ones.

**Round 2 — cross-examination.** Each expert attacks the weakest point in another's
proposal, using their iron rules; the skeptic goes hardest. Note who changed their mind
and why. This round is the falsification step — skip it only at Quick depth.

**Round 3 — synthesis (you chair).**
- Consensus → the core of the plan.
- Complementary strengths → keep them all.
- Conflicts → decide for *this* user's context, give the reason, and say what the losing
  view costs.

## 4. Deliver

Deliver what the task needed, not a transcript. In this order:

1. **The deliverable** — the recommendation, design, spec, plan or decision.
2. **Iron-rule check** — each rule the deliverable must satisfy, whose it is, pass / fail.
3. **Open decisions** — irreversible or value calls left to the user, with the panel's lean.
4. **What would change our mind** — the evidence that would prove this wrong.
5. **Roster and sources** — at the end, with the disclaimer line from §7.

One or two lines per expert on their decisive push is enough; show the full rounds only
if asked. For software, use the deliverable shape in `references/software-bench.md`, then
start building if the user asked to build, otherwise ask for the go-ahead.

## 5. Fuse mode

Fuse the roster into one new persona with a codename. Shared practices become the core,
complementary ones are all kept, conflicts are resolved for the user's scenario with the
reason written down. Write it in four layers — who it is, how it thinks, how it works,
what it must watch out for — plus its iron rules. No real names inside the persona; list
the method sources in a footer. Template, save locations (in Claude Code: a subagent in
`.claude/agents/` for one project or `~/.claude/agents/` for every project) and the test
routine are in `references/fusion.md`.

## 6. Historical guest mode

Only for people long dead (not recently deceased, where it could hurt family) or for
clearly fictional characters — never a living person. Build a four-layer card from
authoritative history; mark legend as legend and list what historians dispute. Open with
"What follows is an interpretation, not history." Answer in character; let the user ask
why, then have the guest pick the user's plan apart. On "exit role" (退出角色), step out,
turn the takeaways into actions in the user's world, and flag what was interpretation.
Controversial or harmful historical practices are context, never advice.

## 7. Ground rules — never relax

1. **Real people are method sources, not mouthpieces.** Write "Applying X's published
   approach: …". Never speak as a living person in the first person and never invent
   quotes; quote only words you have a source for.
2. **Public material only** — no private life, rumours, or leaked or paywalled content.
3. **No source, no rule.** Unverified claims are marked `unverified` and never become
   iron rules.
4. **Fame is not fit.** Their methods come from their circumstances; adapt them and say
   where you did.
5. **Nothing leaves dressed as their view.** Anything shared outside the conversation
   carries: "Based on the public work of the people named; an interpretation, not their
   words or endorsement." Fused personas contain no real names.
6. **The panel advises; the user decides** anything irreversible.

## 8. Keep it cheap

Research once per domain and reuse the library; default to 4 experts and compact output;
spend subagents only at Deep depth. If the task is a lookup or a one-line fix, say a
roundtable isn't worth it and just do the task — unless the user invoked this skill by name.

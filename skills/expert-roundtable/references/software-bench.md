# Software development bench

## Seats

Pick the 3–5 seats the task actually touches. A seat is an angle, not a fixed person.
The candidates below are a starting point from widely known public work — verify the
sources and choose by fit to the task; they are not an endorsement list.

| Seat | The question it guards | Starting candidates |
|---|---|---|
| Product & discovery | Is this the right problem? What is the smallest thing that tests it? | Marty Cagan (*Inspired*, 2nd ed. 2017); Teresa Torres (*Continuous Discovery Habits*, 2021); Ryan Singer (*Shape Up*, 2019) |
| Interaction & UX | Can a first-time user succeed without help? | Don Norman (*The Design of Everyday Things*, rev. 2013); Steve Krug (*Don't Make Me Think, Revisited*, 2014) |
| Design & simplicity | Is complexity hidden behind simple interfaces? | John Ousterhout (*A Philosophy of Software Design*, 2018); Rich Hickey ("Simple Made Easy", 2011) |
| Implementation craft | What is the smallest safe step? Where is the test? | Kent Beck (*Test-Driven Development: By Example*, 2002; *Tidy First?*, 2023); Martin Fowler (*Refactoring*, 2nd ed. 2018) |
| Skepticism & testing | How could this be wrong, and what check would show it? | Richard Feynman ("Cargo Cult Science", 1974); James Bach & Michael Bolton (Rapid Software Testing) |
| Security | What does an attacker do with this? | Adam Shostack (*Threat Modeling: Designing for Security*, 2014) |
| Reliability & operations | What happens at 3 a.m.? How do we roll back? | Beyer et al. (*Site Reliability Engineering*, 2016); Charity Majors et al. (*Observability Engineering*, 2022) |
| Delivery | Does this make us ship faster and safer? | Nicole Forsgren, Jez Humble & Gene Kim (*Accelerate*, 2018) |
| LLM features & agents | Is the model doing what a plain program should? Can we evaluate it? | Anthropic ("Building effective agents", 2024); Simon Willison (simonwillison.net) |

Typical panels:
- **New feature:** product, UX, design & simplicity, skepticism.
- **Architecture or refactor:** design & simplicity, implementation craft, reliability, skepticism.
- **Anything touching money, auth or user data:** add security, always.

## Deliverable shape for software work

1. **Problem and verification target** — what we are trying to prove, and how we will know.
2. **Scope** — in, and deliberately out.
3. **Design** — interfaces first, then internals; the simplest version that meets the target.
4. **Acceptance criteria** — testable statements; each one maps to a test or a check.
5. **Risks and rollback.**
6. **Build order** — smallest safe steps, each one shippable or revertible.
7. **Open decisions** for the user.

## Reviewing existing code or a PR

Each seat reviews the diff through its question. Every finding cites `file:line` and a
concrete failure scenario; drop findings that can't. The chair merges duplicates and
ranks by severity. The panel never approves its own work: if it wrote the code, say so
and ask for an independent check.

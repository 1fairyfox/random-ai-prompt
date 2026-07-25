# Plan Before Execute

**Plan non-trivial work in detail before executing it.** Write the plan down first — structured and
organized — then execute against it. This is for **execution reliability, not paperwork**: a
well-thought-out plan catches contradictions and missing pieces up front, keeps a long multi-file
change coherent, and gives a clear thing to execute against. It primarily benefits the *executor*
(human or AI), not the owner.

Canonical, project-agnostic source: `assets/references/fairyfox.io/hub/standards/planning.md`. It is a
default way of working, wired into the **Default Workflow** in [`../../CLAUDE.md`](../../CLAUDE.md).

## What a plan is

For non-trivial work, before making changes, write a short structured plan:

- **Decisions** — what's being done and the choices made (open questions surfaced, not guessed — see
  [`working-agreements.md`](working-agreements.md) §A2/§A5).
- **Work breakdown** — by file or area, concrete enough to execute step by step. In this project the
  live task list (TaskCreate/TaskUpdate) carries the in-flight breakdown; a durable plan for a
  release-worthy feature lives in [`../plans/`](../plans/next-steps.md).
- **Open items** — anything to confirm before or during execution.
- **Release shape** — branch, SemVer level, how it ships (per [`git-workflow.md`](git-workflow.md) and
  [`versioning.md`](versioning.md)).

Keep durable plans in `notes/plans/` so they live with the project's other notes.

## Phase by default (hub 1.4.0)

Non-trivial work is decomposed into **as many phases as it needs**, across three levels: **research**
(primary sources, local + online — not skipped or rushed), **planning** (as often as needed, primarily
for the executor), and **implementation** (coherent, shippable phases). "Do as much as you can" does
**not** re-anchor "done" to a shippable milestone — a green release mid-effort never implies the work
is finished (see [`mandate-ledger.md`](mandate-ledger.md) "rows remaining: N"). Under-phasing a large
ask is the failure this closes; a mixed adoption (headless-verifiable + browser-gated) is phased and
the deferred slice is named as a tracked `gap`, not held or dropped.

## What's exempt

Trivial, single-step changes (a typo, a one-line fix, an obvious rename) don't need a written plan —
planning overhead shouldn't exceed the work. The bar is "non-trivial": multiple files, multiple steps,
a real decision, or anything you'd otherwise improvise through. Applied with judgment, not as paperwork.

## Verify (is it being followed?)

- Substantive work (a multi-file change, a release-worthy feature, a standards pass) has a **written
  plan that predates execution** — a `notes/plans/` file, or an in-thread/task-list plan agreed before
  edits began.
- The Default Workflow in [`../../CLAUDE.md`](../../CLAUDE.md) states plan-before-execute.
- Trivial one-step changes are not gratuitously bureaucratized.

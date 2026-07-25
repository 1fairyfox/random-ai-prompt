# Checklists are contracts (adopted standard)

RAP's adoption note for the hub standard **`checklists-are-contracts`**. The canonical,
project-agnostic version lives in the read-only hub clone at
`assets/references/fairyfox.io/hub/standards/checklists-are-contracts.md` — re-read it there for
the authoritative wording. This page records what the rule is and how RAP already lives it.

## The rule in plain English

A checklist — a standard's `## Verify` table, a runbook's steps, a docs-site module, or an
**owner's multi-part request** — is a **contract, not a summary**. Every item is owed an
individually-recorded outcome **before** any "done" is claimed. The four rules:

1. **Enumerate every item mechanically, not by judgement.** A touched standard expands to its
   *full* Verify table — never summarized at table level, never "the important ones". The compiler
   of the list does not get to choose which items are worth expanding; that choice is exactly how
   items disappear.
2. **Record each outcome individually before the done-mark exists** — `pass · fixed · N-A (reason)
   · gap (with a due marker)`. A bare `✅` summarizing a multi-item set is **banned wording**;
   replace it with a link to the itemized record (the [adoption manifest](adoption-manifest.md), an
   audit file, the Verify results).
3. **Read optional items ambitiously — descope only out loud.** "Include the ones that exist" /
   "where possible" defaults to the ambitious reading: build the thing. Descoping is allowed only
   *explicitly* and only by the owner; silent omission is a `gap`, never a pass.
4. **Deferral requires falsification, not a plausible reason.** A blocked item carries evidence of
   a real attempt (the command run, the error text, the version checked) **and** a retest trigger.
   Probe first — a bounded probe precedes any "untestable"/"deferred" verdict.

Every pass ends with an explicit **"NOT done / read leniently / needs the owner's eyes"** section —
the reviewer never has to extract it by challenge. And when a session log records a reusable lesson,
the **same commit** adds the behavioural rule to `CLAUDE.md` or the relevant note (a lesson left as
prose is a lesson that will be re-learned).

## How RAP already lives it

- **The enforcing artifact now exists:** [`adoption-manifest.md`](adoption-manifest.md) — no
  `Standards adopted ✅` summary without a backing per-standard row. This is the concrete thing the
  standard is built around, seeded 2026-07-25.
- **The Default Workflow already itemizes** — the lint→smoke→commit→verify loop and the
  `check:docs`/`check:tidy`/`check:committed` gates ([`repo-hygiene.md`](repo-hygiene.md)) are a
  standing checklist run per change, not a summary claim. `check:committed` exists precisely because
  "green locally" was once claimed while the fix sat uncommitted (see [`fix-patterns.md`](fix-patterns.md)).
- **Process reports already end with a "what went wrong / friction" and honest not-done disclosure**
  ([`process-reports.md`](process-reports.md)).
- **The owner-directive case** is spelled out in its own note,
  [`mandate-ledger.md`](mandate-ledger.md).

## Verify

Run the standard's `## Verify` table (in the hub clone) and record the result in
[`adoption-manifest.md`](adoption-manifest.md). Passing means: no unbacked `✅`/"adopted"/"all done"
over a list; per-item outcomes recorded; deferred items carry an attempt log + retest trigger; each
pass ends with a disclosed not-done list; a recorded lesson added its rule in the same commit.

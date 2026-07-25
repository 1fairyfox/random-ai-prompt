# Owner mandates become ledgers (adopted standard)

RAP's adoption note for the hub standard **`mandate-ledger`** — the owner-directive case of
[`checklists-are-contracts`](checklists-are-contracts.md), spelled out. Canonical version in the
read-only hub clone at `assets/references/fairyfox.io/hub/standards/mandate-ledger.md`.

## The rule in plain English

An owner's **multi-part directive is a checklist**, and it binds exactly as a standard's `## Verify`
table does. The failure it prevents: a directive is lossy-compressed at intake ("every command from
the different permissions, used correctly and incorrectly, verified individually" → a task named
"permission matrix tests" that keeps three), the summary task gets checked off, and the
un-transcribed words are unrecoverable because nothing re-reads the original message. **A request
that doesn't become an entry becomes optional.**

The rule: a multi-part owner directive is transcribed **verbatim** into
`notes/plans/<date>-mandate.md` (template: the hub clone's `hub/templates/mandate-ledger.md`)
**before** execution — one row per clause:

| Owner's words (verbatim) | Interpretation | Status | Evidence |
|--------------------------|----------------|--------|----------|

- **Status** is `done` · `blocked-with-evidence` · `awaiting-owner`. A completion claim **cites the
  rows**, not a paraphrase; the phase-end check diffs the delivered work against **the owner's
  original words**, not against the plan file.
- **Deferral requires falsification** — a `blocked-with-evidence` row demands a recorded attempt
  (command, error, version) **and** a retest trigger, never a plausible reason alone.
- **Disclosure is stateful.** An `awaiting-owner` row survives into the next session; the **first
  action** under the same owner next session is to re-present the open rows for a keep/descope
  decision. A repeated mandate escalates every `awaiting-owner` row to do-now, and a second
  repetition of the same item is itself a reportable process failure.
- **No milestone-anchoring under an open mandate.** A release may ship mid-mandate, but the
  completion claim states **"mandate rows remaining: N"** — a green release never implies the
  mandate is done.

## How RAP already lives it (and where it applies)

RAP takes multi-step owner directions regularly (the notes-first rule, the phased 2026-07-19 six-
standard adoption "adopt all, phased to do it well"). The gap this closes is that a **spoken**
mandate previously fell through the `checklists-are-contracts` machinery, which only bound
*standards'* checklists. From now on a genuinely multi-part owner directive gets a
`notes/plans/<date>-mandate.md` ledger before execution. A single-clause request doesn't need one —
this is for the multi-part case, so nothing load-bearing is compressed away.

## Verify

Record the result in [`adoption-manifest.md`](adoption-manifest.md). Passing means: a multi-part
directive has a verbatim one-row-per-clause ledger; completion claims cite rows and diff against the
owner's words; blocked rows carry attempt + retest; open `awaiting-owner` rows are re-presented
first next session; no completion/release claim implied done-ness without a "rows remaining: N"
count under an open mandate.

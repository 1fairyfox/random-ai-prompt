---
date: 2026-07-25
procedure: adopting-updates
node: random-ai-prompt
outcome: completed
hub_version: 1.6.1
hub_commit: 2d614f0
---

# Process Report — adopting-updates, 2026-07-25

> A full, honest account of running a fairyfox system procedure. The point is to improve the
> system — so say what was rough even if the run succeeded. Standard:
> `hub/standards/process-reports.md`.

## Outcome in one line

Adopted the **0.20.2 → 1.6.1** hub span (releases 0.21.0, 1.4.0, 1.5.0, 1.6.0) into this node: seeded
the **first `adoption-manifest.md`** (the 0.21.0 linchpin), authored **four new-standard notes**
(`checklists-are-contracts`, `mandate-ledger`, `docker`, `readme`), folded the material changes into
`planning`/`engineering-quality`/`git-workflow`/`coins`/`compliance`, wired the behavioural rules into
`CLAUDE.md`, and made the **README** cross-link compliant (worded docs link + "Get it" section + mesh
footer). Browser-gated docs-site visual work (chrome 2.2.1 → 2.3.0 + the 1.4.0 subnav/Notes/coins-
presence requirements) is deferred as a **named tracked `gap`**. Notes/docs + README only — no
`VERSION` bump.

## What was done

1. **Check first.** Refreshed the read-only git-ignored mirror. Hub `dev` had been **force-pushed**
   (`697bc5c…2d614f0`, and renumbered from the old 0.20.x scheme to **1.6.1**), so `--ff-only`
   aborted; recovered per the runbook with `git fetch` + `git reset --hard origin/dev` **on the mirror
   only** — project history untouched. Read `authorizations.yml`: the standing
   `adopt-standards-by-default` grant covers all of `hub/standards/` + `hub/templates/`, so applied
   directly (skipped only the report-then-wait pause). The user also expressly authorized full
   application ("in full … as many phases as needed").
2. **Scoped the delta** from `hub/standards/CHANGELOG.md` across the version span (anchor = last
   adopted `hub_version` 0.20.2 from the 2026-07-19 report → current 1.6.1). Read the new/changed
   standards in full (`checklists-are-contracts`, `mandate-ledger`, `docker`, `readme`, `badges`) plus
   the `adoption-manifest` + `README-links` templates.
3. **Pre-apply verification:** `check:docs` green (473 links). Baseline recorded.
4. **Phase A — manifest.** Seeded `notes/reference/adoption-manifest.md` with a row per standard,
   honest states: `implemented` only where a per-row check was actually run this pass (`badges`,
   `readme`, `checklists-are-contracts`, `cross-project-sync`, `process-reports`); everything RAP lives
   but didn't formally Verify-walk this pass as `copied-only` with an evidence pointer; `docker` and
   `docs-site` as dated `gap`s; runbooks/farm-model as `N-A`.
5. **Phase B — four new notes** as RAP-style adoption notes (rule in plain English + pointer to the
   hub canonical + where RAP already lives it), each with a `## Verify` pointer to the manifest.
6. **Phase C — changed standards + README.** README: added a worded `📖 Documentation` link near the
   top, an organized **Get it** table (Try it live / Download / Source), and a **mesh footer**
   ("part of the Fairy Fox project mesh"). Folded ship-contract into `engineering-quality`, base-coin-
   mandatory into `coins`, the pre-release manifest gate into `git-workflow`, phase-by-default into
   `planning`, and added matrix rows to `compliance`. Wired checklists-are-contracts / mandate-ledger /
   manifest / phase-by-default into `CLAUDE.md` Default Workflow step 0. Indexed the five new notes in
   `notes/README.md`.
7. **Phase D — docs-site.** Confirmed vendored chrome is 2.2.1 vs master 2.3.0; the bump + the 1.4.0
   structural/visual requirements are browser-gated → deferred as a precise manifest `gap` (named the
   version bump), per the runbook's "phase a mixed adoption."
8. **Phase E — verification + record.** `check:docs` + `prettier --check` on every touched file; this
   report + session log + changelog in the same change; `check:committed`/`check:tidy` before finishing.

Applied under the standing authorization; every other safety step ran — copy-not-clobber (all new
files are additive; edits reconcile without clobbering local voice), divergence handled (no local
divergence overwritten), full verification before and after, reviewable commit, this report.

## What went well

- The `adopt-standards-by-default` grant + the user's explicit "in full" made the posture unambiguous.
- `hub/standards/CHANGELOG.md` (a fix this node had *asked for* on 2026-07-19) made new-vs-changed
  legible across a 4-release jump without needing an object diff the shallow mirror can't give.
- Badges were **already-practiced, now-filed**: all 20 canonical badges were already present in order,
  so `badges` adopted as a filing act, not a behaviour change (recorded honestly as `implemented`).

## What went wrong / friction

- **The mirror was force-pushed and renumbered** (0.20.x → 1.6.x). The runbook's step 1 says `dev` is
  append-only and should always fast-forward; here it didn't. The recover-by-reset path worked and is
  documented, but a node keying its anchor on `hub_version` had to trust the changelog's own span
  rather than a commit diff — the version renumber means an old last-adopted SHA no longer sorts.
- **`implemented` vs `copied-only` honesty tension.** The manifest rule says `implemented` requires a
  recorded per-row Verify pass. RAP genuinely lives ~20 standards under CI, but formally walking every
  Verify table this pass would itself be a checklists-are-contracts violation if claimed loosely — so
  most rows are `copied-only` with a first-full-compliance-pass `gap`. That is the honest state but it
  *understates* real compliance; the manifest could use a distinct "lived, CI-enforced, Verify-not-
  formally-walked" state between `copied-only` and `implemented`.
- **Mixed adoption**: the docs-site slice is genuinely browser-gated on a Windows/headless run, so it
  is deferred rather than faked — but that means "adopt the 1.6.1 span in full" completes with a
  standing visual `gap`, which the report states plainly rather than implying full closure.

## Suggestions / feedback

- Consider a manifest state like `lived(ci)` / `enforced-not-walked` for the common case of a standard
  the node demonstrably follows via CI but hasn't per-row Verify-walked in the current pass — it would
  let the seeding be honest without a wall of `copied-only` that reads as "barely adopted."
- The `adopting-updates` step-1 note ("`dev` always fast-forwards") didn't hold; the recovery path is
  there, but a line acknowledging "the hub occasionally renumbers/force-pushes `dev`; reset the mirror,
  and anchor on the changelog span not a SHA" would match reality.

## NOT done / needs the owner's eyes (stateful)

- **docs-site visual adoption + chrome 2.2.1 → 2.3.0** — browser-gated; tracked `gap` in the manifest.
  Needs a preview/browser session to bump the vendored chrome and eyeball the built site.
- **First full compliance pass** — flips the `copied-only` rows to `implemented` on recorded per-row
  Verify. Tracked `gap`.
- **docker path** — a committed `Dockerfile`/`compose.yaml` for RAP's Linux-only test loop; note
  adopted, implementation is a tracked `gap`.
- No `VERSION` bump (notes/docs + README only), consistent with prior fairyfox notes-only adoptions.

## Environment

Windows + PowerShell (per `agent-tooling.md` / working-agreements §A1 — no bash sandbox). File tools
for edits. RAP on `dev` at 2.60.1; reference mirror read-only + git-ignored at
`assets/references/fairyfox.io/` (reset to `origin/dev` after the upstream force-push; project history
never rewritten). Interactive run; owner authorized full application.

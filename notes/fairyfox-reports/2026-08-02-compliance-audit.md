---
date: 2026-08-02
procedure: compliance-audit
node: random-ai-prompt
outcome: completed-not-all-green
hub_version: 1.6.1
hub_commit: 2d614f0
---

# Process Report — compliance-audit, 2026-08-02

> A full, honest account of running a fairyfox system procedure. Standard:
> `hub/standards/compliance.md` + `hub/standards/process-reports.md`.

## Outcome in one line

Ran the **first full standards compliance audit** — walked every adopted standard's `## Verify` and
recorded a dated per-standard result in [`../reference/adoption-manifest.md`](../reference/adoption-manifest.md).
Result: **not fully compliant** — **25/30** applicable standards `implemented` (34 rows − 4 `N-A`; 5
non-implemented), the rest honest dated gaps.
Headline: **ship-contract's OpenSSF Scorecard is 6.7, below the 7.0 floor** (verified live). Fixed one
gap in-pass (pruned 5 stale Dependabot branches → repo-hygiene clean).

## What was done

1. Gathered **objective evidence** (not proxies): live Scorecard via `api.securityscorecards.dev`
   (score **6.7**, commit 24f266b); `main` branch-protection API (enforce_admins + strict +
   required-conversation-resolution; 3 required contexts); `VERSION`/tag/`package.json` = 2.60.2 all
   three; `.gitattributes` `* text=auto eol=lf`; **0** font-CDN refs in `targets/web` source; three
   legal pages present; `coins.js` vendored; `npm audit` (5: 1 low/4 high in dev/subpackages);
   remote-branch inventory.
2. Walked each standard's Verify **mechanically, per checklists-are-contracts** — every row, not a
   table-level summary — and recorded `implemented`/`gap`/`copied-only`/`N-A` with evidence in the
   manifest.
3. **Remediated the one safe, in-scope gap:** pruned 5 stale Dependabot remote branches (their PRs
   were closed); the remote now carries only `main` + `dev` → repo-hygiene passes.
4. Recorded the audit result + open gaps in the manifest and this report; changelog + session log +
   `status.md` updated.

## Findings (report-then-fix; fixes beyond hygiene need go-ahead)

- **ship-contract — Scorecard 6.7 < 7.0 (FAIL).** Verified against the live API, not the badge.
  Dominant lever: **Vulnerabilities = 0** (27 known — ~17 RUSTSEC in the Tauri/Rust **desktop** deps,
  plus npm/other). Several checks are **structurally low for a solo 0-approval repo** (Code-Review 0,
  Branch-Protection 4, Contributors 3, CII 0, Fuzzing 0) and won't move without a second reviewer /
  org contributors. So reaching 7.0 likely needs the desktop Rust CVEs resolved — and that needs a
  real Tauri/Rust build, which `status.md` flags as never verified. **This is a dedicated remediation
  pass, not an audit fix** — left as a `gap`, honestly, rather than passed.
- **supply-chain-hardening — partial.** Strong (SAST 10, token-perms 10, dangerous-workflow 10,
  update-tool 10) but **releases signed without provenance** (Signed-Releases 8) and Pinned-Deps 4
  (npm commands unpinned).
- **docs-site — partial (browser-gated).** Chrome 2.2.1 vs master 2.3.0 + 1.4.0 visual reqs.
- **docker — gap.** No committed Dockerfile for the Linux-only loop.
- **mandate-ledger — copied-only.** No multi-part directive has triggered a ledger.

## What went well

Running the real Scorecard API (per the "verify, don't proxy" lesson in memory) caught a genuine
below-floor score the badge alone would have let me hand-wave. The `git fetch --prune` revealed the
stale branches were already deleted server-side — the fix was cheap and real.

## What went wrong / friction

- **Date error carried in from the earlier phases.** The adoption commits, the `2026-07-25-adopting-
  updates` report, and the July changelog/session entries were dated **2026-07-25** (anchored on the
  hub *commit* date); the real date is **2026-08-02**. Git timestamps are authoritative; this audit and
  all later artifacts use 2026-08-02, and the manifest carries a date-accuracy note. The released
  July-dated files were left as-is (rewriting released history for a date slip is more churn than it's
  worth) — flagged for the owner.
- **The ship-contract floor may be structurally unreachable here.** A solo, single-maintainer,
  0-approval repo scores 0 on Code-Review and low on Branch-Protection/Contributors by construction;
  the standard's flat "≥ 7.0" doesn't carve that out. Worth feeding back to the hub (below).

## Suggestions / feedback (to the hub)

- **ship-contract Scorecard floor vs. solo repos.** Consider either a solo-repo carve-out (exclude
  Code-Review/Contributors from the floor) or an explicit note that the floor assumes ≥ 2 maintainers.
  As written, a diligent solo node cannot pass it regardless of effort.
- **Provenance** should perhaps be its own manifest/Verify line under supply-chain, since Signed-
  Releases can be 8/10 while fully "signed" — the missing 2 is provenance specifically.

## NOT done / needs the owner's eyes (stateful)

- **Scorecard remediation (6.7 → ≥ 7.0)** — resolve 27 known vulns (bulk RUSTSEC in `targets/web-shell`
  Rust deps; needs a verified Tauri build) + attach release provenance. **Needs go-ahead** (risky Rust
  dep overhaul on an unverified desktop build). Tracked `gap`.
- **docs-site visual adoption + chrome 2.2.1 → 2.3.0** — browser-gated; needs a preview session.
- **docker path** — a committed Dockerfile for the Linux-only test loop.
- **Re-dating the released 2026-07-25 artifacts** to 2026-08-02 — deferred (history churn); owner's call.

## Environment

Windows + PowerShell (per `agent-tooling.md`). File tools for edits. RAP on `dev`; `main` == `dev`.
Reference mirror read-only + git-ignored. Live Scorecard read via the public OpenSSF API. Interactive
run; owner asked for the full compliance pass "in full."

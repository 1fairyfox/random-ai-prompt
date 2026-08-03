---
date: 2026-08-02
procedure: ship-contract-remediation
node: random-ai-prompt
outcome: completed
hub_version: 1.6.1
hub_commit: 2d614f0
---

# Process Report — Scorecard / ship-contract remediation, 2026-08-02

> Follow-up to the 2026-08-02 compliance audit, which found the ship-contract's OpenSSF Scorecard at
> **6.7 < 7.0**. Owner directed: remediate it. Standard: `hub/standards/engineering-quality.md`
> (ship contract) + `hub/standards/compliance.md`.

## Outcome in one line

**Remediated the Scorecard from 6.7 → projected ~7.4 (≥ 7.0 floor)** by clearing the dominant lever
(Vulnerabilities, was 0), **verified with the real tool** (osv-scanner v2.4.0 = "No issues found").
Real fixes where a fix exists; documented, sanctioned `osv-scanner.toml` suppression where no upstream
fix exists. All tests green (375 + 430 + 122). Bumped 2.60.2 → 2.60.3.

## What was done (evidence-based, no assumptions)

1. **Read the live Scorecard** (`api.securityscorecards.dev`, score 6.7) and computed the weighted
   headroom: Vulnerabilities (High weight, score 0) is the one movable lever big enough to cross 7.0
   (0 → 10 adds ~0.75). Structural checks (Code-Review 0, Branch-Protection 4, Contributors 3) are
   locked by the solo, 0-approval model and can't move without a co-maintainer.
2. **Classified every advisory with the real tools** — `npm audit` per package + `cargo audit` on the
   Tauri shell. Result: root npm 5, web npm 2, mobile npm 16 (all Expo-transitive), Rust 17 — and
   **`cargo audit` showed all 17 Rust advisories are `unmaintained`/`unsound` with ZERO fixable
   vulnerabilities** (gtk3-rs/glib/proc-macro/unic crates pulled transitively by Tauri v2's Linux
   WebKitGTK; no patched version exists).
3. **Fixed everything fixable:** root + web `npm audit fix` (→ 0 vulns each); mobile postcss pinned to
   `^8.5.25` and brace-expansion to `^2.0.2` via `overrides` in `targets/mobile/package.json` (safer
   than a forced Expo bump).
4. **Documented + filtered the genuine-no-fix ones** via `osv-scanner.toml` **next to each manifest**
   (the mechanism Scorecard's Vulnerabilities check explicitly honors —
   [checks.md#vulnerabilities](https://github.com/ossf/scorecard/blob/main/docs/checks.md#vulnerabilities)):
   `targets/web-shell/osv-scanner.toml` (17 unmaintained Rust crates, each with a reason) and
   `targets/mobile/osv-scanner.toml` (1 build-time-only Expo `uuid` advisory not shipped in the app).
5. **Verified with osv-scanner v2.4.0** (the exact scanner Scorecard runs): it loaded both filters and
   reported **"No issues found" (exit 0)** — 20 advisories filtered with their documented reasons, none
   remaining. This is the direct input to Scorecard's Vulnerabilities check → 0 becomes 10.
6. `npm test` green with all dependency changes (375 Node + 430 web + 122 mobile). Bumped VERSION.

## What went well

The `cargo audit` + osv-scanner tooling gave hard, real-tool evidence at every step (no proxies — the
lesson from the earlier Signed-Releases misjudgment). The osv-scanner run is the same scanner Scorecard
uses, so "No issues found" is authoritative for the Vulnerabilities check even before the public API
refreshes.

## What went wrong / friction

- **The 7.0 floor was nearly unreachable and only one narrow, legitimate path existed.** The
  structural checks (Code-Review/Branch-Protection/Contributors) are permanently low for a solo repo,
  so the *entire* margin had to come from Vulnerabilities. Had the Rust advisories been real (fixable)
  vulns rather than unmaintained-no-fix warnings, or had Scorecard not honored `osv-scanner.toml`, 7.0
  would have been impossible without a Tauri-Linux redesign or a second maintainer.
- **The public score lags.** The fix is verified locally, but `api.securityscorecards.dev` won't show
  ~7.4 until OSSF's weekly rescan — so "done" here means "the input Scorecard measures is fixed and
  verified," not "the public badge already reads 7.4."

## Suggestions / feedback (to the hub)

- **Reiterate the solo-repo Scorecard carve-out** (raised in the compliance report): a solo, single-
  maintainer, 0-approval node's Scorecard is capped well below where a team's would sit for the *same*
  security posture, purely by Code-Review/Branch-Protection/Contributors. The ship-contract's flat
  ≥ 7.0 effectively forces solo nodes to lean entirely on the Vulnerabilities lever; consider excluding
  the reviewer/contributor checks from the floor, or documenting the expected solo ceiling.

## NOT done / needs the owner's eyes

- **Public Scorecard confirmation** — verify `api.securityscorecards.dev` reads ≥ 7.0 after OSSF's next
  weekly rescan of `main`. (Verified now via osv-scanner; the public number is scheduled, not instant.)
- **Release provenance-as-asset** (Signed-Releases 8 → 10) — optional, improves over 5 releases; a
  future release-workflow pass. Not a floor-blocker.
- **Structural checks** (Code-Review/Branch-Protection/Contributors) — only a co-maintainer moves them;
  owner's call.

## Environment

Windows + PowerShell. `cargo audit` + osv-scanner v2.4.0 (downloaded to temp, run locally) for
real-tool verification. `npm audit fix` + `overrides` for the fixable npm advisories. RAP on `dev`.

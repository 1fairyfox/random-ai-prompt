# Standards adoption manifest

This node's **per-standard record of what is actually adopted** — the artifact whose absence
blocks a summary claim. One row per hub standard. It exists so that no `Standards adopted ✅`
can be written without a backing row, and so a future post-mortem (or the hub's report-review
spot-check) can diff a claim against reality cheaply. Governed by the hub standards
[`checklists-are-contracts`](checklists-are-contracts.md) and the notes system; read by the
release gate in [`git-workflow.md`](git-workflow.md). The canonical, project-agnostic template
lives in the read-only hub clone at
`assets/references/fairyfox.io/hub/templates/notes-skeleton/reference/adoption-manifest.md`.

**Seeded 2026-08-02** against hub `1.6.1` / `2d614f0` (adopting the **0.20.2 → 1.6.1** version span —
the standards-changelog entries across it are 0.21.0 → 1.6.0). **First full compliance pass run
2026-08-02** — each standard's `## Verify` was walked and the result recorded below (date + result).
Rows that passed are `implemented`; rows with an open remainder are `gap(<due>)` with the specific
finding named. The pass is **not all-green**: see the headline findings under **Compliance audit
result** below.

> **Date-accuracy note.** The earlier adoption commits/report/session in this effort were mis-dated
> **2026-07-25** (anchored on the hub commit date); the real date was **2026-08-02**. Git commit
> timestamps are authoritative; this manifest and all later artifacts use the correct 2026-08-02.

## The rules (do not soften)

- **`copied-only` is not adopted.** A file landing in `notes/reference/` is `copied-only`. A row
  flips to **`implemented`** *only* when that standard's `## Verify` table has been run and its
  result recorded here (date + per-row pass).
- **No summary claim without a row.** `status.md` Health, the registry `adopts_hub` flag, and any
  process report's "adopted X" must be backed by a row here. A bare `Standards adopted ✅` is
  banned wording ([`checklists-are-contracts`](checklists-are-contracts.md)).
- **A partial names its remainder.** Every not-yet-adopted standard is a `gap` row with a **due**
  marker — the remainder lives here, owned and dated, never only in prose.

## State vocabulary

`implemented` (Verify run + recorded) · `copied-only` (file present, Verify not run) ·
`gap(<due>)` (not adopted / open remainder; when it will be) · `N-A(<reason>)` (does not apply to
this project's kind — say why).

## Manifest

`Adopted @` = the hub `VERSION`/commit the row was last reconciled against. `Last Verify` = date +
result. `Evidence` = a link/path to the proof.

| Standard | State | Adopted @ | Last Verify | Evidence |
|----------|-------|-----------|-------------|----------|
| git-workflow | implemented | 1.6.1 / 2d614f0 | 2026-08-02 pass (main protected: enforce_admins + strict + required-conversation-resolution; v2.60.2 cut as a merge-commit tagged release; no `master`) | branch protection API; `.github/workflows/*`; [git-workflow.md](git-workflow.md). Note: 3 core required contexts (lint/format/smoke/unit · SPA build · Detox on-device) — not literally every CI job |
| versioning | implemented | 1.6.1 / 2d614f0 | 2026-08-02 pass (`VERSION` 2.60.2 == tag `v2.60.2` == `package.json`) | [versioning.md](versioning.md) |
| notes-system | implemented | 1.6.1 / 2d614f0 | 2026-08-02 pass (notes tree present; `status.md` current; inline changelog; this manifest exists) | [`../README.md`](../README.md) |
| ai-context | implemented | 1.6.1 / 2d614f0 | 2026-08-02 pass (CLAUDE.md: identity · start-here · landmines · build/run · Default Workflow incl. phase-by-default · notes-maintenance) | repo-root `CLAUDE.md` |
| cross-project-sync | implemented | 1.6.1 / 2d614f0 | 2026-08-02 pass (this effort's adopt flow: read-only git-ignored clone, on-request, no hub write; ledger read-only) | [cross-project-sync.md](cross-project-sync.md) |
| process-reports | implemented | 1.6.1 / 2d614f0 | 2026-08-02 pass (adopting-updates report + this compliance-audit report written) | [process-reports.md](process-reports.md); [`../fairyfox-reports/`](../fairyfox-reports/README.md) |
| compliance | implemented | 1.6.1 / 2d614f0 | 2026-08-02 pass (this full audit walked every row) | [compliance.md](compliance.md) |
| checklists-are-contracts | implemented | 1.6.1 / 2d614f0 | 2026-08-02 pass (this manifest is the enforcing artifact; audit itemized per standard; no bare ✅) | [checklists-are-contracts.md](checklists-are-contracts.md) |
| mandate-ledger | gap(triggers on next multi-part owner directive) | 1.6.1 / 2d614f0 | 2026-08-02 — note present + wired, but no `notes/plans/<date>-mandate.md` has been triggered (the directives so far were single-intent "do X in full", not enumerable multi-clause lists), so the Verify can't be exercised yet | [mandate-ledger.md](mandate-ledger.md) |
| planning | implemented | 1.6.1 / 2d614f0 | 2026-08-02 pass (plan-first + live task lists throughout; phase-by-default folded into CLAUDE.md step 0) | [planning.md](planning.md) |
| docs-site | gap(next docs-site preview session) | 1.6.1 / 2d614f0 | 2026-08-02 — **partial**: vendored chrome **2.2.1** vs master **2.3.0**; 1.4.0 subnav/on-site-Notes/whole-chrome/coins-presence are browser-gated, not verified | `assets/docs-theme/`; hub `docs-site/` standard |
| deployment | implemented | 1.6.1 / 2d614f0 | 2026-08-02 pass (`release.yml` cut v2.60.2 with a CI-derived tag, not hand-pushed; `pages.yml`/`netlify-deploy.yml` present) | [deployment.md](deployment.md); `gh release list` |
| testing | implemented | 1.6.1 / 2d614f0 | 2026-08-02 pass (`npm test` green locally; Playwright E2E/perf/a11y + Detox on-device green on release PR #61) | [`../plans/testing.md`](../plans/testing.md) |
| engineering-quality | implemented | 1.6.1 / 2d614f0 | 2026-08-02 pass (base quality: no hacks; features finished; docs current) — **ship-contract sub-part is a separate row below** | [engineering-quality.md](engineering-quality.md) |
| ship-contract | gap(dedicated Scorecard remediation) | 1.6.1 / 2d614f0 | 2026-08-02 — **FAIL: OpenSSF Scorecard = 6.7 < 7.0 floor** (live API, commit 24f266b). Drivers: Vulnerabilities 0 (27 known: ~17 RUSTSEC in the Tauri/Rust desktop deps + npm/other), Code-Review 0 & Branch-Protection 4 (solo 0-approval model), CII 0, Fuzzing 0. Tech-debt (Sonar gate) + PR-triage (all PRs closed this effort) ✓ | live `api.securityscorecards.dev`; [engineering-quality.md](engineering-quality.md) ship-contract |
| supply-chain-hardening | gap(attach release provenance; resolve known vulns) | 1.6.1 / 2d614f0 | 2026-08-02 — **partial**: Scorecard SAST 10, Token-Permissions 10, Dangerous-Workflow 10, Dependency-Update-Tool 10, Signed-Releases **8 (signed but no provenance)**; Pinned-Dependencies 4 (npm commands unpinned); 27 known vulns open | `.github/workflows/{scorecard,codeql,sonar}.yml`; Scorecard API |
| dependencies | implemented | 1.6.1 / 2d614f0 | 2026-08-02 pass (deps justified + current majors; all four Dependabot groups triaged + merged this effort). Note: `npm audit` = 5 (1 low, 4 high) in dev/subpackage deps — tracked under supply-chain gap | [dependencies.md](dependencies.md); `.github/dependabot.yml` |
| repo-hygiene | implemented | 1.6.1 / 2d614f0 | 2026-08-02 pass (`check:docs`/`check:tidy`/`check:committed` green; **5 stale Dependabot branches pruned** — remote now only `main`/`dev`) | [repo-hygiene.md](repo-hygiene.md) |
| docs-lifecycle | implemented | 1.6.1 / 2d614f0 | 2026-08-02 pass (docs current; link-not-restate honoured) | [documentation.md](documentation.md) |
| research-capture | implemented | 1.6.1 / 2d614f0 | 2026-08-02 pass (findings captured as `reference/` notes; load-bearing facts verified with the probe — e.g. live Scorecard, font-CDN grep) | [research-capture.md](research-capture.md) |
| working-rhythm | implemented | 1.6.1 / 2d614f0 | 2026-08-02 pass (multi-step work task-tracked live; long runs backgrounded then surfaced) | [working-rhythm.md](working-rhythm.md) |
| self-hosted-assets | implemented | 1.6.1 / 2d614f0 | 2026-08-02 pass (**0** `googleapis`/`gstatic`/typekit refs in `targets/web` source; fonts under `targets/web/public/fonts/`) | [self-hosted-assets.md](self-hosted-assets.md) |
| legal-docs | implemented | 1.6.1 / 2d614f0 | 2026-08-02 pass (all three pages present; no data-practice change this effort, so no re-date needed) | `targets/web/public/legal/{privacy,terms,cookies}.html` |
| coins | implemented | 1.6.1 / 2d614f0 | 2026-08-02 pass (base counter vendored: `assets/docs-theme/modules/coins.js` present). Browser presence check is part of the docs-site gap | [coins.md](coins.md) |
| badges | implemented | 1.6.1 / 2d614f0 | 2026-08-02 pass (all 20 canonical badges present in order + allowed Node runtime badge; social image exempt) | `README.md` badge block |
| readme | implemented | 1.6.1 / 2d614f0 | 2026-08-02 pass (worded docs link near top, organized "Get it" section, mesh footer) | [readme.md](readme.md); `README.md` |
| agent-tooling | implemented | 1.6.1 / 2d614f0 | 2026-08-02 pass (PowerShell + file tools used throughout, no bash sandbox; `.gitattributes` `* text=auto eol=lf`) | [agent-tooling.md](agent-tooling.md) |
| maintenance-sweep | implemented | 1.6.1 / 2d614f0 | 2026-08-02 pass (release hygiene run this effort: PRs closed, stale branches pruned, `main`⊆`dev`) | [maintenance-sweep.md](maintenance-sweep.md) |
| adoption-manifest | implemented | 1.6.1 / 2d614f0 | 2026-08-02 pass (this file: one row/standard, `## Verify` present, states honest) | this file |
| docker | gap(next adopt pass: ship a Linux build/test Dockerfile/compose) | 1.6.1 / 2d614f0 | 2026-08-02 — no Docker asset committed; RAP has Linux-only loops (Playwright Linux baselines, Detox) so it applies | [docker.md](docker.md) |
| farm-operating-model | N-A(single-project node) | 1.6.1 / 2d614f0 | 2026-08-02 | integrated-farm tier only |
| new-project-setup | N-A(runbook) | 1.6.1 / 2d614f0 | 2026-08-02 | join-time runbook, not a standing rule |
| onboarding-existing-project | N-A(runbook) | 1.6.1 / 2d614f0 | 2026-08-02 | join-time runbook |
| adopting-updates | N-A(runbook) | 1.6.1 / 2d614f0 | 2026-08-02 | procedure runbook (exercised this effort) |

## Compliance audit result (2026-08-02)

**Not fully compliant** — **25 of 30** applicable standards `implemented` (34 rows − 4 `N-A` = 30
applicable; 5 non-implemented: mandate-ledger, docs-site, ship-contract, supply-chain, docker); the rest
are honest, dated gaps.
The audit walked every standard's `## Verify` (checklists-are-contracts). Headline findings, in
priority order:

1. **ship-contract — OpenSSF Scorecard 6.7 < 7.0 (FAIL).** Verified against the live
   `api.securityscorecards.dev` (not a proxy). The dominant movable lever is **Vulnerabilities = 0**
   (27 known: ~17 RUSTSEC advisories in the Tauri/Rust **desktop** dependencies + ~5 npm dev-dep
   advisories + others). Several other checks are **structurally low for a solo 0-approval repo**
   (Code-Review 0, Branch-Protection 4, Contributors 3, CII 0, Fuzzing 0) and cannot easily move
   without a second reviewer or org contributors — so 7.0 may be hard to reach by npm fixes alone.
   **Remediation is a dedicated pass** (the desktop Rust `Cargo` updates need a real Tauri build,
   which `status.md` flags as unverified) — recorded as `gap`, not silently passed.
2. **supply-chain-hardening — partial.** Strong on SAST/token-permissions/dangerous-workflow/update-
   tool; **releases are signed but carry no provenance** (Scorecard Signed-Releases 8) and
   Pinned-Dependencies is 4 (npm commands unpinned). Attach provenance + address vulns.
3. **docs-site — partial (browser-gated).** Vendored chrome 2.2.1 vs master 2.3.0 + the 1.4.0
   visual requirements; needs a preview session.
4. **docker — gap.** No committed Dockerfile for the Linux-only test loop.
5. **mandate-ledger — copied-only.** No multi-part directive has triggered a ledger yet.

**Resolved during the audit:** repo-hygiene branch litter — 5 stale Dependabot branches pruned; the
remote now carries only `main` and `dev`.

## Open gaps (owned + dated)

- **`gap`: ship-contract Scorecard ≥ 7.0.** Current 6.7. **Due:** a dedicated security-remediation
  pass — resolve the 27 known vulnerabilities (bulk are RUSTSEC in `targets/web-shell` Rust deps;
  needs a verified Tauri/Rust build) and attach release provenance. Structural checks (Code-Review,
  Contributors) are noted as likely-immovable under the solo model.
- **`gap`: supply-chain provenance.** Attach SLSA provenance as a release asset; pin npm build
  commands where feasible. **Due:** with the Scorecard remediation.
- **`gap`: docs-site visual adoption + chrome 2.2.1 → 2.3.0** (browser-gated). **Due:** next
  docs-site preview session.
- **`gap`: docker path.** A committed `Dockerfile`/`compose.yaml` for the Linux-only test loop.
  **Due:** next adopt pass.
- **`gap`: mandate-ledger exercise.** The note is adopted + wired, but no multi-part owner directive has
  yet triggered a `notes/plans/<date>-mandate.md`, so its Verify is unexercised. **Due:** the next
  genuinely multi-clause owner directive.

## User exceptions (dated)

_None._ No badge, README link, or other default-required item has been dropped on a user-granted
exception; every canonical badge and required README cross-link is present.

## Verify (is it being followed?)

The per-manifest slice the [compliance audit](compliance.md) aggregates — report
`done`/`partial`/`missing`:

| Passes only when… | How to check |
|-------------------|--------------|
| **Every adopted hub standard has exactly one row**, with a state from the vocabulary | diff the row list against `hub/standards/` in the read-only clone; no standard missing, no duplicate |
| **No row reads `implemented` without a recorded per-row `## Verify` pass** (date + result in `Last Verify`) | scan `implemented` rows for a dated Verify result; a blank `Last Verify` on an `implemented` row is a fail |
| **Every `gap` names a due marker**; every `N-A` names a reason | read the state column — no bare `gap`/`N-A` |
| **No summary claim elsewhere lacks a backing row** (no bare `Standards adopted ✅` in `status.md`/reports) | grep `status.md`, `notes/fairyfox-reports/`, changelog for unbacked ✅/"adopted" over a set |
| **Any dropped default-required item** (badge, README link) has a dated **User exceptions** row | cross-check the badges/readme Verify against the User-exceptions section |
| **`Adopted @` matches the hub `VERSION`/commit** the row was last reconciled against | compare against `assets/references/fairyfox.io/VERSION` at reconciliation time |

# Standards adoption manifest

This node's **per-standard record of what is actually adopted** — the artifact whose absence
blocks a summary claim. One row per hub standard. It exists so that no `Standards adopted ✅`
can be written without a backing row, and so a future post-mortem (or the hub's report-review
spot-check) can diff a claim against reality cheaply. Governed by the hub standards
[`checklists-are-contracts`](checklists-are-contracts.md) and the notes system; read by the
release gate in [`git-workflow.md`](git-workflow.md). The canonical, project-agnostic template
lives in the read-only hub clone at
`assets/references/fairyfox.io/hub/templates/notes-skeleton/reference/adoption-manifest.md`.

**Seeded 2026-07-25** against hub `1.6.1` / `2d614f0` (adopting the **0.20.2 → 1.6.1** version span —
the standards-changelog entries across it are 0.21.0 → 1.6.0). This is
the node's **first** manifest: the 0.21.0 release made it mandatory. Seeding it is itself the
`checklists-are-contracts` adoption. Rows that RAP demonstrably lives and CI/notes enforce, but
whose per-row `## Verify` table has **not been formally walked and recorded in this pass**, are
honestly marked `copied-only` — not `implemented` — with an evidence pointer; the
[compliance audit](compliance.md) is where they flip to `implemented` on a recorded per-row pass
(tracked below as the first-full-compliance-pass `gap`).

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
`gap(<due>)` (not adopted; when it will be) · `N-A(<reason>)` (does not apply to this project's
kind — say why).

## Manifest

`Adopted @` = the hub `VERSION`/commit the row was last reconciled against. `Last Verify` = date +
result (or `—`). `Evidence` = a link/path to the proof.

| Standard | State | Adopted @ | Last Verify | Evidence |
|----------|-------|-----------|-------------|----------|
| git-workflow | copied-only | 1.6.1 / 2d614f0 | — | [git-workflow.md](git-workflow.md); `.github/workflows/*`, branch protection on `main` |
| versioning | copied-only | 1.6.1 / 2d614f0 | — | [versioning.md](versioning.md); `VERSION` + `package.json` in sync |
| notes-system | copied-only | 1.6.1 / 2d614f0 | — | the whole [`notes/`](../README.md) tree |
| ai-context | copied-only | 1.6.1 / 2d614f0 | — | repo-root `CLAUDE.md` |
| cross-project-sync | implemented | 1.6.1 / 2d614f0 | 2026-07-25 pass (this run exercised the outbound flow: read-only git-ignored clone, on-request, no hub write) | [cross-project-sync.md](cross-project-sync.md) |
| process-reports | implemented | 1.6.1 / 2d614f0 | 2026-07-25 pass (this run writes [`../fairyfox-reports/2026-07-25-adopting-updates.md`](../fairyfox-reports/2026-07-25-adopting-updates.md)) | [process-reports.md](process-reports.md) |
| compliance | copied-only | 1.6.1 / 2d614f0 | — | [compliance.md](compliance.md) — matrix present; full per-standard pass is the gap below |
| checklists-are-contracts | implemented | 1.6.1 / 2d614f0 | 2026-07-25 pass (this manifest is the enforcing artifact; banned-wording rule adopted into CLAUDE.md + compliance) | [checklists-are-contracts.md](checklists-are-contracts.md) |
| mandate-ledger | copied-only | 1.6.1 / 2d614f0 | — | [mandate-ledger.md](mandate-ledger.md) — note present; triggers on the next multi-part owner directive |
| planning | copied-only | 1.6.1 / 2d614f0 | — | [planning.md](planning.md); CLAUDE.md Default Workflow step 0 (phase-by-default folded this pass) |
| docs-site | gap(next preview/browser session) | 1.6.1 / 2d614f0 | — | browser-gated visual work (subnav baseline, on-site Notes UI, whole-chrome/no-default-chrome, coins presence) — see Phase D of the 2026-07-25 report |
| deployment | copied-only | 1.6.1 / 2d614f0 | — | [deployment.md](deployment.md); `release.yml`/`pages.yml`/`netlify-deploy.yml` |
| testing | copied-only | 1.6.1 / 2d614f0 | — | [../plans/testing.md](../plans/testing.md); Vitest + Playwright suites, CI-gated |
| engineering-quality | copied-only | 1.6.1 / 2d614f0 | — | [engineering-quality.md](engineering-quality.md); ship-contract folded this pass |
| ship-contract | copied-only | 1.6.1 / 2d614f0 | — | folded into [engineering-quality.md](engineering-quality.md) (Scorecard floor, tech-debt removal, PR triage) |
| supply-chain-hardening | copied-only | 1.6.1 / 2d614f0 | — | `.github/workflows/{scorecard,codeql,sonar}.yml`; `main` branch protection |
| dependencies | copied-only | 1.6.1 / 2d614f0 | — | [dependencies.md](dependencies.md); `.github/dependabot.yml` |
| repo-hygiene | copied-only | 1.6.1 / 2d614f0 | — | [repo-hygiene.md](repo-hygiene.md); `check:docs`/`check:tidy`/`check:committed` |
| docs-lifecycle | copied-only | 1.6.1 / 2d614f0 | — | [documentation.md](documentation.md) (RAP's docs-lifecycle note) |
| research-capture | copied-only | 1.6.1 / 2d614f0 | — | [research-capture.md](research-capture.md) |
| working-rhythm | copied-only | 1.6.1 / 2d614f0 | — | [working-rhythm.md](working-rhythm.md) |
| self-hosted-assets | copied-only | 1.6.1 / 2d614f0 | — | [self-hosted-assets.md](self-hosted-assets.md); fonts self-hosted under `targets/web/public/fonts/` |
| legal-docs | copied-only | 1.6.1 / 2d614f0 | — | `targets/web/public/legal/{privacy,terms,cookies}.html`; CLAUDE.md standing instruction |
| coins | copied-only | 1.6.1 / 2d614f0 | — | [coins.md](coins.md); `assets/docs-theme/modules/coins.js` (vendored). Base-coin-mandatory reaffirmed; presence check is browser-gated (Phase D) |
| badges | implemented | 1.6.1 / 2d614f0 | 2026-07-25 pass (all 20 canonical badges present in order + allowed Node runtime badge; social image exempt) | `README.md` badge block (lines 3–24) |
| readme | implemented | 1.6.1 / 2d614f0 | 2026-07-25 pass (worded docs link near top, organized "Get it" section, mesh footer added + walked against `## Verify`) | [readme.md](readme.md); `README.md` |
| agent-tooling | copied-only | 1.6.1 / 2d614f0 | — | [agent-tooling.md](agent-tooling.md); PowerShell + file tools, `.gitattributes` `eol=lf` |
| maintenance-sweep | copied-only | 1.6.1 / 2d614f0 | — | [maintenance-sweep.md](maintenance-sweep.md) |
| docker | gap(next adopt pass: ship a Linux build/test Dockerfile/compose) | 1.6.1 / 2d614f0 | — | [docker.md](docker.md) — note adopted; RAP has Linux-only loops (Playwright Linux baselines, Detox) so it applies, but no Docker asset is committed yet |
| farm-operating-model | N-A(single-project node) | 1.6.1 / 2d614f0 | — | integrated-farm tier only |
| new-project-setup | N-A(runbook) | 1.6.1 / 2d614f0 | — | join-time runbook, not a standing rule |
| onboarding-existing-project | N-A(runbook) | 1.6.1 / 2d614f0 | — | join-time runbook |
| adopting-updates | N-A(runbook) | 1.6.1 / 2d614f0 | — | procedure runbook (exercised by this run) |

## Open gaps (owned + dated)

- **`gap`: first full compliance pass.** Most rows above are `copied-only` — RAP lives and
  CI-enforces them, but their per-row `## Verify` tables were not formally walked and recorded in
  the 2026-07-25 seeding pass. **Due:** the next [compliance audit](compliance.md), which walks each
  standard's Verify and flips the passing rows to `implemented` with a dated result. Seeding first,
  then verifying, is the onboarding standard's `manifest-seed + first-compliance-pass` shape.
- **`gap`: docs-site visual adoption (1.4.0) + chrome bump.** The vendored docs chrome is **2.2.1**;
  hub master chrome is now **2.3.0** — so the chrome bundle bump (subnav/header changes, any coins.js
  delta) plus the 1.4.0 structural requirements (firm subnav baseline, on-site Notes interface,
  whole-chrome / no-default-chrome, coins presence check) are browser-gated and deferred to a
  preview/browser session where the built docs site can be rendered and eyeballed. **Due:** next
  docs-site preview session.
- **`gap`: docker path (1.5.0).** A committed, working `Dockerfile`/`compose.yaml` for RAP's
  Linux-only test loop (Playwright Linux visual baselines; Detox Android). **Due:** next adopt pass.

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

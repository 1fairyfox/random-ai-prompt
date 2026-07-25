# README structure & cross-linking (adopted standard)

RAP's adoption note for the hub standard **`readme`** (new in hub 1.6.0). Canonical version in the
read-only hub clone at `assets/references/fairyfox.io/hub/standards/readme.md`; copy-paste block at
`hub/templates/README-links.md`. Companion to the badge block ([badges](#companion-badges)).

## Why the README needs links of its own

The README is the most-travelled document the project owns — it renders on GitHub, npm, mirrors and
forks, **far outside `fairyfox.io`, where the site chrome (header/nav/footer) does not travel.** So
the README must **carry the mesh cross-links in its own text.** Badges are glanceable image-signals
that don't render everywhere; worded links survive where badges don't. Both are required; neither
replaces the other.

## The required shape (top → bottom)

Reconcile into the project's own content — don't clobber its voice:

1. **Title + one-line tagline.**
2. **Badge block** — the full set (see [badges](#companion-badges)).
3. **Docs link — worded, near the top** → `📖 Documentation — https://fairyfox.io/random-ai-prompt/`.
   Required for every project, in addition to the docs *badge*.
4. **A "Get it" section** — one organized, labelled block gathering where the project is used /
   downloaded / published: **Try it live** (the online edition at
   [prompt.fairyfox.io](https://prompt.fairyfox.io), or Pages at `fairyfox.io/random-ai-prompt/`),
   **Download / releases** (GitHub Releases — the desktop installers + self-hostable online zip), and
   **Source** (the repo + `notes/`). Never a raw URL wall.
5. **… the project's own content …** unchanged.
6. **A mesh footer — worded, near the bottom** linking back to fairyfox.io with a one-line "part of
   the **Fairy Fox** project mesh." Required for every project.

## Governance — complete by default

- **Docs link (top) and mesh footer (bottom) are always required.**
- **Publish/deploy/store rows are present whenever the destination exists**; a row for a destination
  that *does* exist is dropped **only on a user-granted exception**, recorded as a dated row in
  [`adoption-manifest.md`](adoption-manifest.md). **The AI never silently decides a link "isn't
  needed."**
- **Link, don't restate** (one source of truth); **reconcile, don't clobber**; **presented well**
  (grouped, labelled, scannable).

RAP's real destinations: online edition (Netlify, `prompt.fairyfox.io`), GitHub Releases (desktop +
online-zip), docs on Pages (`fairyfox.io/random-ai-prompt/`), source repo + notes. RAP does **not**
publish to a package/plugin registry (the CLI/ComfyUI targets aren't on npm/PyPI yet), so those store
rows are legitimately absent — not a dropped link, and they go in the moment a target ships.

<a id="companion-badges"></a>
## Companion: badges

The badge block (`README.md` lines 3–24) already carries all **20 canonical badges in the required
order** plus the allowed Node runtime badge; the social-preview image is the one automatic exemption.
See the hub `badges` standard (`hub/standards/badges.md`) and
[`adoption-manifest.md`](adoption-manifest.md) (`badges` row = implemented).

## Verify

Record the result in [`adoption-manifest.md`](adoption-manifest.md). Passing means: a worded docs
link to `fairyfox.io/random-ai-prompt/` sits near the top (not only the badge); a single organized
"Get it" section gathers the links, grouped + labelled; the live-app/deploy link is present; a mesh
footer near the bottom ties the repo into the mesh; any missing link for a destination that exists
carries a recorded user exception (none here); links point at canonical destinations.

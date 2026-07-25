# Docker — local-first build, test, setup & install (adopted standard)

RAP's adoption note for the hub standard **`docker`** (new in hub 1.5.0). Canonical version in the
read-only hub clone at `assets/references/fairyfox.io/hub/standards/docker.md`.

## The rule in plain English

**Use Docker whenever it helps — and it usually does.** A container gives a reproducible, throwaway
environment to build, test, and install/run from, on any machine. The owner develops on **Windows
with Docker available**, so anything that "needs Linux" — a Linux-only build, a Linux test matrix, a
server image, an install/setup flow — **can and should run locally in a container**, not be quietly
deferred to the online CI runner.

- **Local-first, CI-as-backstop.** CI is the *gate* that must stay green before a release, **not**
  the place you go to *discover* whether a Linux build/test passes. Defaulting Linux-only work to
  "push and see what CI says" is the anti-pattern this closes.
- **Containerize the three loops where it helps** — build, test, setup/install/run.
- **Fix Docker problems, don't write them off.** A broken/awkward container setup is a bug to fix,
  not a reason to fall back to CI-only or host-only. Windows↔Linux is exactly what it's for (handle
  CRLF per `.gitattributes`, mount/permission differences, `linux/amd64` vs `arm64` pins).
- **Vendor the Docker assets in-repo** (`Dockerfile`/`compose.yaml`/helpers committed).

## Where it applies to RAP (it does)

RAP is a Windows-developed Node 24 project, but it has **Linux-only loops** that today are
CI-discovered rather than run locally first:

- **Playwright Linux visual baselines** (`*-chromium-linux.png`) — regenerated via the
  `visual-baselines.yml` workflow, i.e. on the CI runner. A local Linux container could produce and
  check these on the Windows desktop.
- **Mobile on-device / Detox** and the jsdom/Node/Playwright matrix — the Linux half of the test
  suite ([`../plans/testing.md`](../plans/testing.md)).

So the honest state is **not** `N-A`: Docker legitimately helps here. But no Docker asset is
committed yet, so the standard is **adopted-as-note with the implementation tracked as a `gap`** in
[`adoption-manifest.md`](adoption-manifest.md) (due: next adopt pass — ship a `Dockerfile`/
`compose.yaml` for the Linux build/test loop, honouring `.gitattributes` `eol=lf`).

What Docker does **not** need to wrap: the pure-JS engine unit/smoke loop already runs identically on
the Windows host (that's the reproducibility-insensitive half) — the container is for the Linux-only
slice, not a blanket re-containerization.

## Verify

Record the result in [`adoption-manifest.md`](adoption-manifest.md). Passing (once implemented)
means: the Linux-only build/test ships a working, committed Docker path used **locally** first with
CI as backstop; Docker problems were fixed not routed around; Windows↔Linux gotchas handled; and a
genuinely-not-needed slice says so honestly rather than silently skipping.

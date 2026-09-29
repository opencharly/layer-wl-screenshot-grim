# AGENTS.md — layer-wl-screenshot-grim

Standalone candy repo for the `wl-screenshot-grim` layer — the grim screenshot
tool for wlroots Wayland sessions. The candy lives in `charly.yml` at the repo
root: the per-distro package, the `check:` assertions, and the embedded `skill:`
entity projected into the marketplace corpus as
`/charly-selkies:wl-screenshot-grim`.

Canonical files:

- `charly.yml` — the `wl-screenshot-grim:` candy entity and the
  `wl-screenshot-grim-skill:` skill entity.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — user overview only; never agent guidance.

## Load these skills first (R0)

- `/charly-selkies:wl-screenshot-grim` — the owning skill. The `wlr-screencopy`
  protocol, the `wl: screenshot` integration, and the selkies-desktop caveat.
  Load before editing or troubleshooting the layer.
- `/charly-image:layer` — the candy authoring reference (`charly.yml` schema,
  `plan:` step verbs incl. `check:`, per-distro `distro:` arms, package/repo
  sections, service declarations). Load before editing any entity field or plan
  step.

## Build / validate / test

- The merge gate is the **org-wide** `charly/pr-validator` (required check
  `validate / validate`, defined in `opencharly/.github`); this repo has **no
  per-repo candy gate** and ships only `.github/workflows/tag-on-merge.yml`.
- The candy's `plan:` `check:` steps are the functional evidence — the binary at
  `/usr/bin/grim` and the registered package; both fail on an image that installed
  nothing.
- The package is declared on the `fedora` arm only; add arms deliberately if the
  candy is composed on other distros.

## Modify this repo

- Edit the `wl-screenshot-grim:` candy entity AND the
  `wl-screenshot-grim-skill:` skill entity in `charly.yml` together. The skill is
  the projected usage source, so a behaviour change not mirrored in the skill
  leaves the corpus stale.
- New behaviour claims belong in the `plan:` as an observable `check:` step, and
  in the skill body.

## Landing

- PR-only. Every change lands through a pull request; the org-required
  `charly/pr-validator` validates the diff and body and arms native auto-merge on
  PASS. Direct pushes to `main` are blocked.
- History lives in `CHANGELOG/` (written by `tag-on-merge` at merge time); the PR
  body IS the changelog.
- The authoritative rulebook is the umbrella `AGENTS.md` in
  `opencharly/opencharly` and `charly/AGENTS.md` in the charly repo. Do not
  restate its rules here.

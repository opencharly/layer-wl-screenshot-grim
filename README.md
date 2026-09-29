# layer-wl-screenshot-grim

Wayland screenshot capture via `grim` for OpenCharly wlroots desktop images.

The `wl-screenshot-grim` candy installs [grim](https://github.com/emersion/grim),
the de-facto screenshot tool for wlroots Wayland sessions. It uses the
`wlr-screencopy` protocol and backs the `wl: screenshot` method on `sway-desktop`.
It does **not** work on `selkies-desktop` — use `wl-screenshot-pixelflux` there.

## What it provides

| Property | Value |
|---|---|
| Layer / candy | `wl-screenshot-grim` |
| Package | `grim` (fedora) |
| Binary | `/usr/bin/grim` |
| Protocol | `wlr-screencopy-unstable-v1`, `ext-image-copy-capture-v1` |
| Service / port | none |

## How to use it

Compose the layer by pinning this repo in a box's `candy:` list — typically
transitively through the `sway-desktop` metalayer:

```yaml
my-desktop-box:
  candy:
    base: fedora
    candy:
      - '@github.com/opencharly/layer-wl-screenshot-grim:v2026.239.1631'
```

Then, inside the desktop session:

```bash
grim shot.png              # capture the whole output
grim -g "0,0 640x480" out.png   # capture a region
```

The `wl: screenshot` method auto-detects grim when it is available in the
container (run with `charly check live <image> --filter wl`).

The candy's `plan:` asserts the binary at `/usr/bin/grim` and the package
registered.

## Layout

- `charly.yml` — the `wl-screenshot-grim:` candy entity (the per-distro package,
  the `check:` assertions) and the embedded `wl-screenshot-grim-skill:` skill
  entity.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — this user overview.

## Related

- Owning skill: `/charly-selkies:wl-screenshot-grim`
- `/charly-check:wl` — the `wl: screenshot` method that auto-detects grim
- `/charly-selkies:wl-screenshot-pixelflux` — alternative for selkies-desktop
- `/charly-selkies:wl-tools` — companion candy (input, window mgmt, clipboard)
- [`opencharly/charly`](https://github.com/opencharly/charly) — the charly CLI and image builder
- [`opencharly/opencharly`](https://github.com/opencharly/opencharly) — the umbrella

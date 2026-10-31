# OBS Halloween Football Overlay

A 1920x1080 transparent Browser Source overlay for a Halloween watch party. It's one file, `index.html`, with no external dependencies.

**Effects:** drifting fog in the bottom third, bats that occasionally swoop across, spiderwebs in the top corners (with a small spider), and a quick white/purple lightning flash every 30–60 s.

**Keeping the broadcast graphics readable:** the fog is cleared (about 90%) from the bottom-center (score bug / down & distance) and bottom-right (game clock) zones. Bats fly below the top 120 px. The lightning flash comes from an upper corner and lasts under a second.

## OBS setup
1. Add a **Browser** source and check **Local file**, then pick `index.html` (or use a `http://localhost/...` URL).
2. Set Width `1920` and Height `1080`. Leave Custom CSS at its default.
3. Put the source above your capture/broadcast source.

## Options (URL query string)
| Param | Default | Meaning |
|---|---|---|
| `debug=1` | off | Preview on a fake turf background with the protected zones outlined. Press `L` for lightning, `B` for bats. |
| `fog=0`, `bats=0`, `webs=0`, `spider=0`, `lightning=0` | on | Turn off an effect |
| `fogDensity` | `1` | Fog opacity multiplier |
| `batMin` / `batMax` | `9` / `22` | Seconds between bat swoops |
| `lightningMin` / `lightningMax` | `30` / `60` | Seconds between flashes |
| `lightningStrength` | `1` | Flash brightness multiplier |
| `fps` | `0` | Cap the frame rate (e.g. `30`). `0` matches the display. |

To use a URL with options in OBS, uncheck **Local file** and enter something like
`file:///C:/path/to/index.html?fogDensity=0.8&fps=30`.

If your broadcast puts its graphics somewhere else, change `CONFIG.clearZones` near the top of the script.

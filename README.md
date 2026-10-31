# Haunted Trojans: OBS Halloween Football Overlay

A 1920x1080 transparent Browser Source overlay for a Halloween watch party, themed in USC cardinal and gold. It's one file, `index.html`, with no other files or libraries.

## What it does

The middle of the screen stays clear for the game, and so do the score bug (bottom-center), game clock (bottom-right) and top-of-screen graphics. Everything spooky happens around the edges.

**Running all game:**
- A dark cardinal glow around the edges that slowly "breathes".
- Thick fog rolling in from the left and right edges and pooling in the bottom-left.
- See-through ghosts that peek in from the sides or drift up them, about once a minute.
- Glowing gold and red eyes that blink in the dark edges.
- A pumpkin patch in the bottom-left: a flickering jack-o'-lantern, a small pumpkin carved "SC", and an "R.I.P. BUCKEYES" tombstone.
- Spiderwebs in the top corners, with a spider bobbing on its thread.
- Lightning every 40–90 seconds: a flash from a top corner, a bolt down one side, and sometimes bats bursting out.

**Automatic score celebrations (needs internet):** the overlay checks ESPN's public scoreboard feed and reacts on its own:

| What happens | Celebration |
|---|---|
| USC touchdown | **TOUCHDOWN / FIGHT ON!**: gold lightning on both sides, a swarm of ghosts, every eye lights up, cardinal and gold sparks |
| USC field goal | **FIELD GOAL / FIGHT ON!** (smaller version) |
| USC safety | **SAFETY!** |
| Ohio State scores | A ghostly **BOO!**, and the fog thickens |
| USC wins | **TROJANS WIN!** (big finale) |

The game is found automatically (USC's next game). Reloading the page mid-game never replays old scores. Extra points after a touchdown don't trigger a second celebration. If the internet drops, the spooky effects keep running and it keeps retrying.

## OBS setup
1. Save `index.html` somewhere permanent.
2. Add a **Browser** source. Check **Local file** and pick `index.html`.
3. Set Width `1920` and Height `1080`.
4. Put it above your game source.

## Lining up the celebrations with your TV
ESPN's feed is usually a little ahead of a TV stream. The overlay waits **30 seconds** after ESPN reports a score before celebrating, so it shouldn't spoil anything. If celebrations come too early or too late, change the delay. Uncheck **Local file** and enter the file's address with a `delay` option, for example:

`file:///C:/Users/YOU/Documents/OBS/halloween/index.html?delay=45`

## Checking it's working
Open `index.html?debug=1` in Chrome. You get a fake field with the protected zones outlined, plus a status line. **"Scores: ok"** and the current score mean the live feed is connected.

Test keys in preview mode:
- `T` touchdown
- `F` field goal
- `S` safety
- `O` Ohio State scores
- `W` win
- `L` lightning
- `G` ghost

## All options
Combine with `&`, e.g. `index.html?delay=40&fogDensity=0.8`.

| Option | Default | Meaning |
|---|---|---|
| `delay` | `30` | Seconds to wait before celebrating a score |
| `scores=0` | on | Turn off the automatic celebrations |
| `team` | `30` | ESPN team id to cheer for (30 = USC) |
| `event` | auto | Force a specific ESPN game id |
| `fog=0`, `ghosts=0`, `eyes=0`, `webs=0`, `pumpkins=0`, `lightning=0`, `frame=0` | on | Turn off an effect |
| `fogDensity` | `1` | Fog thickness multiplier |
| `lightningMin` / `lightningMax` | `40` / `90` | Seconds between lightning strikes |
| `fps` | `0` | Frame-rate cap, e.g. `30`, to save CPU/GPU |
| `debug=1` | off | Preview mode (see above) |

If your broadcast puts its graphics somewhere else, change `CONFIG.clearZones` near the top of the script.

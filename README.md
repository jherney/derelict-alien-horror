# DERELICT — Scary Edition

A single-file 3D alien horror game that runs entirely in the browser. You are the last living thing aboard the salvage ship **USCSS Ymir**. Recover 5 power cells, unlock the escape bay, and get out before *it* finds you.

## ▶ Play

**https://jherney.github.io/derelict-alien-horror/**

No install, no build step. One HTML file. Headphones strongly recommended — half the game is positional audio.

## Screenshots

<!-- TODO: drop a gameplay screenshot or GIF here
![DERELICT gameplay](screenshots/gameplay.gif)
-->

_Coming soon — capture a hunt sequence or the stalker-at-the-end-of-the-corridor moment._

## Controls

| Input | Action |
| --- | --- |
| Mouse | Look (click once to enter pointer lock) |
| `W` `A` `S` `D` | Move |
| `Shift` | Sprint (drains stamina, very loud) |
| `F` | Toggle flashlight (the click can give you away) |
| `Esc` | Release pointer lock |

## Objective

1. Find **5 power cells** (glowing green) scattered through the ship.
2. Collecting cells is **loud** — it hears you.
3. The fifth cell unlocks the escape bay (door turns green) — and puts it on a permanent hunt.
4. Reach the door without being caught.

## The thing aboard

- **Patrols** the ship on real pathfinding and **hunts by sound** — sprinting, picking up cells, even flipping your flashlight switch makes noise.
- **Hears better when your lamp is on.** Darkness is cover; darkness is also where your dread climbs.
- **Watches.** Sometimes it stands motionless at the end of a corridor, eyes glinting — then is simply gone.
- If it spots you: screech, red klaxon light, and a chase you will probably lose.

## Scare systems

- Randomized horror event director — ship-wide blackouts, skittering that pans across your headphones, whispers, hull booms
- **Dread meter** — proximity, darkness, and hunts build it; high dread causes hallucinated shadow figures and heavier (louder) breathing
- Stamina system — exhausted breathing is audible to it
- Contextual heartbeat that accelerates as it closes in
- Positional audio for its clicking footsteps — you can hear which direction it's coming from
- Environmental storytelling: blood pools, crew remains, and graffiti left by whoever came before you

## Tech

- Plain **HTML/CSS/JS**, one file, no dependencies to install
- **[Three.js](https://threejs.org)** (via CDN) for rendering, fog, and shadow-mapped flashlight
- **WebAudio API** for 100% procedural sound — drone, heartbeat, screeches, whispers, footsteps. No audio files.
- BFS pathfinding on a tile grid for alien navigation
- Zero assets; geometry and textures (including the graffiti) are generated at runtime

## Deployment

Hosted free on **GitHub Pages**, auto-deployed on every push to `main` by the workflow in [`.github/workflows/pages.yml`](.github/workflows/pages.yml).

To run locally: just open `index.html` in a desktop browser (needs internet for the Three.js CDN).

## Tuning

Difficulty and scare density live in clearly-marked constants in `index.html`:

| Knob | Variable / line | Effect |
| --- | --- | --- |
| Scare frequency | `nextScareAt = now + 16000 + …` | Lower = more frequent horror events |
| Detection | `senses = 20 * player.noise + …` | How easily it notices you |
| Hunt speed | `alien.speed = 4.9` | Chase lethality |
| Fog density | `FogExp2(0x000000, 0.13)` | Visibility / claustrophobia |
| Stalker duration | `watchTimer = 1.8 + …` | How long it stands watching |

## License

MIT — do whatever you want with it.

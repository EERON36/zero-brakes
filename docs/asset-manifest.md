# Asset Manifest

This file is the **single source of truth** for every art and audio asset. The game's `ArtManifest.swift` (created on the Mac in M1) mirrors this table. If a size or anchor changes, update **both** and the related GitHub issue.

- Sizes are in **points (pt)**. @3x pixels = pt × 3. @2x is generated automatically by `tools/make_2x.sh`.
- **Anchor** is the pivot the game positions the sprite by, written as a fraction of the canvas: (0, 0) is bottom-left, (1, 1) is top-right.
- **Status:**
  - `placeholder`: the game draws a colored shape.
  - `wip`: art is in progress.
  - `done`: the real PNG is in the game and approved.
- Style rules: [art-style.md](art-style.md).

## M1: Playable prototype

### Hero (layered rig, shared 96 × 96 pt canvas)
Folder: `ZeroBrakes/Resources/Art/Hero.atlas/`

| Key | Canvas (pt) | @3x px | Anchor | Frames | Tintable | Notes | Issue | Status |
|---|---|---|---|---|---|---|---|---|
| `hero_chair_frame` | 96×96 | 288×288 | (0.5, 0.042) | 1 | no | Frame, seat, low back, suspension, grind bar, far rear wheel peeking out. **No** near rear wheel or caster. | #2 | placeholder |
| `hero_wheel_rear` | 40×40 | 120×120 | (0.5, 0.5) | 1 | no | Tire, spokes, **push rim**, hub. Perfect circle, spun by code. Placed at (38, 24) on the hero canvas. | #3 | placeholder |
| `hero_caster` | 12×12 | 36×36 | (0.5, 0.5) | 1 | no | Small front caster wheel, spun by code. Placed at (76, 10). | #3 | placeholder |
| `hero_rider_ride` | 96×96 | 288×288 | (0.5, 0.042) | 1 | no | Seated, leaning forward, hands on push rims. | #4 | placeholder |
| `hero_rider_air` | 96×96 | 288×288 | (0.5, 0.042) | 1 | no | Mid-air tuck, gripping the frame. | #4 | placeholder |
| `hero_rider_crash` | 96×96 | 288×288 | (0.5, 0.042) | 1 | no | Bracing for impact, strapped in, arms protecting his head. Tumbles together with the chair. | #4 | placeholder |
| `hero_rocket_pod` | 24×16 | 72×48 | (0.5, 0.5) | 1 | no | Placed at (22, 44). Nozzle faces left, at pod-local x = 0. | #5 | placeholder |

Hero canvas reference points (pt from bottom-left): ground line y = 4 · rear wheel center (38, 24) · caster center (76, 10) · rocket pod center (22, 44) · nozzle (10, 44).

Draw order (back to front): chair frame (includes the far wheel) → rider → near rear wheel → caster → rocket pod. The flame draws behind the pod.

### Effects
Folder: `ZeroBrakes/Resources/Art/FX.atlas/`

| Key | Canvas (pt) | @3x px | Anchor | Frames | Tintable | Notes | Issue | Status |
|---|---|---|---|---|---|---|---|---|
| `fx_flame_core_01…06` | 48×24 | 144×72 | (1.0, 0.5) | 6 (loop, 18 fps) | **no** (white-hot) | Attaches at the nozzle, extends left. | #5 | placeholder |
| `fx_flame_outer_01…06` | 48×24 | 144×72 | (1.0, 0.5) | 6 (loop, 18 fps) | **yes** (greyscale) | Drawn behind the core. Tinted to the unlocked flame color. | #5 | placeholder |
| `fx_spark` | 16×16 | 48×48 | (0.5, 0.5) | 1 | yes | Particle for crashes and grinds. | #9 | placeholder |
| `fx_smoke` | 32×32 | 96×96 | (0.5, 0.5) | 1 | yes | Rocket and crash smoke puff. | #9 | placeholder |
| `fx_dust` | 32×32 | 96×96 | (0.5, 0.5) | 1 | yes | Landing dust puff. | #9 | placeholder |

### Vehicles (facing left)
Folder: `ZeroBrakes/Resources/Art/Vehicles.atlas/`

| Key | Canvas (pt) | @3x px | Anchor | Frames | Hitbox inset (pt) | Roof height (pt) | Issue | Status |
|---|---|---|---|---|---|---|---|---|
| `veh_compact` | 120×56 | 360×168 | (0.5, 0.0) | 1 | 6 | 52 | #6 | placeholder |
| `veh_van` | 140×72 | 420×216 | (0.5, 0.0) | 1 | 6 | 68 | #6 | placeholder |

Roof height is the height of the flat part of the roof the hero can land on.

### Environment
Folder: `ZeroBrakes/Resources/Art/Environment/`

| Key | Canvas (pt) | @3x px | Anchor | Tiles | Notes | Issue | Status |
|---|---|---|---|---|---|---|---|
| `env_road` | 256×80 | 768×240 | (0, 0) | horizontal | Ride line (where tires touch) at y = 60 pt. | #7 | placeholder |
| `env_bg_far` | 1024×220 | 3072×660 | (0, 0) | horizontal | Skyline, no outlines, transparent sky. Scrolls at 10% speed. | #8 | placeholder |
| `env_bg_mid` | 1024×160 | 3072×480 | (0, 0) | horizontal | Buildings, streetlights, billboards, transparent sky. Scrolls at 35% speed. | #8 | placeholder |
| *(sky)* | — | — | — | — | Gradient drawn in code, no file. | — | code |

### UI
Folder: `ZeroBrakes/Resources/Art/UI.atlas/`

| Key | Canvas (pt) | @3x px | Anchor | Notes | Issue | Status |
|---|---|---|---|---|---|---|
| `ui_nitro_frame` | 160×24 | 480×72 | (0, 0.5) | Empty meter outline. | #10 | placeholder |
| `ui_nitro_fill` | 150×16 | 450×48 | (0, 0.5) | Full bar. Code crops it to the current nitro level. Sits 5 pt inside the frame. | #10 | placeholder |
| `ui_score_plate` | 180×44 | 540×132 | (0, 1) | Panel behind the score number (top-left of the screen). | #10 | placeholder |
| `ui_hint_tap` | 64×64 | 192×192 | (0.5, 0.5) | "Tap to jump" hint icon. | #10 | placeholder |
| `ui_hint_hold` | 64×64 | 192×192 | (0.5, 0.5) | "Hold for rockets" hint icon. | #10 | placeholder |

### Audio and font
| Key | File | Folder | Notes | Issue | Status |
|---|---|---|---|---|---|
| `sfx_jump` | `sfx_jump.caf` | `ZeroBrakes/Resources/Audio/sfx/` | 0.2–0.4 s | #11 | placeholder (silent) |
| `sfx_rocket_loop` | `sfx_rocket_loop.caf` | same | 1–2 s, seamless loop | #11 | placeholder (silent) |
| `sfx_land` | `sfx_land.caf` | same | 0.2–0.4 s | #11 | placeholder (silent) |
| `sfx_crash` | `sfx_crash.caf` | same | 0.8–1.5 s | #11 | placeholder (silent) |
| `sfx_nearmiss` | `sfx_nearmiss.caf` | same | 0.3–0.6 s whoosh | #11 | placeholder (silent) |
| `font_ui` | `.ttf` or `.otf` + `OFL.txt` | `ZeroBrakes/Resources/Fonts/` | Font under the SIL Open Font License | #11 | placeholder (system font) |

### Reference only (not bundled)
| Asset | Folder | Issue |
|---|---|---|
| Hero + chair concept sheet | `art-source/concepts/` | #1 |

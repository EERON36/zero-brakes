# Zero Brakes: Art Style Guide

Every visual asset in Zero Brakes follows this guide. Every art issue links here. If an issue and this guide disagree, the **issue wins for sizes and file names** and **this guide wins for look and feel**. Flag the conflict in the issue.

- **Game:** a one-thumb arcade game for iPhone and iPad, played in landscape. A daredevil in a WCMX-style sports wheelchair with side-mounted rockets jumps over oncoming city traffic.
- **Tone:** **badass, skilled, fearless, stylish.** Think action-sports poster, not comedy. The fun comes from over-the-top stunts, **never** from the character's disability.

---

## 1. Look in one sentence

> **Bold action-sports sticker art:** clean vector-style cartoon shapes, thick dark outlines, flat cel-shaded color (one shadow tone plus one highlight tone), set in a neon city at dusk.

### Mood keywords
Kinetic · confident · street · neon dusk · skate-video energy · sticker-bomb · clean silhouettes.

### Avoid
- Photorealism, painterly textures, soft airbrushed gradients on characters, 3D-render look
- Pixel art
- Grimy or gory violence
- Anything that reads as medical, fragile or pitiful (see §5)
- Real brand logos
- Real athletes' likenesses
- Anything referencing *Fast & Furious* or "NOS". Use generic words: **nitro, boost, rockets**.

---

## 2. Camera and perspective

- **Gameplay sprites are pure side view (profile).** The hero faces **right**. Traffic faces **left** (it drives toward the hero).
- Horizon and ground are perfectly horizontal. No tilt, no fisheye.
- **Light comes from the top-left.** Shadows fall down and to the right.
- **Showing the camber.** In profile the rear-wheel camber would be invisible, so we cheat slightly: the **far-side rear wheel peeks out** behind and slightly above the near wheel, angled so the "V" of the camber is readable. Menu and title art uses a **3/4 front view**, where the camber is clearly visible.

---

## 3. Palette

Use these colors as the base. Tints and shades in between are fine as long as they stay in the family.

| Swatch | Name | Hex | Use |
|---|---|---|---|
| ⬛ | Outline | `#14121A` | All outlines, darkest shadows |
| ⬛ | Asphalt | `#2A2A36` | Road surface, tires |
| 🟦 | Midnight | `#1B1F3B` | Upper sky, far background |
| 🟪 | Dusk purple | `#5B3A8C` | Sky, far buildings |
| 🟧 | Sunset orange | `#FF7A2F` | Horizon glow, hero accents |
| 🟥 | Hot magenta | `#FF3D7F` | Neon signs, hero accents |
| 🟦 | Nitro cyan | `#2EE6FF` | Nitro, rockets, UI highlights |
| 🟨 | Hazard yellow | `#FFD23F` | Hazards, warnings, coins (later) |
| ⬜ | Chrome | `#C9D1D9` | Chair metal, push rims, wheel hubs |
| ⬜ | Off-white | `#F4F1EA` | Highlights, text, lane markings |

### Color rules
- **The hero is always the most saturated thing on screen.** His palette is built from sunset orange, hot magenta, nitro cyan and chrome.
- **Traffic uses muted, desaturated colors**: dusty blue, faded teal, beige, grey-green, brick red at about 50–60% saturation. That way the hero always pops.
- **Backgrounds** get darker and lower-contrast the further back they are.

---

## 4. Line and shading

| Element | Outline thickness (in @3x pixels) | In points |
|---|---|---|
| Hero, chair, vehicles, pickups | **9 px** | 3 pt |
| Particles (smoke, dust) | 6 px | 2 pt |
| Mid background | 6 px | 2 pt |
| Far background | **none** (depth by color only) | — |
| UI panels | 6 px | 2 pt |

- Outline color is always `#14121A`, never pure black.
- **Shading:** flat base color, **one** shadow tone (bottom-right side, following the top-left light) and **one** highlight tone (small sharp shapes, top-left edges). No gradients on characters or vehicles.
- **Metal (chrome):** a hard white specular stripe, cartoon-style.
- **Glass (car windows):** dark blue-grey with one diagonal highlight stripe.

---

## 5. The hero and his chair

### Character
- **Who he is:** a WCMX (wheelchair motocross) daredevil. He's a pro athlete who is confident, focused and stylish.
- **Expression:** determined grin or focused stare, never scared or goofy.
- **Body:** heroic and athletic. Broad shoulders, **strong arms**, a slightly large head for readability at small sizes. Seated height is about **2.5 heads**.
- **Gear:** full-face or open-face helmet with visor, gloves, elbow and knee pads, a jacket or jersey in hero colors.
- **Customization later:** helmet, outfit, skin tone and hair must be easy to swap. Draw clean separable shapes. Don't let the helmet merge into the jacket.
- **Final look:** decided with our playtester, who uses a wheelchair himself. Hero art isn't final until he approves it (label `needs-friend-review`).

### The chair: a real WCMX / sports chair
**Must have:**
- **Rigid, low, compact frame** in chrome or painted tubing
- **Low backrest**, below shoulder-blade height
- **Strongly cambered rear wheels** (tilted inward at the top)
- **Push rims** on the rear wheels (the thinner ring just inside the tire)
- Small **front casters** close to the footrest
- **Rear suspension shocks**
- A **grind bar / anti-tip bar** at the back
- A **lap strap**
- **Two rocket pods** mounted on the sides of the frame behind the seat, with nozzles pointing backward

**Must NOT have:**
- A tall backrest
- Push handles
- Big armrests
- Hospital grey or beige
- Oxygen tanks, IV poles or anything clinical
- A bulky folding frame

**Mood reference (search terms, for inspiration only):** "WCMX chair", "adaptive skatepark", "sports wheelchair camber", "motocross gear". Don't copy any photo or athlete.

### Scale reference (all in points, the game's world units)
| Thing | Size |
|---|---|
| Hero sprite canvas | 96 × 96 pt |
| Hero + chair in ride pose (visible art) | about 80 wide × 70 tall |
| Rear wheel | 40 pt diameter |
| Front caster | 12 pt diameter |
| Compact car | 120 × 56 pt |
| Van | 140 × 72 pt |
| Screen (design-safe area) | 844 × 390 pt |

The hero is drawn at **"heroic scale"**, slightly larger than real life compared with cars (seated height about 1.2× a compact car's height). That keeps him readable.

---

## 6. Canvas, anchors and layers

The game code positions every sprite by its **canvas** and **anchor point**. That's how real art can replace the placeholder shapes without code changes, so these rules are strict.

1. **Exact canvas size.** Deliver exactly the pixel size in the issue. **Never trim or crop the transparent edges.** Empty space is intentional.
2. **Transparent background.** PNG-32 with alpha, sRGB, no background color, no drop-shadow baked onto transparency (unless the issue asks for it).
3. **Coordinates** in issues are in **points**, measured from the **bottom-left** of the canvas. Multiply by 3 for @3x pixels.
4. **Shared hero canvas.**
   - Every hero layer (chair frame, rider poses) uses the **same 96 × 96 pt canvas** with the same ground line and wheel positions.
   - Stacking the layers in an image editor must line them up perfectly.
   - Key reference points on the hero canvas, in points from the bottom-left:

   | Point | Position |
   |---|---|
   | Ground line (bottom of tires) | y = 4 |
   | Rear wheel center | (38, 24), 40 pt diameter |
   | Front caster center | (76, 10), 12 pt diameter |
   | Rocket pod center | (22, 44) |
   | Pod nozzle (rear end of pod) | (10, 44) |

5. **Wheels are separate sprites that the code spins.** They must be perfectly circular and centered on their canvas. The chair-frame layer must **not** include the near rear wheel or the caster. Leave those spots empty, but draw the axle hub mount, fork and frame.
6. **Vehicles:** tires touch the **bottom edge** of the canvas (anchor bottom-center). No empty space below the tires.
7. **Seamless tiles:** background and road tiles must repeat horizontally with no visible seam. The left and right edges must match pixel for pixel.

### Tintable assets
Some assets get their color from the code, so one drawing can produce many unlockable colors:
- **Rocket flames** are drawn in **white and light greyscale** in two layers:
  - **Core:** white-hot, never tinted.
  - **Outer:** greyscale, tinted by the code.
- **Particles** (smoke, dust, spark) are drawn in light greyscale or white.
- The issue says when an asset is tintable.

---

## 7. Export and naming

| Rule | Value |
|---|---|
| Format | PNG-32, transparent, sRGB |
| Master resolution | **@3x** (the pixel size given in each issue) |
| @2x | Generated automatically by `tools/make_2x.sh`. Only deliver @2x if the issue asks for it. |
| File names | `lowercase_snake_case`, **no spaces**, suffix `@3x` → `hero_chair_frame@3x.png` |
| Animation frames | Two-digit numbering → `fx_flame_core_01@3x.png` … `fx_flame_core_06@3x.png` |
| Prefixes | `hero_` hero layers · `veh_` vehicles · `env_` road and background · `fx_` effects · `ui_` interface · `sfx_` sounds |
| Where files go | The exact folder given in the issue (e.g. `ZeroBrakes/Resources/Art/Hero.atlas/`) |
| Raw or unused exports | `art-source/exports/<issue-number>/` (never bundled into the game) |

---

## 8. Backgrounds and environment

- **Setting:** a big neon city at dusk. Midnight blue at the top of the sky fades to sunset orange at the horizon. The sky gradient is drawn by code, so background layers need **transparent skies**.
- **Far layer:** skyline silhouettes in dusk purple and midnight. There are **no outlines**, a few tiny lit windows, and an occasional neon glow.
- **Mid layer:**
  - Closer buildings, streetlights, billboards (with made-up brands only) and graffiti-style shapes.
  - 2 pt outlines, more detail and higher contrast than the far layer, but still darker than the hero.
- **Road:**
  - Dark asphalt with off-white dashed lane markings and a curb.
  - The **ride line** (where tires touch) is **60 pt above the bottom of the road tile**.
- **Composition:** keep the **middle band of the screen** (where traffic and jumps happen) visually calm. Busy detail goes at the top and in the far layer.

---

## 9. UI style

- UI uses the same sticker language: chunky rounded panels, 2 pt outline, a slight offset drop-shadow (a solid `#14121A` shape shifted down-right).
- **Font:**
  - A bold, free font under the SIL Open Font License, such as *Bungee* or *Russo One*. It's chosen in the audio/font issue.
  - Numbers must be very readable.
- **Nitro meter:** nitro cyan, with an energetic, slightly glowing fill.
- **Icons:** simple, bold and readable at 32 pt.

---

## 10. Copy-paste style prompt for Astra

Paste this before the asset-specific description in each issue:

> Clean vector cartoon, bold action-sports sticker style, thick dark outlines (#14121A), flat cel shading with one shadow tone and one highlight tone, light from top-left, strict side-view profile, transparent background, no text, no logos. Palette: midnight #1B1F3B, dusk purple #5B3A8C, sunset orange #FF7A2F, hot magenta #FF3D7F, nitro cyan #2EE6FF, hazard yellow #FFD23F, chrome #C9D1D9, off-white #F4F1EA. Confident, stylish, kinetic mood.

For the hero, add:

> Athletic WCMX wheelchair daredevil, determined expression, helmet, gloves and pads, in a low rigid sports wheelchair with strongly cambered rear wheels, push rims, small front casters, rear suspension, grind bar, low backrest and two side-mounted rocket pods. Not a hospital chair.

---

## 11. Review checklist (every asset)

- [ ] Exact pixel size from the issue, transparent background, not trimmed
- [ ] Correct file name and folder
- [ ] Outline thickness and color match §4
- [ ] Colors from §3. The hero pops, traffic is muted.
- [ ] Side view, facing the correct direction, light from top-left
- [ ] Lines up with the shared canvas and anchor points (hero layers), or tiles seamlessly (backgrounds)
- [ ] Looks right **in-game on a real device** next to the other assets
- [ ] Hero and chair assets approved by our playtester (`needs-friend-review`)

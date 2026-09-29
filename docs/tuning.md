# Tuning Guide

Every number that changes how the game *feels* lives in **one file: `ZeroBrakes/Game/Tuning.swift`**. This guide explains each value in plain language and gives the **starting guess**. These are guesses. Playtesting will change them, and that's the point.

**Units:**
- Distances are in **points (pt)**. The screen is about 844 pt wide and 390 pt tall. The hero is about 70 pt tall.
- Speeds are in pt per second, times are in seconds.

## How to tune during a playtest
1. Triple-tap the **top-left corner** during a run to open the tuning panel. It's available in Xcode and TestFlight builds only.
2. Drag the sliders. Changes apply immediately.
3. When something feels great, tap **Copy values**. Paste the result into `docs/playtests/<date>.md`, and later into `Tuning.swift`.
4. **Reset** returns to the values in `Tuning.swift`.

Tip: change **one thing at a time** and play 3 runs before judging.

---

## Screen layout
| Value | Start | What it does |
|---|---|---|
| `designWidth` / `designHeight` | 844 / 390 | The area guaranteed to be visible on every device. |
| `heroScreenX` | 0.25 | How far from the left edge the hero sits (0 = left edge, 1 = right edge). Lower means more warning time. |
| `groundY` | 60 | Height of the road's ride line above the bottom of the screen. |

## Speed and difficulty
| Value | Start | What it does |
|---|---|---|
| `startSpeed` | 300 | How fast the world scrolls at the start of a run. |
| `maxSpeed` | 650 | Top cruising speed, not counting rockets. |
| `speedRampSeconds` | 90 | How long it takes to reach `maxSpeed`. Lower means it gets hard faster. |
| `trafficSpeedMin` / `Max` | 60 / 140 | Extra speed of oncoming cars on top of the world speed. Higher makes cars rush at you. |
| `spawnGapStart` | 1.6 | Seconds between vehicles at the start. |
| `spawnGapEnd` | 0.8 | Seconds between vehicles at full difficulty. |
| `spawnGapRandomness` | 0.35 | How uneven the gaps are (0 = perfectly regular, 1 = very random). |
| `vanChanceStart` / `End` | 0.2 / 0.5 | Chance that a vehicle is a van (taller) instead of a compact car, early vs late in a run. |
| `fairnessMargin` | 1.15 | Safety factor for the fairness rule. The spawner never places a gap smaller than the hero's jump reach × this. |

## Jump
| Value | Start | What it does |
|---|---|---|
| `jumpVelocity` | 760 | Upward launch speed. Higher means a higher jump. Max height ≈ jumpVelocity² ÷ (2 × gravityUp) ≈ 131 pt. |
| `gravityUp` | 2200 | Gravity while rising. Lower means a floatier rise. |
| `gravityDown` | 3200 | Gravity while falling. Keep it higher than `gravityUp` for a snappy arc. |
| `maxFallSpeed` | 1400 | Speed cap when falling. |
| `minJumpTime` | 0.08 | Even the quickest tap jumps at least this long, so a tap always clears a compact car. |
| `jumpCutMultiplier` | 0.5 | Releasing early multiplies the upward speed by this. Lower means a bigger difference between a tap and a hold. |
| `coyoteTime` | 0.08 | Grace period to still jump just after leaving the ground or a roof. |
| `jumpBuffer` | 0.12 | A tap this soon before landing is remembered and jumps on touchdown. |

## Rockets and nitro
| Value | Start | What it does |
|---|---|---|
| `nitroMax` | 100 | Size of the nitro tank. |
| `nitroDrainPerSecond` | 45 | How fast rockets burn nitro (100 ÷ 45 ≈ 2.2 s of full rockets). |
| `nitroRefillPerSecond` | 10 | Automatic refill (M1 only; stunts refill it from M2). |
| `rocketMinNitro` | 10 | Rockets won't start below this, so they don't sputter. |
| `rocketsStartAtApex` | true | One-Touch scheme: rockets only fire when you're still holding **after** the top of the jump. |
| `rocketLift` | 2600 | Upward push in the air. Close to `gravityDown` means a long glide, higher means you climb. |
| `rocketForwardBoost` | 150 | Extra scroll speed while rockets fire (longer jumps, more score). |
| `rocketBoostEase` | 0.25 | Seconds to ramp the boost on and off, so it feels smooth. |

## Collisions and landings
| Value | Start | What it does |
|---|---|---|
| `heroHitboxInset` | 8 | Hero's crash box is this much smaller than the art on each side. Higher is more forgiving. |
| `vehicleHitboxInset` | 6 | The same, for vehicles. |
| `roofLandingTolerance` | 14 | If the wheels are within this distance of a roof top while falling, it counts as a landing, not a crash. |

## Crash and restart
| Value | Start | What it does |
|---|---|---|
| `crashSlowMoScale` | 0.3 | Game speed during the crash slow-motion (1 = normal). |
| `crashSlowMoDuration` | 0.5 | How long the slow-mo lasts. |
| `retryDelay` | 0.6 | Seconds after a crash before "Tap to retry" accepts a tap, so you don't restart by accident. |

## Score
| Value | Start | What it does |
|---|---|---|
| `unitsPerMeter` | 50 | Converts scroll distance into meters for the score. |
| `pointsPerMeter` | 1 | Distance points. |
| `clearPointsCompact` / `Van` | 50 / 75 | Points for jumping over each vehicle type. |

## Controls
| Value | Start | What it does |
|---|---|---|
| `controlScheme` | `.oneTouch` | `.oneTouch`: tap = jump, hold = rockets. `.split`: tap anywhere = jump, hold the bottom-right button = rockets. |
| `boostButtonSize` | 96 | Size of the Split scheme's boost button. |
| `leftHanded` | false | Mirrors the boost button to the bottom-left. |

## Feedback
| Value | Start | What it does |
|---|---|---|
| `hapticsEnabled` | true | Vibration on jump, land and crash. |
| `screenShakeAmount` | 1.0 | 0 turns screen shake off. |

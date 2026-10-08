# enemy_20 — The Last Hour (Boss · Time manipulator)

Category: **Enemy** · Resistance: Temporal · Element accent: **Temporal** · Canvas 1024×1024

> **Rules that apply to every asset**
>
> - No text, logo, trademark, or watermark anywhere in the image (including on banners, books, signs, or UI mockups).
> - Twin Flank originality boundary: every asset is an original Twin Flank design. Do not reference, imitate, trace, or style-transfer characters, creatures, castles, UI, logos, or trade dress from any existing game or franchise (merge / tower-defense titles included). Names, silhouettes, colour combinations and emblem shapes must not be recognisable as another property. If a generated image resembles a known character, reject it and regenerate.
> - Deliver PNG-24 with straight (non-premultiplied) alpha at exactly the canvas size listed. Drop the file at the path listed; Unity applies the import preset automatically (`Twin Flank → Art Pipeline → Reimport All Sprites` if it was open).
> - Until the painted file exists the game renders a **PLACEHOLDER** (dashed border + id text). Placeholders never count as coverage.

## Identity (bible 12 — Enemies and bosses)
| Field | Value |
|-------|-------|
| id | `enemy_20` |
| name | The Last Hour |
| category | Boss |
| role | Time manipulator |
| base HP / speed | 10500 / 0.40 |
| resistance | Temporal |
| reward | Celestial vault |
| path behavior | Rewinds progress, accelerates adds, and locks one merge tier. |
| telegraph / counterplay | Telegraph: Clock face counts down visibly. Counterplay: Burst during stopped-clock phase. |
| Animation | hourglass orbit, time stop, reverse |
| VFX and sound | clock strike and reversed audio |

## Asset contract
| Key | File | Canvas | PPU | Pivot | Max | Atlas | Border |
|-----|------|--------|-----|-------|-----|-------|--------|
| `enemy_20` | `Enemies/enemy_20.png` | 1024×1024 | 128 | (0.5, 0.12) | 1024 | Atlas_Enemies | — |
| `enemy_20_p2` | `Enemies/enemy_20_p2.png` | 1024×1024 | 128 | (0.5, 0.12) | 1024 | Atlas_Enemies | — |

- Enemies travel camera-left → gate; paint the forward lean toward **camera-left**. Feet on the pivot line.
- Regular 512, Special 512, Mini-boss 768, Boss 1024 canvas — scale in scene is set by code, texel density is what changes.
- Role must be readable from silhouette alone (time manipulator): e.g. runner = long legs + lean, tank = mass low, healer = raised staff, splitter = seams.

## Boss phase variants
| File | Phase | Visual change |
|------|-------|---------------|
| `enemy_20.png` | p1 | Base — as concept prompt |
| `enemy_20_p2.png` | p2 | Stopped clock — hourglass frozen, colour desaturated, single gold highlight |

All phases share footprint, scale and pivot so the swap never pops. Telegraph: Telegraph: Clock face counts down visibly. Counterplay: Burst during stopped-clock phase.

## Palette tokens
| Token | Hex | Use |
|-------|-----|-----|
| `element.temporal` | `#D9B85C` | Temporal — antique brass gold |
| `ui.ink` | `#1F242E` | Outline ink (3-4 px at display size) |
| `world.stone_cool` | `#7C8598` | Cool ambient-shadow stone |
| `ui.danger` | `#E04B3A` | Gate damage, leak, destructive actions |

## Silhouette & material
- Silhouette: Forward-heavy wedge silhouette (bible 08), leaning toward travel direction (camera-left). Meaner than heroes; feet on pivot line.
- Material: Hide, bone, rusted iron, slime, root, crystal — painted with grime; ink outline 3-4 px.
- Enemies are "slightly meaner" than heroes for contrast — sharper angles, lower brows, grime — but still storybook, never gore.

## Animation states the sprite must support
- walk (forward lean)
- telegraph (pre-ability)
- ability_1: hourglass orbit
- ability_2: time stop
- ability_3: reverse
- hit_flash
- death
- phase_transition

## VFX ids referenced
- `vfx_common_shadow_blob`
- `vfx_temporal_impact`
- `vfx_common_boss_telegraph`
- `vfx_common_leak_line`

## Original concept prompt (verbatim from the bible)
```text
Original Twin Flank boss enemy named The Last Hour: visually communicate time manipulator, rewinds progress, accelerates adds, and locks one merge tier., clock strike and reversed audio; premium stylized mobile tower-defense creature, full-body navy studio, clear silhouette, no text, logo, trademark, or watermark.
```

## Approval checklist (bible consistency gate)
- [ ] **palette** — Uses only listed palette tokens (+ neutral shading); element colour appears as rim/accent, not full fill.
- [ ] **silhouette** — Reads at 96 px tall on phone against the moss road; shape language matches category rule.
- [ ] **material** — Hand-painted stone / wood / cloth / brass / crystal / foliage; no flat prototype fills or vector gradients.
- [ ] **scale** — Subject fills the specified fraction of the canvas; consistent with siblings (tiers, phases, states).
- [ ] **pivot** — Feet / base sit on the pivot line given in the contract; no floating shadow offset.
- [ ] **animation** — Pose is a neutral idle that the listed animation states can be derived from; no baked motion blur.
- [ ] **vfx** — No baked-in particles or glow except the listed 'rim' allowance; VFX come from the vfx_* sheets.
- [ ] **mobile_readability** — Passes at 50% scale with 3-4 px ink outline; no detail thinner than 2 px at 512.

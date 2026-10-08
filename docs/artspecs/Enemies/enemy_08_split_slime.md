# enemy_08 — Split Slime (Regular · Splitter)

Category: **Enemy** · Resistance: None · Element accent: **Toxin** · Canvas 512×512

> **Rules that apply to every asset**
>
> - No text, logo, trademark, or watermark anywhere in the image (including on banners, books, signs, or UI mockups).
> - Twin Flank originality boundary: every asset is an original Twin Flank design. Do not reference, imitate, trace, or style-transfer characters, creatures, castles, UI, logos, or trade dress from any existing game or franchise (merge / tower-defense titles included). Names, silhouettes, colour combinations and emblem shapes must not be recognisable as another property. If a generated image resembles a known character, reject it and regenerate.
> - Deliver PNG-24 with straight (non-premultiplied) alpha at exactly the canvas size listed. Drop the file at the path listed; Unity applies the import preset automatically (`Twin Flank → Art Pipeline → Reimport All Sprites` if it was open).
> - Until the painted file exists the game renders a **PLACEHOLDER** (dashed border + id text). Placeholders never count as coverage.

## Identity (bible 12 — Enemies and bosses)
| Field | Value |
|-------|-------|
| id | `enemy_08` |
| name | Split Slime |
| category | Regular |
| role | Splitter |
| base HP / speed | 150 / 0.75 |
| resistance | None |
| reward | 2 coins |
| path behavior | Splits into two fast slimes at half HP. |
| telegraph / counterplay | Telegraph: Body stretches sideways. Counterplay: Overkill, splash, road zones. |
| Animation | squash hop and split |
| VFX and sound | wet pop and droplets |

## Asset contract
| Key | File | Canvas | PPU | Pivot | Max | Atlas | Border |
|-----|------|--------|-----|-------|-----|-------|--------|
| `enemy_08` | `Enemies/enemy_08.png` | 512×512 | 128 | (0.5, 0.12) | 1024 | Atlas_Enemies | — |

- Enemies travel camera-left → gate; paint the forward lean toward **camera-left**. Feet on the pivot line.
- Regular 512, Special 512, Mini-boss 768, Boss 1024 canvas — scale in scene is set by code, texel density is what changes.
- Role must be readable from silhouette alone (splitter): e.g. runner = long legs + lean, tank = mass low, healer = raised staff, splitter = seams.

## Palette tokens
| Token | Hex | Use |
|-------|-----|-----|
| `element.toxin` | `#86D13A` | Toxin — acid lime |
| `ui.ink` | `#1F242E` | Outline ink (3-4 px at display size) |
| `world.stone_cool` | `#7C8598` | Cool ambient-shadow stone |

## Silhouette & material
- Silhouette: Forward-heavy wedge silhouette (bible 08), leaning toward travel direction (camera-left). Meaner than heroes; feet on pivot line.
- Material: Hide, bone, rusted iron, slime, root, crystal — painted with grime; ink outline 3-4 px.
- Enemies are "slightly meaner" than heroes for contrast — sharper angles, lower brows, grime — but still storybook, never gore.

## Animation states the sprite must support
- walk (forward lean)
- telegraph (pre-ability)
- ability_1: squash hop
- ability_2: split
- hit_flash
- death

## VFX ids referenced
- `vfx_common_shadow_blob`
- `vfx_toxin_impact`
- `vfx_common_leak_line`

## Original concept prompt (verbatim from the bible)
```text
Original Twin Flank regular enemy named Split Slime: visually communicate splitter, splits into two fast slimes at half hp., wet pop and droplets; premium stylized mobile tower-defense creature, full-body navy studio, clear silhouette, no text, logo, trademark, or watermark.
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

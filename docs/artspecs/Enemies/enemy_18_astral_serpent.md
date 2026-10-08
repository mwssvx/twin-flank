# enemy_18 — Astral Serpent (Boss · Target chaos)

Category: **Enemy** · Resistance: Arcane phases · Element accent: **Arcane** · Canvas 1024×1024

> **Rules that apply to every asset**
>
> - No text, logo, trademark, or watermark anywhere in the image (including on banners, books, signs, or UI mockups).
> - Twin Flank originality boundary: every asset is an original Twin Flank design. Do not reference, imitate, trace, or style-transfer characters, creatures, castles, UI, logos, or trade dress from any existing game or franchise (merge / tower-defense titles included). Names, silhouettes, colour combinations and emblem shapes must not be recognisable as another property. If a generated image resembles a known character, reject it and regenerate.
> - Deliver PNG-24 with straight (non-premultiplied) alpha at exactly the canvas size listed. Drop the file at the path listed; Unity applies the import preset automatically (`Twin Flank → Art Pipeline → Reimport All Sprites` if it was open).
> - Until the painted file exists the game renders a **PLACEHOLDER** (dashed border + id text). Placeholders never count as coverage.

## Identity (bible 12 — Enemies and bosses)
| Field | Value |
|-------|-------|
| id | `enemy_18` |
| name | Astral Serpent |
| category | Boss |
| role | Target chaos |
| base HP / speed | 8800 / 0.48 |
| resistance | Arcane phases |
| reward | Boss vault |
| path behavior | Reverses target priority and creates decoy eyes. |
| telegraph / counterplay | Telegraph: Sky darkens and eyes open. Counterplay: Manual ability timing and area damage. |
| Animation | coil, eye bloom, star dive |
| VFX and sound | cosmic hum and prism burst |

## Asset contract
| Key | File | Canvas | PPU | Pivot | Max | Atlas | Border |
|-----|------|--------|-----|-------|-----|-------|--------|
| `enemy_18` | `Enemies/enemy_18.png` | 1024×1024 | 128 | (0.5, 0.12) | 1024 | Atlas_Enemies | — |
| `enemy_18_p2` | `Enemies/enemy_18_p2.png` | 1024×1024 | 128 | (0.5, 0.12) | 1024 | Atlas_Enemies | — |

- Enemies travel camera-left → gate; paint the forward lean toward **camera-left**. Feet on the pivot line.
- Regular 512, Special 512, Mini-boss 768, Boss 1024 canvas — scale in scene is set by code, texel density is what changes.
- Role must be readable from silhouette alone (target chaos): e.g. runner = long legs + lean, tank = mass low, healer = raised staff, splitter = seams.

## Boss phase variants
| File | Phase | Visual change |
|------|-------|---------------|
| `enemy_18.png` | p1 | Base — as concept prompt |
| `enemy_18_p2.png` | p2 | Eyes open — decoy eyes bloom along the coils, sky-dark palette shift |

All phases share footprint, scale and pivot so the swap never pops. Telegraph: Telegraph: Sky darkens and eyes open. Counterplay: Manual ability timing and area damage.

## Palette tokens
| Token | Hex | Use |
|-------|-----|-----|
| `element.arcane` | `#C48BFF` | Arcane — prism lilac |
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
- ability_1: coil
- ability_2: eye bloom
- ability_3: star dive
- hit_flash
- death
- phase_transition

## VFX ids referenced
- `vfx_common_shadow_blob`
- `vfx_arcane_impact`
- `vfx_common_boss_telegraph`
- `vfx_common_leak_line`

## Original concept prompt (verbatim from the bible)
```text
Original Twin Flank boss enemy named Astral Serpent: visually communicate target chaos, reverses target priority and creates decoy eyes., cosmic hum and prism burst; premium stylized mobile tower-defense creature, full-body navy studio, clear silhouette, no text, logo, trademark, or watermark.
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

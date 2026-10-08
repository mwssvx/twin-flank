# VFX Sheets — Twin Flank

Category: **VFX** · 80 assets (14 schools × 5 types + 10 common) · Folder `Resources/Art/Sprites/VFX/` · Atlas `Atlas_VFX`

> **Rules that apply to every asset**
>
> - No text, logo, trademark, or watermark anywhere in the image (including on banners, books, signs, or UI mockups).
> - Twin Flank originality boundary: every asset is an original Twin Flank design. Do not reference, imitate, trace, or style-transfer characters, creatures, castles, UI, logos, or trade dress from any existing game or franchise (merge / tower-defense titles included). Names, silhouettes, colour combinations and emblem shapes must not be recognisable as another property. If a generated image resembles a known character, reject it and regenerate.
> - Deliver PNG-24 with straight (non-premultiplied) alpha at exactly the canvas size listed. Drop the file at the path listed; Unity applies the import preset automatically (`Twin Flank → Art Pipeline → Reimport All Sprites` if it was open).
> - Until the painted file exists the game renders a **PLACEHOLDER** (dashed border + id text). Placeholders never count as coverage.

## Art direction (bible 08)
- VFX: Element colors identify mechanics; white core at high energy; silhouettes remain visible.
- Lighting: Warm key light, cool ambient shadows, element rim only during abilities.

## Feedback stack (bible 07 — information before spectacle)
| Event | Visual | Audio | Haptic | Priority |
|-------|--------|-------|--------|----------|
| Summon | Pedestal rune -> portal -> silhouette -> settle | rising crystal chord | light pulse | Medium |
| Merge | Partner highlight -> pull -> compression -> tier reveal | two-tone combine and resolve | medium double | High |
| Normal hit | small flash and damage tick | concurrency-limited impact | none | Low |
| Critical | distinct shape, color, number treatment | sharp accent | light | Medium |
| Status | small icon plus restrained body effect | start only | none | Medium |
| Boss cast | road or pedestal telegraph before effect | unique warning motif | warning pulse | Critical |
| Leak | enemy-to-gate line, gate damage, source label | gate impact | heavy | Critical |
| Reward | resource flies to HUD and total changes | short positive tick | light | Medium |

VFX budget: At most 2 critical, 6 medium, and 18 low-priority transient effects visible. Cull off-camera particles, pool all emitters, cap transparent overdraw, and provide reduced-flash plus reduced-shake modes.

## Per-school atlas: one sheet per (school × type)
| Type | Canvas | Pivot | Contract |
|------|--------|-------|----------|
| `projectile` | 256×128 | (0.5, 0.5) | Projectile body pointing +X; element colour body, white core; 2-3 frames side by side optional. |
| `trail` | 256×64 | (0.0, 0.5) | Ribbon trail, tail at left (pivot), head at right; fades to 0 alpha at tail. |
| `impact` | 256×256 | (0.5, 0.5) | Normal-hit impact flash: small burst + 4-6 sparks; must read at 40 px. |
| `zone` | 512×256 | (0.5, 0.5) | Road-zone footprint (ellipse, top-down 3/4) for ignite / slow / poison / root zones. |
| `status` | 128×128 | (0.5, 0.5) | Status icon glyph on element-tinted disc; 2 px ink outline; used by StatusIconPool. |

| School | Token | Hex | Keys |
|--------|-------|-----|------|
| Physical | `element.physical` | `#C9CDD6` | `vfx_physical_projectile` … `vfx_physical_status` |
| Fire | `element.fire` | `#FF6A2A` | `vfx_fire_projectile` … `vfx_fire_status` |
| Frost | `element.frost` | `#8FD8FF` | `vfx_frost_projectile` … `vfx_frost_status` |
| Storm | `element.storm` | `#6FA8FF` | `vfx_storm_projectile` … `vfx_storm_status` |
| Earth | `element.earth` | `#8B7A4E` | `vfx_earth_projectile` … `vfx_earth_status` |
| Nature | `element.nature` | `#63C24F` | `vfx_nature_projectile` … `vfx_nature_status` |
| Water | `element.water` | `#3FA9E8` | `vfx_water_projectile` … `vfx_water_status` |
| Radiant | `element.radiant` | `#FFD86A` | `vfx_radiant_projectile` … `vfx_radiant_status` |
| Shadow | `element.shadow` | `#6A3F9E` | `vfx_shadow_projectile` … `vfx_shadow_status` |
| Void | `element.void` | `#B26BFF` | `vfx_void_projectile` … `vfx_void_status` |
| Arcane | `element.arcane` | `#C48BFF` | `vfx_arcane_projectile` … `vfx_arcane_status` |
| Toxin | `element.toxin` | `#86D13A` | `vfx_toxin_projectile` … `vfx_toxin_status` |
| Temporal | `element.temporal` | `#D9B85C` | `vfx_temporal_projectile` … `vfx_temporal_status` |
| Spirit | `element.spirit` | `#B7F0E8` | `vfx_spirit_projectile` … `vfx_spirit_status` |

Optional frame sequences: lay frames left → right at equal width inside the canvas (e.g. 4 × 64 px inside 256); note the frame count in the delivery message. Single-frame delivery is accepted.

## Common event VFX
| Key | File | Canvas | PPU | Pivot | Max | Atlas | Border |
|-----|------|--------|-----|-------|-----|-------|--------|
| `vfx_common_summon_rune` | `VFX/vfx_common_summon_rune.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_VFX | — |
| `vfx_common_summon_portal` | `VFX/vfx_common_summon_portal.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_VFX | — |
| `vfx_common_merge_pull` | `VFX/vfx_common_merge_pull.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_VFX | — |
| `vfx_common_merge_reveal` | `VFX/vfx_common_merge_reveal.png` | 512×512 | 128 | (0.5, 0.5) | 512 | Atlas_VFX | — |
| `vfx_common_crit_burst` | `VFX/vfx_common_crit_burst.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_VFX | — |
| `vfx_common_boss_telegraph` | `VFX/vfx_common_boss_telegraph.png` | 512×256 | 128 | (0.5, 0.5) | 512 | Atlas_VFX | — |
| `vfx_common_leak_line` | `VFX/vfx_common_leak_line.png` | 512×64 | 128 | (0.5, 0.5) | 512 | Atlas_VFX | — |
| `vfx_common_gate_impact` | `VFX/vfx_common_gate_impact.png` | 512×512 | 128 | (0.5, 0.5) | 512 | Atlas_VFX | — |
| `vfx_common_reward_fly` | `VFX/vfx_common_reward_fly.png` | 128×128 | 128 | (0.5, 0.5) | 512 | Atlas_VFX | — |
| `vfx_common_shadow_blob` | `VFX/vfx_common_shadow_blob.png` | 256×128 | 128 | (0.5, 0.5) | 512 | Atlas_VFX | — |

- `vfx_common_summon_rune` — Pedestal rune ring — first beat of Summon (rune → portal → silhouette → settle). Palette: `ui.cyan_crystal`, `ui.gold_trim`
- `vfx_common_summon_portal` — Portal disc that the hero silhouette rises through. Palette: `ui.cyan_crystal`, `vfx.white_core`
- `vfx_common_merge_pull` — Partner highlight + pull streaks toward the merge target. Palette: `ui.gold_trim`, `vfx.white_core`
- `vfx_common_merge_reveal` — Tier-reveal burst: compressed ring + gold rays; scale overshoot lives in code, not the sprite. Palette: `ui.gold_trim`, `vfx.white_core`
- `vfx_common_crit_burst` — Critical hit: distinct spiked shape (not a bigger normal hit). Palette: `vfx.white_core`, `ui.gold_trim`
- `vfx_common_boss_telegraph` — Road / pedestal telegraph footprint with warning motif (chevrons), shown before boss effect. Palette: `ui.danger`, `ui.cream`
- `vfx_common_leak_line` — Enemy-to-gate line for Leak event; dashed energy ribbon. Palette: `ui.danger`, `vfx.white_core`
- `vfx_common_gate_impact` — Gate damage crack flash + crystal shards. Palette: `ui.danger`, `world.crystal_gate`
- `vfx_common_reward_fly` — Coin / gem mote that flies to the HUD. Palette: `ui.gold_trim`, `ui.cyan_crystal`
- `vfx_common_shadow_blob` — Soft ground shadow ellipse under units (replaces PlaceholderArt circle). Palette: `ui.ink`

## Prompt template
```text
Twin Flank <school> <type> VFX sprite: <contract>. Element colour <hex> with white core at high energy, soft painted edges, transparent background, no text, logo, trademark, or watermark.
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

# hero_14 — Iron Standard (Epic Team support)

Category: **Hero** · Fantasy: Banner commander · Damage school: **Physical** · Targeting: First / 2 targets

> **Rules that apply to every asset**
>
> - No text, logo, trademark, or watermark anywhere in the image (including on banners, books, signs, or UI mockups).
> - Twin Flank originality boundary: every asset is an original Twin Flank design. Do not reference, imitate, trace, or style-transfer characters, creatures, castles, UI, logos, or trade dress from any existing game or franchise (merge / tower-defense titles included). Names, silhouettes, colour combinations and emblem shapes must not be recognisable as another property. If a generated image resembles a known character, reject it and regenerate.
> - Deliver PNG-24 with straight (non-premultiplied) alpha at exactly the canvas size listed. Drop the file at the path listed; Unity applies the import preset automatically (`Twin Flank → Art Pipeline → Reimport All Sprites` if it was open).
> - Until the painted file exists the game renders a **PLACEHOLDER** (dashed border + id text). Placeholders never count as coverage.

## Identity (bible 10 — Hero roster)
| Field | Value |
|-------|-------|
| id | `hero_14` |
| name | Iron Standard |
| rarity | Epic |
| role | Team support |
| special | Rally Line: Buffs the two nearest heroes and grants temporary attack speed after a merge. |
| Visual | green banner cape, halberd, bronze plate. |
| Animation | banner plant, command point, halberd jab. |
| VFX and sound | drum hit, gold rings, cloth snap. |

## Asset contract
| Key | File | Canvas | PPU | Pivot | Max | Atlas | Border |
|-----|------|--------|-----|-------|-----|-------|--------|
| `hero_14_portrait` | `Heroes/hero_14_portrait.png` | 512×512 | 128 | (0.5, 0.5) | 512 | Atlas_Portraits | — |
| `hero_14_t1` | `Heroes/hero_14_t1.png` | 512×512 | 128 | (0.5, 0.12) | 512 | Atlas_Heroes | — |
| `hero_14_t2` | `Heroes/hero_14_t2.png` | 512×512 | 128 | (0.5, 0.12) | 512 | Atlas_Heroes | — |
| `hero_14_t3` | `Heroes/hero_14_t3.png` | 512×512 | 128 | (0.5, 0.12) | 512 | Atlas_Heroes | — |
| `hero_14_t4` | `Heroes/hero_14_t4.png` | 512×512 | 128 | (0.5, 0.12) | 512 | Atlas_Heroes | — |
| `hero_14_t5` | `Heroes/hero_14_t5.png` | 512×512 | 128 | (0.5, 0.12) | 512 | Atlas_Heroes | — |
| `skill_hero_14` | `UI/skill_hero_14.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |

- Compression: high quality (ASTC 6×6 on iOS / ETC2 on Android via Unity "Compressed" + quality high); mipmaps **off**; filter bilinear; alpha is transparency.
- Battle sprites: feet on the pivot line (12 % from bottom); subject centred horizontally; facing camera-right 3/4; soft ground shadow is **not** baked (uses `vfx_common_shadow_blob`).
- Portrait: bust crop of the T3 look, gold arch framing on navy, centred pivot.
- Skill icon: emblem of *Rally Line* on a navy plate with physical colour and gold rim.

## Tier progression (T1 → T5 must read as one character growing)
| Tier | Title | Rule |
|------|-------|------|
| T1 | T1 — base | Base outfit, signature prop, no glow. Subject height ≈ 70% of canvas. |
| T2 | T2 — trim | Add one metal/crystal trim piece (bracer, pauldron, charm). Height ≈ 75%. |
| T3 | T3 — rim | Element rim light on prop + eyes; second accessory. Height ≈ 80%. |
| T4 | T4 — mantle | Cape / mantle / aura shape extends silhouette; richer prop. Height ≈ 86%. |
| T5 | T5 — ascended | Full evolution: element crown motif, white-core highlights on prop, gold detailing. Height ≈ 92%. |

## Palette tokens
| Token | Hex | Use |
|-------|-----|-----|
| `element.physical` | `#C9CDD6` | Physical — steel grey, dust |
| `rarity.epic` | `#B76BFF` | Epic |
| `ui.ink` | `#1F242E` | Outline ink (3-4 px at display size) |
| `ui.navy_panel` | `#141C33` | Deep navy panel base |
| `ui.gold_trim` | `#E3B44A` | Warm gold trim, primary CTA fill |

Element colour is used for rim light and ability details only; base materials stay in the hand-painted cloth / brass / crystal range.

## Silhouette & material
- Silhouette: Compact triangle + circle silhouette (bible 08). Full body, neutral idle, facing camera-right 3/4. Feet on pivot line.
- Material: Hand-painted cloth, brass, crystal, foliage; 3-4 px ink outline; element rim light only where the ability lives.
- Lighting: warm key light upper-left, cool ambient shadows, element rim only during abilities (bible 08).

## Animation states the sprite must support
- idle_personality (no constant bounce)
- attack_1: banner plant
- attack_2: command point
- attack_3: halberd jab
- merge_reveal
- summon_settle
- hit_flash

Animation is a code-driven timeline (anticipation → event → recovery); the painted asset is a neutral idle that these poses are derived from. Attack event aligns to simulation impact or projectile spawn.

## VFX ids referenced
- `vfx_physical_projectile`
- `vfx_physical_trail`
- `vfx_physical_impact`
- `vfx_common_summon_rune`
- `vfx_common_summon_portal`
- `vfx_common_merge_reveal`

## Original concept prompt (verbatim from the bible)
```text
Premium Twin Flank character concept: green banner cape, halberd, bronze plate; banner commander; team support; full-body neutral hero pose; readable mobile silhouette; hand-painted stylized 3D-like 2D; navy studio backdrop; gold framing; no text, logo, trademark, or watermark.
```

Tier variants: append to the prompt — "Base outfit, signature prop, no glow. Subject height ≈ 70% of canvas." for T1 … "Full evolution: element crown motif, white-core highlights on prop, gold detailing. Height ≈ 92%." for T5. Portrait: append "bust portrait crop, gold arch frame".

## Approval checklist (bible consistency gate)
- [ ] **palette** — Uses only listed palette tokens (+ neutral shading); element colour appears as rim/accent, not full fill.
- [ ] **silhouette** — Reads at 96 px tall on phone against the moss road; shape language matches category rule.
- [ ] **material** — Hand-painted stone / wood / cloth / brass / crystal / foliage; no flat prototype fills or vector gradients.
- [ ] **scale** — Subject fills the specified fraction of the canvas; consistent with siblings (tiers, phases, states).
- [ ] **pivot** — Feet / base sit on the pivot line given in the contract; no floating shadow offset.
- [ ] **animation** — Pose is a neutral idle that the listed animation states can be derived from; no baked motion blur.
- [ ] **vfx** — No baked-in particles or glow except the listed 'rim' allowance; VFX come from the vfx_* sheets.
- [ ] **mobile_readability** — Passes at 50% scale with 3-4 px ink outline; no detail thinner than 2 px at 512.

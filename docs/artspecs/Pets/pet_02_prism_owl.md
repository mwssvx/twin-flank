# pet_02 — Prism Owl (Legendary pet · Summon planning)

Category: **Tactical pet** · Species: Crystal owl · Personality: Calm · Element accent: **Arcane** (derived from species/role)

> **Rules that apply to every asset**
>
> - No text, logo, trademark, or watermark anywhere in the image (including on banners, books, signs, or UI mockups).
> - Twin Flank originality boundary: every asset is an original Twin Flank design. Do not reference, imitate, trace, or style-transfer characters, creatures, castles, UI, logos, or trade dress from any existing game or franchise (merge / tower-defense titles included). Names, silhouettes, colour combinations and emblem shapes must not be recognisable as another property. If a generated image resembles a known character, reject it and regenerate.
> - Deliver PNG-24 with straight (non-premultiplied) alpha at exactly the canvas size listed. Drop the file at the path listed; Unity applies the import preset automatically (`Twin Flank → Art Pipeline → Reimport All Sprites` if it was open).
> - Until the painted file exists the game renders a **PLACEHOLDER** (dashed border + id text). Placeholders never count as coverage.

## Identity (bible 11 — Tactical pets)
| Field | Value |
|-------|-------|
| id | `pet_02` |
| name | Prism Owl |
| species | Crystal owl |
| personality | Calm |
| rarity | Legendary |
| combat role | Summon planning |
| cooldown | 30s |
| unlock | Extreme level 30 |
| passive | Shows one future summon identity. |
| active | Locks the shown identity for the next summon. Trigger: Player taps forecast. Cooldown: 30s. |
| Animation | head tilt, wing reveal, crystal blink |
| VFX and sound | violet prism fan and clear chime |

## Asset contract
| Key | File | Canvas | PPU | Pivot | Max | Atlas | Border |
|-----|------|--------|-----|-------|-----|-------|--------|
| `pet_02_portrait` | `Pets/pet_02_portrait.png` | 512×512 | 128 | (0.5, 0.5) | 512 | Atlas_Portraits | — |
| `pet_02` | `Pets/pet_02.png` | 512×512 | 128 | (0.5, 0.12) | 512 | Atlas_Pets | — |

- Battle sprite is ~60 % of hero height at the same PPU; feet on the pivot line; faces camera-right.
- Portrait must stay a clear icon at 64 px (battle pet slot) — one dominant shape, one accent material.

## Palette tokens
| Token | Hex | Use |
|-------|-----|-----|
| `element.arcane` | `#C48BFF` | Arcane — prism lilac |
| `rarity.legendary` | `#FFB300` | Legendary |
| `ui.ink` | `#1F242E` | Outline ink (3-4 px at display size) |
| `ui.navy_panel` | `#141C33` | Deep navy panel base |

## Silhouette & material
- Silhouette: Small round-bodied companion; ~60% of hero height; clear icon silhouette; feet on pivot line.
- Material: Hand-painted creature materials; one accent material (crystal/brass/ember) per pet.
- Personality "Calm" must be visible in the idle pose (ears, tail, posture) — not through motion.

## Animation states the sprite must support
- idle_personality
- active_1: head tilt
- active_2: wing reveal
- active_3: crystal blink
- return_to_slot

## VFX ids referenced
- `vfx_arcane_impact`
- `vfx_arcane_trail`
- `vfx_common_reward_fly`

## Original concept prompt (verbatim from the bible)
```text
Twin Flank magical companion: crystal owl, calm personality, tactical summon planning role, violet prism fan and clear chime; premium hand-painted stylized mobile-game creature, full-body, navy studio, clear icon silhouette, no text, logo, trademark, or watermark.
```

Portrait variant: append "head-and-shoulders icon portrait, centred, gold ring frame".

## Approval checklist (bible consistency gate)
- [ ] **palette** — Uses only listed palette tokens (+ neutral shading); element colour appears as rim/accent, not full fill.
- [ ] **silhouette** — Reads at 96 px tall on phone against the moss road; shape language matches category rule.
- [ ] **material** — Hand-painted stone / wood / cloth / brass / crystal / foliage; no flat prototype fills or vector gradients.
- [ ] **scale** — Subject fills the specified fraction of the canvas; consistent with siblings (tiers, phases, states).
- [ ] **pivot** — Feet / base sit on the pivot line given in the contract; no floating shadow offset.
- [ ] **animation** — Pose is a neutral idle that the listed animation states can be derived from; no baked motion blur.
- [ ] **vfx** — No baked-in particles or glow except the listed 'rim' allowance; VFX come from the vfx_* sheets.
- [ ] **mobile_readability** — Passes at 50% scale with 3-4 px ink outline; no detail thinner than 2 px at 512.

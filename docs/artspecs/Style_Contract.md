# Style Contract — Twin Flank painted art

This is the one-page contract every spec sheet inherits. Generated from the 10/10 Transformation Bible (sections 07, 08, 09).

> **Rules that apply to every asset**
>
> - No text, logo, trademark, or watermark anywhere in the image (including on banners, books, signs, or UI mockups).
> - Twin Flank originality boundary: every asset is an original Twin Flank design. Do not reference, imitate, trace, or style-transfer characters, creatures, castles, UI, logos, or trade dress from any existing game or franchise (merge / tower-defense titles included). Names, silhouettes, colour combinations and emblem shapes must not be recognisable as another property. If a generated image resembles a known character, reject it and regenerate.
> - Deliver PNG-24 with straight (non-premultiplied) alpha at exactly the canvas size listed. Drop the file at the path listed; Unity applies the import preset automatically (`Twin Flank → Art Pipeline → Reimport All Sprites` if it was open).
> - Until the painted file exists the game renders a **PLACEHOLDER** (dashed border + id text). Placeholders never count as coverage.

## Art direction table (bible 08 — verbatim)
| Dimension | Twin Flank rule |
|-----------|-----------------|
| Theme | Emerald storybook frontier defended by crystal gates and eccentric magical specialists. |
| Shape language | Heroes: compact triangle and circle silhouettes. Enemies: forward-heavy wedges. Castles: stable vertical crystals. |
| Materials | Hand-painted stone, wood, cloth, brass, crystal, foliage. Avoid flat prototype fills. |
| Lighting | Warm key light, cool ambient shadows, element rim only during abilities. |
| UI | Deep navy panels, warm gold trim, cyan crystal actions, restrained rarity accents. |
| Typography | Bold humanist display for actions; highly legible sans for numbers and body. Minimum phone-size rules. |
| VFX | Element colors identify mechanics; white core at high energy; silhouettes remain visible. |
| Animation | Readable anticipation, decisive event, compact recovery, personality idle, no constant bounce. |
| Consistency gate | No asset enters production without palette, silhouette, material, scale, pivot, animation, VFX, and mobile-readability approval. |

## Tone
Middle-cute: cute-but-capable. Chibi-capable proportions with readable weapons and roles; thick 3-4 px ink outlines at display size; warm key light with cool ambient shadows; heroes charming, enemies slightly meaner, castles stable vertical crystals. Never nursery pastel, never grimdark, never flat programmer shapes.

## Category defaults
| Category | Label | Folder | Default canvas | PPU | Pivot | Max size | Atlas |
|----------|-------|--------|----------------|-----|-------|----------|-------|
| `hero_portrait` | Hero portrait | `Heroes/` | 512×512 | 128 | (0.5, 0.5) | 512 | Atlas_Portraits |
| `hero_battle` | Hero battle sprite | `Heroes/` | 512×512 | 128 | (0.5, 0.12) | 512 | Atlas_Heroes |
| `pet_portrait` | Pet portrait | `Pets/` | 512×512 | 128 | (0.5, 0.5) | 512 | Atlas_Portraits |
| `pet_battle` | Pet battle sprite | `Pets/` | 512×512 | 128 | (0.5, 0.12) | 512 | Atlas_Pets |
| `enemy` | Enemy battle sprite | `Enemies/` | 512×512 | 128 | (0.5, 0.12) | 1024 | Atlas_Enemies |
| `map_plate` | Map plate (top-down 3/4) | `Maps/` | 2048×1280 | 128 | (0.5, 0.5) | 2048 | — |
| `castle` | Castle state sprite | `Castles/` | 768×1024 | 128 | (0.5, 0.15) | 1024 | Atlas_Castles |
| `ui` | UI kit | `UI/` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI |
| `vfx` | VFX sheet | `VFX/` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_VFX |

Per-asset overrides live in `Tools/art_manifest.json` (e.g. mini-boss 768, boss 1024, VFX types, 9-slice borders).

## Full palette
| Token | Hex | Use |
|-------|-----|-----|
| `ui.navy_panel` | `#141C33` | Deep navy panel base |
| `ui.navy_raised` | `#1F2B4D` | Raised panel / header / card |
| `ui.gold_trim` | `#E3B44A` | Warm gold trim, primary CTA fill |
| `ui.gold_deep` | `#A87A22` | Gold bevel shadow |
| `ui.cyan_crystal` | `#5EDCF0` | Crystal action accent (ready, selected, summon) |
| `ui.cream` | `#F5EDD9` | Text highlight / parchment |
| `ui.ink` | `#1F242E` | Outline ink (3-4 px at display size) |
| `ui.danger` | `#E04B3A` | Gate damage, leak, destructive actions |
| `ui.success` | `#6BCB77` | Reward / positive tick |
| `world.emerald_deep` | `#144733` | Deep moss shadows, bushes |
| `world.emerald_moss` | `#388C52` | Mid-green ground |
| `world.emerald_leaf` | `#6BB861` | Bright leaf highlight |
| `world.emerald_gold` | `#F2B838` | Storybook light shafts / trim |
| `world.emerald_sky` | `#8CC7E0` | Distant air |
| `world.emerald_bark` | `#614229` | Wood, trunks, rocks |
| `world.stone_cool` | `#7C8598` | Cool ambient-shadow stone |
| `world.brass` | `#C9913A` | Brass fittings |
| `world.crystal_gate` | `#9FE8F4` | Castle crystal body |
| `rarity.common` | `#9AA3B2` | Common |
| `rarity.rare` | `#4FA3FF` | Rare |
| `rarity.epic` | `#B76BFF` | Epic |
| `rarity.legendary` | `#FFB300` | Legendary |
| `element.physical` | `#C9CDD6` | Physical — steel grey, dust |
| `element.fire` | `#FF6A2A` | Fire — ember orange |
| `element.frost` | `#8FD8FF` | Frost — pale ice blue |
| `element.storm` | `#6FA8FF` | Storm — electric blue-white |
| `element.earth` | `#8B7A4E` | Earth — ochre stone |
| `element.nature` | `#63C24F` | Nature — leaf green |
| `element.water` | `#3FA9E8` | Water — clear sea blue |
| `element.radiant` | `#FFD86A` | Radiant — sun gold |
| `element.shadow` | `#6A3F9E` | Shadow — deep violet |
| `element.void` | `#B26BFF` | Void — bright violet on near-black |
| `element.arcane` | `#C48BFF` | Arcane — prism lilac |
| `element.toxin` | `#86D13A` | Toxin — acid lime |
| `element.temporal` | `#D9B85C` | Temporal — antique brass gold |
| `element.spirit` | `#B7F0E8` | Spirit — ghost aqua |
| `vfx.white_core` | `#FFFFFF` | White core at high energy |

## Delivery format
- PNG-24, straight alpha, exact canvas size from the sheet, sRGB, no embedded colour profile surprises.
- File name == manifest key (lower-case, underscores). Drop at the path in the sheet.
- Unity import preset is applied automatically by `ArtSpritePostprocessor` (PPU, pivot, mipmaps off, compression, max size, atlas group). Do not hand-edit the importer.
- Run `Twin Flank → Art Pipeline → Art Coverage Dashboard` to confirm the file flipped from **PLACEHOLDER** to **PAINTED**.

## Approval checklist (bible consistency gate — all eight required)
- [ ] **palette** — Uses only listed palette tokens (+ neutral shading); element colour appears as rim/accent, not full fill.
- [ ] **silhouette** — Reads at 96 px tall on phone against the moss road; shape language matches category rule.
- [ ] **material** — Hand-painted stone / wood / cloth / brass / crystal / foliage; no flat prototype fills or vector gradients.
- [ ] **scale** — Subject fills the specified fraction of the canvas; consistent with siblings (tiers, phases, states).
- [ ] **pivot** — Feet / base sit on the pivot line given in the contract; no floating shadow offset.
- [ ] **animation** — Pose is a neutral idle that the listed animation states can be derived from; no baked motion blur.
- [ ] **vfx** — No baked-in particles or glow except the listed 'rim' allowance; VFX come from the vfx_* sheets.
- [ ] **mobile_readability** — Passes at 50% scale with 3-4 px ink outline; no detail thinner than 2 px at 512.

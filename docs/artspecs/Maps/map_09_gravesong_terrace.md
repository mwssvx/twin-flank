# map_09 — Gravesong Terrace

Category: **Map plate + castle** · Biome: Haunted cemetery · Road: Crossroads · Hazard: Ghost shortcuts · Castle: **Chapel Gate** · Difficulty 54-59

> **Rules that apply to every asset**
>
> - No text, logo, trademark, or watermark anywhere in the image (including on banners, books, signs, or UI mockups).
> - Twin Flank originality boundary: every asset is an original Twin Flank design. Do not reference, imitate, trace, or style-transfer characters, creatures, castles, UI, logos, or trade dress from any existing game or franchise (merge / tower-defense titles included). Names, silhouettes, colour combinations and emblem shapes must not be recognisable as another property. If a generated image resembles a known character, reject it and regenerate.
> - Deliver PNG-24 with straight (non-premultiplied) alpha at exactly the canvas size listed. Drop the file at the path listed; Unity applies the import preset automatically (`Twin Flank → Art Pipeline → Reimport All Sprites` if it was open).
> - Until the painted file exists the game renders a **PLACEHOLDER** (dashed border + id text). Placeholders never count as coverage.

## Identity (bible 13 — Maps, roads, and castles)
| Field | Value |
|-------|-------|
| id | `map_09` |
| name | Gravesong Terrace |
| biome | Haunted cemetery |
| road language | Crossroads |
| hazard | Ghost shortcuts |
| castle | Chapel Gate |
| difficulty | 54-59 |
| featured threat | Astral Serpent |
| primary modifier | Invisible enemies. |

## Asset contract
| Key | File | Canvas | PPU | Pivot | Max | Atlas | Border |
|-----|------|--------|-----|-------|-----|-------|--------|
| `map_09_plate` | `Maps/map_09_plate.png` | 2048×1280 | 128 | (0.5, 0.5) | 2048 | — | — |
| `castle_map_09_intact` | `Castles/castle_map_09_intact.png` | 768×1024 | 128 | (0.5, 0.15) | 1024 | Atlas_Castles | — |
| `castle_map_09_damaged` | `Castles/castle_map_09_damaged.png` | 768×1024 | 128 | (0.5, 0.15) | 1024 | Atlas_Castles | — |
| `castle_map_09_critical` | `Castles/castle_map_09_critical.png` | 768×1024 | 128 | (0.5, 0.15) | 1024 | Atlas_Castles | — |
| `castle_map_09_defeated` | `Castles/castle_map_09_defeated.png` | 768×1024 | 128 | (0.5, 0.15) | 1024 | Atlas_Castles | — |

### Map plate rules
- 2048×1280 top-down 3/4 (camera tilted ~55°). Road enters at the **left edge**, castle plinth sits at the **right third**; branch choices and pedestal arcs (flank sockets) painted as flat stone/wood plinths on either side of the road.
- Entrance, road direction, branch choice, pedestal arcs and the castle destination must remain readable at phone size (bible 13).
- Environmental animation never hides enemies or telegraphs; if a hazard layer is painted, deliver it as a separate PNG named `map_09_plate_hazard.png` (optional).
- No enemies, heroes, UI, or text baked in. Leave the castle footprint as a plain plinth — the castle is a separate sprite so it can swap states.

### Castle states (all four share footprint, scale and pivot)
| File | State | Visual |
|------|-------|--------|
| `castle_map_09_intact.png` | intact | pristine crystal, full glow, banners up |
| `castle_map_09_damaged.png` | damaged | first cracks, one banner torn, glow dimmed 30% |
| `castle_map_09_critical.png` | critical | large fractures, smoke wisps, glow flickering red-tinted, rubble at base |
| `castle_map_09_defeated.png` | defeated | shattered crystal, dark core, collapsed upper third, no glow |

Castle also needs visible **upgrade attachment sockets** (flat plinths at 3 points) so code can attach shield / ability / cosmetic layers.

## Palette tokens
| Token | Hex | Use |
|-------|-----|-----|
| `element.shadow` | `#6A3F9E` | Shadow — deep violet |
| `world.stone_cool` | `#7C8598` | Cool ambient-shadow stone |
| `element.spirit` | `#B7F0E8` | Spirit — ghost aqua |
| `world.emerald_deep` | `#144733` | Deep moss shadows, bushes |

## Silhouette & material
- Plate: Top-down 3/4 environment; road, entrance, branch choice, pedestal arcs and castle destination readable at phone size. Hand-painted terrain, foliage, stone, water; no baked enemies, no baked UI, no baked text.
- Castle: Stable vertical crystal silhouette (bible 08); base sits on pivot line; upgrade attachment sockets visible as flat plinths. Crystal + stone + one biome material (wood/brass/coral/marble); consistent across the 4 damage states.
- Lighting: warm key light from upper-left, cool ambient shadows; the road bed is the lightest ground value so enemies read on it.

## Original concept prompt — map plate (verbatim from the bible)
```text
Top-down 3/4 Twin Flank map: Gravesong Terrace, haunted cemetery, crossroads road, ghost shortcuts, chapel gate, readable entrance and tower sockets, premium hand-painted mobile-game environment, no text or watermark.
```

## Concept prompt — castle (derived from the bible castle name + biome)
```text
Twin Flank castle concept: Chapel Gate, the crystal-gate stronghold of Gravesong Terrace (Haunted cemetery); stable vertical crystal silhouette, hand-painted stone and crystal with haunted cemetery materials, upgrade attachment sockets as flat plinths, front 3/4 view on navy studio backdrop, no text, logo, trademark, or watermark.
```
State variants: append "first cracks, one banner torn, glow dimmed 30%" / "large fractures, smoke wisps, glow flickering red-tinted, rubble at base" / "shattered crystal, dark core, collapsed upper third, no glow".

## Approval checklist (bible consistency gate)
- [ ] **palette** — Uses only listed palette tokens (+ neutral shading); element colour appears as rim/accent, not full fill.
- [ ] **silhouette** — Reads at 96 px tall on phone against the moss road; shape language matches category rule.
- [ ] **material** — Hand-painted stone / wood / cloth / brass / crystal / foliage; no flat prototype fills or vector gradients.
- [ ] **scale** — Subject fills the specified fraction of the canvas; consistent with siblings (tiers, phases, states).
- [ ] **pivot** — Feet / base sit on the pivot line given in the contract; no floating shadow offset.
- [ ] **animation** — Pose is a neutral idle that the listed animation states can be derived from; no baked motion blur.
- [ ] **vfx** — No baked-in particles or glow except the listed 'rim' allowance; VFX come from the vfx_* sheets.
- [ ] **mobile_readability** — Passes at 50% scale with 3-4 px ink outline; no detail thinner than 2 px at 512.

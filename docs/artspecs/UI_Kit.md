# UI Kit — Twin Flank

Category: **UI** · 72 assets · Folder `Resources/Art/Sprites/UI/` · Atlas `Atlas_UI`

> **Rules that apply to every asset**
>
> - No text, logo, trademark, or watermark anywhere in the image (including on banners, books, signs, or UI mockups).
> - Twin Flank originality boundary: every asset is an original Twin Flank design. Do not reference, imitate, trace, or style-transfer characters, creatures, castles, UI, logos, or trade dress from any existing game or franchise (merge / tower-defense titles included). Names, silhouettes, colour combinations and emblem shapes must not be recognisable as another property. If a generated image resembles a known character, reject it and regenerate.
> - Deliver PNG-24 with straight (non-premultiplied) alpha at exactly the canvas size listed. Drop the file at the path listed; Unity applies the import preset automatically (`Twin Flank → Art Pipeline → Reimport All Sprites` if it was open).
> - Until the painted file exists the game renders a **PLACEHOLDER** (dashed border + id text). Placeholders never count as coverage.

## Art direction (bible 08)
- UI: Deep navy panels, warm gold trim, cyan crystal actions, restrained rarity accents.
- Typography: Bold humanist display for actions; highly legible sans for numbers and body. Minimum phone-size rules. (fonts are not art assets — no text in any PNG.)

## Navigation rules (bible 09)
- Persistent header: profile, coins, gems, energy, settings or overflow.
- Persistent bottom navigation: Home, Heroes, Deck, Battle, Shop; Events accessed from prominent home card.
- One primary action per screen; secondary actions use lower contrast.
- Back navigation is predictable; modal dialogs never replace full pages accidentally.
- Badges indicate actionable change, not permanent visual noise.
- Every currency icon has number, tooltip, and source/sink explanation.
- Collection uses virtualization, filters, role icons, and locked silhouettes - never brown placeholders.
- Responsive gate: Test 16:9, 18:9, 19.5:9, tablets, notches, and text scaling. No critical touch target below 44 logical pixels and no body text below the approved mobile minimum.

## Global UI contract
- PPU 128, pivot centre, mipmaps off, bilinear, alpha is transparency, compression high quality.
- 9-slice frames: the **Border** column is the slice inset in px on all four sides; keep corners decorative and edges tileable.
- Icons: one silhouette idea each; 3 px ink outline; readable at 44 logical px (minimum touch target).
- Rarity accents are restrained: frame corners + gem only, never a full-colour wash.
- Legacy chest names (`wooden/silver/golden/legendary`) map to the bible ladder Scout Cache → Iron → Emerald → Arcane; `ArtAssetLibrary.GetChestSprite` handles the alias.

## Palette
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
| `rarity.common` | `#9AA3B2` | Common |
| `rarity.rare` | `#4FA3FF` | Rare |
| `rarity.epic` | `#B76BFF` | Epic |
| `rarity.legendary` | `#FFB300` | Legendary |

### Panels
| Key | File | Canvas | PPU | Pivot | Max | Atlas | Border |
|-----|------|--------|-----|-------|-----|-------|--------|
| `ui_panel_navy` | `UI/ui_panel_navy.png` | 512×512 | 128 | (0.5, 0.5) | 512 | Atlas_UI | 64 |
| `ui_panel_raised` | `UI/ui_panel_raised.png` | 512×512 | 128 | (0.5, 0.5) | 512 | Atlas_UI | 48 |
| `ui_panel_header` | `UI/ui_panel_header.png` | 512×160 | 128 | (0.5, 0.5) | 512 | Atlas_UI | 48 |
| `ui_modal_frame` | `UI/ui_modal_frame.png` | 512×512 | 128 | (0.5, 0.5) | 512 | Atlas_UI | 80 |
| `ui_tooltip` | `UI/ui_tooltip.png` | 256×128 | 128 | (0.5, 0.5) | 512 | Atlas_UI | 24 |

- `ui_panel_navy` — 9-slice main panel: navy fill, 6 px gold trim, inner bevel. Palette: `ui.navy_panel`, `ui.gold_trim`
- `ui_panel_raised` — 9-slice card / list row background. Palette: `ui.navy_raised`, `ui.gold_deep`
- `ui_panel_header` — Persistent header bar (profile, coins, gems, energy, settings). Palette: `ui.navy_raised`, `ui.gold_trim`
- `ui_modal_frame` — Modal dialog frame with crystal corner ornaments. Palette: `ui.navy_panel`, `ui.gold_trim`, `ui.cyan_crystal`
- `ui_tooltip` — Tooltip bubble 9-slice (currency source/sink explanations). Palette: `ui.navy_raised`, `ui.cream`

### Buttons
| Key | File | Canvas | PPU | Pivot | Max | Atlas | Border |
|-----|------|--------|-----|-------|-----|-------|--------|
| `ui_button_primary` | `UI/ui_button_primary.png` | 512×160 | 128 | (0.5, 0.5) | 512 | Atlas_UI | 48 |
| `ui_button_secondary` | `UI/ui_button_secondary.png` | 512×160 | 128 | (0.5, 0.5) | 512 | Atlas_UI | 48 |
| `ui_button_crystal` | `UI/ui_button_crystal.png` | 512×160 | 128 | (0.5, 0.5) | 512 | Atlas_UI | 48 |
| `ui_button_disabled` | `UI/ui_button_disabled.png` | 512×160 | 128 | (0.5, 0.5) | 512 | Atlas_UI | 48 |
| `ui_button_back` | `UI/ui_button_back.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `ui_button_close` | `UI/ui_button_close.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `ui_toggle_on` | `UI/ui_toggle_on.png` | 256×128 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `ui_toggle_off` | `UI/ui_toggle_off.png` | 256×128 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |

- `ui_button_primary` — Primary CTA (BATTLE, SUMMON): gold fill, bevel, one per screen. Palette: `ui.gold_trim`, `ui.gold_deep`, `ui.ink`
- `ui_button_secondary` — Secondary action: navy fill, thin gold outline, lower contrast. Palette: `ui.navy_raised`, `ui.gold_deep`
- `ui_button_crystal` — Crystal action (skill ready, confirm merge): cyan crystal fill. Palette: `ui.cyan_crystal`, `ui.navy_panel`
- `ui_button_disabled` — Disabled state: desaturated navy, grey outline. Palette: `ui.navy_panel`, `rarity.common`
- `ui_button_back` — Round back chevron. Palette: `ui.navy_raised`, `ui.cream`
- `ui_button_close` — Round close X. Palette: `ui.navy_raised`, `ui.danger`
- `ui_toggle_on` — Settings toggle on. Palette: `ui.cyan_crystal`, `ui.navy_panel`
- `ui_toggle_off` — Settings toggle off. Palette: `ui.navy_panel`, `rarity.common`

### Badges
| Key | File | Canvas | PPU | Pivot | Max | Atlas | Border |
|-----|------|--------|-----|-------|-----|-------|--------|
| `ui_badge_dot` | `UI/ui_badge_dot.png` | 128×128 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |

- `ui_badge_dot` — Actionable-change badge (never permanent noise). Palette: `ui.danger`, `ui.cream`

### Collection
| Key | File | Canvas | PPU | Pivot | Max | Atlas | Border |
|-----|------|--------|-----|-------|-----|-------|--------|
| `ui_locked_silhouette` | `UI/ui_locked_silhouette.png` | 512×512 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `ui_slot_empty` | `UI/ui_slot_empty.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | 32 |

- `ui_locked_silhouette` — Locked hero card silhouette mask — never a brown placeholder. Palette: `ui.navy_panel`, `ui.navy_raised`
- `ui_slot_empty` — Empty deck / pet slot frame. Palette: `ui.navy_panel`, `ui.gold_deep`

### Rarity frames
| Key | File | Canvas | PPU | Pivot | Max | Atlas | Border |
|-----|------|--------|-----|-------|-----|-------|--------|
| `frame_common` | `UI/frame_common.png` | 512×512 | 128 | (0.5, 0.5) | 512 | Atlas_UI | 48 |
| `frame_rare` | `UI/frame_rare.png` | 512×512 | 128 | (0.5, 0.5) | 512 | Atlas_UI | 48 |
| `frame_epic` | `UI/frame_epic.png` | 512×512 | 128 | (0.5, 0.5) | 512 | Atlas_UI | 48 |
| `frame_legendary` | `UI/frame_legendary.png` | 512×512 | 128 | (0.5, 0.5) | 512 | Atlas_UI | 48 |

- `frame_common` — Card frame, common: plain stone. Palette: `rarity.common`, `ui.navy_raised`
- `frame_rare` — Card frame, rare: blue crystal corners. Palette: `rarity.rare`, `ui.navy_raised`
- `frame_epic` — Card frame, epic: violet crystal + gold filigree. Palette: `rarity.epic`, `ui.navy_raised`
- `frame_legendary` — Card frame, legendary: full gold with crystal crown. Palette: `rarity.legendary`, `ui.gold_trim`

### Currency
| Key | File | Canvas | PPU | Pivot | Max | Atlas | Border |
|-----|------|--------|-----|-------|-----|-------|--------|
| `icon_gold` | `UI/icon_gold.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `icon_gem` | `UI/icon_gem.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `icon_energy` | `UI/icon_energy.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `icon_heart` | `UI/icon_heart.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `icon_hero_shard` | `UI/icon_hero_shard.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `icon_pet_token` | `UI/icon_pet_token.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `icon_event_sigil` | `UI/icon_event_sigil.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |

- `icon_gold` — Coins — stacked gold coins with crystal facet. Palette: `ui.gold_trim`, `ui.gold_deep`
- `icon_gem` — Gems — cyan crystal gem. Palette: `ui.cyan_crystal`, `element.arcane`
- `icon_energy` — Energy — lightning bolt in crystal. Palette: `element.storm`, `vfx.white_core`
- `icon_heart` — Gate health heart (battle HUD). Palette: `ui.danger`, `ui.cream`
- `icon_hero_shard` — Hero shards — broken portrait crystal. Palette: `rarity.epic`, `ui.gold_trim`
- `icon_pet_token` — Pet tokens — paw-stamped brass coin. Palette: `world.brass`, `world.emerald_leaf`
- `icon_event_sigil` — Event sigils — star sigil medallion. Palette: `element.radiant`, `ui.navy_panel`

### Header
| Key | File | Canvas | PPU | Pivot | Max | Atlas | Border |
|-----|------|--------|-----|-------|-----|-------|--------|
| `icon_settings` | `UI/icon_settings.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `icon_profile` | `UI/icon_profile.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |

- `icon_settings` — Settings gear. Palette: `ui.cream`, `ui.navy_raised`
- `icon_profile` — Profile frame. Palette: `ui.cream`, `ui.gold_trim`

### Navigation
| Key | File | Canvas | PPU | Pivot | Max | Atlas | Border |
|-----|------|--------|-----|-------|-----|-------|--------|
| `nav_home` | `UI/nav_home.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `nav_heroes` | `UI/nav_heroes.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `nav_deck` | `UI/nav_deck.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `nav_battle` | `UI/nav_battle.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `nav_shop` | `UI/nav_shop.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `nav_events` | `UI/nav_events.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |

- `nav_home` — Bottom nav: Home (crystal gate glyph). Palette: `ui.cream`, `ui.cyan_crystal`
- `nav_heroes` — Bottom nav: Heroes (helm glyph). Palette: `ui.cream`, `ui.cyan_crystal`
- `nav_deck` — Bottom nav: Deck (fanned cards). Palette: `ui.cream`, `ui.cyan_crystal`
- `nav_battle` — Bottom nav: Battle (crossed banner + sword). Palette: `ui.gold_trim`, `ui.cream`
- `nav_shop` — Bottom nav: Shop (chest glyph). Palette: `ui.cream`, `ui.cyan_crystal`
- `nav_events` — Home card: Events (star banner). Palette: `element.radiant`, `ui.cream`

### Chests
| Key | File | Canvas | PPU | Pivot | Max | Atlas | Border |
|-----|------|--------|-----|-------|-----|-------|--------|
| `chest_scout_cache` | `UI/chest_scout_cache.png` | 512×512 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `chest_iron` | `UI/chest_iron.png` | 512×512 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `chest_emerald` | `UI/chest_emerald.png` | 512×512 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `chest_arcane` | `UI/chest_arcane.png` | 512×512 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `chest_royal_vault` | `UI/chest_royal_vault.png` | 512×512 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `chest_celestial_vault` | `UI/chest_celestial_vault.png` | 512×512 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |

- `chest_scout_cache` — Chest ladder 1: Scout Cache — leather satchel-chest. Palette: `world.emerald_bark`, `world.brass`
- `chest_iron` — Chest ladder 2: Iron Chest. Palette: `world.stone_cool`, `ui.ink`
- `chest_emerald` — Chest ladder 3: Emerald Chest. Palette: `world.emerald_leaf`, `ui.gold_trim`
- `chest_arcane` — Chest ladder 4: Arcane Chest. Palette: `element.arcane`, `ui.navy_panel`
- `chest_royal_vault` — Chest ladder 5: Royal Vault. Palette: `ui.gold_trim`, `ui.danger`
- `chest_celestial_vault` — Chest ladder 6: Celestial Vault. Palette: `element.radiant`, `element.spirit`

### Role icons
| Key | File | Canvas | PPU | Pivot | Max | Atlas | Border |
|-----|------|--------|-----|-------|-----|-------|--------|
| `role_carry` | `UI/role_carry.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `role_control` | `UI/role_control.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `role_support` | `UI/role_support.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `role_guard` | `UI/role_guard.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `role_economy` | `UI/role_economy.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |

- `role_carry` — Role icon: carry (arrow burst). Palette: `ui.cream`, `element.fire`
- `role_control` — Role icon: control (chain link). Palette: `ui.cream`, `element.frost`
- `role_support` — Role icon: support (halo). Palette: `ui.cream`, `element.radiant`
- `role_guard` — Role icon: guard / tank (shield). Palette: `ui.cream`, `element.earth`
- `role_economy` — Role icon: economy (coin note). Palette: `ui.cream`, `ui.gold_trim`

### Battle chrome
| Key | File | Canvas | PPU | Pivot | Max | Atlas | Border |
|-----|------|--------|-----|-------|-----|-------|--------|
| `ui_pad_wood` | `UI/ui_pad_wood.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `ui_pedestal_locked` | `UI/ui_pedestal_locked.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `ui_road_dirt` | `UI/ui_road_dirt.png` | 256×128 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `ui_lane_arrow` | `UI/ui_lane_arrow.png` | 128×128 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `ui_gate_hp_bar` | `UI/ui_gate_hp_bar.png` | 512×64 | 128 | (0.5, 0.5) | 512 | Atlas_UI | 16 |
| `ui_hp_bar_enemy` | `UI/ui_hp_bar_enemy.png` | 128×32 | 128 | (0.5, 0.5) | 512 | Atlas_UI | 8 |

- `ui_pad_wood` — Flank pedestal top-down: wood disc, moss rim, cream summon rune. Palette: `world.emerald_bark`, `world.emerald_leaf`, `ui.cream`
- `ui_pedestal_locked` — Socket-locked pedestal overlay (boss lock). Palette: `world.stone_cool`, `ui.danger`
- `ui_road_dirt` — Generic packed-earth road tile (fallback when map plate lacks baked road). Palette: `world.emerald_bark`, `world.emerald_leaf`
- `ui_lane_arrow` — Road direction arrow decal. Palette: `ui.cream`, `ui.ink`
- `ui_gate_hp_bar` — Gate HP bar frame 9-slice. Palette: `ui.navy_panel`, `ui.danger`, `ui.gold_trim`
- `ui_hp_bar_enemy` — Enemy HP bar 9-slice. Palette: `ui.ink`, `ui.danger`

### Skill icons
| Key | File | Canvas | PPU | Pivot | Max | Atlas | Border |
|-----|------|--------|-----|-------|-----|-------|--------|
| `skill_hero_01` | `UI/skill_hero_01.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `skill_hero_02` | `UI/skill_hero_02.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `skill_hero_03` | `UI/skill_hero_03.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `skill_hero_04` | `UI/skill_hero_04.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `skill_hero_05` | `UI/skill_hero_05.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `skill_hero_06` | `UI/skill_hero_06.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `skill_hero_07` | `UI/skill_hero_07.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `skill_hero_08` | `UI/skill_hero_08.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `skill_hero_09` | `UI/skill_hero_09.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `skill_hero_10` | `UI/skill_hero_10.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `skill_hero_11` | `UI/skill_hero_11.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `skill_hero_12` | `UI/skill_hero_12.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `skill_hero_13` | `UI/skill_hero_13.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `skill_hero_14` | `UI/skill_hero_14.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `skill_hero_15` | `UI/skill_hero_15.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `skill_hero_16` | `UI/skill_hero_16.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `skill_hero_17` | `UI/skill_hero_17.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `skill_hero_18` | `UI/skill_hero_18.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `skill_hero_19` | `UI/skill_hero_19.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |
| `skill_hero_20` | `UI/skill_hero_20.png` | 256×256 | 128 | (0.5, 0.5) | 512 | Atlas_UI | — |

- `skill_hero_01` — Skill icon for Emberwing: Special - Flame Seed: Every fifth shot ignites a road zone for 4s. Emblem shape must differ from other icons of the same school. Palette: `element.fire`, `ui.navy_panel`, `ui.gold_trim`
- `skill_hero_02` — Skill icon for Vale Arrow: Special - True Line: Shots gain 8% damage per uninterrupted hit on the same target. Emblem shape must differ from other icons of the same school. Palette: `element.physical`, `ui.navy_panel`, `ui.gold_trim`
- `skill_hero_03` — Skill icon for Cairn Warden: Special - Fracture: Every third hit removes armor and sends a short shockwave. Emblem shape must differ from other icons of the same school. Palette: `element.earth`, `ui.navy_panel`, `ui.gold_trim`
- `skill_hero_04` — Skill icon for Luma Grace: Special - Beacon: Periodically shields the gate and two adjacent heroes. Emblem shape must differ from other icons of the same school. Palette: `element.radiant`, `ui.navy_panel`, `ui.gold_trim`
- `skill_hero_05` — Skill icon for Hex Veyr: Special - Loaded Curse: Cycles slow, vulnerability, silence, then detonates all marks. Emblem shape must differ from other icons of the same school. Palette: `element.void`, `ui.navy_panel`, `ui.gold_trim`
- `skill_hero_06` — Skill icon for Volt Spear: Special - Overcharge: Chain count increases with merge tier; final jump stuns. Emblem shape must differ from other icons of the same school. Palette: `element.storm`, `ui.navy_panel`, `ui.gold_trim`
- `skill_hero_07` — Skill icon for Gearshot Brann: Special - Breach Round: Reloaded shot pierces armor and knocks the target backward. Emblem shape must differ from other icons of the same school. Palette: `element.physical`, `ui.navy_panel`, `ui.gold_trim`
- `skill_hero_08` — Skill icon for Sira Frostfang: Special - White Trail: Applies stacking chill; max stacks freeze and reset. Emblem shape must differ from other icons of the same school. Palette: `element.frost`, `ui.navy_panel`, `ui.gold_trim`
- `skill_hero_09` — Skill icon for Thornroot: Special - Briar Gate: Creates a thorn patch at the busiest road segment. Emblem shape must differ from other icons of the same school. Palette: `element.nature`, `ui.navy_panel`, `ui.gold_trim`
- `skill_hero_10` — Skill icon for Sol Aegis: Special - Dawn Wall: Blocks one enemy ability and reflects a fraction of damage. Emblem shape must differ from other icons of the same school. Palette: `element.radiant`, `ui.navy_panel`, `ui.gold_trim`
- `skill_hero_11` — Skill icon for Mire Quill: Special - Catalyst: Poisons combine and explode when three types overlap. Emblem shape must differ from other icons of the same school. Palette: `element.toxin`, `ui.navy_panel`, `ui.gold_trim`
- `skill_hero_12` — Skill icon for Nox Crescent: Special - Final Cut: Teleports to finish enemies below a threshold, then returns. Emblem shape must differ from other icons of the same school. Palette: `element.shadow`, `ui.navy_panel`, `ui.gold_trim`
- `skill_hero_13` — Skill icon for Astra Prism: Special - Refraction: Beams split differently based on target spacing. Emblem shape must differ from other icons of the same school. Palette: `element.arcane`, `ui.navy_panel`, `ui.gold_trim`
- `skill_hero_14` — Skill icon for Iron Standard: Special - Rally Line: Buffs the two nearest heroes and grants temporary attack speed after a merge. Emblem shape must differ from other icons of the same school. Palette: `element.physical`, `ui.navy_panel`, `ui.gold_trim`
- `skill_hero_15` — Skill icon for Coralynn: Special - Undertow: Pulls three enemies together and briefly slows their segment. Emblem shape must differ from other icons of the same school. Palette: `element.water`, `ui.navy_panel`, `ui.gold_trim`
- `skill_hero_16` — Skill icon for Sporekin Pip: Special - Bloom Chain: Spores jump among five enemies; killed carriers leave buff spores. Emblem shape must differ from other icons of the same school. Palette: `element.nature`, `ui.navy_panel`, `ui.gold_trim`
- `skill_hero_17` — Skill icon for Dorran Bolt: Special - Siege Pin: Ballista bolt pierces the road and pins the largest target. Emblem shape must differ from other icons of the same school. Palette: `element.physical`, `ui.navy_panel`, `ui.gold_trim`
- `skill_hero_18` — Skill icon for Tikket: Special - Second Chance: First merge each wave may be previewed and canceled once. Emblem shape must differ from other icons of the same school. Palette: `element.temporal`, `ui.navy_panel`, `ui.gold_trim`
- `skill_hero_19` — Skill icon for Eira Echo: Special - Encore: Kills during the melody return bonus summon resource once per interval. Emblem shape must differ from other icons of the same school. Palette: `element.spirit`, `ui.navy_panel`, `ui.gold_trim`
- `skill_hero_20` — Skill icon for Null Monk: Special - Empty Palm: Converts one empty pedestal into a temporary choice between two summons. Emblem shape must differ from other icons of the same school. Palette: `element.void`, `ui.navy_panel`, `ui.gold_trim`

## Prompt template
```text
Twin Flank UI kit element: <description>. Deep navy panels, warm gold trim, cyan crystal actions, restrained rarity accents; hand-painted mobile game UI, crisp edges, transparent background, no text, logo, trademark, or watermark.
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

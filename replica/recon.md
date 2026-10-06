# Recon map: Rush Royale (iOS / Android), plus Random Dice and Dice vs Monsters

Scope: the battle loop and the systems around it (summon economy, merge rules, targeting, waves and bosses, difficulty, progression, monetization). We are not cloning it. This feeds the design of an original game, Twin Flank.
For: Twin Flank, a solo-dev portrait merge tower defense for mobile.
Date: 2026-10-06

## Sources

| # | source | URL | notes |
| --- | --- | --- | --- |
| 1 | App Store listing (Rush Royale) | https://apps.apple.com/us/app/id1526121033 | v38.0, 4.52 stars from 95,786 ratings (iTunes lookup, 2026-10-06) |
| 2 | App Store listing (Random Dice) | https://apps.apple.com/us/app/id1462877149 | v9.5.5, 4.57 stars from 52,976 ratings |
| 3 | App Store listing (Dice vs Monsters: Roguelike TD) | https://apps.apple.com/us/app/id6504301485 | v2.12.2, 4.43 stars from 10,975 ratings; closest to our roguelite idea |
| 4 | App Store listing (Merge Clash) | https://apps.apple.com/us/app/id1506854108 | 4.78 stars from 14,054 ratings; its review feed returned nothing |
| 5 | Rush Royale official About page | https://rr.my.games/en/about | modes, cards, bosses, heroes |
| 6 | Official update notes 20.0 / 28.0 / 30.0 / 35.1 | https://rr.my.games/en/news/ | progression caps, PvP format, pacing |
| 7 | User's own system reference (built with Codex from sources 1, 5, 6) | ~/Desktop/rush_royale_game_system_reference.pdf | 28 pages; mechanics below are summarised from it |
| 8 | App Store reviews, official RSS feed | `itunes.apple.com/us/rss/customerreviews/...` | 1,497 reviews after de-duplication; see `reviews-*.csv`, `feedback-*.md` |
| 9 | Rush Royale revenue milestone | https://www.pocketgamer.biz/rush-royale-surpasses-500m-in-lifetime-revenue/ | $500M lifetime, 105M downloads |

## Core loop

Spend a match resource to summon random deck units onto a small board, merge identical pairs into stronger pieces, and survive waves and board-wrecking bosses longer than your opponent.

## Battle mechanics (what makes it tick)

| system | Rush Royale rule | why it works | where it fails (evidence) |
| --- | --- | --- | --- |
| Board | 3x5 grid, 15 cells, separate from the enemy road | scarce space forces merge decisions | abstract; the ads show a road and towers, the game does not (source 7, p3) |
| Summon | pay mana; a random deck card spawns on a random empty cell; the next summon costs more | cheap early bodies, expensive late, so you stop spamming | you control timing only, not what or where; streaks feel rigged (Random Dice: 60 RNG reviews) |
| Mana income | kills and wave clears pay mana | killing well snowballs into more options | none major |
| Merge | same unit + same rank -> rank+1 of a **random** deck unit | each merge is a gamble, which keeps it tense | it can destroy a good board; feels like luck, not skill |
| Card power-up | spend mana to buff every copy of one card for the match | a third spending option that competes with summon | none major |
| Targeting | each unit has a rule: first, random, highest HP, nearby, none | role identity; deck synergy | "closest" targeting makes towers waste shots (DvM review) |
| Waves | timed waves, then a boss; three hearts | clear pacing | hidden multipliers in newer PvP formats |
| Bosses | disrupt the board: petrify, transform, de-rank, shuffle, swap | tests board resilience | random board-shuffling bosses read as unfair ("roulette wheel of a boss", Random Dice) |
| Heroes | one active ability above the deck, charges over time | a second timing decision | premium heroes = paid power |

## Meta mechanics

- Four kinds of "level": permanent card level (to 15), match rank (1-7), match card power-up, hero level (to 100). The reference stresses never showing these with the same icon.
- Rarity: common to legendary. 41 of 77 cards are legendary, according to one review.
- PvP trophies, leagues, seasons; co-op dungeons; clans; monthly event units and passes.

## Screens (core slice)

| ID | screen | purpose | key components |
| --- | --- | --- | --- |
| S01 | Home | start a battle, see chests and passes | mode card, battle button, currency header, bottom nav |
| S02 | Deck | choose 5 units and a hero | card grid, deck slots, unit detail |
| S03 | Battle | the game | board, road, mana, summon button, card power-up row, hearts, wave and boss strip |
| S04 | Result | win or lose, rewards | trophies, chest, ad-to-double |
| S05 | Shop | offers, chests, gems | offer cards, chest odds |
| S06 | Chest open | reward reveal | card flip, counts |

## Flows

```
F01 Play one battle
    S01 -> S03 (summon, merge, power up, ~3-5 min) -> S04 -> S01
    happy path taps: battle button, then ~30-80 in-battle actions
F02 Upgrade a unit
    S01 -> S02 -> unit detail -> upgrade -> S02
```

## Inferred battle data model (guesses, confidence medium)

```
UnitDef      id, role, rarity, targetRule, baseStats, rankScaling, powerUpLevels, triggers[]
BoardPiece   cellIndex, unitId, rank, statuses[], counters{}
Wave         id, duration, spawnGroups[{enemy, count, interval}], hpMultiplier, nextBoss
EnemyDef     id, class (common|fast|tank|carrier|miniboss|boss), hp, speed, armor, abilities[]
Match        seed, deckIds[5], mana, summonCost, hearts, waveIndex, commandLog[]
```

## Out of scope (do not clone)

- Their units, heroes, names, art, sounds, UI layout, exact numbers.
- Real-time PvP and its matchmaking, servers and anti-cheat: expensive, and the top source of complaints.
- Clans, dungeons and the live-service event calendar.

## Size

For our original slice: 6 screens, 2 flows, 5 entities. Hard parts: feel and readability of combat at phone size, balance, ads and purchases plugins. Size: M (a few weeks of focused sessions) for a polished single-map slice.

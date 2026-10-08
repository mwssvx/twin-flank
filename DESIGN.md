# Twin Flank — Game Logic (v1 slice)

The pitch: **a skill-first merge defense. You choose where every hero stands, you see what's coming, and nothing random or paid decides the fight.**

The hooks (what a 5-second video shows, all real gameplay):
1. **Flip the flank**: one tap sends the horde down the left or right road (§9a).
2. **Watch it evolve**: a tier-5 merge transforms the hero in a 1-second cinematic and blasts nearby enemies (§3).
3. **Melt the swarm**: waves of 80–150 tiny enemies wiped out by splash heroes (§8).
4. **Last-second saves**: telegraphed bosses and merges make "castle on 1 HP, one move left" moments happen naturally.

_Decisions of 8 Oct 2026: added the Flank Switch, tier-5 evolution, swarm waves and the daily challenge; simplified targeting, interest and currencies._
Research behind each rule: `replica/fixes.md` (1,497 real reviews of Rush Royale, Random Dice, Dice vs Monsters).

The test for every rule below: *would a smart player ever feel cheated or feel the game is dumb here?* If yes, the rule is wrong.

---

## 1. The screen

Portrait. A painted map with one winding **road** from the top (spawn portal) to the **castle** at the bottom. On **fork maps**, the road splits into a left and a right flank at a switch and joins again before the castle (§9a). **10 pads** sit beside the road, 5 on each flank. Every pad covers a different stretch of road: pads on the inside of a bend cover two stretches, so they're worth more. That's the first thing a good player learns.

Bottom HUD: Aether, the **SUMMON** button with its price, the **Next** hero preview, wave counter, speed (x1/x2, free), pause.

## 2. Summoning

- Costs Aether. First summon **10**, each summon after costs **+10** more (10, 20, 30…). Merging does not lower the price. More bodies get expensive, which is what stops summon spam.
- **What you get is a shuffle bag**: the bag holds 2 copies of each of your 5 deck heroes (10 cards), drawn in random order, then refilled. No hero can appear 3 times in a row, and every hero shows up twice per 10 summons. Fixes "20 summons of the same dice".
- **Next preview**: you always see the next hero in the bag before you pay, so the decision is "is this hero worth 30 Aether right now, on that pad?"
- **You choose the pad.** Tap SUMMON → valid empty pads glow with the hero's range circle drawn → tap a pad. Cancel is free. You can never spend Aether without placing.
- If no pad is free, SUMMON shows "No free pad: merge or move" instead of doing nothing.

## 3. Merging

- Drag a hero onto **the same hero at the same tier** → one hero, **same identity, tier +1** (tiers 1–5, art for all five exists). The hero stays on the **target** pad, so you choose which position survives. The source pad is freed.
- While dragging, legal partners glow, illegal ones grey out, and a ghost shows the result's new stats and range.
- **Why merging is a real decision, not automatic:**
  - A tier is worth **2.2×** the tier below it in damage. Two T1s → one T2 is only +10% total damage, but it frees a pad and puts the power in one spot.
  - Two T1s on different bends cover twice the road. One T2 covers one stretch hard. Swarms punish concentration, bosses punish spreading.
  - Tier 3 unlocks the hero's **special**, tier 5 its **signature**. Merges are breakpoints, not just bigger numbers.
- **The evolution moment (tier 5).** Reaching tier 5 is the biggest event in a run:
  - The game freezes for 1 second: no time passes in the rules, so the pause never costs you anything. The hero glows, transforms into its tier-5 art, and lets out a **shockwave** that deals 3× its damage to every enemy in range and pushes them back slightly.
  - Shockwave and push-back are real rules, not just visuals.
  - Tier 3 gets a smaller version: a 0.3 s flash and a ring, with no freeze.
  - Setting "Evolution scenes: full / short". Short is a 0.3 s flash with the same shockwave, for players who've seen it many times.

## 4. Moving

- Drag a hero to an empty pad to move it. Allowed at any time, but the hero **stops attacking for 1.5 s** while it repositions. Moving is a tool (dodging a boss slam, chasing a flier path), not free.

## 5. Economy (Aether)

| source | amount |
| --- | --- |
| Start of a run | 60 (enough for 3 summons: 10+20+30) |
| Kill | per enemy: 1 basic, 2 armored or fast, 5 miniboss |
| Wave clear | 15 + 2 per wave number |
| **Interest** at wave end | +1 per 10 Aether you're holding, max +5 |

Two ways to use Aether pull against each other every wave: **summon now** (board presence) or **hold** (interest and a reserve for the boss). Interest is the reason saving is ever smart. Without it, the best play is always "spend everything", which is dumb.

**Interest must be seen.** At wave end a coin pops next to the Aether counter: "+4 interest (40 saved)". Interest unlocks at level 4 with a one-line tip. **Test rule:** if testers don't notice it or never save on purpose, it is removed rather than explained harder.

## 6. Combat and targeting (where most games look stupid)

- Every hero has a **range circle**, an **attack speed** and a **damage type**: Physical or Magic.
- **Targeting is smart by default.** New players never have to touch it. Changing it is an advanced tool that **unlocks at level 8**, introduced as a new power.
- **Targeting modes**, default set by role, tap a hero to change (after level 8):
  - **First**: the enemy closest to the castle (default for most).
  - **Strongest**: highest current HP (tank-breakers).
  - **Cluster**: the spot that hits the most enemies (splash).
  - **Weakest**: lowest HP in range (finishers).
- **No overkill.** Heroes track damage already in flight. If an arrow will already kill a goblin, the next hero picks a different target. Three archers never waste three shots on one dying enemy.
- **Projectiles home in.** If the target dies mid-flight, the shot retargets the next enemy within a short distance, or fizzles visibly. No shots hitting empty air.
- **Ground vs air.** Flying enemies take a straight line to the castle, shown as a dotted line, ignoring the road. Some heroes can't hit air (the golem). That's a deck and placement decision, shown on the hero card with an icon.
- **Armor**: Physical damage is reduced by armor, Magic ignores it. Magic-shell enemies are the opposite. Every enemy type has a clear answer.

## 7. Heroes in the slice (6, all art exists)

| hero | role | type | targets | special at T3 | signature at T5 |
| --- | --- | --- | --- | --- | --- |
| Vale Arrow (archer) | fast single target | Physical | ground + air, First | every 4th shot pierces | volley of 5 arrows every 6 s |
| Emberwing (phoenix) | splash | Magic | ground + air, Cluster | burning ground for 3 s | firestorm on a road stretch |
| Cairn Warden (stone golem) | tank breaker | Physical | ground only, Strongest | hits shred armor | slam stuns everything in range |
| Volt Spear (storm spearman) | chain | Magic | ground + air, First | chain +1 target | every chain stuns 0.3 s |
| Sira Frostfang (ice wolf rider) | control | Magic | ground + air, First | slow 30% | freeze 1 s every 5th hit |
| Luma Grace (healer) | support | — | — | heroes on **adjacent pads** attack 15% faster | castle heals 1 HP per wave |

Luma makes adjacency a placement puzzle. Start deck: any 5; the 6th unlocks from the first chest.

## 8. Enemies in the slice (art exists)

| enemy | class | what it asks of you |
| --- | --- | --- |
| Skitter Goblin | basic | anything, splash is efficient |
| **Rabble** (goblin art at 55% size) | **swarm**: tiny HP, packs of 20–40 | splash and chain heroes; single-target heroes drown |
| Ironhide Boar | armored, slow, tanky | Magic or armor shred |
| Nightwing Brood | flying, fast, fragile | anti-air heroes near the castle side |
| Prism Crawler | magic shell | Physical damage |
| Split Slime | splits into 2 on death | splash, or the fragments leak |
| Mirecap | heals nearby enemies every 3 s | kill it first (Weakest/First focus) |
| War Banner Captain (miniboss, wave 5) | speeds up nearby enemies | burst it down |
| **Root Titan (boss, wave 10)** | see §9 | |

Each leak hits the castle for the enemy's **leak value**. The castle has **100 HP**, with 4 visual states (art exists).

| enemy | leak value |
| --- | --- |
| Rabble | 1 |
| Basic | 5 |
| Boar, Crawler, Mirecap, Slime | 10 |
| Brood (flying) | 4 |
| Miniboss | 25 |
| Boss | everything left |

**Swarm waves.** Some waves are a horde of 80–150 Rabble arriving in packs, mixed with a few normal enemies.
- They exist to be melted by splash and chain heroes; this is the screen-filling moment for videos.
- A swarm leak is 1 HP each, so a few leaks hurt but don't end the run.
- Performance rule: 200 enemies on screen at 60 fps on the test phones. They're drawn as a batch, and the Rabble have no individual HP bars.

## 9. Bosses: telegraphed, counterable, never random

Root Titan, three moves on a fixed rhythm, each with a **2.5 s warning drawn on screen**:
- **Root Slam**: a pad glows red, then roots that hero for 6 s. *Counter*: move the hero away (1.5 s pause beats a 6 s root).
- **Bark Skin**: 50% physical resist for 5 s, shown as a bark shell. *Counter*: Magic heroes, or saving burst.
- **Sapling Call**: spawns 4 basic enemies behind it. *Counter*: splash coverage behind the boss.

Nothing a boss does is random, and nothing permanently destroys a hero. Fixes "roulette wheel of a boss".

## 9a. The Flank Switch (signature mechanic, prototype)

On fork maps the road splits into a **left flank** and a **right flank** at a switch, and the two join again before the castle. A big lever sits at the fork.

- **Tap the lever** to send enemies down the other flank. Only enemies that haven't reached the fork yet are affected. Enemies already on a flank finish it, and fliers ignore roads completely.
- **Cooldown 4 s** after each flip, shown as a ring around the lever, so the switch is a timing decision, not a button to spam.
- **Why it's a real decision:**
  - Flanks have different pads and lengths. The long flank exposes enemies to more heroes but you need heroes built there. The short one is quick but needs strong heroes.
  - Splitting a wave across both flanks (flip mid-wave) spreads the load but needs defense on both sides.
  - Swarm waves want your splash flank; armored waves want your Magic flank.
  - The next-wave preview tells you what's coming, so you can plan which flank to build up.
- **Boss interaction:** a boss may **jam** the switch for 6 s, warned 2.5 s ahead like every boss move. Flip before it jams.
- **Readability:** an arrow on the road shows the current direction; the lever glows when ready; enemies that will take the switched path flash once when you flip.
- **Rollout:** first appears in Map 1, levels 7–9, as a prototype. If testers find it fun, it becomes the core of the game and Map 2 onward; if not, it's removed and nothing else depends on it.
- **Bots** in the balance simulator get a switch policy too (flip toward the flank with more damage for the next enemy type), so fork levels are tuned like any other.

## 10. Waves and boons

- A wave ends when all its enemies are dead or leaked. Waves are **not timed**, so you're never punished by a clock you can't see.
- Between waves: the **next wave preview** (enemy icons and counts), then **choose 1 of 3 boons**. Then press Start. There's no timer; it's a planning break.
- **Boons only offer what fits your deck** (no "Emberwing +50%" if Emberwing isn't in it), so a choice is never dead. One free reroll per run, one more via an optional ad.
- Slice boon list (12): Thrift (summon cost step 10→7) · Bounty (+1 Aether per kill) · Deep Pockets (interest cap +5) · Long Bow (archer range +25%) · Ember Seeds (burn ×2) · Armor Breaker (Physical ignores half armor) · Overcharge (Volt chains +2) · Frost Nova (Sira freeze every 5th hit) · Rally (Luma bonus +10%) · Merge Rush (merging refunds 5 Aether) · Second Wind (castle +25 max HP and heal 25) · Twin Flank (heroes on directly opposite pads +15% damage).

## 11. Winning, losing, stars

- Win: survive wave 10. Lose: castle at 0.
- Stars: ★ win, ★★ castle ≥ 50%, ★★★ no leaks.
- **Losing teaches**: the result screen names the main cause from real run data ("6 Brood leaked: your anti-air was on the spawn side"; "Boss Bark Skin blocked 4,000 physical damage") and suggests one fix.
- Revive once per run via an optional ad (castle back to 50 HP). If the ad fails to load, the revive is still granted.

## 11a. Daily challenge (at launch)

- **One level a day, the same for everyone**: same map, waves, seed, boons offered and a **fixed deck at equal hero levels**. Collection power doesn't matter; only skill does.
- The seed comes from the date (UTC), so no server is needed to create it.
- **Score**: waves cleared, then castle HP left, then time.
- **Leaderboards** through Game Center (iOS) and Google Play Games (Android): free, no server of our own.
- **One scored attempt per day**; practice runs are unlimited but don't score. No paid or ad extra attempts, so the leaderboard stays fair.
- Reward: a small chest for playing, a better one for the top 10%.
- Unlocks after level 5, so new players learn first.

## 12. Progression (meta)

- Win → chest → **hero shards** (unlock new heroes) and **coins** (permanent hero levels).
- Hero levels are small and capped: +3% damage per level, max level 10 (+30%). Levels **never reset**, and if we ever rebalance a hero, upgrades are refunded.
- New heroes are **sidegrades**: new roles and new combos, never just bigger numbers. No power creep.
- **Launch has only two currencies: coins and hero shards.**
- **Gems** (premium) come later, together with cosmetics: skins, extra boon rerolls, chest keys. Never sold as raw power.

## 13. Content plan (built for 100 levels and beyond)

- Heroes, enemies, maps, levels, boons and waves are **data files**, not code. A new hero = art + one data file (+ a small script only for a truly new mechanic).
- Levels vary by **map** (road shape, pad layout), **enemy mix**, and **modifiers** ("fog: ranges −20%", "double fliers", "rich: +50% Aether, cost step +15"). Never HP-only scaling, and never recycled level cycles.
- Plan: 10 maps × 10 levels = 100, delivered in batches after the first map is polished. New heroes, villains and maps keep coming after that.

## 14. Money (fair by design)

- **Never** an ad during a run. Optional rewarded ads only: revive, double chest, extra boon reroll.
- **Remove ads**: one cheap purchase.
- Free x2 speed. No energy system. No PvP at launch, so spending never beats another player.
- Cloud save (Game Center / Google Play Games) and Restore Purchases from day one.

## 15. Feel rules

- Every action answers within 100 ms with motion and sound: summon (portal → drop → settle), merge (pull → flash → reveal), hit (flash + number), kill (pop + Aether flies to the counter).
- The board must read in 3 seconds at phone size: hero tier is visible on the sprite, enemy HP bars appear only when damaged, damage numbers are capped so they don't hide the road.
- The game pauses automatically when the app goes to the background and resumes exactly where it was.

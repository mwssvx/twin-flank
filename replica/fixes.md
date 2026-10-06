# What players hate, what's missing, what's unsolved — and how Twin Flank answers it

Sample: 1,497 App Store reviews (official RSS feed, US, most recent 500 per app, de-duplicated):
Rush Royale 498 (Feb–Oct 2026), Random Dice 499 (Jan 2024–Oct 2026), Dice vs Monsters 500 (Apr 2025–Oct 2026).
One source only (App Store), so every theme is marked "thin" by the ranker. Counts are regex matches, so treat them as rough. Full tables: `feedback-*.md`.

## 1. What they hate

| # | problem | evidence | quote |
| --- | --- | --- | --- |
| 1 | **Ads interrupting play** | DvM: 361 of 500 reviews mention ads (avg 1.6★); 93 mention ads mid-game | "Why not place the ads after the stage?" ([DvM 1★](https://apps.apple.com/us/app/id6504301485?see-all=reviews#review-12722896088)); "the ad broke the wave and you can’t complete the stage." ([DvM 2★](https://apps.apple.com/us/app/id6504301485?see-all=reviews#review-13593831277)) |
| 2 | **Pay-to-win / spending decides fights** | RR 98 of 498 (avg 2.4★); DvM 58; RD 25 | "stopped overpowering the new unit (only to nerf it right after the next new unit comes out)" ([RR 5★](https://apps.apple.com/us/app/id1526121033?see-all=reviews#review-14440990311)) |
| 3 | **Luck decides, and streaks feel rigged** | RD 60 RNG reviews; RR 23; DvM 38 | "You can't make me believe that after summoning 20+ times I got the same dice in a row fairly." ([RD 1★](https://apps.apple.com/us/app/id1462877149?see-all=reviews#review-13870037165)) |
| 4 | **Unfair PvP matchmaking** | RR 36; RD 34 | "matched against someone that was like 500% higher on damage percent" ([RR 4★](https://apps.apple.com/us/app/id1526121033?see-all=reviews#review-14595518263)) |
| 5 | **Balance churn: your upgraded unit gets nerfed** | RR 44; RD 46 | "they’ll nerf it b/c you’re doing good with it" ([RR 1★](https://apps.apple.com/us/app/id1526121033?see-all=reviews#review-13858152442)) |
| 6 | **Bosses that randomly wreck your board** | RD 14 difficulty-or-boss reviews (thin) | "that roulette wheel of a boss." ([RD 4★](https://apps.apple.com/us/app/id1462877149?see-all=reviews#review-12925243650)) |
| 7 | **Bugs, crashes, connection losses** | DvM 70; RD 52; RR 20 | — |
| 8 | **Dumb targeting wastes shots** | 1 review, but it describes a core logic flaw | "The attacks target the closest minion ... you spread your attacks out against them all instead of targeting the weakest one" ([DvM 2★](https://apps.apple.com/us/app/id6504301485?see-all=reviews#review-12619624073)) |

## 2. What is missing

- **New content instead of recycled levels**: "the level cycle just repeats, with 12 being the same as 1" ([DvM 2★](https://apps.apple.com/us/app/id6504301485?see-all=reviews#review-12938665844)).
- **Speed-up without paying**: "pay $13 to double the speed" ([DvM 1★](https://apps.apple.com/us/app/id6504301485?see-all=reviews#review-12812177995)).
- **Save and restore purchases across reinstalls**: "no account linking to save historical game data" ([DvM 1★](https://apps.apple.com/us/app/id6504301485?see-all=reviews#review-13270875974)).

## 3. What is unsolved (positioning)

- **A skill-first merge TD with no PvP pressure to pay.** Players praise skill when they see it: "you can’t buy skill" ([RD 5★](https://apps.apple.com/us/app/id1462877149?see-all=reviews#review-11329678856)); "with the strategy aspect it’s more engaging than other mobile games" ([RR 4★](https://apps.apple.com/us/app/id1526121033?see-all=reviews#review-14338483710)).
- **Endgame that stays interesting once you're strong**: "Once I get a certain set of dice the game becomes 'easier'." ([RD 5★](https://apps.apple.com/us/app/id1462877149?see-all=reviews#review-11378674215)).

## Fix plan for Twin Flank

| # | rule we build | fixes | size |
| --- | --- | --- | --- |
| 1 | **No forced ads during a run, ever.** Only opt-in rewarded ads at natural breaks (revive once, double chest, reroll boons). One cheap "Remove ads" purchase. If an ad fails, the player still gets the reward. | hate #1 | S |
| 2 | **Solo PvE only at launch. Permanent upgrades are small and capped; new heroes are sidegrades, not power creep. No nerfs to things people upgraded without a refund.** | hate #2, #4, #5 | M |
| 3 | **Shuffle-bag summoning with a "Next" preview.** All 5 deck heroes come up once per 5 summons, in random order, so no streaks; you always see what's coming. | hate #3 | S |
| 4 | **Bosses telegraph and can be countered**: a 2–3 s warning on the exact pad or road section, with a player response (drag the hero away, save Aether for a burst). Nothing random destroys your board. | hate #6 | M |
| 5 | **Smart targeting by role**: First (closest to gate) by default, Strongest for tank-breakers, Cluster for splash, Weakest-in-range for executes. Tap a hero to switch its target mode. | hate #8 | S |
| 6 | **Free x2 speed from level 1.** | missing | S |
| 7 | **Local save every wave + Game Center / Google Play cloud save and Restore Purchases.** | missing, hate #7 | M |
| 8 | **Levels differ by map, enemy mix and modifiers, never by HP inflation alone.** No recycled level cycles. | missing, unsolved | L (content) |

## The angle

> For merge tower-defense players **who are tired of losing to whales, luck and ads**, Twin Flank **is a skill-first merge defense where you choose where every hero stands, see what's coming, and never get an ad in the middle of a fight.**
> Evidence: ads (DvM 361 reviews), pay-to-win (RR 98), RNG (RD 60).

Alternatives considered:
- "The merge tower defense where your heroes stay yours": a merge never turns your hero into a random one, and an upgrade is never nerfed away. Evidence: RR balance (44) plus RNG.
- "Tower defense you can see": a real road, real towers; what the genre's ads show is what you play (user's own reference, p3).

Recommended: the first. It is the strongest evidence and it shapes the whole design (no PvP, no mid-run ads, visible next summon).

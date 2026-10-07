# Twin Flank — Roadmap to Launch and Beyond

_Written 7 October 2026. This is the working plan. Game rules live in `DESIGN.md`; the research behind them in `replica/`._

---

## Where things stand

- **Decided:** rebuild Twin Flank as an original, skill-first merge defense. Portrait mobile, solo PvE, no ads during a run, no pay-to-win. TypeScript + PixiJS, shipped to iPhone and Android with Capacitor.
- **Done:**
  - Research: 1,497 App Store reviews of Rush Royale, Random Dice and Dice vs Monsters, ranked into what players hate (`replica/fixes.md`).
  - Game rules with real numbers (`DESIGN.md`).
- **Assets we already own** (from the Unity project, `~/Merge towers`):
  - 20 painted heroes × 5 tiers, plus portraits.
  - 20 enemies, plus boss phase art.
  - Castle in 4 damage states.
  - 38 effect sprites.
  - UI icons, rarity frames and pads.
  - One map plate (1080×1920).
  - 7 placeholder sounds and 1 music loop.
- **Archived:** the Unity project stays in git (`e650683`, `a7feb98`) and is not developed further.
- **Not started:** any game code, store accounts, the name check.

---

## How to read this plan

- **Stages go in order.** Each stage ends with a **Gate**, a test it must pass before the next stage starts. Steps inside a stage can mostly run in parallel.
- **Owner:** **You**, **Claude**, or **Both**.
- **Size** (Claude's build effort): **S** = within one work session, **M** = one or two sessions, **L** = several.
- **⭐ = easy to forget, costly to skip.**
- **Your check** = you play it on your phone and tell me what feels wrong. This is the one part I can't do for you.

## Principles for every decision

1. **Polish one thing before adding the next.** Map 1 must be finished and feel great before Map 2 exists. This is what went wrong with Cursor: 100 levels on paper, none of them good.
2. **Rules before pictures.** The game logic is built and tested on its own first, so the visuals never decide who wins.
3. **Fair by design.** No ads in the middle of a fight, no paid power, no hidden difficulty changes, no random board-wrecking.
4. **Every session ends with something you can see**: a screenshot, a short video, or a link you can open on your phone.
5. **Content is data.** A new hero, enemy, map or level is a data file and art, not new code.
6. **Measure, don't guess.** A balance simulator plays thousands of runs; analytics show where real players quit.
7. **Original.** Never copy another game's names, art, UI layout, sounds or numbers.

## Targets

| area | target |
| --- | --- |
| Frame rate | 60 fps on iPhone 11 and a ~$150 Android phone; never below 45 fps in a boss fight |
| Load time | Under 4 s from tap to the home screen on a mid phone |
| Download size | Under 120 MB at launch |
| Stability | 99.5% crash-free sessions |
| Readability | A new player can say what's happening on the battle screen within 3 seconds |
| Tutorial | 80% of new players finish level 3 |
| Retention (testers) | Day 1 ≥ 35%, Day 7 ≥ 12%. Small samples, so treat these as signals, not proof |

---

## Stage 0 — Foundations

- [ ] **0.1 Project setup.**
  - Vite + TypeScript + PixiJS v8, ESLint, Vitest (logic tests), Playwright (screen tests).
  - Folders: `src/sim` (rules), `src/view` (drawing), `src/ui` (menus), `src/data` (content files), `src/platform` (phone features), `tools/`.

  **Claude · S**
- [ ] **0.2 Asset import pipeline.** A script that:
  - copies the painted art out of the Unity project;
  - trims empty borders and sets every hero's anchor at its feet;
  - packs sprite sheets and converts big backgrounds to WebP;
  - makes phone and tablet sizes.

  Re-runnable whenever art changes. **Claude · S**
- [ ] **0.3 ⭐ Art audit.**
  - Check every sprite the first slice needs: style, scale between tiers, feet position, and how readable it is at phone size.
  - Check that `map_01_plate` works as a battle map, or whether we need a new one.
  - Output: a "have / fix / make" list (Appendix B).

  **Both · S**
- [ ] **0.4 ⭐ Name check for "Twin Flank".**
  - App Store and Google Play search.
  - Trademark search: USPTO, WIPO Global Brand Database, EUIPO.
  - Domain and TikTok/Instagram handles.
  - Not legal advice; if we sell seriously, ask a lawyer.

  **Both · S**
- [ ] **0.5 ⭐ Store accounts and payouts.** Start now, because approvals take days to weeks.
  - **Apple Developer Program**, $99/year. The same account also covers Jıyın.
  - **Google Play Console**, $25 one time.
  - **Check that you can be paid in your country and with your bank**:
    - Apple: Paid Apps agreement, banking, tax forms.
    - Google Play: merchant/payments profile. Not every country can sell in-app purchases, so check before relying on it.
    - AdMob: payment method.

  If one of these is blocked, we change the money plan early, not after launch. **You**
- [ ] **0.6 App identity.** Bundle ID (e.g. `com.twinflank.game`), version scheme (`1.0.0`, build numbers), product IDs for purchases. **Claude · S**
- [ ] **0.7 Working rhythm.**
  - Each session: one goal, a commit, a screenshot or video, and a line in the Progress log at the bottom of this file.
  - A hosted preview link (Vercel) so you can open the latest build on your phone any time.

  **Claude · S**

**Gate:** the project runs in the browser showing the map and one hero; the asset script works; the accounts are applied for.
**Estimate:** 2 sessions.

---

## Stage 1 — The rules engine (no graphics yet)

Everything in `DESIGN.md` §2–§10, as pure logic that runs without a screen. This is the part that decides whether the game feels smart or dumb.

- [ ] **1.1 Simulation core.**
  - Fixed tick at 30 per second, so results never depend on frame rate.
  - Seeded random numbers, so the same seed plus the same moves give the same result.
  - All player actions are commands (summon, place, merge, move, set target, pick boon, start wave), checked before they happen.

  **Claude · S**
- [ ] **1.2 Map model.**
  - The road as a curve with distance markers; pads with positions; the straight path that fliers take.
  - **Pad value:** how much road each pad covers at each range. Used by the hint system, the bots and level design.

  **Claude · M**
- [ ] **1.3 Heroes.**
  - Stats per tier (2.2× per tier), attack timing, Physical/Magic damage, range, ground/air.
  - The tier 3 special and tier 5 signature.
  - Luma's adjacency buff.

  **Claude · M**
- [ ] **1.4 ⭐ Smart targeting.**
  - First, Strongest, Cluster and Weakest modes.
  - **No overkill:** heroes track damage already in flight.
  - Homing shots that retarget or fizzle.
  - Tap-to-change mode.

  **Claude · M**
- [ ] **1.5 Enemies.**
  - Movement by distance along the road.
  - Armor, magic shell, flying, healer aura, splitting on death, the miniboss speed aura.
  - Status effects (slow, stun, burn, root) with clear stacking rules: same effect refreshes, never stacks forever.

  **Claude · M**
- [ ] **1.6 Economy.**
  - Rising summon cost.
  - Shuffle bag: 2 of each deck hero, never 3 in a row.
  - Next preview, kill and wave rewards, interest (+1 per 10 held, max +5).
  - Merge and move rules, including the 1.5 s move pause.

  **Claude · S**
- [ ] **1.7 Waves and bosses.**
  - Wave scripts with spawn groups.
  - The miniboss.
  - The Root Titan's three telegraphed moves on a fixed rhythm, with warnings sent to the screen 2.5 s ahead.

  **Claude · M**
- [ ] **1.8 Boons.**
  - Modifiers that hook into the rules.
  - Deck-aware offers, so a choice is never dead.
  - One free reroll per run.

  **Claude · M**
- [ ] **1.9 Content files and validation.**
  - Heroes, enemies, maps, waves, boons and levels as JSON, checked against schemas when loaded.
  - A broken file stops the game with a clear message instead of misbehaving.

  **Claude · S**
- [ ] **1.10 ⭐ Rule tests** (about 60). Examples:
  - A summon never lands on an occupied pad and never spends Aether without placing.
  - Merges only work for the same hero and tier, and the hero stays on the target pad.
  - No 3 of the same hero in a row.
  - No overkill.
  - The same seed played 100 times gives the identical result.
  - The boss never permanently removes a hero.

  **Claude · M**
- [ ] **1.11 ⭐ Balance simulator and bots.** A command that plays thousands of runs per level with different bot styles:
  - "spam summon";
  - "merge everything";
  - "smart", which uses pad value, counters enemy types and picks good boons.

  It reports win rate, castle HP left, leaks per wave and the Aether curve, and flags levels that are trivial or impossible. Every level gets tuned with it. **Claude · L**

**Gate:**
- All rule tests pass.
- On level 1, the smart bot wins ≥ 90% and the spam bot wins 20–50%. Mindless play should lose sometimes, good play almost never.
- I send you a one-page balance report.

**Estimate:** 7–9 sessions.

---

## Stage 2 — First playable battle

- [ ] **2.1 Renderer.**
  - Portrait 1080×1920 design size, scaled to any phone, with safe areas.
  - Layers: ground, road, pads, units sorted by depth, shots, effects, HUD.

  **Claude · S**
- [ ] **2.2 Map 1 on screen.**
  - Map plate, pads, castle, spawn portal.
  - A developer overlay that shows the road path and pad value.

  **Claude · S**
- [ ] **2.3 Sprites and scale rules.**
  - A hero is about 1.3× a pad's width, standing on it, not floating in front.
  - Each tier is slightly bigger with a stronger glow, and the tier is visible at a glance.
  - Enemies are scaled by class.

  **Claude · S**
- [ ] **2.4 Smooth motion.**
  - Drawing interpolates between rule ticks.
  - Enemies face the way they walk, with a small walking bob.

  **Claude · S**
- [ ] **2.5 ⭐ Touch controls.**
  - Tap SUMMON, then pads glow with the hero's range circle, then tap a pad.
  - Drag to merge or move, with a ghost preview and legal targets lit.
  - Tap a hero to open the targeting wheel.
  - Every touch target is at least 44 points; dragging must feel right with a thumb.

  **Claude · M**
- [ ] **2.6 HUD v0.** Aether, SUMMON with its price, Next preview, wave, castle HP, x2 speed, pause. **Claude · S**
- [ ] **2.7 ⭐ Automatic screenshot runs.** A script plays a scripted battle in a phone-sized browser and saves screenshots at key moments. Every later session compares against them, so nothing breaks unnoticed. **Claude · S**

**Gate:**
- A full 10-wave run plays in a phone-sized browser with no console errors.
- Screenshots attached.

**Your check:** play 2 runs on your phone from the preview link; tell me what confused you.
**Estimate:** 4–5 sessions.

---

## Stage 3 — Feel and art pass (make Map 1 beautiful)

The stage Cursor never managed. Nothing new is added; everything is made to feel good.

- [ ] **3.1 Motion.** GSAP (now free) for timing curves:
  - summon: portal 80 ms → drop 180 ms → squash and settle 160 ms;
  - merge: pull 90 ms → flash with a 50 ms hit-stop → reveal 180 ms with a small overshoot;
  - drag lift and tilt, a shake on an illegal drop, and a quick dash when moving.

  **Claude · M**
- [ ] **3.2 Combat feel.**
  - Each hero has a small wind-up and recoil.
  - Shots use the painted effect sprites by damage school, with impact sparks and a white hit flash.
  - Damage numbers are pooled and capped; crits look different.
  - Deaths pop, and the Aether reward flies to the counter.

  **Claude · M**
- [ ] **3.3 Readability.**
  - Enemy HP bars only when damaged; armor and shell icons.
  - Fliers have a shadow and a dotted path; healers pulse.
  - Boss warnings are drawn on the exact pad or road stretch.
  - Leaks show a red line to the castle and the castle cracks.

  **Claude · M**
- [ ] **3.4 Ambience.** Drifting leaves, light shafts, a soft vignette, a gentle castle glow, a subtle camera shake on leaks and boss hits (can be switched off). All of it fades back when combat gets busy. **Claude · S**
- [ ] **3.5 Sound v1.**
  - About 40 sound effects with random pitch and variations (Appendix C).
  - Limits so 20 arrows don't sound like noise.
  - A music loop for Map 1 with a boss layer, and music ducking for big moments.

  **Both · M** (you approve the music)
- [ ] **3.6 UI kit.**
  - One style for buttons, panels, chips, cards and the boon card: deep navy, warm gold, crystal cyan.
  - Two free fonts with commercial licenses (OFL): one bold for actions, one easy to read for numbers.
  - I write image prompts for missing pieces; you generate them in ChatGPT; I cut them out and fit them in.

  **Both · M**
- [ ] **3.7 Map 1 art.** If the existing plate can't carry the polish, a new painted map with the road and pad spots drawn in. Same prompt workflow. **Both · M**
- [ ] **3.8 ⭐ Performance budget.**
  - Every repeating object is pooled, textures stay under 150 MB, and there are no frame hitches.
  - Measured on the slowest phone we have, not on the Mac.

  **Claude · S**
- [ ] **3.9 ⭐ Polish review.**
  - Side-by-side screenshots against the concept art.
  - A raw 30-second screen recording that should already look good enough for a store trailer.

  **Claude · S**

**Gate:** every item in the Polish checklist (Appendix I) passes.
**Your check:** you play and write down 5 things that feel off; we fix until you have nothing to write.
**Estimate:** 8–10 sessions.

---

## Stage 4 — A complete run

- [ ] **4.1 Levels 1–10 of Map 1.** Wave scripts tuned with the simulator. Each level adds one idea; level 10 is the Root Titan. **Claude · M**
- [ ] **4.2 Boons screen.** 3 cards, deck-aware, a reroll, and 12 boon icons. **Both · M** (icons via prompts)
- [ ] **4.3 Between waves.**
  - Next-wave preview (enemy icons and counts), the boon pick, then a Start button.
  - No timer, so the break is for planning.

  **Claude · S**
- [ ] **4.4 Boss and miniboss.**
  - Root Titan with its telegraphs and counters.
  - War Banner Captain's speed aura.
  - Boss music and an entrance moment.

  **Claude · M**
- [ ] **4.5 ⭐ Results screen that teaches.**
  - Stars and rewards.
  - The main cause of a loss, worked out from the run's data, plus one suggestion. Example: "7 Brood leaked: no anti-air near the castle. Try Vale Arrow on the lower pads."

  **Claude · M**
- [ ] **4.6 Pause menu.** Restart, quit, settings, x2 speed, and automatic pause when the app goes to the background. **Claude · S**
- [ ] **4.7 Revive.** Once per run, castle back to 10 HP. Free for now; later an optional ad (Stage 8). **Claude · S**
- [ ] **4.8 ⭐ Resume after the app is killed.** The run is saved at the start of every wave and continues from there. **Claude · S**

**Gate:**
- All 10 levels pass their simulator win-rate bands.
- Killing the app mid-run and reopening resumes the wave.

**Your check:** play levels 1–10. Say which felt too easy, too hard or boring.
**Estimate:** 5–6 sessions.

---

## Stage 5 — The game around the battle

- [ ] **5.1 Home screen.** Painted scene, a big Play button for your next level, the chest slot, and a few icons. One main action, no clutter. **Both · M**
- [ ] **5.2 Level path.** 10 level nodes per map on a painted path, with stars and the boss node. **Both · M**
- [ ] **5.3 Heroes screen.**
  - Collection cards in rarity frames; locked heroes as silhouettes.
  - Hero detail: all 5 tier arts, stats, role, ground/air icons, what the T3 and T5 abilities do, and level up with coins.

  **Claude · M**
- [ ] **5.4 Deck builder.** Pick 5. Warns but never blocks, e.g. "No anti-air in this deck". **Claude · S**
- [ ] **5.5 Chests and rewards.**
  - Chest tiers with **odds shown**; shards and coins.
  - Duplicates turn into coins.
  - The first chest (after level 3) always unlocks Luma Grace.

  **Claude · M**
- [ ] **5.6 Currencies.**
  - Coins (earned) for hero levels, capped at +30%.
  - Gems (premium, later) only for cosmetics, rerolls and chest keys.

  **Claude · S**
- [ ] **5.7 ⭐ Save system.**
  - Local save with a version number and upgrade steps for old saves.
  - Safe writes (never half-saved) and a backup copy.

  **Claude · S**
- [ ] **5.8 ⭐ Economy check.** Simulate coin income against upgrade costs, so a free player never hits a wall before level 30 and maxing a hero takes weeks, not years. **Claude · S**

**Gate:** a fresh install through level 10, unlocking a hero, upgrading and changing the deck, all survives an app restart.
**Estimate:** 6–8 sessions.

---

## Stage 6 — First-time experience, settings, languages

- [ ] **6.1 Tutorial woven into play.** Level 1: summon and place. Level 2: merge. Level 3: targeting and boons. Short hints with hands and arrows, no walls of text, skippable. **Claude · M**
- [ ] **6.2 Contextual hints.** The first time fliers appear: "Fliers ignore the road. Use heroes with the wing icon." Shown once each. **Claude · S**
- [ ] **6.3 Settings.** Music, sound, haptics, screen shake, reduced flashing, damage numbers, language, restore purchases, privacy policy, support contact, credits. **Claude · S**
- [ ] **6.4 ⭐ Accessibility.**
  - Damage types and enemy traits use shape and color, so they're color-blind safe.
  - Larger text option; reduced motion.

  **Claude · S**
- [ ] **6.5 Languages.**
  - All text in translation files from day one.
  - English and Russian at launch; Kyrgyz optional.
  - You review the Russian and Kyrgyz.

  **Both · M**
- [ ] **6.6 Haptics.** Light tap on summon, double on merge, heavy on a leak; can be switched off. **Claude · S**

**Gate:** 2–3 people who've never seen the game finish level 3 without help. You watch silently and note where they hesitate.
**Estimate:** 4–5 sessions.

---

## Stage 7 — On real phones

- [ ] **7.1 Capacitor apps.** iOS and Android projects, app icon, splash screen, portrait lock. **Claude · S**
- [ ] **7.2 Screens.** Notches and safe areas, aspect ratios from 16:9 to 20:9, an iPad layout that isn't a stretched phone. **Claude · S**
- [ ] **7.3 Sound on phones.** Audio unlocks on first touch, low latency, respects the mute switch, and pauses for calls. **Claude · S**
- [ ] **7.4 ⭐ Device performance pass.** Test on the oldest phones we target (iPhone 11 class and a ~$150 Android) and fix what's slow. **Both · M** (you have the phones)
- [ ] **7.5 App lifecycle.** Pause in the background, resume, handle low memory, no lost progress. **Claude · S**
- [ ] **7.6 Test builds.** TestFlight (needs 0.5) and Google Play internal testing. Every build numbered and noted in the Progress log. **Both · S**
- [ ] **7.7 ⭐ Crash and error reporting.** Sentry (free tier) with readable stack traces, so we know about crashes before reviews do. **Claude · S**

**Gate:** 30 minutes of play on a low-end Android with no crash, about 50+ fps, and the phone not getting hot.
**Estimate:** 3–4 sessions.

---

## Stage 8 — Money and services

- [ ] **8.1 Rewarded ads (AdMob), opt-in only.**
  - Used for revive, double chest and an extra boon reroll. Never during a wave.
  - If an ad fails, the player still gets the reward.

  **Claude · M**
- [ ] **8.2 ⭐ Consent and tracking rules.**
  - Google's consent form for Europe and the UK.
  - Apple's tracking prompt only if we use personalized ads.
  - Settings that match what the privacy labels say.

  **Claude · S**
- [ ] **8.3 Purchases via RevenueCat** (free until $2.5k/month revenue).
  - **Remove ads** (about $2.99–4.99) and a cosmetic starter pack.
  - Restore Purchases, tested in Apple and Google sandboxes.

  **Both · M** (you create the products in the store consoles)
- [ ] **8.4 ⭐ Cloud save.**
  - Game Center (iOS) and Google Play Games saved games, so a new phone or reinstall keeps progress and purchases.
  - Clear rule when two saves differ: keep the one with more progress.

  **Claude · M**
- [ ] **8.5 Analytics.** GameAnalytics (free, made for games). Events in Appendix G; funnels for tutorial, levels 1–10 and revive use. **Claude · S**
- [ ] **8.6 ⭐ Privacy policy, terms, support page.** One small website (Vercel) with a support email. Lists exactly what the ads, analytics and crash tools collect. **Claude · S**
- [ ] **8.7 Remote balance file.** Level and economy numbers fetched from the website, with a safe fallback built in, so balance fixes don't need an app review. **Claude · S**

**Gate:**
- Ads work with test IDs.
- Purchase and restore work in sandbox.
- The consent form appears from a European IP.
- Analytics events arrive.
- The privacy policy is live.

**Estimate:** 5–6 sessions.

---

## Stage 9 — Prove it before scaling

- [ ] **9.1 ⭐ Google Play closed test.** New personal Play accounts must run a closed test with at least 12 testers for 14 days before they can publish (check the current rule). Start it the day the first Android build exists, because it blocks launch. **You**
- [ ] **9.2 TestFlight beta.** External testers need a short Apple beta review. **Both**
- [ ] **9.3 Feedback loop.** A Telegram group plus an in-game "Send feedback" button that attaches the level and device. **Claude · S**
- [ ] **9.4 ⭐ The ad test ($100).**
  - 3 short vertical videos (15–20 s) built from **real gameplay**, with an AI-made hook in the first 2 seconds.
  - Run them on TikTok and Instagram.
  - Measure stop rate, click rate, cost per click and cost per install.
  - I capture and cut the gameplay; you make the hooks and run the ads.

  **Both**
- [ ] **9.5 ⭐ Go / no-go review.**
  - Tutorial completion ≥ 80%, level 3 reached ≥ 70%, Day-1 return ≥ 35%, crash-free ≥ 99.5%, and what testers say.
  - Decide together: launch, fix first, or rethink.

  **Both**

**Gate:** the go decision, written down with the numbers.
**Estimate:** 2 sessions, plus 2–3 weeks of waiting for testers.

---

## Stage 10 — Launch content and store page

- [ ] **10.1 Launch content.** Built with the editor from 12.1 once it exists; until then by hand with the simulator.
  - **Maps 1 and 2 (20 levels)**, 8 heroes, 10 enemies, 2 bosses.
  - Map 2 brings a loop road, Prism Crawler, Shieldbone, Gearshot Brann and the Bell Bastion boss.
  - All tuned with the simulator and played by you.

  **Both · L**
- [ ] **10.2 Store listing.**
  - Name, subtitle, short and long description in English and Russian, keywords.
  - 6–8 portrait screenshots for the required iPhone sizes, plus Android phone screenshots and a Google Play feature graphic.
  - A 15–30 s app preview video captured from the game itself.

  **Both · M**
- [ ] **10.3 ⭐ Store forms.**
  - Age rating questionnaire (fantasy violence, ads).
  - Apple App Privacy labels and the Google Play Data safety form.
  - Target audience 13+, to stay out of Google's Families rules with ads.
  - Encryption export answer (standard HTTPS only, so exempt).
  - Content rights (we own or license all art, fonts and sounds).

  **Both · S**
- [ ] **10.4 App store search basics.** Keywords like merge, tower defense, TD, heroes, strategy, offline; localized; no competitor names anywhere. **Claude · S**
- [ ] **10.5 Landing page.** One page with the trailer, store links, privacy and support. **Claude · S**

**Gate:** both store listings approved in review and ready to release.
**Estimate:** 6–8 sessions.

---

## Stage 11 — Launch

- [ ] **11.1 Quiet launch.** Release in both stores with no ads for the first 1–2 weeks, and fix whatever real players break. Apple's 7-day phased rollout and a staged Android rollout limit the damage. **Both · S**
- [ ] **11.2 Launch push.**
  - The best creative from 9.4 gets the remaining ad budget.
  - Weekly TikTok/Instagram devlog clips: real merges, boss fights, "making of" with you.
  - Honest posts in tower-defense communities that allow self-promotion.

  **You**
- [ ] **11.3 First weeks.** Daily crash check, reply to every review, fast fixes. Optional over-the-air updates for small fixes (Capacitor live updates, within store rules). **Both**
- [ ] **11.4 Look back.** What worked, what the numbers say, what to build next. **Both · S**

**Estimate:** 2 sessions, plus your posting time.

---

## Stage 12 — 100 levels and beyond

- [ ] **12.1 ⭐ Level editor** (in the browser).
  - Draw the road, drop pads and decorations, write waves.
  - **Run the simulator right in the editor** and see win rates before saving.
  - Exports the data files.
  - This is what makes 100 levels affordable.

  **Claude · L**
- [ ] **12.2 Content updates every 3–4 weeks.** Each: 1 map (10 levels), 1 new hero, 1–2 new enemies or a boss, new boons. Plan to level 100 in Appendix D. **Both**
- [ ] **12.3 New systems, in this order.**
  1. Daily challenge: the same seed for everyone, with a leaderboard.
  2. Endless mode.
  3. Hero active abilities.
  4. Pets (specs for 20 already exist).
  5. Weekly event modifiers.
  6. Cosmetic skins and the gem shop.
  7. Achievements.

  **Both**
- [ ] **12.4 PvP only if it's fair.** If we ever add it: asynchronous (racing another player's recorded run), with hero levels equalized. Never a reason to pay. **Both**
- [ ] **12.5 Live tools.** An events calendar driven by the remote file, plus a dashboard of where players quit. **Claude · M**

---

## Timeline (estimate, not a promise)

| stages | sessions | what you'll have |
| --- | --- | --- |
| 0–2 | 13–16 | a playable battle on your phone |
| 3–4 | 13–16 | Map 1 polished, 10 full levels |
| 5–8 | 18–23 | a complete app on TestFlight / Google Play testing |
| 9 | 2 + 2–3 weeks | real tester numbers, ad test results |
| 10–11 | 8–10 | launch with 20 levels |
| 12 | ongoing | +10 levels about every 3–4 weeks → level 100 about 8 updates after launch |

At about 3 sessions a week, launch is roughly **5–6 months** away. More sessions make it faster; skipped gates make it worse, not faster.

---

## Appendix A — Tech stack

| need | choice | why |
| --- | --- | --- |
| Language | TypeScript | catches mistakes early; one language for game, tools and website |
| Rendering | PixiJS v8 (WebGL/WebGPU) | fast 2D sprites, made for this kind of game |
| Motion | GSAP | free, precise timing curves for polish |
| Sound | Howler.js (Web Audio) | sound pools, sprites, mobile unlock |
| Build | Vite | instant reloads while I work |
| Phone apps | Capacitor | one codebase for iOS and Android, native plugins |
| Logic tests | Vitest | runs the rules engine in milliseconds |
| Screen tests | Playwright | plays the game in a phone-sized browser and screenshots it |
| Content checking | Zod schemas | catches broken data files before the game runs |
| Ads | AdMob (Capacitor plugin) + Google consent form | rewarded ads only |
| Purchases | RevenueCat | handles Apple and Google purchases and restore; free to start |
| Cloud save | Game Center / Google Play Games | no accounts or passwords for players |
| Analytics | GameAnalytics | free, made for games |
| Crashes | Sentry | free tier, readable errors |
| Website | Vercel | privacy policy, support page, remote balance file |

## Appendix B — Art: have, fix, make

| item | status | for |
| --- | --- | --- |
| 6 slice heroes × 5 tiers + portraits | **have**, audit scale and feet | Stage 2 |
| Heroes 7–20 | **have** | later maps |
| 20 enemies + boss phases | **have** | all |
| Castle × 4 states (Map 1) | **have** | Stage 2 |
| Map 1 battle plate | **have**, verify quality (0.3) | Stage 2 / 3.7 |
| 38 effect sprites (14 schools + common) | **have** | Stage 3 |
| Icons (coin, gem, shard, heart, settings, profile), rarity frames, pads, HP bars | **have** | Stage 2–5 |
| Button set, 9-slice panels, chips, boon card frame | **make** | 3.6 |
| 12 boon icons | **make** | 4.2 |
| Logo and app icon | **make** | 3.6 / 7.1 |
| Chests (3 tiers, closed and open) | **make** | 5.5 |
| Home screen scene, level path background | **make** | 5.1 / 5.2 |
| Map 2 plate + castle × 4 | **make** | 10.1 |
| Store screenshots frames, feature graphic | **make** | 10.2 |

**Art rules:**
- Every new image is generated against the same style reference (`Tools/ai_art/style_ref.png` in the Unity project), cut out cleanly, and checked next to existing art before it's used.
- Keep the prompts in `art/prompts/`, so the style stays the same for years of updates.

## Appendix C — Sound list (about 40 effects + music)

- **UI:** tap, confirm, deny, open panel, close panel, reward tick, coin.
- **Building:** summon portal, hero lands, merge pull, merge reveal (pitch rises with tier), move dash, illegal drop.
- **Combat:** one attack sound per hero (6), one impact per damage school (6), crit accent, enemy death (3 variations), split slime pop, healer pulse.
- **Danger:** leak hit, castle crack, boss warning, boss slam, boss roar, miniboss horn.
- **Flow:** wave start horn, wave clear chime, boon pick, victory, defeat, chest open, chest reveal.
- **Music:** menu theme, Map 1 loop, boss layer, victory sting, defeat sting.
- **Sources:**
  - CC0 libraries (Kenney, CC0 on Freesound) and royalty-free bundles (Sonniss GDC).
  - Or AI music on a plan whose terms allow commercial use.
  - Every file and its license is listed in `CREDITS.md`.

## Appendix D — Content plan to level 100

| map | levels | road idea | new enemy | hero unlocked | boss |
| --- | --- | --- | --- | --- | --- |
| 1 Emerald Highlands | 1–10 | S-curve, teaching map | Goblin, Boar, Brood, Slime, Mirecap, Banner Captain | Luma Grace (first chest) | Root Titan |
| 2 Amberwood Circuit | 11–20 | loop: enemies pass pads twice | Prism Crawler, Shieldbone | Gearshot Brann | Bell Bastion |
| 3 Frozen Observatory | 21–30 | ice lanes speed enemies up | Frost Matriarch | Coralynn | Frost Matriarch (empowered) |
| 4 Cinder Caldera | 31–40 | lava pads burn heroes (avoid or accept) | Molten Burrower (tunnels) | Nox Crescent | Pyrewing Rex |
| 5 Moonlit Mire | 41–50 | fog shrinks ranges | Void Imp (blinks) | Hex Veyr | Astral Serpent |
| 6 Prism Caverns | 51–60 | **two roads**, a true twin flank | Mirror Sentinel (reflects) | Astra Prism | Mirror Sentinel Prime |
| 7 Clockwork Dunes | 61–70 | a bridge that rotates each wave | Stone Tusk | Tikket | Stone Tusk Colossus |
| 8 Coral Causeway | 71–80 | tide covers road stretches | (new art) | Thornroot | (new art) |
| 9 Gravesong Terrace | 81–90 | spirits skip a road stretch | Spectral Gatebreaker | Eira Echo | Spectral Gatebreaker |
| 10 Eclipse Citadel | 91–100 | everything combined | — | Null Monk | The Last Hour (rewinds time) |

Rules:
- Each map teaches one new idea.
- Each level differs by road, enemy mix and modifiers, never by HP alone.
- Every level passes the simulator before you play it.
- Names reuse the existing art; anything marked "new art" needs generating.

## Appendix E — Money you'll spend

| item | cost | when |
| --- | --- | --- |
| Apple Developer Program | $99/year (shared with Jıyın) | Stage 0 |
| Google Play Console | $25 once | Stage 0 |
| Ad test + launch ads | $100–300 | Stages 9 and 11 |
| Sound/music (optional) | $0–60 | Stage 3 |
| Domain (optional) | $0–15/year | Stage 8 |
| RevenueCat, Sentry, GameAnalytics, AdMob, Vercel | $0 at our size | — |
| **Total** | **about $225–500** | |

## Appendix F — ⭐ Store and legal checklist (the forgotten stuff)

- [ ] Privacy policy URL and support URL, live before submission.
- [ ] Age rating questionnaire (Apple) and content rating (IARC on Google Play).
- [ ] Apple App Privacy labels; Google Play Data safety form; both must match what the ad, analytics and crash tools collect.
- [ ] Google consent form (EU/UK); Apple tracking prompt only if used.
- [ ] Target audience 13+; no kids category while there are ads.
- [ ] Restore Purchases button (Apple requires it).
- [ ] All purchases through the store's own billing.
- [ ] Screenshots and preview video show real gameplay (Apple requires previews captured from the app).
- [ ] No competitor names in the title, keywords or ads.
- [ ] Encryption export question (standard HTTPS only, so exempt).
- [ ] Banking and tax forms (Apple and Google) and AdMob payments set up.
- [ ] Google Play: 12-tester closed test for 14 days; current target API level.
- [ ] Apple: built with the currently required Xcode/SDK.
- [ ] Trademark check on the name; licenses recorded for fonts, sounds and art in `CREDITS.md`.
- [ ] AI art: confirm the image tool's terms let you use outputs commercially.
- [ ] Not legal advice: talk to a lawyer before spending real money on marketing.

## Appendix G — Analytics events

`app_open` · `tutorial_step` · `level_start` (level, deck) · `wave_end` (wave, castle HP, leaks, Aether held) · `boon_offered` / `boon_picked` · `summon` (cost) · `merge` (hero, tier) · `boss_telegraph_dodged` · `level_end` (result, stars, main loss cause, duration) · `revive_offered` / `revive_used` · `chest_opened` · `hero_unlocked` / `hero_upgraded` · `ad_offered` / `ad_watched` / `ad_failed` · `purchase` · `settings_changed`.

No personal data, no names, no exact location. Listed in the privacy policy.

## Appendix H — Risks

| risk | how likely | what we do |
| --- | --- | --- |
| Web-based game runs slow on cheap Androids | medium | performance budget from Stage 3, tested on a cheap phone in Stage 7; heavy effects scale down automatically |
| Store payouts or Google selling not available in your country | medium | check in 0.5; if blocked, lean on ads, publish via an eligible entity, or adjust |
| New art doesn't match the old style | medium | one style reference, saved prompts, side-by-side check before use |
| Balance feels off after launch | high | simulator plus remote balance file: fix without an app update |
| Scope creep ("just one more feature") | high | stage gates; new ideas go to Stage 12, not the current stage |
| Apple rejects the app | low–medium | follow Appendix F; original name and art; real screenshots |
| Long breaks kill momentum | medium | small sessions, a preview link always ready, Progress log so we pick up instantly |
| Few players find the game | high | honest ad test before scaling, devlog clips, store search basics; accept that this is a long game |

## Appendix I — Polish checklist (Stage 3 gate, re-checked before launch)

- [ ] Every tap gets a visible and audible reaction within 100 ms.
- [ ] Summon, merge, move, attack, hit, death and leak each have anticipation → action → settle.
- [ ] The battlefield reads in 3 seconds: road, pads, castle HP, what's coming next.
- [ ] Heroes stand on their pads at a consistent scale; the tier is clear at a glance.
- [ ] No shot ever hits empty air or a dead enemy.
- [ ] Damage numbers never hide the road; at most a capped number on screen.
- [ ] Boss warnings are impossible to miss and always fair.
- [ ] An illegal action always says why (shake plus a short message).
- [ ] No hitches: steady 60 fps on the test phones, also in the boss fight.
- [ ] Sound has variety (no machine-gun repetition) and a sensible mix.
- [ ] Every screen follows the UI kit: same buttons, panels, fonts and spacing.
- [ ] Text never overflows or gets cut off, in English and Russian.
- [ ] Nothing important sits under the notch or the home bar.
- [ ] Pausing, backgrounding and resuming never break a run.
- [ ] A raw 30-second recording looks good enough to be an ad.

---

## Progress log

| date | stage | what changed | evidence |
| --- | --- | --- | --- |
| 2026-10-06 | — | Research (1,497 reviews) and game rules written | `replica/`, `DESIGN.md` |
| 2026-10-07 | — | This roadmap | `ROADMAP.md` |

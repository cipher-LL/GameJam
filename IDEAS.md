# GameJam — Brainstorm

A scratchpad for game ideas. The goal: a **very simple, dopamine-inducing singleplayer Android game** we can release on the Play Store as a learning exercise. We're optimizing for:

- **Simple** — single screen, touch-only, no networking
- **Dopamine-inducing** — instant feedback, easy wins, satisfying feedback loops
- **Cheap to build** — no custom art, minimal code, finishable in a week
- **Completeable** — actually finish and ship, not just a prototype

This file is a brainstorm. Ideas get added freely, then filtered down to one we prototype.

---

## 1. Goals & constraints

| Must have | Should have | Won't have (v1) |
|-----------|-------------|-----------------|
| Single screen | Daily reward loop | Networking |
| Touch-only input | Sound effects | Account system |
| Offline playable | Score persistence | Multiplayer |
| Run-length: 1-10 min | Haptic feedback | Custom art (use primitives or free assets) |
| Feels good in 30 sec |  | |

The hardest constraint is the "no custom art" — many addictive games rely on juicy sprites/particles. We'll lean on **motion, color, and screen-shake** to compensate.

---

## 2. Addictive archetypes

Categories of singleplayer games that have proven dopamine loops:

- **Auto-battler with choice** — passive combat + meaningful choices between rounds (Slay the Spire, Dicey Dungeons, Balatro, Luck be a Landlord)
- **Idle/incremental** — progress accumulates over time, even while away (Cookie Clicker, Adventure Capitalist, Idle Miner Tycoon)
- **Endless reflex** — tap/swipe at the right moment, run ends on failure (Flappy Bird, Color Switch, Helix Jump)
- **Endless runner** — swipe to dodge, world gets harder (Temple Run, Subway Surfers)
- **Merge/2048-style** — combine tiles, ramp up, "one more try" (2048, Threes, Royal Match)
- **Match-3** — swipe to align, cascades, combos (Candy Crush, Royal Match)
- **Tower defense** — place units, watch them fight (Bloons TD, Kingdom Rush)
- **Stack/build** — physics-based stacking, momentum (Stack, Build a Bridge)
- **Rhythm/timing** — tap to the beat, lose rhythm and fail (Beat the Boss, Geometry Dash)

For our v1, the best candidates are archetypes with **simple visuals** and **short rounds** (so players can play "one more" easily). Idle games and match-3 are the most visually forgiving.

---

## 3. Dopamine mechanics catalog

The psychology ingredients. Stack 2-3 of these in a game and it's usually addictive.

- **Variable ratio rewards** — rewards come after a random number of actions, not a fixed schedule (slot machine, loot boxes)
- **Progress bars filling** — a visible "you're 60% to the next thing" drives completion compulsion
- **Streak counters** — "you've won 5 in a row, don't break it" (loss aversion)
- **Prestige** — reset progress for a permanent multiplier (idle games)
- **Near-miss psychology** — "you almost got the rare drop" (slot machine reels stopping one short)
- **Juice** — particles, screen shake, sound, slow-mo on impact. The "feel" of a hit
- **"Just one more" loops** — short round length, fast restart, no penalty for ending
- **Cascading rewards** — one good thing leads to another (Candy Crush combos, "kill two with one" effects)
- **Audio dopamine** — satisfying sound on success, escalating pitch on combo
- **Anticipation** — show the reward coming before it arrives (slot machine reel slowing down, level-up bar filling)

---

## 4. Game ideas

Each idea is intentionally tight (3-5 bullets) so we can scan them. The first three are **auto-battle with upside/downside choice** variants, since that's the most promising direction.

### Idea A — **Risk & Run**

Auto-battle survival with per-round risk/reward choices.

- **Core loop:** fight an auto-battle (no input during the fight). Win → choose 1 of 3 powers, each with a clear upside AND a clear downside. Lose → run ends, you collect the "souls" you earned for permanent upgrades.
- **Why it works:** combines two dopamine sources: the satisfaction of winning an auto-battle (no skill, just momentum) and the meaningful choice of which tradeoff to take. The downsides force interesting decisions; the upsides compound.
- **Example choice:** "Deal 50% more damage" + "Take 30% more damage", vs. "Heal to full after each fight" + "Enemies deal 20% more damage each round", vs. "Gain 2x souls" + "Max HP halved"
- **Complexity:** low. 1 screen, 3 buttons per round, a number-ticker for HP/damage. Auto-battle logic is a simple damage formula.
- **Android-feasibility:** perfect. No art needed — just numbers, color bars, and some particle effects on hit.

### Idea B — **Card Climb**

Auto-battle with deck-building via 2-pick-1 each round.

- **Core loop:** each round is an auto-battle against a stronger enemy. Win → see 2 cards, keep 1, discard the other. Cards are abilities that fire during the auto-battle (heal on hit, deal bonus damage at low HP, gain armor for one round, etc.).
- **Why it works:** the "2-pick-1" mechanic forces commitment. Every card you skip is gone forever, but the one you take defines your build. The auto-battle plays out your build, so you watch your decisions matter.
- **Complexity:** medium. Need card art (or just icons + colors), a small deck system, and per-card battle effects.
- **Android-feasibility:** good if we use simple colored squares for cards. The deck-building itself is the dopamine, not the visuals.

### Idea C — **Greed Gauntlet**

Auto-battle where you choose whether to RISK your winnings for a bigger payoff.

- **Core loop:** auto-battle 5 enemies in a row. After each win, choose: **Cash out** (save your winnings to your run total) or **Press on** (next enemy is harder, but payout doubles). If you die, you lose all un-cashed winnings. Cash out at the end and buy permanent upgrades.
- **Why it works:** pure loss aversion + greed. The "press on" choice is a metagame on its own — when do you cut your losses?
- **Complexity:** low. Just a number going up and a yes/no decision.
- **Android-feasibility:** very good. The whole game is a number animating up and a "Press on" / "Cash out" prompt.

### Idea D — **Tapper's Gambit**

Tap-based reflex game with per-round upgrades.

- **Core loop:** round starts, a sequence of taps appears (e.g., a circle to tap, a fast swipe to dodge). Do it perfectly → win + choose 1 of 3 buffs (e.g., "taps are 30% bigger", "slower sequence", "double points"). Miss a step → lose a life.
- **Why it works:** active engagement (you have to be good at the tap game) + meaningful choice after each win. The buffs change the difficulty curve.
- **Complexity:** medium. Need a tap-target system and a sequence generator.
- **Android-feasibility:** good but the tap game needs some animation polish to feel good.

### Idea E — **Idle Clicker with Prestige**

Tap to earn, upgrade, prestige, repeat.

- **Core loop:** tap a big button to earn coins. Spend coins on auto-clickers, multipliers, etc. After hitting a milestone, **prestige**: reset everything for a permanent boost. Add new tiers of upgrades.
- **Why it works:** classic. The prestige loop is a built-in "start over but better" dopamine source. Numbers go up, that's the whole game.
- **Complexity:** low to medium. Mostly UI work — number displays, upgrade buttons, a prestige button.
- **Android-feasibility:** perfect. No art needed, just numbers and a few colored buttons.
- **Risk:** this is a very well-trodden genre. Hard to stand out, but very easy to ship.

### Idea F — **2048-Style Merge with Twist**

Merge tiles until they overflow, with a twist mechanic chosen at start.

- **Core loop:** classic 2048 swipe-to-merge. Twist: at the start of each run, choose a "rule" (e.g., "all merges give +1 to a second number", "swipe in a circle to spawn a free tile", "merges give you a 'time slow' charge"). The twist changes the strategy.
- **Why it works:** the twist means each run is a new puzzle. The merge mechanic itself is the proven dopamine hit.
- **Complexity:** medium. 2048 is well-trodden code (you can port a JS implementation easily).
- **Android-feasibility:** good.

### Idea G — **Endless Avoid**

Single-finger dodge game.

- **Core loop:** a character moves automatically. Tap to jump/swap lanes to dodge obstacles. Each milestone (every 10s?) gives a small choice — e.g., "smaller character (harder to dodge, more points)" vs "slower obstacles" vs "lives +1".
- **Why it works:** one-finger mobile is the standard. The mid-run choice adds depth without complicating the core reflex game.
- **Complexity:** medium-high. Needs sprite animations, obstacle generation, collision.
- **Android-feasibility:** moderate. The "no custom art" rule bites here.

### Idea H — **Rhythm Tap**

Tap to a generated rhythm.

- **Core loop:** generated beat plays, circles fall to a target line, tap when they hit. Miss → lose. Get to a checkpoint → choose 1 of 2 modifiers ("bigger target", "slower scroll", "double points but harder patterns").
- **Why it works:** rhythm + choice is a strong combo. Music is the dopamine; choices add depth.
- **Complexity:** high. Need a beat generator, a music engine, accurate timing.
- **Android-feasibility:** moderate. Music licensing is a concern for Play Store.

---

## 5. Filtering criteria

To pick the idea we prototype, we score against these:

| Criterion | Weight | Why |
|-----------|--------|-----|
| **Single screen, no scrolling** | high | mobile form factor, easy to build |
| **No custom art needed** | high | we're not artists; "juice" can be done with particles + color |
| **< 1 week of dev time** | high | learning exercise, not a year-long project |
| **Auto-battle + upside/downside choice** | high | this is the direction we want to explore |
| **Touch-only input** | medium | standard for mobile |
| **Sound: optional or trivial** | medium | no music licensing headaches |
| **Tested on cheap Android phones** | medium | Play Store is broad, not just flagships |
| **No networking, no accounts** | medium | privacy + scope |

If an idea fails any "high weight" criterion, drop it.

---

## 6. Current leading candidate

**Idea A — Risk & Run** is the front-runner:
- Hits every "high weight" criterion.
- The auto-battle + upside/downside mechanic is exactly the design we want to explore.
- Pure numbers + color → no art blocker.
- Run length is naturally short (a few minutes), perfect for "one more".
- Permanent souls currency gives a meta-loop that survives dying.

Ideas B (Card Climb) and C (Greed Gauntlet) are close seconds — same mechanic, different framing. We should prototype **all three back-to-back** to see which feels best in actual play, then commit to one.

---

## 7. Open questions to decide before coding

1. **Engine:** native Android (Kotlin/Java) or a cross-platform engine (Flutter, React Native, Godot, Unity)? Native is the simplest for our scope; Godot or Flutter are also reasonable.
2. **Sound:** do we want procedural sound (Web Audio API-style, generated at runtime) or do we record a few hits ourselves?
3. **Persistence:** local SharedPreferences/SQLite? Do we want a "high score" badge?
4. **Difficulty curve:** how quickly do the auto-battles scale? What's the "soft cap" before runs get tedious?
5. **Run-end state:** do we show a recap of the choices you made? (Probably yes — it's a meta-source of "what if I had picked the other one" dopamine.)
6. **Ads / IAP:** Play Store apps often have ads. Do we want a banner ad, or a single rewarded ad for "revive"? Skip for v1 to keep scope tight.
7. **What makes the downsides fair?** If the downside is "you take 30% more damage" but the upside is "50% more damage", that's only a buff when you're winning anyway. We need to design the tradeoffs to feel meaningful — sometimes the obvious choice is wrong.

---

## 8. Next steps (once we pick an idea)

1. **Prototype in HTML/JS first.** Just a single file with the core loop playable in a browser. Validate the feel before committing to a stack.
2. **If it feels good, port to Android.** Pick the engine based on the prototype's complexity.
3. **Ship the simplest possible version.** One screen, one mode, no extras.
4. **Add features in v1.1 only if we have fun playing it ourselves.**

---

## 9. Backlog of ideas (parking lot)

Anything we dismiss or defer to v2:
- Multiplayer leaderboards (networking, accounts)
- Daily challenges (needs server or device-time tricks)
- Skin shop (art, not in scope for v1)
- Multiple game modes (premature)
- Story / narrative (overkill)

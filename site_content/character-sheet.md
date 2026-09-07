# Character Sheet Formulas

How every number on your character sheet is worked out: the stat block carried by an item or a prefix, the derived stats, HP and MP with their per-class constants and level bands, the level-50 Health bonus, the percentage pipeline that quest and pet bonuses run through, and the weapon proc.

These are the formulas the site's own character planner uses.

---

## 1. The stat vector — 27 slots

An item or a prefix stores its bonuses as a packed string of 27 positions,
always in this order.

| # | Stat | # | Stat | # | Stat |
|---|---|---|---|---|---|
| 0 | Strength | 9 | MDMin | 18 | NonElemental |
| 1 | Health | 10 | MDMax | 19 | Curse |
| 2 | Intelligence | 11 | OTP | 20 | Flame dmg |
| 3 | Wisdom | 12 | Evasion | 21 | Ice dmg |
| 4 | Agility | 13 | Defense | 22 | Lightning dmg |
| 5 | HP | 14 | Absorb | 23 | Poison dmg |
| 6 | MP | 15 | Fire | 24 | Paralyzis |
| 7 | PDMin | 16 | Ice | 25 | HP% |
| 8 | PDMax | 17 | Lightening | 26 | Mana% |

A mixing stone uses a different order: **28** positions, the same up to 24 and then
**25 = enemy defence, 26 = HP, 27 = mana**. Read a stone with the item order and
every one of its effects comes out as the wrong stat.

Decoding it yields **3,537** item stat rows across 704 items and **229**
prefix stat rows across 102 prefixes — which is where the stats on every item
and talisman page come from.

Worked example — Intensified Steel Armor stores `||||||||||||15|36|4`:
positions 12, 13 and 14 are filled, so the item gives **Evasion 15, Defense 36,
Absorb 4**.

### The one encoding exception, recorded rather than guessed

Thirty-one positions across **nine Mix Master stones** (Stone of Flame, Ice,
Lightening, Poison, Paralyzis, Strength, Skill, Mystery, Demons Blood) run past
position 26 and contain commas. Those carry **two comma-separated sets of
effects in the mixing order**, not one. They are read as two rather than cut down
to one; what the second set means is **not confirmed**.

---

## 2. Class ordering

Classes are numbered `0 Archer · 1 Knight · 2 Magician ·
3 Thief`. That is alphabetical, and the game's own class table agrees with it. Every
per-class constant below is resolved through this ordering, and all eight
HP and MP denominators land on known values under it and under no other
ordering, which is what confirms it.

---

## 3. Derived stats

`Lv` is character level. `Gear`, `Misc`, `Quest%` and `Pet%` are what your
equipment, buffs, quest bonuses and pet contribute.

```
OTP      = Fix(0.2777778 × Str) + Fix(Agi / 8) + gearOTP + miscOTP
Evasion  = Fix(Agi / 3) + gearEva + miscEva
PDMin    = Fix((Str − 10) × 11 / 30) + Fix((Agi − 5) / 11) + Fix(Lv × 7 / 10) + 2
PDMax    = Fix((Str − 5) × 8 / 15)   + Fix((Agi + 17) × 11 / 47) + Lv − 3
MDMin    = Fix((Int − 8) × 7 / 12)   + Fix(Wis / 7)
MDMax    = Fix(Int × 7 / 12)         + Fix(Wis × 0.31249) − 3
```

`0.2777778` is 15/54, so OTP reproduces the community reimplementation's `15×Str/54 + Agi/8` exactly.

## 4. HP and MP

```
HP = Fix( (52 × Lv / 3 × coeffHP + Hea² × qHP[class] + 115) × (1 + HP% / 100) ) × flag
     + lateHeaBonus
MP = Fix( (8 × Lv + Wis² × qMP[class] + Wis + 140) × (1 + Mana% / 100) )
     + Lv × mpBand × 2

coeffHP:  Lv ≥ 81 → 1.765 · ≥ 76 → 1.5 · ≥ 72 → 1.305 · else 1.0
mpBand:   Lv ≥ 81 → 3     · ≥ 76 → 2   · ≥ 72 → 1     · else 0
```

| Class | `qHP` | as `2/deno` | `qMP` | as `2/deno` |
|---|---|---|---|---|
| Archer | 2/13 | deno 13 | 1/6 | deno 12 |
| Knight | 1/5 | deno 10 | 2/13 | deno 13 |
| Magician | 1/7 | deno 14 | 1/5 | deno 10 |
| Thief | 2/13 | deno 13 | 1/6 | deno 12 |

**All eight denominators are confirmed twice over**, by two readings that were made
independently of each other. It also confirms the level bands:

- `52 × 1.305 = 67.86` against the community reimplementation's `67.8162` at level ≥ 72
- `52 × 1.5 = 78` against `78` at level ≥ 76 — **exact**
- `52 × 1.765 = 91.78` against `91.758` at level ≥ 81
- MP: `(8 + 2×mpBand) × Lv` gives 8 / 10 / 12 / 14 — **exactly** the community reimplementation's
  `coeff_MP`, at the same level thresholds

KalEncyclopedia stops at the level-81 band; the engine formulas continue with
bands at 86, 91 and 96, which this source simply does not cover (it is a 2011
tool). The `+115` HP constant and the `+140 + Wis` MP constants are confirmed.

### Two mechanics worth knowing

**A level-50+ Health bonus on HP.** On top of the formula above:

```
band          = clamp( Fix((Lv − 50) / 5) + 1, 0, 5 )
lateHeaBonus  = Fix( Fix(Hea² × qHP[class]) × (0.14 + 0.1 × band) )
```

So from level 50 the Health quadratic is paid **again**, at 24% at levels 50–54,
rising 10 points per five levels to **64% from level 70 onward**. On a
Health-stacked build this is a large amount of HP, and most guides leave it
out.

**An HP-doubling flag.** The whole pre-bonus HP term is multiplied by
either **×1 or ×2**. What turns it on is **not confirmed**: nothing names it.

---

## 5. Defense, and the percentage pipeline

```
Defense = Fix(baseDef + gearDef + inputDef) + miscDef
if <high-level gate>:                                   # gate not confirmed
    Defense += Fix( (Lv − 65) × 5 + Defense × 2 / 50 )
Defense = Fix( Defense × (100 + Quest%) / 100 × (100 + Pet%def) / 100 )
```

**Defence has no stat-derived base at all** here — it comes entirely from gear and
buffs. That contradicts the common advice that Health raises defence as well as HP.
On this evidence it does not, or at least nothing models it that way. The
disagreement is left standing rather than quietly resolved.

The same two multipliers close every offensive stat:

```
final = Fix( Fix( (base + gear) × (100 + Quest%) / 100 ) × (100 + Pet%) / 100 )
```

with `Pet%` slot 0 applied to PDMin, PDMax, MDMin and MDMax, slot 1 to Defense,
and slot 2 to Evasion. **A pet giving a percentage bonus to damage, defence and evasion is something
most guides never mention.**

A second conditional appears in Evasion, gated the same opaque way:

```
if <gate>:  Evasion += Fix( Evasion × (Lv / 2) / 400 )
```

What switches either gate on is not recorded anywhere. Left **unconfirmed** rather than guessed at.

---

## 6. The weapon proc — "EB"

`CalcEB` is **not** item enhancement. It computes a proc with a chance and a
damage range, from the weapon's own damage columns:

```
physical:  min = Fix( PDMin + ebLevel × 0.05 × PDMin + 3 × k )
           max = Fix( PDMax + ebLevel × 0.10 × PDMax + 3 × k )
magical:   the same over MDMin / MDMax
displayed: "EB Chance : <c>% , EB Damage : <min> - <max>"
```

So the minimum scales at **5% per EB level** and the maximum at **10%**. The
identity of `k`, and how the enhancement level and the proc chance relate to
the enhancement cost table, is **not confirmed** — that table has 16 levels,
and its two requirement series (1,2,2,4,5,7,10,13,21,29,
45,92,188,192,196,200 and 1,3,5,9,14,21,31,44,65,94,139,231,419,611,807,1007)
match neither Bango's `+N` grid nor each other's shape.

# KalOnline_Engine_Formulas.md — The Combat Engine

**Version 3, 2026-07-25.** The original binary's critical path, lookup tables,
PvP divisors and block tables have now been extracted and checked against the
reference implementation.

## Provenance and confidence

| Tag | Meaning |
|---|---|
| `[ORIG]` | Read out of the Hex-Rays decompile of Inixsoft's own `MainSvrT.exe`, 2006 build. **Ground truth for the original engine.** |
| `[REIMPL]` | From `Ollrogge/Bango`, a modern clean-room C++ reimplementation. The author reverse-engineered these; treat as a second opinion, not as authority. |
| `[MOD]` | From private-server mod DLLs. Lowest confidence. |
| `[CONTESTED]` | Two readings disagree and it is not settled. |

**Everything here describes the original 2006 engine.** Rafael plays on **Bango**, a highrate private server of the 2009/2012 lineage running a patched descendant. Shapes are almost certainly intact; **every constant is unconfirmed for Bango until measured.** See `SOURCES.md` for the authority ranking and `KalOnline_Formula_Recovery_Plan.md` Phase 5 for the calibration.

## Corrections incorporated since version 1

1. **Magic does not ignore mitigation — it ignores *defence and absorb*, but resistance is applied, multiplicatively, one stage earlier in the pipeline.** v1 said magic had no mitigation at all. That was drawn from `GetFinalDamage` alone, which is only the last stage. `CMagic::Excute` applies resistance before it. This changes the calibration design: magic is still a clean probe of the attacker side, but only once the target's resistance is known or held constant.
2. **The original critical-hit rule is additive and settled.** The body at
   `0x0043EAC0` returns a bonus and its call site adds that bonus to the normal
   hit. With no fatal-damage stat, the result is exactly **1.5×**. Whether
   Bango retained that constant remains a live-calibration question.

---

## 1. The stat storage pattern `[ORIG]`

Every combat stat exists twice: a **point** value and a **percentage** value.

```c
int CChar::GetMinAttack(CChar *this)
{
    return this->m_prtyPt.nMinAttack
         + this->m_prtyPer.nMinAttack * this->m_prtyPt.nMinAttack / 100;   // integer division
}
```

So `final = points + pct × points / 100`. Two structs, `m_prtyPt` and `m_prtyPer`, hold the same field list. **This is the entire mechanism by which gear, prefixes, enhancement and buffs work** — a buff with `m_nUpType == 1` writes into `m_prtyPt`, one with `m_nUpType == 2` writes into `m_prtyPer`, and `m_nUpType == 3` goes through `UpdateProperty`.

Note this differs from the reimplementation, which uses a flat `m_wXxxAdd` companion instead of a percentage. **The original is authoritative.** Anywhere below that a formula ends in `+ gear`, the real expression is the points-plus-percentage form above.

---

## 2. Derived stats from Str / Hea / Int / Wis / Agi `[REIMPL]`

> **Contradicted in play, 2026-07-25 — do not use the magic lines below.**
> A naked level-38 Magician (Str 8, Hea 70, Int 77, Wis 50, Agi 8) on the Bango
> test server read **MDMin 47 and MDMax 56**. The formulas below give **50 and
> 59** — high by exactly 3 at both ends. The KalEncyclopedia simulator's forms,
> `Fix((Int−8)×7/12) + Fix(Wis/7)` and `Fix(Int×7/12) + Fix(Wis×0.31249) − 3`,
> reproduce the observed values exactly.
>
> Everything else in this section **was confirmed** by the same sheet: OTP 3,
> Evasion 2, PDMax 41, resistances 8/8/8/7/5, and **MaxHP 1473 / MaxMP 994 to
> the point**, which also confirms the Magician denominators, the `+115` and
> `+140 + Wis` constants and `52×Level/3`. `PDMin` read 27, matching the form
> below and beating KalEncyclopedia's, which is high by 1 at Strength 8 and 9.
>
> The measured set is `engine\bango_measured.py`; the observation is
> `calibration\OBSERVED_SHEETS.csv`. Per standing rule 5 the original text is
> left in place rather than overwritten.

```
OTP  (hit)   = Agi/8 + 15×Str/54            + gear
EVA  (dodge) = Agi/3                        + gear
MinAttack    = 1 + (11×Str − 80)/30 + (Agi − 5)/11 + 7×Level/10  + gear
MaxAttack    = (8×Str − 25)/15 + 18×Agi/77 + Level               + gear
MinMagic     = (7×Int − 20)/12 + Wis/7                           + gear
MaxMagic     = 7×Int/12 + 14×Wis/45                              + gear

Resist Fire / Ice / Lightning = Int/9    + gear
Resist Curse                  = Wis/9    + gear
Resist Non-elemental (Palsy)  = Hea/9    + gear
```

**Every division truncates.** `Agi/8` at 39 Agility is 4, not 4.875. Multiply-before-divide is preserved throughout (`15 × Str / 54`, never `15 × (Str/54)`) and that ordering is load-bearing.

Readings:

- **Agility is both the hit stat and the dodge stat**, but dodge is 2.7× more responsive: 1 EVA per 3 Agi against 1 OTP per 8 Agi.
- **Strength buys OTP faster than Agility does** — 15/54 ≈ 1 per 3.6 Str.
- **Intelligence is roughly twice the magic stat Wisdom is** for max magic (7/12 ≈ 0.583 vs 14/45 ≈ 0.311).
- Resistances come free with the caster stats at 1 per 9 points.
- `GetAgi()` reads a member named `m_wDex`. Agility and Dexterity are the same stat under two names — relevant when reading `InitMonster.txt`, which calls it `dex`.

### HP and MP `[REIMPL]`

```
MaxHP = coeff_HP(Level) × Level / 3 + 115 + 2×Hea² / denoHP[class] + gear
MaxMP = coeff_MP(Level) × Level     + 140 + Wis + 2×Wis² / denoMP[class] + gear

coeff_HP: Level ≥96 → 195 · ≥91 → 141.8147 · ≥86 → 111.426 · ≥81 → 91.758
          ≥76 → 78 · ≥72 → 67.8162 · else 52
coeff_MP: Level ≥96 → 20 · ≥91 → 18 · ≥86 → 16 · ≥81 → 14 · ≥76 → 12 · ≥72 → 10 · else 8

denoHP = { Knight 10, Mage 14, Archer 13, Thief 13, Shaman 14 }
denoMP = { Knight 13, Mage 10, Archer 12, Thief 12, Shaman 10 }
class index: 0 Knight · 1 Mage · 2 Archer · 3 Thief · 4 Shaman
```

Two subtleties worth keeping:

- The HP coefficient literals are **doubles**, so `coeff × Level / 3` is floating-point and does *not* truncate; only the final return does. The MP coefficients are integers, so MP is integer arithmetic throughout. The `2×Hea²/denoHP` term truncates in both.
- **The level bands are a later-episode change.** The 2006 build uses a flat `52×Level/3` and `8×Level + 140`. A server on the 2009/2012 lineage very likely has the bands. **Which one Bango uses is a high-priority calibration target** and is trivially checked: HP at level 72 either jumps or doesn't.

**The quadratic term is the whole story.** Health does not add HP linearly. On a Knight, 10→20 Health adds ~60 HP; 90→100 Health adds ~3,800. That is why every saved build in `PL_SAVE.csv` runs Health at or near the top, and it means "how many points in Health" is never answerable by a linear rule of thumb.

### Stat point costs `[REIMPL]`

Cost of raising a stat is the sum of a per-point table indexed by the stat's **current** value — buying N points costs `table[cur] + table[cur+1] + … + table[cur+N−1]`. Two tables exist; each class gets the cheaper one on exactly one stat:

| Class | Discounted stat |
|---|---|
| Knight | Strength |
| Mage | Intelligence |
| Archer, Thief | Agility (Dex) |
| Shaman | *none* |

Health and Wisdom are always full price, for everyone.

| Cost per point | Standard table range | Discounted table range |
|---|---|---|
| 1 | 0–49 | 0–59 |
| 2 | 50–69 | 60–89 |
| 3 | 70–89 | 90–119 |
| 4 | 90–109 | 120–149 |
| 5 | 110–129 | 150–179 |
| 6 | 130–149 | 180–209 |
| 7 | 150–199 | 210–239 |
| 8 | 200–249 | 240–249 |

Tables are 250 entries and neither function bounds-checks, so **250 is the effective stat cap**. Note this makes the discount worth far more than it looks: at value 100 a Knight pays 3 for Strength where anyone else pays 4, and at 150 it is 5 against 7.

---

## 3. The physical pipeline

```
1.  rolled   = Random(MinAttack, MaxAttack)              uniform, inclusive
2.  skill    = per-skill GetAttack(owner, rolled)        adds to the roll; see §6
3.  CheckHit(attacker, target, skillHitBonus)            miss → 0
4.  swing timing scales the damage                       see §5
5.  GetFinalDamage(target, damage, PHYSICAL):
        if PvE:  damage ±= g_nAddDefLv[|levelDiff|]
        damage  −= target.GetFinalDefense(attackType)
        if damage ≤ 0 → 0
        damage  −= damage × target.GetFinalAbsorb() / 100
        buff 0x200 → +10%   else buff 0x40000000 → +7%
6.  crit revision                                        see §5, additive bonus
```

**Defence is subtractive, absorb is a percentage, and the order is defence first.** Flat defence is therefore worth most against many small hits; absorb is worth the same proportion against everything.

`def1` is **close-range** defence and `def2` is **far-range**. The index is the *attacker's* attack type, so `mon_def1` is what a Knight faces and `mon_def2` is what an Archer faces.

The physical level-difference bonus applies **in PvE only** — player-versus-player physical damage has no level term.

```
g_nAddDefLv[0..99] =
  0  0  0  1  1  3  3  6  6  9   9 12 12 15 15 18 18 21 21 24
 24 27 27 30 30 33 33 36 36 39  39 42 42 45 45 48 48 51 51 54
 54 57 57 60 60 63 63 66 66 69  69 72 72 75 75 78 78 81 81 84
 84 87 87 90 90 93 93 96 96 99  99 thereafter
```

### PvP-only defender bonuses `[ORIG]`

When the attacker is a player rather than a monster:

```
FinalDefense = Defense(type) + Level / table1[3×type + class]
FinalAbsorb  = Absorb + 15
FinalResist  = Resist/10 + Level / table2[class] + 25
```

Against monsters: `FinalAbsorb = Absorb`, `FinalResist = Resist/10`, no level term. **Players are flatly 15 percentage points more absorbent and 25 points more resistant against each other than against mobs** — which is why PvP and PvE gear conclusions diverge. The original binary contains the divisor arrays **`{4,4,5,1,5,3}`** and **`{4,1,2}`** at `0x004D9180` and `0x004D9198`.

---

## 4. Magic — corrected `[ORIG]`

This is `CMagic::Excute`, the shared path every offensive spell runs through:

```c
dwReviseTick = CSkill::ReviseTick(this, pOwner);
nResist      = CMagic::GetResist(this, pOwner, pChar);        // a PERCENTAGE MULTIPLIER
v7           = CChar::GetMagic(pOwner);                       // Random(MinMagic, MaxMagic)
nMagic       = this->GetMagic(this, pOwner, v7);              // per-skill virtual, see §6
v8           = dwReviseTick * (nResist * nMagic / 100);       // integer division
v9           = <fatal / net-damage revision virtual>;
pChar->Damage(pChar, pOwner, v8 / v9);                        // integer division
```

and the resistance term:

```c
nDiffLevel = pOwner->m_nLevel - pTarget->m_nLevel;
v3         = pTarget->GetFinalResist(pTarget, pOwner, this->GetResistNum(this));
nResist    = max(0, v3 - nDiffLevel × |nDiffLevel| / 6);      // integer division
return (nResist >= 100) ? 0 : 100 - nResist;                  // as a percentage multiplier
```

So the full magic sequence is:

```
base    = Random(MinMagic, MaxMagic)
value   = skill.GetMagic(owner, base)                 per-skill; caps apply to the skill part only
effRes  = max(0, targetResist − levelDiff×|levelDiff|/6)
damage  = value × (100 − min(effRes,100)) / 100
then GetFinalDamage(MAGIC):  damage += levelDiff × |levelDiff| / 4
                             no defence, no absorb
```

Consequences:

- **Resistance is a straight percentage reduction and it caps out at 100 — a fully resistant target takes zero.** Mob `mon_res1..5` values divided by 10 are what enter this.
- **Level difference enters twice, with opposite sign conventions**: once shrinking effective resistance by `diff²/6`, once adding flat damage by `diff²/4`. Both favour the higher-level attacker, and both are quadratic.
- **Defence and absorb genuinely do not touch magic.** A high-defence, high-absorb, low-resistance target is soft to magic and hard to melee. This is the single most exploitable asymmetry in the game.

---

## 5. Hit, criticals, attack speed

### Hit / miss `[ORIG]`

```
diff      = attackerLevel − defenderLevel,  clamped ±100
levelTerm = sign(diff) × g_nAddOTPLv[|diff|]
total     = skillHitBonus + levelTerm + attackerOTP − defenderEVA,  clamped ±41
chance%   = total ≥ 0 ? g_nHitChance[total] : 100 − g_nHitChance[|total|]
hit       = chance ≥ Random(1..100)
```

MState `0x2000000` short-circuits to an automatic hit. Against monsters, buff `0x4000` adds +10 and `0x20000000` adds +5. Buff `0x8000` on the target gives the attacker −5.

```
g_nHitChance[0..50] =
 50 52 52 54 54 56 56 58 58 60  60 62 62 64 64 66 66 68 68 70
 70 72 72 74 74 76 76 78 78 80  80 82 82 84 84 86 86 88 88 90
 90 95 95 95 95 95 95 95 95 95 95

g_nAddOTPLv[0..100] =
  0  0  0  0  0  1  2  3  4  5   6  7  8  9 10 11 12 13 14 15
 16 17 18 19 20 22 24 26 28 30  32 34 36 38 40 43 46 49 52 55
 58 61 64 67 70 74 78 82 86 90  90 thereafter
```

- **Parity is a coin flip.** Equal OTP, equal EVA, equal level → 50%.
- **+1% per point, saturating hard.** 95% is the ceiling and 5% the floor. Everything past +41 is wasted.
- **Level difference dominates gear.** Under 5 levels the term is exactly zero — so mobs within 4 levels are "level doesn't matter". At 20 levels it is 16 points; at 45 it is **74**, which no realistic gear spread approaches.

The three arrays above were read directly from the original PE at
`0x004D8130`, `0x004D82C8` and `0x004D8398`. Their canonical lengths are 101,
51 and 100 integers; nearby extra zeroes are alignment padding. They match
`engine/kal_engine.py` exactly.

### Criticals `[ORIG]`

`CChar::GetFatalDamage` at `0x0043EAC0` returns:

```
if (skillFatalRate + charFatalRate) ≥ Random(1..100):
    bonus = damage × (2 × critDamageStat + 50) / 100
```

The physical attack call site adds that return value to the normal damage.
Therefore a bare critical is **1.5×**, and each fatal-damage point adds another
2% of the normal hit. The reimplementation cannot corroborate it — its
`GetFatalDamage` is a stub — but the original body and caller settle the 2006
engine.

This remains a Bango calibration target: a matched normal/critical pair should
be exactly 1.5× if the later server retained the rule.

### Attack speed `[ORIG for the accessor, REIMPL for the gate]`

Attack speed values — `mon_attspd`, a weapon's `aspeed` — are **per-swing cooldowns in milliseconds**, not rates.

```
hits per second = 1000 / ASpeed

speedPct ≤ 0:   ASpeed = base × (|speedPct| + 100) / 100
speedPct > 0:   ASpeed = base × 100 / (speedPct + 100)
```

A **positive** speed percentage **divides** the delay. +100% halves the cooldown; it does not double a rate. A 700 ms weapon swings 1.43×/s, and at +50% the C integer result is **466 ms**, or 2.146×/s.

`[REIMPL]` adds a swing gate the decompile has not confirmed: a swing landing before **60% of the cooldown** has elapsed is dropped silently, and between 60% and 100% the damage is scaled linearly by the fraction elapsed. If that is faithful it means attack-speed gear is worth less than the nominal rate suggests whenever you are input-limited rather than cooldown-limited.

---

## 6. The skill system `[ORIG]`

**There is no dispatch switch.** `CPlayerSkill::Open()` consumes a 152-entry
map at `.data:0x4E21A8`, keyed by `(class << 16) + skillIndex`. The map is not
flat data: `sub_4AE930` constructs its entries at startup. The passive
initializer extractor in `research/extract_skill_map.py` recovered every key,
constructor and vtable into `research/skill_map_2006.json`.

Every skill is a C++ class. The base carries:

```c
m_nSkill  m_nLevel(grade)  m_nLmtLevel  m_dwLmtSpecialty  m_nLmtSkill  m_nLmtSkillLevel
m_nLmtMaxLevel  m_nRedistribute  m_nDecMP  m_nLastTime  m_dwDelayPre  m_dwDelay
m_dwActionDelay  m_nV1  m_nV2  m_dwTick  m_nRage  m_nContiCnt
```

`m_nV1` / `m_nV2` are the two generic value slots that `InitSkill.txt` fills. Fatal rate, hit bonus, MP cost, delay and element tag are **virtuals**, so each skill class supplies its own.

**The shared shape of every offensive skill:**

```
final = <capped, grade-scaled, stat-scaled skill term> + <random base attack or magic roll>
```

The skill term is capped; the weapon/gear roll is added **after** the cap, so gear damage is never capped by the skill.

### The three magic masteries are not what they look like `[ORIG]`

`GetResistNum()` is the element tag, and it selects which mastery passive applies:

| Element | Mastery effect |
|---|---|
| **Fire** (0) | Cuts cast delay: `delay −= 5 × masteryPoints × delayPre / 100` |
| **Ice** (1) | Every hit applies a free slow: `CreateBuff(0, points + 2, −20 × points)` |
| **Lightning** (2) | **Flat damage: `+20 × masteryPoints`**, added into the *max* end of the roll |

Lightning Mastery is a straight `+20 damage per point`. That is a very different proposition from a percentage mastery, and it makes the Lightning line's max roll scale with mastery in a way Fire and Ice do not.

---

## 7. Magician skill formulas `[ORIG, verbatim]`

`L` = skill grade (`m_nLevel`), `CL` = character level, `INT`/`WIS` = the character's stats. **Every `/` truncates.** Each result is capped as shown, then the random base roll is added.

### Single target

| Skill (class) | Value | Cap |
|---|---|---|
| Fire Magic (`CFire`) | `(3×CL/2 + 3×L×INT/10)/2` | `21×L + 30`, then `+ base + 2×L` |
| Ice Magic (`CIce`) | `(3×CL/2 + 3×L×INT/13)/2` | `16×L + 30` |
| Hail (`CIceLance`, 2006 label `IceLance`) | `(3×CL/2 + 10×L×INT/4)/2 + 240` | `150×L + 400` |
| Flame Bomb (`CFireExplosion`, 2006 label `FireExplosion`) | `(3×CL/2 + 10×L×INT/3)/2 + 380` | `150×L + 500` |
| Ice Requiem (`CIceRequiem`) | `(3×CL/2 + 2×L×INT/6)/2 + 480` | **500 flat** |
| Explosion (`CFireEruption`, 2006 label `FireEruption`) | `(3×CL/2 + 14×L×INT/3)/2 + 580` | `300×L + 600` |
| Spirit Blast (`CSpiritBlast`) | `(9×CL/2 + 5×L×INT)/2` | `200×L + 600` |

### The Lightning line — rolled min/max, and the only line that picks up mastery

| Skill (class) | Min | Max | Caps |
|---|---|---|---|
| Lightning Magic (`CLitning`, idx 4) | `(3×CL/2 + 2×L×INT/16)/2` | min `+ 20×masteryPts` | min `12×L+30` · max `12×L+180` |
| Shock Wave (`CShock`, idx 9) | `(5×CL/3 + 6×L×INT/4)/2 + 50` | `20×masteryPts + (5×CL/3 + 11×L×INT/3)/2 + 150` | min `60×L+200` · max `200×L+200` |
| Lightning Blow (`CSpark`, idx 23) | `3×CL/2 + (3×L×INT/10)/2 + 10` | **Lightning Magic's own value** + `3×CL/2 + (5×L×INT/8)/2 + 30 + 20×masteryPts` | min `30×L+150` · max `40×L+200` |
| Lightning Summons (`CCallLitning`, idx 31) | `3×CL/2 + 20×masteryPts + (2×L×INT/7)/2 + 320` | `3×CL/2 + 20×masteryPts + (10×L×INT/2)/2 + 320` | min `L + 450` ⚠ · max `200×L+700` |
| Chain Lightning (`CChainLitning`, idx 41) | `3×CL/2 + 20×masteryPts + (7×L×INT/3)/2 + 360` | `3×CL/2 + 20×masteryPts + (10×L×INT/4)/2 + 700` | **700 / 1000 flat** |
| Thunder (`CThunderLitning`, idx 42) | `3×CL/2 + 20×masteryPts + (5×L×(3×INT/2)/3)/2 + 360` | `3×CL/2 + 20×masteryPts + (10×L×(3×INT/2)/2)/2 + 700` | min `154×L+456` · max `300×L+900` |

Two things stand out. **Lightning Blow calls Lightning Magic's `GetMagic` and adds it in** — if `m_pSkill[4]` is null it returns 0 outright. So Lightning Magic's grade feeds directly into Lightning Blow's damage, which makes the existing mage plan's heavy Lightning Magic investment correct for a reason the plan never states. And **Lightning Summons' min cap is `L + 450`**, coefficient 1 where every sibling has a two- or three-digit coefficient — almost certainly an Inixsoft typo that has been in the game for twenty years, and it means the skill's min damage is effectively pinned near 450.

### Area

| Skill | Value | Cap |
|---|---|---|
| Splashy Ice (`CMagicWideIce`, 2006 label `MagicWideIce`) | `(5×CL/3 + 5×L×INT/7)/2` | `40×L + 120` |
| Fire Blow (`CMagicWideFire`, 2006 label `MagicWideFire`) | `(5×CL/3 + 6×L×INT/5)/2` | `70×L + 150`, then `+ base + 8×L` |
| Explosive Burst (`CExplosiveBurst`) | `(6×CL/2 + 4×L×INT/5)/2 + 580` | **900 flat** |

### Healing — Wisdom-scaled, and they do **not** add the magic roll

| Skill | Value | Cap |
|---|---|---|
| Heal (`CHealingAny`) | `30×L + (7×CL/11 + 3×L×WIS/11)/2 + 70 + Random(0, 2×L)` | `40×L + 100` |
| Great Heal (`CHealingAnyPlus`) | `50×L + (8×CL/11 + 5×L×WIS/9)/2 + 500 + Random(0, L)` | `50×L + 650` |
| Restoration (`CRestoration`) | `100×L + 11×WIS/3 + 750 + Random(0,100)` | **1600 flat** |
| Quick Heal (`CHealingAnyQuick`) | `25% of target max HP` | — |
| Instant Heal (`CHealingInstance`) | `(20×L + 15)% of target max HP` | — |
| Great Restore (`CHealingGreatRe`) | **full heal** | none |
| Party Heal (`CHealingParty`) | `60×L + (CL/2 + 8×L×WIS/7)/2 + 100 + Random(0, 10×L)` | `180×L` |

The percentage heals scale with the *target's* max HP and ignore Wisdom entirely — on a high-Health target they outperform every flat heal by a wide margin.

### Utility

```
Meditation      buff 2, duration 10×L + 720,  MP cost CL − 9×L      (clears MState 1)
Refining Weapon buff 36, duration 900,        value 8×L + 16
Cold Binding    buff 8 (move stop), duration 2×L + 6, max 5 stacks
Hypnotism       buff 26 (sleep),    duration 5×L + 4, max 8 stacks
Revival         restores 13% of max HP and 11% of max MP
```

### Confirmed skill indices

4 Lightning Magic · 9 Shock Wave · 16 Revival · 22 Cure2 · 23 Lightning Blow
· 24 Splashy Ice / `MagicWideIce` · 27 Frost · 28 Group Cure · 31 Lightning
Summons · 32 Hail / `IceLance` · 41 Chain Lightning · 42 Thunder · 44 Ice
Restriction · 45 Ice Storm · 46 Explosion / `FireEruption` · 47 Explosive
Burst · 48 `FireRain` · 55 Perfect Cure · 57 Group Cure2 · 58 Perfect Group
Cure2.

⚠ `CThunder::GetAttack` is a Hex-Rays misnaming — its body is a Rage self-buff belonging to a third-job skill. Magician Thunder is `CThunderLitning`.

---

## 8. Buff and state flags `[ORIG]`

Two 64-bit words per character: `m_nBState` (buffs) and `m_nMState` (movement/control), tested by `IsBState` / `IsMState`.

| Flag | Word | Effect |
|---|---|---|
| `0x200` | B | damage `+= damage/10` (+10%) |
| `0x40000000` | B | damage `+= 7×damage/100` (+7%) |
| `0x8000` | B | attacker gets −5 hit against this target |
| `0x4000` | B | attack modifier branch |
| `0x10000` | B | 10% proc gate |
| `0x800` / `0x1000` | B | mutually exclusive buff pair (types 54 / 53) |
| `0xC000000`, `0x8000000` | B | drop-rate tiering, 1–4 |
| `0x2000000` | M | **automatic hit** |
| `0x200` | M | movement suppressed |
| `0x1` | M | cleared on cast (Meditation) |

Buff ids used by the Magician tree: 0 slow · 2 Meditation · 7 Stun · 8 Move-stop (Cold Binding) · 23 Rage · 26 Sleep · 36 Weapon enchant (Refining Weapon).

---

## 9. Monsters

**Monsters use the *same* stat formulas as players** `[REIMPL]`, with the `InitMonster.txt` values as **additive offsets on top**, not as absolutes:

```
MonsterMinAttack = 1 + (11×Str − 80)/30 + (Agi − 5)/11 + 7×Level/10 + macro.minAttack
MonsterHit       = Agi/8 + 15×Str/54 + macro.hit
MonsterMaxHP     = coeff(Level) × Level/3 + 115 + 2×Hea²/14 + macro.hp
```

The HP denominator is hardcoded 14 for monsters where players index by class.
**This explains a puzzle in the source config**: `InitMonster.txt` routinely
carries `(hp 1)` because that token is an additive macro, not final HP. The
KalEncyclopedia export's `MONSTERS.mon_hp` is different: it appears to be the
already-materialized result. Demon Vulgar gives 133 and Demon Scout 168, both
exact matches to the formula above plus their raw macro. The calculator may use
the CSV's `mon_hp` as final HP, but must never substitute a raw
`InitMonster.txt (hp …)` token for it.

### The other four columns are macros, and HP is the exception `[verified 2026-07-31]`

The paragraph above is right about `mon_hp` and the inference it invites — that
the export materializes its values — is **wrong for every other combat column**.
`mon_otp`, `mon_eva`, `mon_minatt` and `mon_maxatt` are the raw `(hit)`,
`(dodge)` and `(attack)` tokens, copied unchanged.

Evidence, generated by `tools\monster_stat_check\check_monster_macros.py` into
`analysis\monster_stat_check\`: legacy rows were matched to 2006 records on a
signature of level and the five primary stats plus MP and attack speed — never
on the columns being judged, and never by id, since `mon_azon` and the 2006
`index` are unrelated spaces. Of **175 high-confidence pairs**:

| Column | `InitMonster` token | identical | differs |
|---|---|---|---|
| `mon_otp` | `(hit N)` | **175** | 0 |
| `mon_eva` | `(dodge N)` | **175** | 0 |
| `mon_minatt` / `mon_maxatt` | `(attack type min max)` | **175** | 0 |
| `mon_hp` | `(hp N)` | 0 | 97 |

So anything reading those four must add the derivation before use:

```
MonsterHit       = Agi/8 + 15×Str/54                                   + macro.hit
MonsterDodge     = Agi/3                                               + macro.dodge
MonsterMinAttack = 1 + (11×Str−80)/30 + (Agi−5)/11 + 7×Level/10        + macro.minAttack
MonsterMaxAttack = (8×Str−25)/15 + 18×Agi/77 + Level                   + macro.maxAttack
```

Worked example — **Demon Vulgar**, Str 21, Agi 2, level 1, `(hit 0) (dodge 0)
(attack 0 7 7)`. Its on-target point is `2/8 + 15×21/54 = 0 + 5 = 5`, not the
stored **0**; its attack is `1 + 5 + 0 + 0 + 7 = 13` to `10 + 0 + 1 + 7 = 18`,
not the stored **7–7**. Reading the macro as final is the defect that inflated
Kal Atlas's evasion-versus-monster figure until 2026-07-31.

`CMonster::GetHit` and `::GetDodge` carry an `//unsure` comment in the
reimplementation's own source. Their shape is identical to `CPlayer::GetHit` /
`::GetDodge`, which is the corroboration; none of it is confirmed on Bango.

**A second reading of the HP Health term.** Fitting the materialized `mon_hp`
over the 97 pairs that carry both numbers, `coeff(Level)×Level/3 + 115 +
Health²/5 + macro.hp` is exact on **93**, where the reimplementation's
`2×Health²/14` is exact on **3** — and those three only because both truncate to
the same value at Health ≤ 3. Since the reimplementation marks that denominator
`?` itself, both are kept in `engine\kal_engine.py` (`monster_max_hp` and
`monster_max_hp_kalenc_fit`) rather than one replacing the other. Neither is
confirmed on Bango, and it changes nothing downstream while `mon_hp` is used as
a final value.

`(attack <type> <min> <max>)` — the first integer is an attack type and the loader discards it.

AI: the reimplementation's state machine is `IDLE / WALK / CHASE / FORCEATTACK / ATTACK / DEAD / KNEE`, but it never reads the macro's `ai` field. **`mon_ai` semantics remain unknown.**

⚠ **Unresolved discrepancy.** The 2006 `InitMonster.txt` gives monster index 1 `(exp 200)`; the reimplementation's shipped XML gives the same monster `exp="2"`. A factor of 100 sits somewhere between the two and the conversion code does not divide. Do not trust either number until this is settled.

---

## 10. Items → stats `[REIMPL]`

Equipping runs `ApplySpec`, which pushes every field of the item's shared macro through `UpdateProperty`; unequipping runs `FreeSpec`, identical with every value negated:

```
defense, hit, dodge, absorb, resist ×5, hp, mp,
minAttack, maxAttack, minMagic, maxMagic, str, hth, int, wis, dex
```

An item's stats live on the **shared type macro** (the `InitItem` row), not on the instance. Weapon attack speed and range are pure passthrough from the macro. Prefixes are a parallel `CPrefix::ApplySpec` / `FreeSpec` pair with the same add/subtract discipline, and prefix rerolling is driven by consumable charm items carrying a `(Changeprefix …)` specialty.

### `InitItem.txt` record `[ORIG]`

```lisp
(item (name 256) (Index 1) (Image "Wea001") (Action 1 1) (class weapon sword) (code 1 1 1 1)
      (country 252) (level 1) (wear 1) (limit Knight 1) (range 16) (buy 4) (sell 1) (endurance 4)
      (specialty (aspeed 700) (Attack 3 10) (hit 15)))
```

`specialty` sub-tokens: `aspeed`, `Attack min max`, `hit`, `defense`, `dodge`, `absorb`, `resistfire/ice/litning/curse/palsy`, `hp`, `mp`, `str/hth/int/wis/dex`, `Changeprefix`.

### `InitMonster.txt` record `[ORIG]`

```lisp
(monster (name 1) (index 1) (country 0 1 2) (race 0) (level 1) (ai 1) (range 20) (sight 160 240)
         (exp 200) (itemgroup 1 2) (str 21) (hth 1) (int 10) (wis 10) (dex 2) (hp 1) (mp 70)
         (aspeed 2400) (hit 0) (dodge 0) (attack 0 7 7) (magic 0 0) (defense 0 0) (absorb 0)
         (mspeed 1600 800) (quest (2 1 901 1) (3 1 902 1)))
```

This maps one-to-one onto `MONSTERS.csv`'s columns — confirmation that the CSVs are an export of exactly this table for some version.

---

## 11. What is still missing

| Mechanic | Status |
|---|---|
| **Enhancement `+N` → stat gain** | **No source found anywhere.** Not a table, not a formula, not an item field. The reimplementation has no enhancement code at all. `EBS.csv` gives cost and revision requirement only. |
| Upgrade cost `1500×(level+1)` and max upgrade level | Unverified — could not be confirmed or refuted |
| Set bonuses | No set-detection code and no `(set …)` token in the 2006 data. May simply not exist in this era. |
| Endurance loss and repair cost | Only the `CSpecRepair::Enchant` signature and the `(endurance N)` maximum |
| Experience award formula and death penalty | Not found |
| The skill-index → class table | **All 152 initializer entries extracted**; three class-wide index-62 fallbacks have no `InitSkill.txt` label |
| `mon_ai` semantics | Unknown |
| PvP constant arrays `{4,4,5,1,5,3}`, `{4,1,2}` | **Extracted from the original binary; Bango unverified** |
| Non-Magician skill formulas | Class index exists (~350 classes, all named); bodies not yet extracted |

## 12. Verification list carried to `MEMORY.md`

- [x] Settle original critical body and caller — additive, bare critical 1.5×
- [ ] Check in Bango whether a matched critical is exactly 1.5×
- [ ] Does Bango use the level-banded HP coefficient or the flat 2006 one — check for a jump at level 72
- [x] Extract the original three lookup tables and match the implementation
- [ ] Are those three original lookup tables still stock on Bango
- [ ] Resolve the `exp 200` vs `exp 2` factor of 100
- [ ] Confirm the 60%-cooldown swing gate exists in the original
- [x] Extract all 152 skill-map keys, constructors and vtables from the binary initializer
- [ ] Find enhancement `+N` stat gain — the largest remaining hole

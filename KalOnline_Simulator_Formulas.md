# KalOnline_Simulator_Formulas.md — The KalEncyclopedia Character Simulator

Formulas read out of the character simulator inside `KalEncyclopedia.exe`
(Chaos Soft, build `1.0.4196.25298`, file dated 2011-06-28, .NET 1.1). They were
recovered by passively parsing the assembly's CIL, not by running it.

## Provenance and confidence

Values here carry the tag **`[KALENC-2011]`**. That is a *third* independent
source alongside the two the project already had:

| Tag | Source | What it is |
|---|---|---|
| `[ORIG]` | Decompiled 2006 Inixsoft server binary | The real engine, but a 2006 build |
| `[REIMPL]` | Public server reimplementation | A community reconstruction, single-source |
| `[KALENC-2011]` | This file | A 2011 third-party simulator, independently written |

**None of the three is Bango.** KalEncyclopedia is a 2011 tool built against
some official-lineage server, and its own database is the KalEncyclopedia export
already in `data\`. Its value is that it was written by someone else, from
different evidence, and therefore **agreement between `[KALENC-2011]` and
`[REIMPL]` is genuine corroboration** where previously the reimplementation was
single-source and unverified.

Rafael reports the simulator matches his live level 38 Mage "on the dot", which
is a fourth, live data point — but an informal one. The naked-character-sheet
test in `calibration\IN_GAME_TEST_PROTOCOL.md` is what converts that impression
into a measurement, and it now has sharper predictions to separate: see
§7.

**Every division truncates toward zero.** The simulator calls Visual Basic's
`Fix()`, which truncates rather than rounding, at exactly the points marked.

---

## 0. Settled in play, 2026-07-25

A naked level-38 Magician sheet (Str 8, Hea 70, Int 77, Wis 50, Agi 8) was read
off the live client and **explains all 13 derived values with nothing left
over**. It splits the two sources rather than crowning either:

| Reading | Observed | This document | `[REIMPL]` | Winner |
|---|---|---|---|---|
| MaxHP / MaxMP | **1473 / 994** | 1473 / 994 | same | both, exact |
| MDMin / MDMax | **47 / 56** | 47 / 56 | 50 / 59 | **this document** |
| PDMin | **27** | 28 | 27 | **`[REIMPL]`** |
| PDMax, OTP, Evasion, Fire/Ice/Lightning | **41, 3, 2, 8/8/8** | match | match | both |
| NonElemental / Curse | **7 / 5** | not derived | 7 / 5 | **`[REIMPL]`** |

**PDMin is where this document loses.** Its `2 + Fix((11·Str − 110)/30)` and the
reimplementation's `1 + Fix((11·Str − 80)/30)` agree at every Strength from 0 to
250 **except 8 and 9**, where the numerator turns negative and `Fix` truncates
toward zero instead of yielding the −1 that keeps them aligned. The observed
character had Strength 8 — a two-value window, which is the only reason one
screenshot could settle it.

The composed result is `engine\bango_measured.py`, tier 2, and it is what the
site's build simulator uses. Nothing below is edited; this section records which
parts survived contact with the game.

---

## 1. The stat vector — 27 slots `[KALENC-2011]`

The assembly's `modGlobal::strStats` array names 27 stat slots in a fixed order.
This is the index that decodes the `|`-delimited `ita_rev` and `pre_rev` columns,
which the project had been carrying as opaque strings.

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

A second array, `strStatsMix`, holds **28** slots for the Mix Master context and
differs at the tail: **25 = Enemy Defense, 26 = HP, 27 = Mana**. Do not use the
27-slot order to read a mixing stone.

Decoded output is in `analysis\kalenc_stat_vectors\`: **3,537** item stat rows
across 704 items and **229** prefix stat rows across 102 prefixes.

Worked example — `Intensified Steel Armor`, `ita_rev = "||||||||||||15|36|4"`:
slots 12, 13, 14 are populated, so the item gives **Evasion 15, Defense 36,
Absorb 4**.

### The one encoding exception, recorded rather than guessed

Thirty-one positions across **nine Mix Master stones** (Stone of Flame, Ice,
Lightening, Poison, Paralyzis, Strength, Skill, Mystery, Demons Blood) run past
slot 26 and contain commas. Those rows carry **two comma-separated vectors in
the 28-slot Mix order**, not one. The decoder flags them and reports the count
rather than silently truncating; what the two vectors mean is **to confirm**.

---

## 2. Class ordering

The simulator's class combo box is indexed `0 Archer · 1 Knight · 2 Magician ·
3 Thief`. That is alphabetical, and it is confirmed independently by `CASTS.csv`
(`1 Archer, 2 Knight, 3 Magician, 4 Thief`). Every per-class constant below is
resolved through this ordering, and the fact that all eight HP/MP denominators
land on the reimplementation's values under it — and under no other ordering —
is itself the confirmation.

---

## 3. Derived stats `[KALENC-2011]`

`Lv` is character level. `Gear`, `Misc`, `Quest%` and `Pet%` are the simulator's
input boxes.

```
OTP      = Fix(0.2777778 × Str) + Fix(Agi / 8) + gearOTP + miscOTP
Evasion  = Fix(Agi / 3) + gearEva + miscEva
PDMin    = Fix((Str − 10) × 11 / 30) + Fix((Agi − 5) / 11) + Fix(Lv × 7 / 10) + 2
PDMax    = Fix((Str − 5) × 8 / 15)   + Fix((Agi + 17) × 11 / 47) + Lv − 3
MDMin    = Fix((Int − 8) × 7 / 12)   + Fix(Wis / 7)
MDMax    = Fix(Int × 7 / 12)         + Fix(Wis × 0.31249) − 3
```

`0.2777778` is 15/54, so OTP reproduces `[REIMPL]`'s `15×Str/54 + Agi/8` exactly.

### Agreement and disagreement with `[REIMPL]`

| Stat | `[REIMPL]` | `[KALENC-2011]` | Verdict |
|---|---|---|---|
| OTP | `Agi/8 + 15×Str/54` | same | **agree** |
| Evasion | `Agi/3` | same | **agree** |
| PDMin | `1 + (11×Str − 80)/30 + (Agi−5)/11 + 7×Lv/10` | `2 + (11×Str − 110)/30 + …` | **agree** — the two forms are algebraically identical, because 110 − 80 is exactly the divisor 30 |
| PDMax | `(8×Str − 25)/15 + 18×Agi/77 + Lv` | `(8×Str − 40)/15 + (Agi+17)×11/47 + Lv − 3` | **differ by ±1 at some stat values** — 18/77 = 0.23377 vs 11/47 = 0.23404, and the constants differ |
| MDMin | `(7×Int − 20)/12 + Wis/7` | `(7×Int − 56)/12 + Wis/7` | **differ by 3** |
| MDMax | `7×Int/12 + 14×Wis/45` | `7×Int/12 + Fix(0.31249×Wis) − 3` | **differ by 3** |

The magic disagreements are a flat 3 and are the sharpest thing on this page:
one naked character sheet settles both. Note the two sources are *not*
independent about which is right — `[ORIG]` §2 is itself tagged `[REIMPL]`, so
neither has engine authority for magic.

---

## 4. HP and MP `[KALENC-2011]`

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

**This confirms `[REIMPL]` on all eight denominators**, which were previously
single-source. It also confirms the level bands:

- `52 × 1.305 = 67.86` against `[REIMPL]`'s `67.8162` at level ≥ 72
- `52 × 1.5 = 78` against `78` at level ≥ 76 — **exact**
- `52 × 1.765 = 91.78` against `91.758` at level ≥ 81
- MP: `(8 + 2×mpBand) × Lv` gives 8 / 10 / 12 / 14 — **exactly** `[REIMPL]`'s
  `coeff_MP`, at the same level thresholds

KalEncyclopedia stops at the level-81 band; the engine reference continues with
bands at 86, 91 and 96, which this source simply does not cover (it is a 2011
tool). The `+115` HP constant and the `+140 + Wis` MP constants are confirmed.

### Two mechanics the knowledge base does not have

**A level-50+ Health bonus on HP.** On top of the formula above:

```
band          = clamp( Fix((Lv − 50) / 5) + 1, 0, 5 )
lateHeaBonus  = Fix( Fix(Hea² × qHP[class]) × (0.14 + 0.1 × band) )
```

So from level 50 the Health quadratic is paid **again**, at 24% at levels 50–54,
rising 10 points per five levels to **64% from level 70 onward**. On a
Health-stacked build this is a large amount of HP that no document in this
project currently accounts for.

**An HP-doubling flag.** The whole pre-bonus HP term is multiplied by
`chkFlag.CheckState + 1`, i.e. **×1 or ×2**. What the simulator's checkbox
represents is **to confirm** — it is not labelled in the metadata.

---

## 5. Defense, and the percentage pipeline `[KALENC-2011]`

```
Defense = Fix(baseDef + gearDef + inputDef) + miscDef
if <high-level gate>:                                   # gate to confirm
    Defense += Fix( (Lv − 65) × 5 + Defense × 2 / 50 )
Defense = Fix( Defense × (100 + Quest%) / 100 × (100 + Pet%def) / 100 )
```

**Defense has no stat-derived base at all** in this simulator — it comes
entirely from gear and buffs. That contradicts
`KalOnline_Knowledge_Base_v2.md`, which says Health "increases HP and defense".
On this evidence the defense half of that sentence is wrong, or at least is not
modelled. Flagged under standing rule 5 rather than edited.

The same two multipliers close every offensive stat:

```
final = Fix( Fix( (base + gear) × (100 + Quest%) / 100 ) × (100 + Pet%) / 100 )
```

with `Pet%` slot 0 applied to PDMin, PDMax, MDMin and MDMax, slot 1 to Defense,
and slot 2 to Evasion. **Pets giving a percentage bonus to damage, defense and
evasion is not in any project document.**

A second conditional appears in Evasion, gated the same opaque way:

```
if <gate>:  Evasion += Fix( Evasion × (Lv / 2) / 400 )
```

Both gates are read from hidden form fields whose meaning the metadata does not
name. Recorded as **to confirm**, not guessed at.

---

## 6. The weapon proc — "EB" `[KALENC-2011]`

`CalcEB` is **not** item enhancement. It computes a proc with a chance and a
damage range, from the weapon's own damage columns:

```
physical:  min = Fix( PDMin + ebLevel × 0.05 × PDMin + 3 × k )
           max = Fix( PDMax + ebLevel × 0.10 × PDMax + 3 × k )
magical:   the same over MDMin / MDMax
displayed: "EB Chance : <c>% , EB Damage : <min> - <max>"
```

So the minimum scales at **5% per EB level** and the maximum at **10%**. The
identity of `k`, and how `ebLevel` and the chance relate to `EBS.csv`'s
`eb_lvl / eb_rev / eb_srev / eb_price` columns, is **to confirm** — `EBS.csv`
has 16 levels, and the `eb_rev` and `eb_srev` series (1,2,2,4,5,7,10,13,21,29,
45,92,188,192,196,200 and 1,3,5,9,14,21,31,44,65,94,139,231,419,611,807,1007)
match neither Bango's `+N` grid nor each other's shape.

---

## 7. What this changes for the in-game tests

`calibration\IN_GAME_TEST_PROTOCOL.md` test A1 (naked character sheet) was
written to check a single unverified formula set. It now separates **two
competing sets**, which makes it strictly more informative:

| Reading | If `[REIMPL]` is right | If `[KALENC-2011]` is right |
|---|---|---|
| MDMin | `(7×Int − 20)/12 + Wis/7` | exactly **3 lower** |
| MDMax | `7×Int/12 + 14×Wis/45` | exactly **3 lower** |
| PDMax | `(8×Str−25)/15 + 18×Agi/77 + Lv` | differs by **±1** depending on Str and Agi |

Everything else in §3 and §4 the two sources agree on, so a naked sheet that
matches is confirming both at once.

Two further readings are now worth taking that the protocol did not ask for:

- **HP at level 49 versus level 50.** If the level-50 Health bonus is real,
  HP jumps by `Fix(Hea² × qHP × 0.24)` at the boundary — a large, obvious step
  that a level-1 alt cannot reach but a levelling character crosses once.
- **A pet equipped versus not**, with nothing else changed, on PDMin/PDMax,
  Defense and Evasion. The simulator says all three take a straight percentage.

---

## 8. What has not been read yet

The assembly holds **2,841 methods across 22 types**; all of it is disassembled
under `research\kalencyclopedia\extract\il\`, and this document covers the
simulator's stat core only. Untouched, in rough order of likely value:

- `frmSkills::loadINV`, `MenuItem_*_Click` and `mnu*_Popup` — **how an item,
  prefix, grade, set bonus, Bead of Fire and enhancement stone each turn into
  the `EStats` vector**. This is the largest remaining prize and is what would
  settle the enhancement-band question.
- `frmSkills::ResetBuffs` / `StoreBuffs` / `chk_CheckedChanged` — the buff table.
- `frmSkills::DS_Text_to_Stats` — the dragon-scroll/stat text parser.
- `frmMix` (438 methods) — Imperial mixing, against
  `Imperial_Mixing_System_Guide.md`.
- `frmRevis` (153 methods) — the prefix and EB browser.
- `frmSkills::CalcALLRES` — resistances, partially read.
- `B2MS_Common.dll` — the vendor's shared library; `Output.dll` is native.

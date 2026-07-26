# data\ — Raw KalEncyclopedia Database Exports

Thirteen CSV files exported from the KalEncyclopedia program database on **2026-01-31**, copied into this folder **2026-07-24**. They are the foundation `KalOnline_Knowledge_Base_v2.md` was written from. Since Bango's client tables were parsed on 2026-07-25, these files are authoritative only as documented fallbacks; use `bango_data\CSV_AUTHORITY.csv` for the per-file verdict.

**These files are read-only.** Script over them, join them, derive from them — but never edit them in place, and never regenerate one from a summary. Derived tables belong in new files at the folder root, each noting which CSVs produced it.

All schemas below were read off the files directly, not inferred. Row counts exclude the header.

## File inventory

| File | Rows | Cols | Contents |
|---|---|---|---|
| `CASTS.csv` | 4 | 2 | The 4 base classes |
| `POSITIONS.csv` | 28 | 5 | Class advancement paths — 7 per class |
| `LVL_PLAYERS.csv` | 99 | 2 | Player XP table, L01–L99 |
| `LVL_EGGS.csv` | 80 | 2 | Pet ("Ancient Animal") stats, G01–G80 |
| `SKILLS.csv` | 206 | 17 | Every skill, with level gating, prerequisites and per-grade damage formulas |
| `ITEMS.csv` | 704 | 12 | All items and equipment |
| `PREFIXES.csv` | 102 | 4 | All item prefixes and their stat bonuses |
| `EBS.csv` | 16 | 4 | Enhancement Bead cost table, +1 to +16 |
| `MONSTERS.csv` | 283 | 35 | All monsters with full combat stats |
| `DROPS.csv` | 11,931 | 8 | Drop table linking monsters to items |
| `QUESTS.csv` | 157 | 11 | All quests: 74 Quest, 62 RQ, 21 Event |
| `OPTIONS.csv` | 1 | 3 | KalEncyclopedia program settings, not game data |
| `PL_SAVE.csv` | 8 | 19 | Saved character builds from the KalEncyclopedia planner |

## Where to look — question → table routing index

Read this before opening any CSV. Left column is the kind of question, right column is the file and the exact columns that answer it. **Bold** marks the column that actually carries the answer; the others are the keys you need to get there.

### Characters, classes, advancement

| Question | File → columns |
|---|---|
| What classes exist? | `CASTS.csv` → `cl_azon` **`cl_megn`** (1 Archer · 2 Knight · 3 Magician · 4 Thief) |
| What can this class advance into, and when? | `POSITIONS.csv` → `po_class` = `cl_azon`, **`po_megn`**, **`po_lvl`** |
| Which skill trees does a position unlock? | `POSITIONS.csv` → **`po_skills`** (comma-separated `sk_poz` IDs) → `SKILLS.csv.sk_poz` |
| XP needed for level N | `LVL_PLAYERS.csv` → `lpl_id` = `L<NN>`, **`lpl_exp`** (cumulative) |
| Someone's saved build | `PL_SAVE.csv` → `pl_name`, `pl_cast`, `pl_pos`, `pl_lvl`, **`pl_stat2`** (`Str#Hea#Int#Wis#Agi`), `pl_skills` |

### Skills

| Question | File → columns |
|---|---|
| What does this skill do? | `SKILLS.csv` → **`sk_desc`**, **`sk_form`** (template with `#0`/`#1` slots) |
| What number does it produce at grade G? | `SKILLS.csv` → **`sk_pars`** (reverse-Polish, `\|`-separated per slot), capped by **`sk_maxpars`** |
| When can I take it, and how many grades? | `SKILLS.csv` → **`sk_lvl`** (`"levels\|grades"` string) — decode per the skill-system section of `KalOnline_Knowledge_Base_v2.md` |
| What does it require first? | `SKILLS.csv` → **`sk_pre`** (`"SKILL_NAME\|GRADE"`; `"\|0"` = none) |
| MP cost / cast time / cooldown / range / duration | `SKILLS.csv` → **`sk_mana`** (RPN), **`sk_charge`** ms, **`sk_coold`** ms, **`sk_range`**, **`sk_lasting`** |
| Active or passive? | `SKILLS.csv` → **`sk_type`** (1 passive, 2 active) |

⚠️ `sk_megn` is **not unique**. Always filter by `sk_poz` as well.

### Items, equipment, enchanting

| Question | File → columns |
|---|---|
| An item's stats | `ITEMS.csv` → **`ita_rev`** (stat block), `ita_type`, `ita_grade` |
| Can my class/level use it? | `ITEMS.csv` → **`ita_class`** (blank = all), **`ita_lvllim`** |
| What's it worth? | `ITEMS.csv` → **`ita_price`** |
| What does a prefix add? | `PREFIXES.csv` → **`pre_rev`** (pipe-**positional**: `"3"`=Str, `"\|3"`=Hea, `"\|\|3"`=Int, `"\|\|\|3"`=Wis, `"\|\|\|\|3"`=Agi, then HP, MP, OTP, defence…), `pre_grd` |
| Enhancement cost to +N | `EBS.csv` → `eb_lvl`, **`eb_rev`** (per level), **`eb_srev`** (cumulative), **`eb_price`** (`.` is a **thousands** separator) |

### Monsters, drops, farming

| Question | File → columns |
|---|---|
| A monster's combat stats | `MONSTERS.csv` → `mon_lvl`, **`mon_hp`**, `mon_minatt`/`mon_maxatt`, `mon_mag1/2`, **`mon_def1`** (close) / **`mon_def2`** (far), **`mon_absorb`**, `mon_otp`, `mon_eva`, `mon_attspd` |
| Its elemental resistances | `MONSTERS.csv` → **`mon_res1`…`mon_res5`** = Fire, Ice, Lightning, Non-elemental, Curse |
| XP per kill / kills per level | `MONSTERS.csv.`**`mon_exp`** ÷ `LVL_PLAYERS.csv.lpl_exp` |
| How it behaves | `MONSTERS.csv` → `mon_ai`, `mon_range`, `mon_sight1/2`, `mon_move1/2` |
| What drops from monster X | `DROPS.csv` → filter **`drp_monst`** = `MONSTERS.mon_azon`, then `drp_item` → `ITEMS.ita_azon` |
| The actual drop rate | **Bango uses the KalEncyclopedia rate** (player-confirmed externally 2026-07-26). Require the current Bango monster-item association, then use **`drp_chance1 × drp_chance2 / 100`** on every same-name pair row. |
| Which talisman/prefix is on the dropped equipment | `DROPS.csv` → **`drp_rev`**. Text names the talisman/prefix; blank means the base item without one. Do not collapse variants. |

⚠️ `drp_group1` is a **drop-group ID, not a monster ID**. The monster is `drp_monst`.

### Quests

| Question | File → columns |
|---|---|
| What is this quest / how do I do it? | `QUESTS.csv` → **`que_name`**, **`que_text`** (numbered walkthrough) |
| What does it reward? | `QUESTS.csv` → **`que_rew`** — search case-insensitively, the file mixes "Skill point" and "Skill Point" |
| Which quests give a skill point? | `QUESTS.csv` → the 12 rows Quest 07, 11, 12, 13, 14, 16, 19, 21, 22, 23, 27, 32 |
| Level and target | `QUESTS.csv` → `que_lvl`, `que_monst`, `que_item` |

⚠️ `que_id` is **not unique**. The key is `(que_id, que_type)`.

### Pets

| Question | File → columns |
|---|---|
| Pet stats at grade G | `LVL_EGGS.csv` → `leg_id` = `G<NN>`, **`leg_stat`** (one string, `attack / defense / magic`) |

### Not in these tables at all

The CSVs hold **entity data** — what things *are*. They hold none of the **engine arithmetic** that turns those numbers into outcomes. Anything below is not derivable from `data\` and must not be guessed:

| Question | Where it actually lives |
|---|---|
| How much damage do I do to a monster? | Server engine → `KalOnline_Engine_Formulas.md` |
| How much do I take? | Server engine → same |
| Will I hit / be dodged? | Server engine (`CheckHit`, OTP vs EVA + level table) |
| Critical chance and multiplier | Server engine (`GetFatalDamage`) |
| What 1 point of Str/Hea/Int/Wis/Agi actually gives | Server engine (`ReviseProperty`) |
| How `mon_attspd` converts to hits per second | Server engine (`GetASpeed` — it is a **cooldown in ms**) |
| How a skill's `sk_pars` value becomes real damage | Server engine, per-skill `GetAttack()` |
| What `+N` enhancement actually adds | `bango_data\ENHANCEMENT_BONUSES.csv` — exact Bango +1…+15 values for eight stat families and three still-unidentified application bands |
| Set bonuses | Server engine (`CPrefix::ApplySpec`) |

### Sources that are not in `data\`

| Source | What it holds | Provenance |
|---|---|---|
| `<game>\data\Rate\droplist.txt` | The live server's drop table, plain text | **Bango, current** — admin-generated |
| `<game>\data\Rate\questlist.txt` | Live quest list with exp / contribution / SP / prereqs / steps | **Bango, current** — header says `generated by generate_questlist.py` |
| `<game>\data\Rate\monster-quest-indicator.txt` | Which monsters count for which quest | **Bango, current** |
| `<game>\data\Config\config.pk` | Client tables: `inititem.dat`, `jobsystem.dat` (skills), `prefix.dat`, `droplist.dat`, `questlist.dat`, `message.dat` and 25 others | **Bango, current** — decrypted, independently audited and parsed into `bango_data\`; 31/31 entries accounted for |

⚠️ **Provenance warning.** The 13 CSVs here were exported from KalEncyclopedia on 2026-01-31 and describe *whatever game version KalEncyclopedia was built against*. Rafael plays on **Bango**, a highrate private server of the 2009/2012 lineage. Where a Bango-current source above disagrees with a CSV, **Bango wins** — that is a standing decision, recorded in `MEMORY.md` 2026-07-25.

### Bango reconciliation verdict

| Legacy CSV | Status after the Bango parse |
|---|---|
| `ITEMS`, `SKILLS`, `PREFIXES` | Superseded for client-visible definitions |
| `QUESTS` | Superseded for level, name, rewards, prerequisites and steps |
| `DROPS` | Split authority: Bango associations win; same-name KalEncyclopedia rows supply the confirmed rates and talisman/base variants |
| `MONSTERS` | Bango IDs/names supersede; combat stats remain unverified fallback |
| `CASTS`, `POSITIONS`, `LVL_PLAYERS`, `LVL_EGGS`, `EBS` | Unverified fallback; no complete client equivalent |
| `OPTIONS` | Program settings, not game data |
| `PL_SAVE` | Planner user data, not server/client authority |

The machine-readable verdict and exact row-level diffs are
`bango_data\CSV_AUTHORITY.csv` and `bango_data\RECONCILIATION.md`.

## Schemas

### CASTS.csv
`cl_azon` (class ID 1–4), `cl_megn` (name). 1 Archer · 2 Knight · 3 Magician · 4 Thief.

### POSITIONS.csv
`po_azon` (position ID 1–28), `po_class` (→ `cl_azon`), `po_megn` (name), `po_lvl` (level required), `po_skills` (comma-separated list of `sk_poz` skill-tab IDs this position can access).

Seven rows per class: the level 1 / 30 / 50 (×2) / 70 (×2) chain plus a `po_lvl = 0` "Free <class>" entry. In-game spellings differ slightly from the knowledge base's cleaned-up names — the raw data has "Wondering Knight", "Wondering Archer", "Vagabond Sword-man".

### LVL_PLAYERS.csv
`lpl_id` (`L01`…`L99`), `lpl_exp` (cumulative XP required). Note the discontinuities at 20, 30, 40, 50, 71, 80, 84, 89, 94 — the curve steps rather than growing smoothly.

### LVL_EGGS.csv
`leg_id` (`G01`…`G80`), `leg_stat` (a single string, `attack / defense / magic`).

### SKILLS.csv
| Column | Meaning |
|---|---|
| `sk_megn` | Skill name. **Not unique** — the same name appears in several trees (e.g. "Artillery" ×8, "Lightning Slash" ×2). Always filter by `sk_poz` as well. |
| `sk_type` | `1` passive (54 skills), `2` active (152 skills) |
| `sk_poz` | Skill tab / tree, 1–28. Cross-reference `POSITIONS.po_skills` to know which class positions can take it. |
| `sk_desc` | In-game description (multi-line) |
| `sk_order` | Display order within the tab |
| `sk_pic` | Icon ID |
| `sk_lvl` | **The level-gating string** — `"levels\|grades"`. Levels left of the pipe, number of grades unlocked at each level right of it. `"30 60\|5 2"` = grades 1–5 at level 30, grades 6–7 at level 60. |
| `sk_pre` | Prerequisite, `"SKILL_NAME\|GRADE"`; `"\|0"` means none |
| `sk_form` | Effect template shown in-game, with `#0`, `#1` placeholders |
| `sk_pars` | **Per-grade value formulas in reverse-Polish notation**, `\|`-separated to fill `#0`, `#1`. Variables: `sk_lvl` (skill grade), `ch_lvl`, `ch_int`, `ch_wis`, `ch_agi` (character level and stats). Example, Shock Wave `#0`: `50 5 sk_lvl * 6 / + 3 ch_int * sk_lvl * 4 / +` = 50 + (5 × grade)/6 + (3 × INT × grade)/4. |
| `sk_maxpars` | Caps on the computed values, same `\|` ordering |
| `sk_mana` | MP cost (also RPN) |
| `sk_charge` | Cast time, ms |
| `sk_coold` | Cooldown, ms |
| `sk_range` | Range |
| `sk_lasting` | Duration |
| `sk_honor` | Honour flag |

The decoding of `sk_lvl` — including free grades for pre-50 skills unlocking at 50+, and the Stone of Birth cascade — is written out with worked examples in the skill-system section of `KalOnline_Knowledge_Base_v2.md`. Read it before doing skill arithmetic.

### ITEMS.csv
`ita_azon` (item ID), `ita_itype`, `ita_grade`, `ita_class` (Archer / Knight / Magician / Thief, or blank for all), `ita_type` (Armor, Boots, Bow, Dagger, Helmet, Ring, Shield, Medicine, Geons, …), `ita_name`, `ita_lvllim` (level requirement), `ita_rev` (stat block), `ita_price`, `ita_pic`, `ita_pic2`, `ita_3d`.

`ita_itype` values actually present: 0 (51), 1 (251), 2 (10), **3 (228)**, 4 (18), 5 (30), **6 (62)**, 7 (7), 8 (1), 9 (11), **10 (3)**, **11 (15)**, **12 (16)**, **255 (1)**. The knowledge base documents only 0, 1, 2, 4, 5, 7, 8, 9 — the bolded types are undocumented. Determine them from `ita_type` / `ita_name` before relying on them.

48 distinct `ita_grade` values including variants (`G65b`, `G70b`) and oddities (`G0`, `G00`, blank) — do not assume the clean `G46 / G50 / G55 / G60 / G65 / G70` ladder covers everything.

### PREFIXES.csv
`pre_azon` (ID 1–102), `pre_name`, `pre_rev` (**pipe-positional stat block**), `pre_grd` (grade/tier).

`pre_rev` encodes which stat gets the bonus by *position*, so leading pipes are significant: `"3"` = +3 Strength, `"|3"` = +3 Health, `"||3"` = +3 Intelligence, `"|||3"` = +3 Wisdom, `"||||3"` = +3 Agility. Longer strings carry HP, MP, OTP, defence and further fields — e.g. Legendary is `"5|5|5|5|5|75|75|||||||5"` (+5 to all five stats, +75 HP, +75 MP, and a value in the 14th position). The knowledge base's prefix tables cover IDs 1–50 plus four compound prefixes; **the file has 102**, including the class-progression prefixes (Wandering/Skillful/Veteran/Expert Knights, Archers, Scholars) and the high-end ones (Distinct, Steely, Breakthroughs, Decisional, Magical Powers, Legendary, The King GuhBalHans, Rash).

Raw names differ from the knowledge base's tidied versions: `"Strong mans"` not "Strong Man's", `"Steels"` not "Steel's", `"Veteran  Knights"` with a double space.

### EBS.csv
`eb_lvl` (`01`…`16`), `eb_rev` (revision required for that level), `eb_srev` (cumulative revision), `eb_price`. Numbers use `.` as a **thousands** separator (`"1.500"` = 1,500).

### MONSTERS.csv
35 columns. `mon_azon` (monster ID), `mon_name`, `mon_group` (1–23), `mon_lvl` (1–98), `mon_hp`, `mon_ai`, `mon_range`, `mon_sight1/2`, `mon_exp`, then the stat block `mon_str`, `mon_hea`, `mon_int`, `mon_wis`, `mon_agi`, `mon_mp`, `mon_attspd`, `mon_otp`, `mon_eva`, `mon_minatt`, `mon_maxatt`, `mon_mag1/2`, `mon_def1/2`, `mon_absorb`, `mon_move1/2`, the five resistances `mon_res1`…`mon_res5` (Fire, Ice, Lightning, Non-Elemental, Curse), and `mon_pic`, `mon_3d`.

`mon_exp` plus `LVL_PLAYERS.csv` gives kills-per-level directly; `mon_otp` / `mon_eva` / `mon_def1` drive hit and damage estimates.

### DROPS.csv
`drp_azon` (row ID), `drp_group1` (**drop-group ID, up to 1034 — not the monster ID**), `drp_group2` (drop category), `drp_chance1`, `drp_chance2`, `drp_item` (→ `ITEMS.ita_azon`, resolves for all 11,931 rows), `drp_monst` (**→ `MONSTERS.mon_azon`, this is the monster**, resolves for all rows), `drp_rev` (drop variant; on equipment, the talisman/prefix carried by the item).

Drop rate:

```
Actual Rate % = drp_chance1 × drp_chance2 / 100
```

Rafael externally confirmed on 2026-07-26 that this is also Bango's drop-rate
model and values. Use Bango's current `droplist.dat` for the monster-item
association, then join the normalized monster and item names to these rows for
the rate and `drp_rev` variants. Do not copy chance values into an unmatched
Bango pair.

Worked example, row 0: Demon Vulgar (`drp_monst` 1) drops Geons at `chance1` 60 and `chance2` 92 → **55.2%**. Quoting `drp_chance1` alone as the drop rate is the standard error here.

Two cautions the knowledge base does not mention:

- `drp_chance2` is often a **float** (`77.300003`, `0.2`, `0.1`) — parse as float, not int.
- `drp_group2` takes values **1–6**, not the 1–4 the knowledge base describes (counts: 1→934, 2→3138, 3→4369, 4→2464, 5→680, 6→346). The meaning of 5 and 6 is unverified.
- On equipment rows, text `drp_rev` values are talisman/prefix names. Blank
  means the base item without a talisman. Some names do not match
  `PREFIXES.pre_name` exactly (`"Strong Knights"`, `"Skillful Archers "` with
  a trailing space), so normalize punctuation and whitespace but keep the raw
  value visible.
- Every numeric `drp_rev` value in this export occurs on a Geons row (388
  rows). Those values are not prefix IDs and must not be linked to a talisman.

### QUESTS.csv
`que_id`, `que_type` (`Quest` 74 · `RQ` 62 · `Event` 21), `que_lvl` (1–90), `que_name`, `que_monst`, `que_item`, `que_text` (numbered walkthrough, multi-line), `que_rew`, `que_pic1/2/3`.

**`que_id` is not unique** — it repeats across types, so the key is `(que_id, que_type)`. Quest 07 and Event 07 and RQ 07 are three different quests.

Verified against the guide: exactly **12** rows have a skill-point reward in `que_rew` — Quest 07, 11, 12, 13, 14, 16, 19, 21, 22, 23, 27, 32, at levels 11–38. This matches the checklist in `KalOnline_Quest_Progression_Guide.md` exactly. A further 39 quests award contribution points.

Search `que_rew` case-insensitively: the file mixes "Skill point" and "Skill Point".

### OPTIONS.csv
`OP_PATH`, `OP_3D`, `OP_MSG`. Program settings for the KalEncyclopedia viewer, not game data. Records the game data path as `D:\Download\KalOnlineEng\data\`.

### PL_SAVE.csv
Eight saved character builds from the KalEncyclopedia planner. `pl_name`, `pl_cast` (→ `cl_azon`), `pl_pos` (→ `po_azon`), `pl_lvl`, `pl_stat1`…`pl_stat6`, `pl_inv1`…`pl_inv5` (five full equipment loadouts, `#`-separated: five armour slots, weapon, pet, ten prefix slots, nine enhancement values, accessory, Beads of Fire, set bonus, stone, pet, scrolls), `pl_skills` (`#` per tree, `|` per skill, values are grades), `pl_quest` (per-quest state), `pl_extra`, `pl_pic` (embedded JPEG).

`pl_stat2` is the allocated stat line, `Str#Hea#Int#Wis#Agi`.

| Name | Class | Position | Lv | Str / Hea / Int / Wis / Agi |
|---|---|---|---|---|
| ChamberHUN | Magician | Ascetic | 77 | 8 / 95 / 60 / 50 / 90 |
| TirandA | Magician | Military Adviser | 66 | 8 / 90 / 60 / 70 / 66 |
| JaSMiNe | Magician | Ascetic | 52 | 8 / 90 / 60 / 50 / 51 |
| Zanbare | Knight | General | 69 | 95 / 93 / 8 / 8 / 70 |
| PeRCiVaL | Knight | God of Sword | 53 | 90 / 86 / 8 / 8 / 50 |
| SorchA | Thief | Unearthly Ghost | 62 | 50 / 98 / 8 / 10 / 90 |
| Meriel | Archer | God of Bow | 55 | 50 / 79 / 8 / 10 / 100 |
| Thani | Archer | Apprentice Archer | 42 | 58 / 52 / 8 / 21 / 90 |

Whether these are live characters, other players' builds, or planner experiments is not recorded — ask before treating any of them as "the" character.

## Known caveats

- Some values in this database are **server-specific**. The Imperial Mixing guide documents Lv. 3 rare-stone stats as "the stats on your server"; the enhancement price table and drop chances may be similarly local. Label rather than generalize.
- The knowledge base's tables are curated subsets of these files (50 of 102 prefixes, 8 of 14 item types, sampled XP and pet rows). Where a question needs completeness, read the CSV.

# KalOnline Encyclopedia - Complete Knowledge Base

## Overview

This document contains comprehensive information about **KalOnline**, a Korean MMORPG. This knowledge base is derived from the KalEncyclopedia program database and source code, enabling AI assistants to answer detailed questions about game mechanics, items, monsters, skills, and character building.

---

## Game Basics

### Character Classes

KalOnline has **4 base classes**, each with unique playstyles:

| Class ID | Class Name | Primary Stats | Role |
|----------|------------|---------------|------|
| 1 | **Archer** | Agility, Strength | Ranged DPS |
| 2 | **Knight** | Strength, Health | Tank/Melee DPS |
| 3 | **Magician** | Intelligence, Wisdom | Magic DPS/Healer |
| 4 | **Thief** | Agility, Strength | Melee DPS/Assassin |

### Class Advancement Paths (Positions)

Each class can advance through different specializations:

#### Archer Paths
- Level 1: Wandering Archer
- Level 30: Apprentice Archer
- Level 50: Expert Archer OR Imperial Commander
- Level 70: God of Bow (from Expert) OR Imperial General (from Commander)

#### Knight Paths
- Level 1: Wandering Knight
- Level 30: Apprentice Knight
- Level 50: Vagabond Swordsman OR Commander
- Level 70: God of Sword (from Vagabond) OR General (from Commander)

#### Magician Paths
- Level 1: Scholar
- Level 30: Literary Person
- Level 50: Hermit OR Chairperson of Joong-Bang
- Level 70: Ascetic (from Hermit) OR Military Adviser (from Chairperson)

#### Thief Paths
- Level 1: Wandering Thief
- Level 30: Thief Guild Member
- Level 50: Hitman OR I Swordsman
- Level 70: Dark Shadow (from Hitman) OR Unearthly Ghost (from Swordsman)

---

## Character Stats

### Primary Stats
| Stat | Abbreviation | Description |
|------|--------------|-------------|
| Strength | Str | Increases physical damage |
| Health | Hea | Increases HP and defense |
| Intelligence | Int | Increases magic damage |
| Wisdom | Wis | Increases MP,magic defense and, for mages, amount healed with healing spells |
| Agility | Agi | Increases evasion and attack speed |

### Secondary Stats
| Stat | Abbreviation | Description |
|------|--------------|-------------|
| HP | HP | Health Points |
| MP | MP | Mana Points |
| PDMin/PDMax | - | Physical Damage (min/max) |
| MDMin/MDMax | - | Magic Damage (min/max) |
| OTP | OTP | On-Target Point (accuracy) |
| Evasion | Eva | Chance to dodge attacks |
| Defense | Def | Reduces physical damage taken |
| Absorb | Abs | Damage absorption |

### Elemental Resistances
- Fire (F)
- Ice (I)
- Lightning (L)
- Non-Elemental (NE)
- Curse (C)

### Stat Point Costs

Stat points cost increases at certain thresholds:

**For Knights (Strength stat):**
| Stat Value | Cost per Point |
|------------|----------------|
| 1-60 | 1 point |
| 61-90 | 2 points |
| 91-120 | 3 points |
| 121-150 | 4 points |
| 151-180 | 5 points |
| 181-210 | 6 points |
| 211+ | 7 points |

**For Other Classes (all stats):**
| Stat Value | Cost per Point |
|------------|----------------|
| 1-50 | 1 point |
| 51-70 | 2 points |
| 71-90 | 3 points |
| 91-110 | 4 points |
| 111-130 | 5 points |
| 131-150 | 6 points |
| 151+ | 7 points |

---

## Equipment System

### Equipment Types

#### Armor Pieces (ita_itype = 1)
- Armor (body)
- Boots
- Gloves
- Helmet
- Shorts (pants)

#### Weapons (ita_itype = 0 for full sets, varies for individual)
- **Knight**: Swords, Two-Hand Swords
- **Archer**: Bows
- **Magician**: Sticks (staves)
- **Thief**: Daggers, Claws

#### Other Equipment Types
- ita_itype = 2: Shields
- ita_itype = 4: Accessories
- ita_itype = 5: Consumables
- ita_itype = 7: Rings
- ita_itype = 8: Necklaces
- ita_itype = 9: Stones (enhancement stones)

### Equipment Grades

Equipment is organized by grade (G## format), indicating tier/level:
- G46: Level ~35-43 equipment
- G50: Level ~46-50 equipment
- G55: Level ~51-55 equipment
- G60: Level ~56-60 equipment
- G65: Level ~61-65 equipment
- G70: Level ~66-70 equipment

Higher grade = better base stats.

---

## Prefix System (Item Enchantments)

Items can have **prefixes** that add bonus stats. Prefixes are organized by what stat they boost:

### Strength Prefixes (Position 1)
| Prefix | Bonus |
|--------|-------|
| Forced | +1 Str |
| Unlawful | +2 Str |
| Harsh | +3 Str |
| Strong Man's | +4 Str |
| Strongest Man's | +5 Str |
| Melee's | +6 Str |
| Bloody Fight's | +7 Str |
| Slaughterous | +8 Str |
| Barbaric | +9 Str |
| Invincible | +10 Str |

### Health Prefixes (Position 2)
| Prefix | Bonus |
|--------|-------|
| Healthy | +1 Hea |
| Vigorous | +2 Hea |
| Heroic | +3 Hea |
| Vital | +4 Hea |
| Ablaze | +5 Hea |
| Iron Legs | +6 Hea |
| Steel's | +7 Hea |
| Limitable | +8 Hea |
| Infinitely | +9 Hea |
| Diamond | +10 Hea |

### Intelligence Prefixes (Position 3)
| Prefix | Bonus |
|--------|-------|
| Fictional | +1 Int |
| Sharp | +2 Int |
| Keen | +3 Int |
| Ordinary | +4 Int |
| Wise | +5 Int |
| Mystic | +6 Int |
| Worshipful | +7 Int |
| Sublime | +8 Int |
| Pure | +9 Int |
| Absolute | +10 Int |

### Wisdom Prefixes (Position 4)
| Prefix | Bonus |
|--------|-------|
| Fixed | +1 Wis |
| Confirmatory | +2 Wis |
| Celebrated | +3 Wis |
| Dignified | +4 Wis |
| Merciful | +5 Wis |
| Predictive | +6 Wis |
| Foreseeable | +7 Wis |
| Noble | +8 Wis |
| Reverent | +9 Wis |
| Paradoxic | +10 Wis |

### Agility Prefixes (Position 5)
| Prefix | Bonus |
|--------|-------|
| Agile | +1 Agi |
| Reflective | +2 Agi |
| Instant | +3 Agi |
| Flexible | +4 Agi |
| Dashy | +5 Agi |
| Rush | +6 Agi |
| Fierce | +7 Agi |
| Flashy | +8 Agi |
| Unlimited | +9 Agi |
| Gliding | +10 Agi |

### Special/Compound Prefixes
| Prefix | Bonuses |
|--------|---------|
| Legendary | +5 all stats, +75 HP, +75 MP |
| The King, GuhBalHan's | +6 all stats, +100 HP, +80 MP |
| Wandering Knight's | +1 Str, +1 Hea, +1 Agi, +1 OTP |
| Expert Knight's | +4 Str, +3 Hea, +3 Agi, +75 HP, +25 MP, +2 OTP, +5 Def |

---

## Enhancement (EB) System

Weapons can be enhanced using Enhancement Beads (EB). Each level increases damage but costs more:

| EB Level | Revision Required | Cumulative Revision | Price |
|----------|-------------------|---------------------|-------|
| +1 | 1 | 1 | 1,500 |
| +2 | 2 | 3 | 3,000 |
| +3 | 2 | 5 | 4,500 |
| +4 | 4 | 9 | 6,000 |
| +5 | 5 | 14 | 7,500 |
| +6 | 7 | 21 | 9,000 |
| +7 | 10 | 31 | 10,500 |
| +8 | 13 | 44 | 12,000 |
| +9 | 21 | 65 | 13,500 |
| +10 | 29 | 94 | 15,000 |
| +11 | 45 | 139 | 16,500 |
| +12 | 92 | 231 | 18,000 |
| +13 | 188 | 419 | 19,500 |
| +14 | 192 | 611 | 21,000 |
| +15 | 196 | 807 | 22,500 |
| +16 | 200 | 1,007 | 24,000 |

---

## Experience & Leveling

### Player Experience Table (Sample)

| Level | Total XP Required |
|-------|-------------------|
| 1 | 5 |
| 10 | 1,125 |
| 20 | 17,493 |
| 30 | 166,758 |
| 40 | 1,211,834 |
| 50 | 10,255,633 |
| 60 | 63,902,104 |
| 70 | 396,260,232 |
| 80 | 12,271,870,776 |
| 90 | 113,984,718,984 |
| 99 | 980,241,432,400 |

### Pet/Egg Stats by Grade

Pets (Ancient Animals) gain stats as they level. Format: Attack / Defense / Magic

| Grade | Stats (Atk/Def/Mag) |
|-------|---------------------|
| G01 | 1 / 1 / 1 |
| G10 | 6 / 3 / 2 |
| G20 | 11 / 6 / 4 |
| G30 | 16 / 8 / 6 |
| G40 | 22 / 12 / 8 |
| G50 | 25 / 14 / 9 |
| G60 | 28 / 19 / 13 |
| G70 | 35 / 25 / 21 |
| G80 | 45 / 30 / 26 |

---

## Monster Groups

Monsters are categorized into groups based on location/type:

| Group ID | Description |
|----------|-------------|
| 1 | Demon soldiers (early game) |
| 2 | Big Handed creatures |
| 3 | Demon military |
| 4 | Water Dragons |
| 5 | Cave monsters |
| 6-10 | Mid-level areas |
| 11-15 | High-level areas |
| 16-23 | End-game areas |

---

## Drop System

Drops are organized by groups and chances:

- **drp_group1**: Drop-group ID — not the monster ID
- **drp_group2**: Drop category (values 1–6 occur; their exact meanings are unverified)
- **drp_chance1**: Base drop percentage
- **drp_chance2**: Secondary chance within category
- **drp_item**: Item ID that drops
- **drp_monst**: Monster ID
- **drp_rev**: Drop revision/variant. On equipment, text values name the talisman/prefix carried by the dropped item; blank means the base item without a talisman. Numeric values occur on Geons rows and must not be interpreted as prefix IDs.

**Calculating actual drop rate:**
```
Actual Rate = (drp_chance1 / 100) × (drp_chance2 / 100) × 100%
```

Example: If chance1=60 and chance2=4, actual rate = 0.6 × 0.04 = 2.4%

**Bango application (player-confirmed 2026-07-26):** Bango uses these
KalEncyclopedia rates. First require the current monster-item association in
`bango_data/DROPS.csv`, then join the normalized monster and item names to this
table. Keep every matching row separate because each equipment `drp_rev`
represents a different talisman/base variant with its own rate.

---

## Quest Types

| Type | Description |
|------|-------------|
| Quest | Main storyline quests |
| Event | Special event quests |
| RQ | Repeatable quests (can be done multiple times) |

---

## Skills System

### Earning Skill Points

**Players earn skill points from two sources:**

1. **Leveling**: **1 skill point per level** starting from level 2
   - Levels 2-65 = 64 skill points total

2. **Quest Rewards**: Some quests reward skill points
   - Check the `que_rew` column in QUESTS.csv for "Skill point" or "Skill Point"
   - Approximately 12 quests between levels 11-38 reward 1 skill point each

**Total by level 65: 76 skill points** (64 from levels + 12 from quests)

### Skill Types
- **Type 1**: Passive skills (always active)
- **Type 2**: Active skills (must be activated)

### Skill Positions (which tree/tab they appear in)
Each class has multiple skill tabs numbered by position.

### Skill Point Investment Rules

**How Skill Points Are Spent:**
- Each grade of a skill costs 1 skill point
- Example: To reach grade 5 of a skill, you spend 5 skill points total (1 per grade)
- Skills can have different maximum grades (some go to 5, others to 10, 20, etc.)

### Skill Grade Progression & Availability

**CRITICAL: Each skill has a maximum available grade based on character level AND skill format restrictions.**

**Theoretical maximum grade** = `min(skill_max_grade, current_level - skill_start_level + 1)`

**However, the skill's format (see next section) may further restrict when certain grades become available.**

For example, a skill with format "30 60|5 2" means:
- Grades 1-5 only available at level 30+
- Grades 6-7 only available at level 60+
- Even if the formula says grade 7 is possible at level 37, the format restricts it to grade 5 maximum

**Examples:**

1. **Splashy Ice** (starts at level 34, max 5 grades):
   - Level 34: Max grade available = 1 (34 - 34 + 1 = 1)
   - Level 35: Max grade available = 2 (35 - 34 + 1 = 2)
   - Level 36: Max grade available = 3
   - Level 37: Max grade available = 4
   - Level 38+: Max grade available = 5 (capped at skill max)

2. **Magic Mastery: Ice** (starts at level 30, format "30 60|5 2", max 7 grades):
   - Level 30: Max grade available = 1 (30 - 30 + 1 = 1)
   - Level 31: Max grade available = 2 (31 - 30 + 1 = 2)
   - Level 34: Max grade available = 5 (34 - 30 + 1 = 5, capped by format at 5 until level 60)
   - Level 36: Max grade available = 5 (format restricts grades 6-7 until level 60)
   - Level 60: Max grade available = 6 (60 - 30 + 1 = 31, but format now allows grade 6)
   - Level 61: Max grade available = 7 (format allows grade 7 at 61)

3. **After using Stone of Birth to reset:**
   - If you reset a skill at level 50, you can immediately rebuild it to any grade up to min(skill_max, 50 - skill_start_level + 1)
   - Example: Resetting Splashy Ice at level 50 allows immediate investment to grade 5 (since 50 - 34 + 1 = 17, which exceeds the max of 5)

### Skill Level Requirements Format

Skills have level requirements in format: `"LVL1 LVL2 LVL3|POINTS1 POINTS2 POINTS3"`

**Interpreting the format:**
- Left side of `|`: Level requirements for each grade threshold
- Right side of `|`: Number of grades available at each threshold

**Example 1:** `"30 60|5 2"`
- At level 30: Grades 1-5 available (5 grades)
- At level 60: Grades 6-7 available (2 additional grades)
- Total: 7 grades maximum

**Important: Grade availability is still constrained by the progression rule above!**
- At level 30: Only grade 1 is available (30 - 30 + 1 = 1)
- At level 31: Grade 2 becomes available
- At level 34: Grade 5 becomes available
- At level 60: Grades 6-7 become available

**Example 2:** `"50 57 63|1 1 1"`
- Level 50: Grade 1 available
- Level 57: Grade 2 available  
- Level 63: Grade 3 available
- Cost: 1 skill point per grade

### Free Skill Upgrades (Level 50+ Rule)

**Skills that start at level 49 or below receive free grade upgrades for any grades unlocked at level 50+.**

**Bango verification status:** This rule comes from the legacy
KalEncyclopedia schedules. Bango's current client schedules reproduce every
declared band on 156 class-scoped legacy twins, but omit the legacy level-60
free band on 15 otherwise exact matches. Client files do not establish whether
those automatic grades still occur on the live Bango server. Treat the rule as
**to confirm in play for Bango**, not as a Bango-file fact.

**How it works:**
1. Count the skill points needed for grades unlocked before level 50
2. All grades that unlock at level 50 or higher are **FREE** (cost 0 skill points)

**Examples:**

1. **Meditation** `"32 60|3 2"`:
   - Grades 1-3: Unlocked at levels 32-34, cost 3 skill points
   - Grades 4-5: Unlocked at levels 60-61, cost 0 skill points (FREE)
   - Total cost: 3 skill points for 5 grades

2. **Refining Weapon** `"50 57 62 66 69|1 1 1 1 1"`:
   - Starts at level 50, so NO free upgrades
   - All 5 grades cost skill points
   - Total cost: 5 skill points

3. **Magic Mastery: Ice** `"30 60|5 2"`:
   - Grades 1-5: Available at levels 30-34, cost 5 skill points
   - Grades 6-7: Available at levels 60-61, cost 0 skill points (FREE)
   - Total cost: 5 skill points for 7 grades

### Skill Prerequisites

Format: `"SKILL_NAME|REQUIRED_GRADE"`

- Example: `"Perfect Evasion|10"` means you need Perfect Evasion at grade 10 first
- Prerequisites must be met before investing in dependent skills
- When using Stone of Birth, resetting a skill also resets all dependent skills

### Stone of Birth (SoB) Item

**Stone of Birth is an item that resets skill points, allowing reallocation.**

**How Stone of Birth Works:**

1. **Select a skill to reset**
   - The selected skill is reset to grade 0
   - **Exception: Lightning Magic cannot go below grade 1** (it always starts at 1 by default)
   - All skill points invested in that skill are refunded

2. **Cascade effect on dependent skills**
   - Any skill that has the reset skill as a prerequisite is ALSO reset
   - All skill points from dependent skills are also refunded
   - This cascades through the entire skill tree

3. **Prerequisites are checked again**
   - After reset, you cannot invest in a skill unless its prerequisites are met
   - You must rebuild prerequisite skills first before accessing dependent skills

**Example:**
- You have: Lightning Magic (10), Lightning Blow (10), Lightning Summons (2)
- Lightning Summons requires Lightning Blow grade 10
- If you use SoB on Lightning Magic:
  - Lightning Magic resets to **1** (not 0, because it cannot go below 1) - refund 9 SP
  - Lightning Blow ALSO resets to 0 (refund 10 SP) because it requires Lightning Magic grade 10
  - Lightning Summons ALSO resets to 0 (refund 2 SP) because it requires Lightning Blow grade 10
  - Total refund: 21 SP
  - You must rebuild Lightning Magic to 10, then Lightning Blow to 10, before you can invest in Lightning Summons

**Strategic Use:**
- SoB allows players to optimize builds by temporarily investing in skills for certain level ranges
- Example: Use Shock Wave for levels 31-33, then reset it at level 34 to invest in Ice skills
- Careful planning prevents wasting SoB uses and ensures efficient skill point allocation

---

## Dragon Fuse System

Dragons can be fused with equipment for bonuses:

| Dragon Type | Weapon Bonus | Armor Bonus |
|-------------|--------------|-------------|
| Imoogi (Silver) | +1-2% Dmg, +1 R.Stat, +2 OTP, +30 HP, +10 MP | +3-4% Def, +1 R.Stat |
| Shadow Dragon (Green) | +3-4% Dmg, +1 R.Stat, +4 OTP, +50 HP, +30 MP | +5-6% Def, +1 R.Stat |
| Blood Dragon (Red) | +5-6% Dmg, +1 R.Stat, +6 OTP, +70 HP, +50 MP | +7-8% Def, +1 R.Stat |

---

## Beads of Fire System

Beads of Fire (BoF) add bonus stats to armor:
- Each piece can have BoF socketed
- Bonuses stack across armor set
- Different BoF levels provide different stat increases

---

## Set Bonuses

Wearing full sets of same-grade armor provides set bonuses:
- Full G60 set bonus
- Full G65 set bonus
- Full G70 set bonus

Set bonuses typically include: +% Damage, +Defense, +HP, +Resistances

---

## Damage Calculation Formulas

### Physical Damage
```
Base Damage = Weapon PDMin to Weapon PDMax
Strength Bonus = Strength × multiplier (class-dependent)
Total = (Base + Strength Bonus) × (1 + Enhancement Bonus) × (1 + Prefix Bonus)
```

### Magic Damage
```
Base Damage = Weapon MDMin to Weapon MDMax
Intelligence Bonus = Intelligence × multiplier
Total = (Base + Int Bonus) × (1 + Enhancement Bonus)
```

---

## Tips for Character Building

### Knight Build Tips
- Focus on Strength and Health
- Strength increases physical damage significantly
- Health provides survivability
- Two-hand swords for damage, Sword+Shield for tanking

### Archer Build Tips
- Balance Agility and Strength
- Agility improves evasion and attack speed
- Strength increases arrow damage

### Magician Build Tips
- Intelligence for damage
- Wisdom for MP pool, magic defense and amount healed
- Can spec into healing or damage

### Thief Build Tips
- Agility is king for evasion
- Strength for damage
- High-risk, high-reward playstyle

---

## Data Reference Notes

When answering questions, reference the CSV data files:
- **ITEMS.csv**: All equipment with stats
- **MONSTERS.csv**: All monsters with stats and drops
- **DROPS.csv**: Drop tables linking monsters to items
- **SKILLS.csv**: All skills with formulas
- **QUESTS.csv**: All quests
- **PREFIXES.csv**: All item prefixes
- **LVL_PLAYERS.csv**: XP table
- **LVL_EGGS.csv**: Pet stat progression
- **EBS.csv**: Enhancement costs
- **POSITIONS.csv**: Class advancement paths
- **CASTS.csv**: Base classes

---

## Common Player Questions

**Q: What's the best armor for a level 50 Knight?**
A: Look for G50 Diamond Scaled Armor set. Prioritize Health and Strength prefixes.

**Q: Where do I farm Legendary prefix items?**
A: Higher level monsters (60+) have better chances for rare prefixes. Check the DROPS table.

**Q: How much XP do I need for level 70?**
A: 396,260,232 total XP.

**Q: What skills should a beginner Magician get?**
A: Start with basic attack magic, then Cure for healing. Fire Magic or Ice Magic for damage.

**Q: How many skill points do I get per level?**
A: You earn 1 skill point per level starting from level 2 (64 total by level 65). Additionally, some quests reward skill points - check the `que_rew` column in QUESTS.csv for entries containing "Skill point" or "Skill Point". Total available by level 65: approximately 76 points.

**Q: Can I reset my skills?**
A: Yes, using a Stone of Birth (SoB) item. This resets a selected skill and all dependent skills, refunding the skill points.

---

*This knowledge base enables AI assistants to answer detailed questions about KalOnline game mechanics, items, monsters, character building, and more.*

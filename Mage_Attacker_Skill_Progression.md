# Attacker Mage — Optimal Skill Progression (Levels 2–69)

## Build Philosophy

This is a **Lightning-primary, Ice-secondary attacker mage** build optimized for damage output and competitive server-launch scenarios. The strategy uses a **level-65 Stone of Birth (SoB) reskill package** to redistribute points into the full tri-element Storm kit for endgame.

> **Bango-current correction — 2026-07-25.** The previous version was
> contradicted by `bango_data\QUESTS.csv` and by Heal's registered `7|5`
> schedule. It understated the level-65 budget, treated two paid Heal grades as
> free, undercounted the reset refund, and omitted three reset Lightning skills
> from the rebuild. The figures below were recomputed by
> `tools\mage_plan_recompute\recompute_mage_plan.py`; the audit ledger is in
> `analysis\mage_plan_recompute\`.

**Core principles:**
- Lightning is the primary damage school (instant burst, no DoT complications)
- Ice is secondary (Splashy Ice for AoE, Frost/Cold Binding for CC)
- Fire is skipped entirely until the level-65 reskill
- Utility skills (Heal, Meditation, Speed Up) are picked up at minimum viable investment
- Support skills (Cure, Revival, Restore) get 1 point each for group utility

## Skill Point Budget

| Source | Points |
|---|---|
| Levels 2–65 | 64 |
| Bango quest rewards at or below level 65 (12 quests) | 15 |
| **Total available by 65** | **79** |

Bango has **14 skill-point quests worth 17 SP in total**; the final two points
arrive at levels 76 and 77. This difference from the legacy export and the
2012-era player guide is classified **`bango-modification`**.

Free upgrades (grades unlocked at level 50+ on pre-50 skills) do not cost points. Notably: Magic Mastery: Lightning and Ice grades 6–7 (free at 60–61), Meditation grades 4–5 (free at 60–61), and Revival (M) grade 2 (free at 60). Heal is `7|5`: all five grades unlock before level 50 and therefore all five cost SP.

---

## Progression Table

### Phase 1 — Levels 2–12: Ice Magic Foundation

| Lv | Skill Change | SP Spent | Cumulative SP |
|---|---|---|---|
| 2 | — (save point) | 0 | 1 |
| 3 | Ice Magic 0→1 | 1 | 1 |
| 4 | Ice Magic 1→2 | 1 | 1 |
| 5 | Ice Magic 2→3 | 1 | 1 |
| 6 | Ice Magic 3→4 | 1 | 1 |
| 7 | Ice Magic 4→5 | 1 | 1 |
| 8 | Ice Magic 5→6 | 1 | 1 |
| 9 | Ice Magic 6→7 | 1 | 1 |
| 10 | Ice Magic 7→8 | 1 | 1 |
| 11 | Ice Magic 8→9 | 1 | 2 |
| 12 | Ice Magic 9→10 | 1 | 2 |

**Rationale:** Ice Magic is the leveling workhorse for levels 3–20. Max it to 10 ASAP. Level 2's point is saved because Ice Magic unlocks at level 3.

### Phase 2 — Levels 13–20: Banking Points

| Lv | Skill Change | Notes |
|---|---|---|
| 13–20 | — | Bank all points; the Bango ledger reaches **17 banked SP** after level 20 |

**Rationale:** No worthwhile offensive skills unlock until Lightning Blow at 21. Lightning Magic (base skill, starts at grade 1 for free) does not need investment yet. All points are saved for the level 21 spike.

### Phase 3 — Levels 21–30: Lightning Blow + Mastery

| Lv | Skill Change | SP Spent | Notes |
|---|---|---|---|
| 21 | Lightning Magic 1→10, Lightning Blow 0→1 | 10 | Leaves 8 SP banked after the level-21 point arrives |
| 22 | Lightning Blow 1→2 | 1 | |
| 23 | Lightning Blow 2→3 | 1 | |
| 24 | Lightning Blow 3→4 | 1 | |
| 25 | Lightning Blow 4→5 | 1 | |
| 26 | Lightning Blow 5→6 | 1 | |
| 27 | Lightning Blow 6→7 | 1 | |
| 28 | Lightning Blow 7→8 | 1 | |
| 29 | Lightning Blow 8→9 | 1 | |
| 30 | Lightning Blow 9→10, Magic Mastery: Lightning 0→1 | 2 | Mastery unlocks at 30 |

**Rationale:** Lightning Blow is the primary single-target nuke. Maxing it to 10 is the top priority. Magic Mastery: Lightning is a passive that boosts max magic attack — grab grade 1 immediately at 30.

### Phase 4 — Levels 31–38: Mastery + Ice AoE + Utility

| Lv | Skill Change | SP Spent | Notes |
|---|---|---|---|
| 31 | MM: Lightning 1→2 | 1 | |
| 32 | MM: Lightning 2→3, Meditation 0→1 | 2 | Meditation unlocks at 32 |
| 33 | MM: Lightning 3→4, Meditation 1→2 | 2 | |
| 34 | MM: Lightning 4→5, Meditation 2→3, Splashy Ice 0→1, MM: Ice 0→5 | 8 | Big level — 1 + 1 + 1 + 5 SP. MM: Ice grades 6–7 will be free at 60+ |
| 35 | Splashy Ice 1→2 | 1 | |
| 36 | Splashy Ice 2→3 | 1 | |
| 37 | Splashy Ice 3→4, Speed Up 0→1 | 2 | Speed Up unlocks at 36 |
| 38 | Splashy Ice 4→5, Speed Up 1→2 | 2 | |

**Rationale:** MM: Lightning 5 is the cap until level 60 (grades 6–7 are free at 60+). Splashy Ice is the primary AoE — max it. MM: Ice boosts slow chance on ice spells. Speed Up is essential mobility (3 grades max pre-50).

### Phase 5 — Levels 39–49: Support & CC Toolkit

| Lv | Skill Change | SP Spent | Notes |
|---|---|---|---|
| 39 | Speed Up 2→3 | 1 | |
| 40 | Heal 0→1 | 1 | |
| 41 | Heal 1→2 | 1 | |
| 42 | Heal 2→3 | 1 | |
| 43 | Cure 0→1 | 1 | Requires Heal 3. Labeled "Cure 1" in some UIs, actual skill name is "Cure" |
| 44 | Revival (M) 0→1 | 1 | Requires Cure 1. Essential group utility |
| 45 | Frost 0→1 | 1 | Requires Splashy Ice 1. Single-target freeze CC |
| 46 | Restore 0→1 | 1 | Requires Revival (M) 1. Full HP restore |
| 47 | Shock Wave 0→1 | 1 | Requires Lightning Magic 5. Lightning AoE |
| 48 | Shock Wave 1→2 | 1 | |
| 49 | Shock Wave 2→3 | 1 | |

**Rationale:** Heal 3 is the minimum needed to unlock the Cure→Revival→Restore chain. Frost provides hard CC. Shock Wave is a secondary AoE option (Lightning-element).

### Phase 6 — Levels 50–64: Advanced Skills

| Lv | Skill Change | SP Spent | Notes |
|---|---|---|---|
| 50 | Refining Weapon 0→1 | 1 | Starts at 50, all 5 grades cost SP (no free upgrades) |
| 51 | Shock Wave 3→4 | 1 | |
| 52 | Shock Wave 4→5 | 1 | |
| 53 | Lightning Summons 0→1 | 1 | Requires Lightning Blow 10 |
| 54 | Cold Binding 0→1 | 1 | Requires Frost 1. AoE freeze |
| 55 | — | 0 | Save point |
| 56 | Ice Restriction 0→1 | 1 | Requires Splashy Ice 2. Single-target ice nuke + slow |
| 57 | Refining Weapon 1→2, Lightning Summons 1→2 | 2 | Both unlock grade 2 at 57 |
| 58 | Cold Binding 1→2 | 1 | |
| 59 | Chain Lightning 0→1 | 1 | Requires Lightning Blow 10. Lightning chain AoE |
| 60 | Revival (M) 1→2 | 0 | **FREE** (grade unlocks at 60, skill starts pre-50) |
| 61 | — | 0 | MM: Lightning 5→7, MM: Ice 5→7, and Meditation 3→5 apply free |
| 62 | Refining Weapon 2→3 | 1 | |
| 63 | Cold Binding 2→3, Thunder 0→1 | 2 | Thunder requires Lightning Summons 2 |
| 64 | Heal 3→5 | 2 | Heal is `7|5`; grades 4–5 are paid |

**Checkpoint:** The plan has spent **75 SP** and banks **3 SP** at the end of
level 64. The level-65 point raises the pre-reset bank to **4 SP**.

---

## Level 65: Stone of Birth Reskill

At level 65, reset **Ice Magic, Magic Mastery: Ice, Lightning Magic, and Heal**.
Their dependents cascade from the current Bango prerequisite graph.

These are **four independent selected roots**. Under the documented
selected-skill SoB rule, this exact package requires four reset selections; the
registered files do not establish that one item resets all four. If Rafael's
server supplies a full-tree event reset, confirm that behaviour in game. The
allocation arithmetic below is valid for the stated four-root reset set.

### What Gets Reset (Cascade)

| Reset Target | Grade Lost | SP Refunded | Cascade Reason |
|---|---|---|---|
| Ice Magic | 10→0 | 10 | Direct reset |
| → Splashy Ice | 5→0 | 5 | Requires Ice Magic 10 |
| → → Frost | 1→0 | 1 | Requires Splashy Ice 1 |
| → → → Cold Binding | 3→0 | 3 | Requires Frost 1 |
| → → Ice Restriction | 1→0 | 1 | Requires Splashy Ice 2 |
| MM: Ice | 7→0 | 5 | Independent selected root; grades 6–7 were free |
| Lightning Magic | 10→1 | 9 | Cannot go below 1 (base skill rule) |
| → Lightning Blow | 10→0 | 10 | Requires Lightning Magic 10 |
| → Shock Wave | 5→0 | 5 | Requires Lightning Magic 5 |
| → → Lightning Summons | 2→0 | 2 | Requires Lightning Blow 10 |
| → → → Thunder | 1→0 | 1 | Requires Lightning Summons 2 |
| → → Chain Lightning | 1→0 | 1 | Requires Lightning Blow 10 |
| Heal | 5→0 | 5 | Direct reset; all five grades were paid |
| → Cure | 1→0 | 1 | Requires Heal 3 |
| → → Revival (M) | 2→0 | 1 | Requires Cure 1 (grade 2 was free) |
| → → → Restore | 1→0 | 1 | Requires Revival (M) 1 |
| **Total refunded** | | **61** | Computed from paid grades |

### Rebuild at Level 65

The 61-SP refund plus the 4-SP bank gives **65 SP to reallocate**:

| Skill | Grade | SP Cost | Notes |
|---|---|---|---|
| Lightning Magic | 1→10 | 9 | Rebuild (starts at 1, cannot go to 0) |
| Ice Magic | 0→10 | 10 | Rebuild |
| Fire Magic | 0→10 | 10 | **NEW** — unlocked via refund. Needed for Fire Blow |
| Lightning Blow | 0→10 | 10 | Rebuild |
| Splashy Ice | 0→2 | 2 | Minimum for Ice Restriction prereq |
| Fire Blow | 0→5 | 5 | **NEW** — requires Fire Magic 10 |
| Frost | 0→1 | 1 | Rebuild for CC |
| Cold Binding | 0→1 | 1 | Rebuild |
| Ice Restriction | 0→1 | 1 | Rebuild |
| Chain Lightning | 0→1 | 1 | Rebuild |
| Explosive Burst | 0→1 | 1 | **NEW** — requires Fire Blow 5. Fire AoE nuke |
| Thunder Storm | 0→1 | 1 | **NEW** — requires Chain Lightning 1. Lightning Storm |
| Ice Storm | 0→1 | 1 | **NEW** — requires Ice Restriction 1. Ice Storm |
| Fire Storm | 0→1 | 1 | **NEW** — requires Explosive Burst 1. Fire Storm |
| Heal | 0→1 | 1 | Minimal rebuild |
| Shock Wave | 0→5 | 5 | Rebuild after the Lightning reset |
| Lightning Summons | 0→2 | 2 | Rebuild after Lightning Blow |
| Thunder | 0→1 | 1 | Rebuild after Lightning Summons |
| **Subtotal rebuild** | | **63** | **2 SP remain banked** |

### Post-65 Remaining Investments

| Lv | Skill Change | SP Spent | Notes |
|---|---|---|---|
| 66 | Refining Weapon 3→4, Thunder 1→2 | 2 | Uses the level point plus 1 banked SP; 1 remains |
| 67 | MM: Ice 0→1 | 1 | Rebuild the reset mastery; 1 remains |
| 68 | MM: Ice 1→2 | 1 | 1 remains |
| 69 | Refining Weapon 4→5, MM: Ice 2→3 | 2 | Uses the level point plus the final banked SP |

---

## Final Build Summary at Level 69

### Offensive Skills

| Skill | Grade | Element | Role |
|---|---|---|---|
| Lightning Magic | 10 | Lightning | Base attack |
| Ice Magic | 10 | Ice | Base attack |
| Fire Magic | 10 | Fire | Base attack |
| Lightning Blow | 10 | Lightning | Primary single-target nuke |
| Splashy Ice | 2 | Ice | AoE + slow |
| Fire Blow | 5 | Fire | AoE + DoT |
| Shock Wave | 5 | Lightning | AoE |
| Lightning Summons | 2 | Lightning | Single-target burst |
| Chain Lightning | 1 | Lightning | Chain AoE |
| Explosive Burst | 1 | Fire | Area nuke |
| Thunder Storm | 1 | Lightning | Sustained area damage |
| Ice Storm | 1 | Ice | Sustained area damage |
| Fire Storm | 1 | Fire | Sustained area damage |
| Thunder | 2 | Lightning | Single-target burst |
| Ice Restriction | 1 | Ice | Single-target + slow |
| Frost | 1 | Ice | Hard CC (freeze) |
| Cold Binding | 1 | Ice | AoE freeze |

### Passive / Mastery

| Skill | Grade | Notes |
|---|---|---|
| Magic Mastery: Lightning | 7 | Grades 6–7 free at 60+ |
| Magic Mastery: Ice | 3 | Reset at 65 and rebuilt. Buy grades 4–5 at 70–71; grades 6–7 then cost 0 |
| Refining Weapon | 5 | +Attack/Magic attack |
| Meditation | 5 | Grades 4–5 free at 60+ |

### Utility / Support

| Skill | Grade | Notes |
|---|---|---|
| Heal | 1 | Minimal self-heal (post-reskill) |
| Speed Up | 3 | Movement buff |
| Cure | — | Lost in reskill (Heal only at 1, Cure needs Heal 3) |
| Revival (M) | — | Lost in reskill |
| Restore | — | Lost in reskill |

**Trade-off at 65:** The reskill sacrifices the Cure→Revival→Restore support chain to fund tri-element Storms. This is deliberate for an attacker build — group healing is deprioritized in favor of maximum AoE damage coverage.

---

## Key Decision Points

1. **Level 2:** Save point (Ice Magic starts at 3)
2. **Level 13–20:** Bank everything for the level-21 Lightning Blow spike
3. **Level 34:** Big investment level — Splashy Ice + MM: Ice in one burst
4. **Level 43–46:** Support chain (Cure→Revival→Restore) — minimum investment for group utility
5. **Level 65:** Four-root SoB reskill package — transforms from Lightning specialist into tri-element Storm mage
6. **Post-65 trade-off:** No more Cure/Revival/Restore — pure attacker commitment

## Verification

The complete per-level bank, reset cascade, quest list, and final grades are
machine-readable in `analysis\mage_plan_recompute\`. Tests lock the Bango
cutoff (**15 quest SP by level 65**), the full reward total (**17 SP**), Heal
3→5 (**2 SP**), the reset refund (**61 SP**), and the rebuild (**63 SP**).

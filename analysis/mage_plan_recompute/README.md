# Attacker-Mage recomputation evidence

Generated from the current Bango quest table, current Bango prerequisite graph,
and `bango_data\SKILL_GRADE_SCHEDULES.csv`. Where Bango omits a legacy
level-60 free band, the legacy band remains an explicit, unverified fallback
rather than a Bango fact. Arithmetic is produced by
`tools\mage_plan_recompute\recompute_mage_plan.py`.

- Classification: **bango-data-with-unverified-legacy-free-band-fallback**
- Free-upgrade rule: **legacy rule retained for arithmetic; Bango live retention is not established by client files**
- Bango skill-point quests: **14 quests / 17 SP**
- At or below level 65: **15 quest SP**
- Total available at level 65: **79 SP**
- Heal 3→5 cost: **2 SP**
- Pre-reset spend / bank: **75 / 4 SP**
- Computed reset refund: **61 SP**
- Rebuild spend / bank: **63 / 2 SP**
- Level-69 ending bank after the scheduled allocations: **0 SP**

The documented selected-skill reset rule requires **4**
independent root selections for this exact reset set. A claim that one item resets
all four roots is not established by the registered files and remains an in-game
confirmation point.

# Bango ↔ KalEncyclopedia reconciliation

Generated from the byte-exact Bango client decode on 2026-07-25. Matching uses
normalized display names where numeric ID spaces differ. Exact row-level
evidence is in the adjacent `RECONCILIATION_*.csv` files.

## Result

- Items: **1,838** Bango records versus 704 legacy rows.
  **354** normalized names match;
  **951** are Bango-only and
  **244** are legacy-only.
- Skills: **536** Bango records versus 206 legacy rows.
  **172** normalized names match;
  **233** are Bango-only and
  **23** are legacy-only.
- Skill parameters: **422** of the overlapping
  mana/range/cast/cooldown fields are semantically identical after parsing and
  canonicalization; **52** differ only
  because legacy melee range uses `0` where Bango uses `weapon_range`; and
  **150** are genuine value/formula
  differences with attribution left open.
- Prefixes: **682** Bango records versus 102 legacy rows.
  **102** IDs overlap and
  **580** IDs exist only in Bango.
- Drops: **24,271** Bango monster-item rows. At normalized
  monster/item-name level, **1,528** pairs
  match, **8,632** are Bango-only, and
  **9,478** are legacy-only.
- Quests: **116** Bango rows.
  **51** names match,
  **65** are Bango-only, and
  **106** are legacy-only.

## Authority verdict

`ITEMS.csv`, `SKILLS.csv`, and `PREFIXES.csv` are superseded for client-visible
definitions. `QUESTS.csv` is superseded for the listed quest fields.
`DROPS.csv` has split authority: Bango supplies current monster-item
associations, while the 2026-07-26 player-confirmed external premise makes
same-name KalEncyclopedia rows current for `chance1`, `chance2` and `drp_rev`
rate/talisman variants. Unmatched Bango pairs have no mapped rate.

`MONSTERS.csv` is only partially superseded: Bango's 1,004 ID→name mappings win,
while combat stats remain an explicitly unverified legacy fallback. `CASTS`,
`POSITIONS`, `LVL_PLAYERS`, `LVL_EGGS`, and `EBS` also remain unverified
fallbacks because the recovered client archive has no directly equivalent
complete table. `OPTIONS` is viewer configuration and `PL_SAVE` is planner user
data, so neither is game authority.

The machine-readable 13-row verdict is `CSV_AUTHORITY.csv`.

## Important structural findings

1. Bango item IDs use `inititem.dat` `Index`, not the KalEncyclopedia
   `ita_azon` space. Reconciliation by raw ID would be false; for example,
   Short Iron Sword is Bango index 1 but legacy ID 174.
2. Bango `jobsystem.dat` is much broader than the planner export and includes
   player, monster and other client skill definitions. Legacy `sk_poz` tree IDs
   are not synthesized where the client has no equivalent.
3. Skill `action` IDs are class-scoped, not global. All prerequisite conditions
   are resolved against the source skill's exact `limit` scope. The official
   Mage, Knight and Archer pages confirm the compare-position labels; both
   official Thief pages are `TODO` and no Shaman class page is present, so
   `label_verification` keeps that limitation visible.
4. Bango `prefix.dat` extends far beyond the legacy 102-row table. English
   `prefixname` strings cover only the subset shipped in `message.dat`; unnamed
   high IDs retain exact stat records with an explicit unresolved-name marker.
5. `prefix.dat` contains **360 exact enhancement rows**: +1 through +15 for
   HP, MP, attack+magic, Strength, Dexterity, Intelligence, Wisdom and Health,
   each in three application bands. The values are Bango-current client data;
   the meaning of the three bands is not named in decoded English data and is
   left unverified.
6. `config.pk:droplist.dat` preserves a numeric value and `n`/`y`/`q` flag, but
   not the legacy two-stage chance fields. The native value is still not a
   probability; current rates come from the separately registered
   Bango/KalEncyclopedia equivalence and a normalized pair join.
7. The other client tables are not discarded: all s-expressions and text
   records are indexed in the raw coverage outputs, including event, task,
   swap/crafting, object, tips, guidebook, checksum and server-list data.
8. `SKILL_GRADE_SCHEDULES.csv` has one row for all **536**
   skills. Class-scoped comparison finds
   **156** exact legacy
   reproductions, **15**
   schedules that differ only by an omitted legacy level-60 free band, and
   **2** genuine Bango
   schedule changes. The free-band mechanic cannot be settled from client
   files and is marked for in-game confirmation.
9. Same-name skills are never cross-matched between scopes. Mage Thunderbolt
   (`mage-75`) reproduces legacy `75|5`; the one-grade Gunchi Thunderbolt
   (`gunchie-76`) is a separate transformation skill, not a Bango change to the
   Mage skill.

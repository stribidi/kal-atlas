# Bango client data

Generated from Rafael's recovered Bango `config.pk` by
`tools/bango_data_builder/build_bango_data.py`.

**Provenance:** every entity row is `bango-file` (tier 3 in `SOURCES.md`).
These files supersede the tier-5 KalEncyclopedia exports only for the fields
named below. Client data can still lag live server behaviour; measurements and
server files outrank it.

## Row counts

| File | Rows |
| --- | --- |
| `CSV_AUTHORITY.csv` | 13 |
| `DROPS.csv` | 24,271 |
| `ENHANCEMENT_BONUSES.csv` | 360 |
| `FILE_MANIFEST.csv` | 31 |
| `ITEMS.csv` | 1,838 |
| `ITEM_ATTRIBUTES.csv` | 5,187 |
| `JOBSYSTEM.csv` | 9 |
| `MESSAGES.csv` | 10,312 |
| `MONSTER_QUESTS.csv` | 369 |
| `PARSE_ANOMALIES.csv` | 1 |
| `PARSE_ERRORS.csv` | 0 |
| `PREFIXES.csv` | 682 |
| `PREFIX_ATTRIBUTES.csv` | 952 |
| `QUESTS.csv` | 116 |
| `QUEST_STEPS.csv` | 187 |
| `QUEST_STEP_ITEMS.csv` | 182 |
| `RAW_SEXPR_RECORDS.csv` | 18,094 |
| `RECONCILIATION_DROP_PAIRS.csv` | 19,638 |
| `RECONCILIATION_ITEMS.csv` | 1,549 |
| `RECONCILIATION_PREFIXES.csv` | 682 |
| `RECONCILIATION_QUESTS.csv` | 222 |
| `RECONCILIATION_SKILLS.csv` | 428 |
| `RECONCILIATION_SKILL_PARAMS.csv` | 624 |
| `SHINSU_ABILITIES.csv` | 4 |
| `SKILLS.csv` | 536 |
| `SKILL_GRADE_SCHEDULES.csv` | 536 |
| `SKILL_PREREQUISITES.csv` | 68 |
| `TASKQUEST_ITEMS.csv` | 76 |
| `TEXT_LINES.csv` | 6,543 |

## Core schemas

- `ITEMS.csv` mirrors the legacy `ITEMS.csv` columns where the mapping is
  direct: Bango `Index` → `ita_azon`, resolved `itemname` → `ita_name`,
  `level` → `ita_grade`, `limit[1]` → `ita_lvllim`, and `buy` → `ita_price`.
  Unsupported legacy viewer
  encodings stay blank. Every native field is preserved in the `bango_*`
  columns; nested stats are queryable in `ITEM_ATTRIBUTES.csv`.
- `SKILLS.csv` mirrors direct name/type/description/icon/effect fields. Bango
  prefix-form `parameter` expressions are retained exactly and converted to
  post-order RPN in `bango_parameter_rpn_json`. `compare` positions 1–4 are
  exposed as mana/energy, range, cast milliseconds and cooldown milliseconds
  in both the legacy-shaped columns and named `bango_*_rpn_json` columns.
  `bango_compare_label_status_json` records whether each label was confirmed by
  ability text and/or a populated official class page; the official Thief pages
  are currently `TODO`, and no Shaman page exists, so those class-specific
  labels remain visibly unverified. The legacy `sk_pars` field stays blank
  because Bango's ability parameters also include costs and durations, so
  copying them into the legacy damage-only field would be false. Native
  conditions and the full record stay in `bango_*` JSON columns.
- `SKILL_PREREQUISITES.csv` resolves every `condition` edge by class-scoped
  `action` ID and reports unresolved or ambiguous targets instead of dropping
  them. Action IDs are not globally unique across classes.
- `SKILL_GRADE_SCHEDULES.csv` converts `bango_level_json` plus cumulative
  `bango_maxlevel_json` into the canonical incremental schedule used by the
  project, with one row per Bango skill. It classifies exact legacy
  reproductions, Bango-only schedules, source disagreements, records without a
  client schedule, and the legacy level-60 free bands that Bango's client
  records omit. The client cannot establish whether those automatic/free bands
  still occur live, so that question remains visibly unverified.
- `PREFIXES.csv` carries Bango prefix ID/name plus exact native stat JSON.
  `PREFIX_ATTRIBUTES.csv` is the normalized tall table. The legacy positional
  `pre_rev` encoding is deliberately not synthesized.
- `ENHANCEMENT_BONUSES.csv` is the complete Bango +1…+15 grid found in
  `prefix.dat`: eight stat families across three application bands. The exact
  bonuses are known; the client text does not establish what the three bands
  apply to, so `application_band_meaning` remains `unverified`.
- `DROPS.csv` carries Bango monster/item IDs, resolved names, the numeric value,
  and the literal `n` / `y` / `q` flag. Those native rows do **not** expose the
  legacy `chance1 × chance2` fields, so the columns stay blank. A
  player-confirmed external premise dated 2026-07-26 establishes that Bango
  uses the KalEncyclopedia rates: consumers join normalized monster and item
  names to `data/DROPS.csv` and preserve every `drp_rev` variant.
- `QUESTS.csv` mirrors level/name/text/reward fields and retains exact Bango
  experience, contribution, skill points, prerequisite and raw steps.
  `QUEST_STEPS.csv` and `QUEST_STEP_ITEMS.csv` normalize the step structure.
- `MESSAGES.csv` is the complete namespaced string table, including
  `itemname`, `monstername`, `prefixname`, `itemdesc`, `npcname` and `sys`.
- `JOBSYSTEM.csv`, `MONSTER_QUESTS.csv`, and `TASKQUEST_ITEMS.csv` expose
  additional native client tables with no clean legacy equivalent.
- `RAW_SEXPR_RECORDS.csv` retains every parsed s-expression as compact JSON.
  `TEXT_LINES.csv` retains each nonblank record in the five plain-text inputs.
- `FILE_MANIFEST.csv` proves coverage for all 31 archive entries by SHA-256,
  byte size, classification, record count and parsed count.
- `PARSE_ERRORS.csv` is header-only for a successful build.
- `PARSE_ANOMALIES.csv` records source defects that do not prevent record
  recovery, including the unmatched top-level delimiter in `task-k.dat`.

All JSON cells are compact UTF-8 JSON. Invalid source CP949 bytes are displayed
as `\xNN`; the parser never replaces or silently drops them.

## Legacy CSV authority

The third-party CSVs divide into current Bango fields that are superseded,
unverified fallbacks, non-game/user data, and one explicit exception:
Rafael's 2026-07-26 external confirmation makes same-pair KalEncyclopedia drop
rates and variants Bango-applicable.

| Legacy CSV | Verdict | Current Bango coverage |
| --- | --- | --- |
| `CASTS.csv` | legacy-fallback-unverified | Bango skills confirm class tokens, but there is no Bango class master table. |
| `POSITIONS.csv` | legacy-fallback-unverified | Bango exposes skill keys and limits, not a directly equivalent advancement table. |
| `LVL_PLAYERS.csv` | legacy-fallback-unverified | No level-XP curve exists in the recovered client config. |
| `LVL_EGGS.csv` | legacy-fallback-unverified | No directly equivalent pet-grade table exists in the recovered config. |
| `SKILLS.csv` | superseded-for-client-skill-definitions | Bango names, limits, schedules, formulas, costs and descriptions win; legacy planner tree IDs remain annotation only. |
| `ITEMS.csv` | superseded-for-client-item-definitions | Bango item IDs, stats, grade, requirements and prices win; legacy type taxonomy is annotation only. |
| `PREFIXES.csv` | superseded | Bango prefix IDs and stat records win. Some high IDs lack an English name string. |
| `EBS.csv` | legacy-fallback-unverified | Recovered client data does not contain the equivalent enhancement-cost table. |
| `MONSTERS.csv` | partially-superseded | Bango IDs and names win. Combat stats remain legacy fallback and are not confirmed Bango values. |
| `DROPS.csv` | split-authority-rates-confirmed | Bango monster-item associations and n/y/q flags win. For a matching normalized monster-item pair, legacy chance1/chance2 and drp_rev rows are Bango-applicable rate/talisman variants; unmatched pairs have no mapped rate. |
| `QUESTS.csv` | superseded-for-listed-fields | Bango level, names, rewards, prerequisites and steps win; legacy viewer-only type/picture fields remain annotation. |
| `OPTIONS.csv` | not-game-data | KalEncyclopedia program settings; no Bango authority question. |
| `PL_SAVE.csv` | user-data-not-reconciled | Saved planner builds, not server/client entity data. |

See `RECONCILIATION.md` and the six `RECONCILIATION_*.csv` files for the
row-level comparisons.

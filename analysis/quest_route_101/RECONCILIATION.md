# Quest route reconciliation

Extracted from `research/quest_guide_versions/kal_quest_guide_full_10.html`
(revision **10**, SHA-256 `55f7ee9e17d602b1d9b44e20c16fd0bdc768ec38518facdf7da6f4c8d578aca1`).

- Stages: **36**
- Route entries: **91**
- Ordered steps: **337**
- Distinct `(town, npcId)` pairs: **58**
- Bango name matches: **71**
- Matched rows with at least one parsed disagreement: **39**
- No Bango name match: **20**

The route-local quest numbers were never compared to Bango IDs. Regular quest
numbers first recover a legacy display name; Bango matching then uses exact,
registered renamed-quest, or high-confidence normalized names. Eight generic
event-route rows use registered current Bango names after their ordered
objectives were checked; source accept/turn-in or multi-part rows can therefore
share one Bango quest. Bango level, XP, contribution, skill points,
prerequisite and steps win wherever matched.

No hotlinked or embedded images were copied.

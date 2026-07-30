# Quest route reconciliation

Extracted from `research/quest_guide_versions/kal_quest_guide_full-30.7.-v1.0.html`
(revision **v1.0 (30.7.)**, SHA-256 `4bddfd5a52fe5fc59b72bd277f5806c5f0d2492a29c0c66cf86b3639fa03bda0`).

- Stages: **31**
- Route entries: **71**
- Ordered steps: **270**
- Distinct `(town, npcId)` pairs: **58**
- Bango name matches: **66**
- Matched rows with at least one parsed disagreement: **34**
- No Bango name match: **0**
- Activity-batch rows covering several quests at once: **5**
- Highest level the source routes: **60**

The route-local quest numbers were never compared to Bango IDs. Regular quest
numbers first recover a legacy display name; Bango matching then uses exact,
registered renamed-quest, or high-confidence normalized names. Generic
event-route rows use registered current Bango names after their ordered
objectives were checked; source accept/turn-in or multi-part rows can therefore
share one Bango quest. Bango level, XP, contribution, skill points,
prerequisite and steps win wherever matched.

A `route_kind` of `batch` marks a row that is an activity batch rather than one
quest — v1.0 opens with five of them, covering the first seven quests together.
Such a row has no single Bango quest by construction, which is why it is
counted apart from a failed match.

No hotlinked or embedded images were copied by this tool.

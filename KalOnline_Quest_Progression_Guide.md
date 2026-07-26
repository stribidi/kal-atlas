# KalOnline — Optimized Quest Progression Guide

## How to Use This Guide

Quests are grouped into **Phases** by level range. Within each phase, quests are batched into **Steps** that maximize simultaneous farming. NPC blocking chains (where two quests share an NPC, forcing sequential completion) are tracked throughout.

**Teleportation is free** between all villages (Narootuh, Cargo Station, Geuh Mine, Pub of Giant Bird, Fort). Travel time is only relevant when moving from a village to a hunting zone.

**Authority note (2026-07-25):** batching/order comes from the legacy route and
the permitted player guide; current levels and rewards come from
`bango_data\QUESTS.csv` wherever a name match exists. The `Q##` labels in the
first six phases are legacy display numbers, not Bango IDs. The full 91-row
translation and every disagreement are in
`analysis\quest_route_101\QUEST_RECONCILIATION.csv`.

---

## Hunting Zone Quick Reference

Instead of grid coordinates, zones are described by their position relative to the nearest village.

| Short Name | Description | Key Mobs |
|---|---|---|
| **North of Narootuh** | Coastal corridor just north of village | Demon Vulgar, Wild Small Demon |
| **East of Narootuh** | Valley at Narootuh's east exit | Demon Vulgar, Wild Small Demon |
| **Narootuh–Cargo road** | Eastern road connecting the two villages | Demon Escort Soldier/Archer, Big Handed Inhabitant/Slave |
| **Bay curve west of Cargo** | Perimeter around the water west of Cargo Station | Demon Escort Soldier/Archer, Suicide Bomber |
| **Just north of Cargo** | Valley junction on the road out of Cargo toward Mine | Big Handed Inhabitant/Slave, Demon Carcass Scavenger, Suicide Bomber |
| **Midway Cargo-to-Mine** | Central valley choke point on Cargo–Mine road | Big Handed Inhabitant/Slave, Demon Carcass Scavenger, Demon Soldier |
| **East cape past Cargo** | Dead-end peninsula east of Cargo | Big Handed Inhabitant/Slave, Carcass Scavenger, Demon Soldier, Infantry, Throwing Soldier |
| **South approach to Mine** | Valley just south of Geuh Mine | Big Handed Warrior (Blue/Red), Demon Soldier, Demon Infantry |
| **Mine–Pub valley** | Connector valley between Geuh Mine and Pub | Big Handed Warrior (Blue/Red), Demon Soldier, Infantry, Wild Demon Soldier, Shock Trooper, Flag Bearer, Water Dragon, Throwing Soldier |
| **North of Mine** | Dead-end plateau above Geuh Mine | Wild Demon Soldier, Shock Trooper, Flag Bearer, Water Dragon |
| **West of Pub** | Large open valley west of Pub of Giant Bird | Demon Band, Armored Knight, Mad Knight, Commander, Hungry Water Dragon, Water Dragon Predator/Commander |
| **Road south toward Fort** | Main road south of Narootuh leading to Fort | Big Handed Warrior (Blue/Red), Demon Soldier, Infantry, Wild Demon Soldier, Shock Trooper, Flag Bearer, Water Dragon, Throwing Soldier |
| **Northwest of Fort** | Immediate approach northwest of Fort | Water Dragon, Hungry Water Dragon, Flag Bearer, Wild Demon Soldier, Shock Trooper |
| **West of Fort** | Deep area west of Fort approach | Demon Band, Flag Bearer, Water Dragon Predator, Hungry Water Dragon, Armored Knight, Mad Knight, Commander, Water Dragon Commander |
| **Southwest beach (ghost zone)** | Coastal area southwest beyond Fort | Devil Soldiers, all Ghost types, Demon Mad Knight |
| **Far south peninsula** | Southernmost peninsula beyond the beach | All Devil Soldier types |

---

## NPC Blocking Chains

If an NPC appears in Quest A (lower level) and Quest B (higher level), **A must be completed before B can start**.

### Critical Chains

**Sae-Won (Cargo-4)** — longest chain, 6 quests:
> Q03 → Q08 → Q17 → Q18 → Q19 → Q23

**Yea-Jin (Narooth-1):**
> Q07 → Q09 → Q13

**Gwee-Sik (Mine-3):**
> Q05 → Q11 → Q15 → Q30

**Joo-Nong (Mine-2):**
> Q10 → Q13 → Q15

**Guh-Sosun (Cargo-2):**
> Q09 → Q20 → Q22

**Jae-Ga (Fort-14):**
> E08 → E09 → E10 → E11

### Other Chains

- **Ha-Jik (Narooth-11):** Q06 → Q11
- **Gwang-Chun (Narooth-26):** Q01 → Q06
- **Noo-Woong (Cargo-7):** Q05 → Q06
- **Won-Jung (Cargo-1):** Q07 → Q21
- **Ok-Jin (Cargo-5):** Q10 → Q14
- **Yang-Do (Mine-19):** Q14 → Q27
- **In-Pill (Cargo-8):** E03 → E04
- **HyungJoo-SeungGong (Mine-1):** E05 → E06
- **Mother Moon Hee (Fort-32):** Q24 → Q26

### Combined Prerequisite Table

| Quest | Must Complete First (NPC reason) |
|---|---|
| Q06 (Lv10) | Q01 (Gwang-Chun) + Q05 (Noo-Woong) |
| Q08 (Lv12) | Q03 (Sae-Won) |
| Q09 (Lv13) | Q07 (Yea-Jin) |
| Q11 (Lv15) | Q05 (Gwee-Sik) + Q06 (Ha-Jik) |
| Q13 (Lv17) | Q09 (Yea-Jin) + Q10 (Joo-Nong) |
| Q14 (Lv18) | Q10 (Ok-Jin) |
| Q15 (Lv19) | Q11 (Gwee-Sik) + Q13 (Joo-Nong) |
| Q17 (Lv21) | Q08 (Sae-Won) |
| Q20 (Lv26) | Q09 (Guh-Sosun) |
| Q22 (Lv28) | Q20 (Guh-Sosun) |
| Q23 (Lv29) | Q19 (Sae-Won) |
| Q26 (Lv32) | Q24 (Mother Moon Hee) |
| Q27 (Lv33) | Q14 (Yang-Do) |
| Q30 (Lv36) | Q15 (Gwee-Sik) |

---

## Phase 1 — Levels 1–8: Narootuh Basics

### Step 1A: Delivery + SpearHead Cluster

**Q01 — Favor of Sailor Gwang-Chun** (Lv1) — Delivery only, no combat. Pick up from Gwang-Chun (Narooth-26), deliver message to Nu-Rook (Cargo-3), return. Do this early to free Gwang-Chun for Q06.

**Q02 — Message Collection** (Lv1) — Kill Demon SpearHead, return to Sea-Geun (Narooth-6).

**Q03 — Grasp the Situation of Demons** (Lv1) — Kill Demon SpearHead, return to Mak-Ahnsoo (Narooth-24), then deliver map to Sae-Won (Cargo-4).

> **FARM CLUSTER: Q02 + Q03 together.** Both target Demon SpearHead. Activate both, farm, turn in both. Deliver Q03's map to Sae-Won — this frees him for Q08 later.

**E01 — Beginning of Long Journey** (Lv1) — Kill Demons Plungerer, return to Chun-Sooin (Narooth-9). Can overlap with Q02/Q03 area.

### Step 1B: Escort Cluster (Level 6+)

**Q04 — General, Poong-seup's Missing** (Lv6) — 10× Demon Escort Archer bows → Ji-Hun (Narooth-10).

**E02 — Appointment of General In-Pill /a** (Lv1) — 30× Demon Escort Soldier & Archer heads → Sae-Ryu (Narooth-27).

> **FARM CLUSTER: Q04 + E02 together.** Both target Escort mobs. Farm at the **Narootuh–Cargo road** or **bay curve west of Cargo**.

### Step 1C: Suicide Bomber (Level 8)

**Q05 — Farmer, Noo-Woong's Favor** (Lv8) — 10× Suicide Bomber oil. Talk to Noo-Woong (Cargo-7) → Gwee-Sik (Mine-3) → hunt at **just north of Cargo** or **bay curve west of Cargo** → turn in to Noo-Woong.

> ⚠️ **Finish Q05 before Phase 2.** It blocks Q06 (via Noo-Woong) and Q11 (via Gwee-Sik).

---

## Phase 2 — Levels 10–13: Cargo Corridor Mega-Cluster

The **midway Cargo-to-Mine** and **just north of Cargo** zones contain Big Handed Inhabitant, Big Handed Slave, Demon Carcass Scavenger, Suicide Bomber, and Demon Soldier all together. This is where you stack the most quests simultaneously.

### Step 2A: The Big Cluster

**Prerequisites:** Q01 done ✓, Q05 done ✓, Q03 map delivered to Sae-Won ✓

1. Pick up **Q06** (Lv10) from Ha-Jik (Narooth-11) → walk through the talk chain until you reach the hunting step.
2. Pick up **E03** from In-Pill (Cargo-8) — Big Handed Inhabitant heads.
3. Pick up **Q07** (Lv11) from Won-Jung (Cargo-1) — Big Hand Slaves for Peony/Vetch. **[+1 SKILL POINT]**

> **FARM CLUSTER: Q06 + E03 + Q07 at midway Cargo-to-Mine / just north of Cargo.**
>
> | Quest | Monster | Items Needed |
> |---|---|---|
> | Q06 | Big Handed Inhabitant | 15 Teeth |
> | Q06 | Demon Carcass Scavenger | 5 Straw Rice Bags |
> | E03 | Big Handed Inhabitant | Heads |
> | Q07 | Big Hand Slaves | 10 Peony + 10 Vetch |

> 💡 **Pre-farm 22× White Peony + 22× Milk Vetch** during Q07. The extra 12+12 are for Q09. Peony/Vetch are regular Slave drops — stockpile now to make Q09 an instant turn-in later.

### Step 2B: Carcass Scavenger Double-Dip

1. Turn in E03 to In-Pill (Cargo-8).
2. Pick up **E04** from In-Pill — Demon Carcass Scavenger (In-Pill's Scabbard).
3. Pick up **Q08** (Lv12) from Sae-Won (Cargo-4) — 25× Demon Carcass.

> **FARM CLUSTER: E04 + Q08 — same mob!** Both quests target Demon Carcass Scavenger. Farm at **midway Cargo-to-Mine / just north of Cargo**. Every kill drops items for both quests.

> ⚠️ **Do NOT start Q08 before E04 is active.** Same mob — farm both simultaneously.

### Step 2C: Turn-In Wave + Q09

1. Turn in Q06, Q07, Q08, E04.
2. Pick up **Q09** (Lv13) from Guh-Sosun (Cargo-2). Requires Q07 done (frees Yea-Jin).
3. Q09 needs 12 Peony + 12 Vetch — **already pre-farmed!** Do the talk steps and hand in immediately.

---

## Phase 3 — Levels 14–20: Mine–Pub Valley Mass Farm

The **Mine–Pub valley** (between Geuh Mine and Pub) contains Big Handed Warrior (Blue+Red), Demon Soldier, Demon Infantry, Wild Demon Soldier, Shock Trooper, Flag Bearer, Water Dragon, and Throwing Soldier — all in one zone. Eight quests farm here.

### Step 3A: First Batch — 4 Quests Simultaneously

All four use different NPCs. No blocking. Activate all at once.

| Quest | Lv | Monster | Items | Reward |
|---|---|---|---|---|
| Q10 | 14 | Demon Soldier | 20 Teeth | +3,534 XP |
| Q11 | 15 | Big Handed Blue Warrior | 25 Rice Cake | **+1 SP** |
| Q12 | 16 | Big Handed Red Warrior | Wa-Ryu's Talisman | **+2 SP (Bango)** |
| E05 | 1 | Big Handed Warriors (both) | 40 Heads | +1,000 XP |

> **FARM CLUSTER: Q10 + Q11 + Q12 + E05 at Mine–Pub valley.** Every Blue/Red Warrior kill feeds Q11 or Q12 *and* E05. Demon Soldiers are mixed in for Q10. The **south approach to Mine** also has Blue/Red Warriors + Soldiers as overflow.

> 💡 **Turn in Q10 ASAP** — it unblocks both Q13 (via Joo-Nong) and Q14 (via Ok-Jin).

### Step 3B: Second Batch — After Q10 Done

| Quest | Lv | Monster | Items | Unlocked By | Reward |
|---|---|---|---|---|---|
| Q13 | 17 | Demon Infantry | 30 Gold | Q09 (Yea-Jin) + Q10 (Joo-Nong) | **+1 SP** |
| Q14 | 18 | Demon Throwing Soldier | 30 Bamboo Poles | Q10 (Ok-Jin) | **+2 SP (Bango)** |

Both mobs present in **Mine–Pub valley**. Farm alongside any remaining Q11/Q12 items.

> 💡 **Turn in Q11 and Q13 promptly** — both are needed to unlock Q15.

### Step 3C: Triple Stack — Q15 + Q16 + Q17

**Prerequisites:** Q11 done (Gwee-Sik) + Q13 done (Joo-Nong) → unlocks Q15. Q08 done → unlocks Q17 (Sae-Won).

| Quest | Lv | Monster | Items | NPC | Reward |
|---|---|---|---|---|---|
| Q15 | 19 | Wild Demon Soldier | 30 Statues | Gwee-Sik (Mine-3) | +5,600 XP |
| Q16 | 20 | Demon Shock Trooper | 30 Gold | Ja-Gan (Cargo-14) | **+1 SP** |
| Q17 | 21 | Demon Flag Bearer | 35 Red Flags | Sae-Won (Cargo-4) | +8,500 XP |

> **FARM CLUSTER: Q15 + Q16 + Q17 at Mine–Pub valley / North of Mine.** All three NPCs are different — no blocking. All three mobs coexist in the same zone.

### Step 3D: Water Dragon (After Q17 Done)

**Q18 — Beheading the Demon Water Dragon** (Lv23) — 35× Demon Water Dragon heads → Sae-Won (Cargo-4). Farm at **North of Mine** or **northwest of Fort**.

> 💡 Sae-Won chain progress: Q03 ✓ → Q08 ✓ → Q17 ✓ → Q18 ✓ → Q19 next.

---

## Phase 4 — Levels 25–29: Upper Zones

The **west of Pub** zone contains Demon Band, Armored Knight, Mad Knight, Commander, Hungry Water Dragon, Water Dragon Predator, and Water Dragon Commander. The **west of Fort** zone has similar spawns. Multiple quests cluster here.

### Step 4A: Triple Stack — Q19 + Q20 + Q21

All three use different NPCs. No blocking between them.

| Quest | Lv | Monster | Items | NPC | Reward |
|---|---|---|---|---|---|
| Q19 | 25 | Demon Drum | 40 Drums | Sae-Won (Cargo-4) | **+1 SP** |
| Q20 | 26 | Demon Armoured Knight | 40 Armor | Guh-Sosun (Cargo-2) | **+21,750 XP (Bango)** |
| Q21 | 27 | Hungry Demon Water Dragon | 40 Clothes | Won-Jung (Cargo-1) | **+1 SP** |

> **FARM CLUSTER: Q19 + Q20 + Q21 at west of Pub / west of Fort.** Armored Knights and Hungry Water Dragons both spawn in these zones. Farm all three simultaneously.

### Step 4B: Double Stack — Q22 + Q23

After Q19 done (frees Sae-Won) and Q20 done (frees Guh-Sosun):

| Quest | Lv | Monster | Items | NPC | Reward |
|---|---|---|---|---|---|
| Q22 | 28 | Water Dragon Predator | 40 Skin | Guh-Sosun (Cargo-2) | **+1 SP** |
| Q23 | 29 | Demon Mad Knight | 40 Heads | Sae-Won (Cargo-4) | **+1 SP** |

> **FARM CLUSTER: Q22 + Q23 at west of Pub / west of Fort.** Both Water Dragon Predators and Mad Knights spawn in these zones.

---

## Phase 5 — Levels 30–38: Fort Ghosts & Government Service

### Step 5A: Government Service Chain (E06–E10)

At level 30, the Government Service event chain opens. These are sequential via shared NPCs.

| Quest | Name | Monster | Notes |
|---|---|---|---|
| E06 | Gov. Service /a | Demon Commander (1 head) | HyungJoo-SeungGong → Jin-Pyung (Mine). Needs E05 done. |
| E07 | Gov. Service /b | Castoff Baby Ghost, Ghost of Young Man/Woman | Hyun-Choong → Jin-Haeryang (Fort). **Independent NPC — run in parallel.** |
| E08 | Gov. Service /c | — (talk chain only) | Jae-Ga (Fort-14). No combat. |
| E09 | Gov. Service /d | Devil Soldiers (all types) | Jae-Ga. Needs E08 done. |
| E10 | Gov. Service /e | 1st Devil, 2nd Devil (bosses) | Jae-Ga. Needs E09 done. Rewards class trinket. |

> 💡 E07 uses different NPCs from E06/E08 — run E07 in parallel with the Jae-Ga chain.

### Step 5B: Ghost Quest Series

Ghost quests each use **unique Fort NPCs** — no blocking between them, except Q24 → Q26 (both use Mother Moon Hee at Fort-32).

| Quest | Lv | Monster | NPC (Fort) | Reward |
|---|---|---|---|---|
| Q24 | 30 | Cast of Baby Ghost | Mother Moon Hee (32) | +29,000 XP |
| Q25 | 31 | Ghost of Young Man | Heung-Pae (30) | +35,000 XP |
| Q26 | 32 | Ghost of Young Women | Duk-Yoon (41) + Mother Moon Hee (32) | +42,000 XP |
| Q27 | 33 | Demon Commander | Yang-Do (Mine-19) | **+2 SP (Bango; current ID 24)** |
| Q28 | 34 | Ghost of Blacksmith | Soo-Go (37) | +62,000 XP |
| Q29 | 35 | Ghost Of Ghost Guard | Dan-Bok (16) | +76,000 XP |
| Q30 | 36 | Demon Dragon Commander | Gwee-Sik (Mine-3) | **+79,000 XP (Bango)** |
| Q31 | 37 | Ghost Of Fellow Traveller | Ga-Gi (1) | +80,000 XP |
| Q32 | 38 | Ghost of Sealed Troop | Soo-Sung (18) | **+1 SP** |

All ghost mobs are at the **southwest beach beyond Fort**. Q27 and Q30 target commanders at **west of Pub** or **west of Fort** — different zone, do during travel between turn-ins.

### Step 5C: Optimal Ghost Batching

Since ghost quests mostly have unique NPCs, batch by level:

1. **Lv 30–31:** Activate Q24 + Q25 together. Farm ghosts at southwest beach.
2. **Lv 32–33:** Turn in Q24. Activate Q26 (Mother Moon Hee now free) + Q27 (Demon Commander at west of Pub — different zone). Farm ghosts for Q26 at southwest beach, Commander at west of Pub.
3. **Lv 34–36:** Q28 + Q29 + Q30 — all unique NPCs. Q28/Q29 ghosts at southwest beach, Q30 commanders at west of Pub. Stack all three.
4. **Lv 37–38:** Q31 + Q32 — both at southwest beach, unique NPCs. Stack both.

---

## Phase 6 — Levels 39–45+: Devil Soldiers & Mask Quests

### Step 6A: Devil Soldier Quests

| Quest | Lv | Monster | NPC (Fort) |
|---|---|---|---|
| Q33 | 39 | Devil Soldier With Bow | Yoo-Sang (13) |
| Q34 | 40 | Devil Soldier With Spear | Lim-Gang (2) |

Different NPCs — stack both. Farm at **southwest beach** or **far south peninsula**. If E09 (Gov. Service /d) is still active, triple-stack — it also targets Devil Soldiers.

### Step 6B: Mask Quest Series (Lv 41–45)

Each mask quest uses a **different numbered Fort NPC** (Fort-8 through Fort-12). No blocking between any of them. Stack as many as your level allows.

| Quest | Lv | Monster | Items | NPC |
|---|---|---|---|---|
| Q36 | 41 | Devil Troop Of Pain | 100 Masks | Woo-Joong (Fort-8) |
| Q38 | 42 | Devil Troop Of Greed | 100 Masks | Jwa-II (Fort-9) |
| Q40 | 43 | Devil Troop Of Jealousy | 100 Masks | Geun-Pyung (Fort-10) |
| Q42 | 44 | Devil Troop Of Hatred | 100 Masks | Dan-Joong (Fort-11) |
| Q44 | 45 | Devil Troop Of Madness | 100 Masks | Choi Choong (Fort-12) |

> 💡 All unique NPCs — if you're Lv43+ you can have Q36+Q38+Q40 active simultaneously. At Lv44 add Q42, at Lv45 add Q44.

Companion story quests (Q35, Q37, Q39, Q41, Q43) run in parallel — they use different NPCs from the mask quests.

### Step 6C: Event Quests

**E11 — Green Crystal of Doggebi Forest** (Lv40) — Devil Troop Of Absorbing Green. From Jae-Ga (Fort-14). Requires E10 done.

**E00 — Ancients Animals** (Lv15) — Naughty Doggebi. From Chang (Narooth-8). Unique NPC — can be done whenever you reach the Doggebi area.

---

## Skill Point Quest Checklist

The legacy 12-point checklist was contradicted by Bango-current client data on
2026-07-25. The authoritative 14-quest / 17-point checklist is at the end of
the extended route below. This is a **`bango-modification`**: the 2012 player
guide and legacy export agree with each other, while Bango changed the rewards.

---

## Extended Route — Levels 46–101

**Authority:** route order and batching come from the permitted player-authored
guide; current level/reward/step fields come from `bango_data\QUESTS.csv`
where a name match exists. Bango wins every recorded disagreement. The complete
91-row reconciliation, including unmatched/ambiguous event rows, is preserved
in `analysis\quest_route_101\QUEST_RECONCILIATION.csv`.

### Route 46+ Stage 1 — Doggebi broom collection

**Level / location:** Lv 46-49 — Out of town only, four NPCs in a row.

> **Farm cluster:** Quests 45-49 all need 5 "Blood of Big Handed" on top of
> their unique drop — stockpile that material once for the whole chain.

| Quest | Lv | Objective / route | Current Bango reward | Evidence |
|---|---:|---|---|---|
| The Limper's Favor | 46 | Kill Doggebi Of Monster Face for its broom + 5x Blood of Big Handed | 491510 XP; 1 contribution; 0 SP | Bango Q47 |
| The Blind Man's Favor | 47 | Kill Doggebi with Gong for its broom + 5x Blood of Big Handed | 590926 XP; 1 contribution; 0 SP | Bango Q48 |
| The Coward | 48 | Kill Drunken Doggebi for its broom + 5x Blood of Big Handed | 710280 XP; 1 contribution; 0 SP | Bango Q49 |
| The Hunchback's Favor | 49 | Kill Doggebi with Mask of Black Crow for its broom + 5x Blood of Big Handed | 853562 XP; 1 contribution; 0 SP | Bango Q50 |

### Route 46+ Stage 2 — Lv 50 kickoff: 2nd Job Change + Doggebi grind

**Level / location:** Lv 50 — Out of town, then the Fort.

> **Farm cluster:** Do Event Quest 20's permanent 2nd Job choice immediately.
> Event Quests 21–22 both farm Doggebi outside the Fort near D1.

| Quest | Lv | Objective / route | Current Bango reward | Evidence |
|---|---:|---|---|---|
| The Deaf Man's Favor | 50 | Find the Black Panther Mask Doggebi broom + 5x Blood of Big Handed | 1025563 XP; 1 contribution; 0 SP | Bango Q51 |
| [Event] New Government Position! | 50 | Return to Jae-Ga, receive the permanent 2nd Job position, and prepare for the level-70 continuation | 0 XP; 0 contribution; 0 SP | Bango Q9009; player route calls this Event 20 |
| Event Quest 21 | 50 | Kill 50 Giant Doggebi | 500000 XP; 0 contribution; 0 SP | player route; no confident Bango name match |
| Event Quest 22 | 50 | Kill 50 Guardian of Doggebi, then Angry Doggebi of Monster Face near D1 for Captured Doggebi | 500000 XP; 0 contribution; 0 SP | player route; no confident Bango name match |

### Route 46+ Stage 3 — Lv 51-52: One-armed Man + Forsaken Fort

**Level / location:** Lv 51-52 — Out of town, then Forsaken Fort.

> **Farm cluster:** Event Quests 23–25 use the same Doggebi Master NPC. Farm
> every required Doggebi spirit before turning them in.

| Quest | Lv | Objective / route | Current Bango reward | Evidence |
|---|---:|---|---|---|
| One-Armed Man's Favor | 51 | Find Giant Doggebi's Broom + 5x Blood of Big Handed | 1232024 XP; 1 contribution; 0 SP | Bango Q52 |
| Event Quest 23 | 52 | Monster Face, Gong and Drunken Doggebi spirits | 681882 XP; 0 contribution; 0 SP | player route; no confident Bango name match |
| Event Quest 24 | 52 | Black Crow and Black Panther Mask Doggebi spirits | 681882 XP; 0 contribution; 0 SP | player route; no confident Bango name match |
| Event Quest 25 | 52 | Giant and Guardian Doggebi spirits | 681882 XP; 0 contribution; 0 SP | player route; no confident Bango name match |
| Event Quest 26 | 52 | Kill 10 of each of the seven Doggebi types | 681882 XP; 0 contribution; 0 SP | player route; no confident Bango name match |

### Route 46+ Stage 4 — Lv 52-53: Manager's errand + first Pub visit

**Level / location:** Lv 52-53 — Out of town, then Fort → Pub of the Giant Bird.

| Quest | Lv | Objective / route | Current Bango reward | Evidence |
|---|---:|---|---|---|
| Legend of the Oh-Do Canyon Bridge | 52 | Guardian of Doggebi's Stone + 5x Water Dragon Blood | 1479838 XP; 1 contribution; 0 SP | Bango Q53 |
| The Dead People Around The Tomb(1) | 53 | 5x Skeleton Warrior's Head from Rotten Skeleton Warrior | 1777279 XP; 1 contribution; 0 SP | Bango Q58 |

### Route 46+ Stage 5 — Lv 54-57: Tomb Keeper grind chain

**Level / location:** Lv 54-57 — Pub of the Giant Bird.

> **Farm cluster:** Event Quests 30–33 and the regular Tomb quests cycle
> through Tomb Keeper [Gang-Man] (#13). Stack the Royal Tomb objectives across
> the whole level range.

| Quest | Lv | Objective / route | Current Bango reward | Evidence |
|---|---:|---|---|---|
| The Dead People Around The Tomb(2) | 54 | 5x Skeleton Warrior's Ribs | 2134273 XP; 1 contribution; 0 SP | Bango Q59 |
| Event Quest 28 | 54 | Kill 20 each of five D1 Doggebi types | 3013282 XP; 0 contribution; 0 SP | player route; no confident Bango name match |
| The Dead People Around The Tomb(3) | 55 | 5x Royal Tomb Keeper's Book | 2562731 XP; 1 contribution; 0 SP | Bango Q60 |
| Event Quest 30 | 55 | Get 5x Speed Up Medicine | 3289241 XP; 0 contribution; 0 SP | player route; no confident Bango name match |
| Event Quest 31 | 55 | Kill 60 each Rotten Skeleton Warrior (Sword/Lance) | 5289241 XP; 0 contribution; 0 SP | player route; no confident Bango name match |
| Event Quest 32 | 55 | Kill 100 Maid of Honor of the Royal Tomb | 12000000 XP; 0 contribution; 0 SP | player route; no confident Bango name match |
| The Dead People Around The Tomb(4) | 56 | 5x Royal Tomb Keeper's Lute | 3076950 XP; 1 contribution; 0 SP | Bango Q61 |
| Event Quest 33 | 57 | Kill 100 Minister of the Royal Tomb | 12975811 XP; 0 contribution; 0 SP | player route; no confident Bango name match |
| The Dead People Around The Tomb(5) | 57 | 5x Royal Tomb Keeper's Sword | 3694082 XP; 1 contribution; 0 SP | Bango Q62 |

### Route 46+ Stage 6 — Lv 58: City of Priest

**Level / location:** Lv 58 — Pub of the Giant Bird, then City of Priest.

> **Farm cluster:** Event Quests 35–37 share Priest [Ahn-Hyunsoo] (#11).
> Event Quest 38 switches to High Priest [Sur-An] (#9).

| Quest | Lv | Objective / route | Current Bango reward | Evidence |
|---|---:|---|---|---|
| The Dead People Around The Tomb(6) | 58 | 5x Royal Tomb Keeper's Shield | 4434711 XP; 1 contribution; 0 SP | Bango Q63 |
| Event Quest 35 | 58 | Get 5x Baked Mackerel in Soy Sauce | 10000000 XP; 0 contribution; 0 SP | player route; no confident Bango name match |
| Event Quest 36 | 58 | Kill 60 each Royal Tomb Keeper (Sword/Shield) | 10000000 XP; 0 contribution; 0 SP | player route; no confident Bango name match |
| Event Quest 37 | 58 | Kill 60 each Royal Tomb Keeper (Hammer/Spear) | 20835821 XP; 0 contribution; 0 SP | player route; no confident Bango name match |
| Event Quest 38 | 58 | Kill 60 of all four Royal Tomb Keeper variants | 20000000 XP; 0 contribution; 0 SP | player route; no confident Bango name match |

### Route 46+ Stage 7 — Lv 59-60: Tomb Keeper finale

**Level / location:** Lv 59-60 — Pub of the Giant Bird.

| Quest | Lv | Objective / route | Current Bango reward | Evidence |
|---|---:|---|---|---|
| The Dead People Around The Tomb(7) | 59 | 5x Royal Tomb Keeper's Spear | 5323540 XP; 1 contribution; 0 SP | Bango Q64 |
| The Dead People Around The Tomb(8) | 60 | 5x Royal Tomb Keeper's Iron Hammer | 6390210 XP; 1 contribution; 0 SP | Bango Q65 |

### Route 46+ Stage 8 — Lv 70: 3rd Job Change + Forest of Elements

**Level / location:** Lv 70 — Fort → City of Priest → Forest of Elements →
City of Priest.

> **Farm cluster:** Farm the five element sets and the four endgame drop items
> before returning to the altars. The current client splits this advancement
> into multiple event rows, so the player guide's combined route has no safe
> one-row Bango match.

| Quest | Lv | Objective / route | Current Bango reward | Evidence |
|---|---:|---|---|---|
| [Event] Gateway to success | 70 | Collect 20 each of five low-level elements; purify them at the altars; collect the four D4/Highlands/D2/Emok items, Complete E-Moogy's Scale and Horn of Doggebi Lord | 0 XP; 0 contribution; 0 SP | Bango Q9010; player route calls this Event 40 |
| Event Quest 41 | 70 | Collect five D5 essence types, 100 Essence of Undead and I'Lryer's Ring; obtain the Moving Trinket for Valley of Devah | 0 XP; 0 contribution; 0 SP | player route; composite, no safe one-row Bango match |

### Bango-only skill-point insertions — Levels 76–77

These current client quests are absent from the 2012-era route. Skipping either
loses one permanent skill point.

| Quest | Lv | Objective | Current Bango reward |
|---|---:|---|---|
| Precious recovery | 76 | Recover Green Bead, Ancestor's Treasure Sword and Prophetic Book from Goblins / Goblin Conjurators | 70183730 XP; **1 SP** |
| Guard of D'evah | 77 | Defeat Guard of D'evah and return to Dae-Gil | 84222881 XP; **1 SP** |

### Route 46+ Stage 9 — Lv 81: skill training

**Level / location:** Lv 81 — City of Priest.

| Quest | Lv | Objective / route | Evidence |
|---|---:|---|---|
| Quest 63 | 81 | Receive Training; choose OTP, EVA or DEF. The chosen skill scales with character level up to grade 20 | player route; no confident Bango name match |

### Route 46+ Stage 10 — AWAKEN trilogy

**Level / location:** Lv 91 / 96 / 101 — Narootuh → Emok Island → Valley of
Devah.

> **Farm cluster:** All three start at "DEAD Hye min", between Narootuh NPC 43
> and Refining Demon Gong. This is a landmark description; the source has no
> numbered pin.

| Quest | Lv | Objective / route | Evidence |
|---|---:|---|---|
| 1st AWAKEN | 91 | Kill 200 Twisted Demon Officer of Attack + 200 Twisted Imperial Demon Commander; collect 20 Mysterious Marble + 5 Piece of Shining Gold | player route; no confident Bango name match |
| 2nd AWAKEN | 96 | Craft 2 Gold Ingots; collect 60 Mysterious Marble + 15 Piece of Shining Gold | player route; no confident Bango name match |
| 3rd AWAKEN | 101 | Obtain Processing Awaken Lv3 from D'evah Boss; craft 1 Gold Ingot; collect 120 Mysterious Marble + 30 Piece of Shining Gold | player route; no confident Bango name match |

## Extended NPC Blocking / Route-Order Chains

Finish earlier uses before relying on the same NPC to offer a later quest.
The extraction preserves **58 distinct real-town `(town, npcId)` pairs**; these
are the shared high-level chains that affect the extension:

| Town / NPC | Ordered quest uses | Levels |
|---|---|---|
| City of Priest — Priest [Ahn-Hyunsoo] (#11) | Event Quest 35 → 36 → 37 | 58 → 58 → 58 |
| City of Priest — High Priest [Sur-An] (#9) | Event Quest 38 → Ceremony for elements2 | 58 → 70 |
| Temporary Fort — Soldier [Jae-Ga] (#20) | Government Service /d → Green Crystal → Event 20 → Event 22 → Event 28 → Ceremony for elements2 | 30 → 40 → 50 → 50 → 54 → 70 |
| Pub of the Giant Bird — Tomb Keeper [Gang-Man] (#13) | Tomb(1) → Tomb(2) → Tomb(3) → Events 30–32 → Tomb(4) → Event 33 → Tomb(5) → Tomb(6) → Tomb(7) → Tomb(8) | 53 → 54 → 55 → 55 → 56 → 57 → 58 → 59 → 60 |

The full pair list and ordered step evidence are in
`analysis\quest_route_101\NPC_CHAINS.csv` and
`analysis\quest_route_101\FRIEND_QUEST_STEPS.csv`.

## Current Bango Skill-Point Quest Checklist

**14 quests award 17 total SP.** These values come from
`bango_data\QUESTS.csv`, including the level cutoff used by the Mage plan.

| Bango ID | Quest | Lv | SP | XP |
|---:|---|---:|---:|---:|
| 7 | Won-Jung and Yae-Jin's Love | 11 | **1** | 2500 |
| 11 | Undelivered Rice Cake | 15 | **1** | 4000 |
| 12 | Wa-Ryu's Talisman | 16 | **2** | 8000 |
| 13 | Finding Yae-Jin's Father | 17 | **1** | 4500 |
| 14 | Collecting Yang-Do's Bamboo Poles | 18 | **2** | 9600 |
| 16 | Ja-Gan's Good Conduct | 20 | **1** | 7000 |
| 19 | Demon's Drum | 25 | **1** | 12000 |
| 21 | Collecting Clothes Stained with Blood | 27 | **1** | 16300 |
| 22 | Materials of Winter Clothes | 28 | **1** | 19000 |
| 23 | Hunting the Demon Mad Knight | 29 | **1** | 22000 |
| 24 | Helping Yang-Do | 33 | **2** | 47000 |
| 33 | Dilemma of Jae-Ga Troop's Scouts | 38 | **1** | 90000 |
| 77 | Precious recovery | 76 | **1** | 70183730 |
| 79 | Guard of D'evah | 77 | **1** | 84222881 |

# Quest map images and their credits

`QUEST_MAPS.json` carries all 80 pins and every quest→pin link. Pin positions
are **percentages of their own map image**, so a pin only lands correctly on
the exact artwork it was placed against. Substituting a different map of the
same place puts every pin in the wrong spot.

All nine maps are present.

## Credits

This artwork is other people's work. The site names its author under every map
it draws, and the quest pages repeat the credit in their source note.

| Maps | By | Where it came from |
|---|---|---|
| `naroo`, `jook`, `geum`, `fort`, `pub`, `cop` — the six town maps | **mystic-city.de** | [KalOnline quest guides and maps](https://mystic-city.de/System/viewpage.php?page_id=48) |
| `wild`, `wildcargo`, `forest` — the three out-of-town crops | **Vresko.com** | world map artwork, republished by mystic-city.de and embedded in the guide |

The quest text and the route itself also originate with mystic-city.de's
guides; the pin placement and the level ordering are the friend's own work on
top of them.

Rafael's call, 2026-07-26: the maps may be published with the credit shown.

## Files

| Map | File | Size |
|---|---|---|
| `naroo` — Narootuh | `map-naroo.jpg` | 1176 × 1310 |
| `jook` — Jook-Suh Cargo Station | `map-jook.jpg` | 1000 × 1199 |
| `geum` — Geum-Oh Mine | `map-geum.jpg` | 1000 × 1368 |
| `fort` — Temporary Fort of Geum-Ohee Castle | `map-fort.jpg` | 1361 × 1221 |
| `pub` — Pub of the Giant Bird | `map-pub.jpg` | 886 × 719 |
| `cop` — City of Priest | `map-cop.jpg` | 1159 × 1236 |
| `wild` — Forsaken Fort area | `map-wild.jpg` | 538 × 514 |
| `wildcargo` — Cargo / Geum-Oh Mine area | `map-wildcargo.jpg` | 385 × 610 |
| `forest` — Forest of Elements / Tower of Priest | `map-forest.jpg` | 346 × 457 |

## Regenerating

```
python tools\quest_map_ingest\fetch_town_maps.py          # only if a town map is missing
python tools\quest_map_ingest\extract_quest_maps.py "<guide>.html"
python tools\knowledge_base_site\build_site_manifest.py
python tools\knowledge_base_site\build_deploy.py
```

`extract_quest_maps.py` picks up whichever map images are already on disk, so
the fetch only ever has to run once.

## Remaining gap

Ten quest steps are `F()` landmarks — dungeons and field locations with no town
map at all. They render as plain labels rather than pins, which is what the
original guide does too.

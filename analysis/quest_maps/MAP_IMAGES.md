# Quest map images — what is here and what is missing

`QUEST_MAPS.json` carries all 80 pins and every quest→pin link. Pin positions
are **percentages of their own map image**, so a pin only lands correctly on the
exact artwork it was placed against. Substituting a different map of the same
place puts every pin in the wrong spot.

## Present (3 of 9 maps, 22 of 80 pins)

Extracted from the guide file itself, where they are embedded as data URIs:

| Map | File | Size |
|---|---|---|
| `wild` — Forsaken Fort area | `map-wild.jpg` | 538 × 514 |
| `wildcargo` — Cargo / Geum-Oh Mine area | `map-wildcargo.jpg` | 385 × 610 |
| `forest` — Forest of Elements / Tower of Priest | `map-forest.jpg` | 346 × 457 |

## Missing (6 of 9 maps, 58 of 80 pins)

The six town maps — `naroo`, `jook`, `geum`, `fort`, `pub`, `cop` — are not in
the guide file. It hot-links them from `mystic-city.de`, and that artwork is
**not the guide author's to license**, which is why nothing was copied here.
This is the open item already recorded in `MEMORY.md`.

The site handles their absence rather than breaking: those maps show their pin
list with the same click-to-highlight behaviour in both directions, and say the
image is not included.

## To add them

Rafael's call, not the agent's. If the answer is yes:

```
python tools\quest_map_ingest\fetch_town_maps.py
```

It downloads the six JPEGs into this folder under the names the site already
looks for (`map-naroo.jpg` and so on), then rebuild the manifest and bundle.
Nothing else changes — the pins are already correct for that artwork.

If the answer is no, the alternative is to re-place 58 pins against the Bango
client's own map textures under `data\HyperText\MiniMap\`, which is manual work
per pin and would need a `.gtx` → PNG converter first.

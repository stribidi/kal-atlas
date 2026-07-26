# server_profile — the one place server rates are set

`SERVER_PROFILE.json` holds the rates that differ between KalOnline servers.
The KalEncyclopedia tables in `data\` are a 2011 export of some other server's
values; anything that scales with a server setting is computed from this file
rather than restated.

## What reads it

- `tools\knowledge_base_site\index.html` — the Levels page (player XP table,
  the monster-XP-per-level calculator and the egg table) multiplies by
  `experience_rate` and divides egg days by `egg_experience_per_day`.

## How to change a rate

Edit the number and set the matching `*_confirmed` flag to `true` once it has
been checked in play. Nothing else needs regenerating — the site reads the file
at run time. Rebuild `SITE_MANIFEST.json` only if the file is newly added.

Unconfirmed rates are labelled as unconfirmed wherever they change a displayed
number, per standing rule 6: a rate nobody has measured is not presented as a
measured one.

## Fields

| Field | Meaning | Default |
|---|---|---|
| `experience_rate` | Multiplier on every monster and quest XP value | `1` |
| `drop_rate_multiplier` | Multiplier on drop chances | `1` |
| `geons_rate` | Multiplier on Geons drops | `1` |
| `egg_experience_per_day` | XP an egg gains per day of carrying; divides `ExpToLvl` to give the day count KalEncyclopedia showed | `4800` |

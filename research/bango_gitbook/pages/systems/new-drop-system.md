> For the complete documentation index, see [llms.txt](https://bango-organization.gitbook.io/kalonline-2012-content/llms.txt). Markdown versions of documentation pages are available by appending `.md` to page URLs; this page is available as [Markdown](https://bango-organization.gitbook.io/kalonline-2012-content/systems/new-drop-system.md).

# New Drop System

Regular drop system is very straight-forward: each monster keeps track of all players that attack it. Aggro is based on hostility which is a number of damage that player dealt to the monster. The hostility may be increased (Staggering Blow) or decreased (Protection) depending on skill and player buff state.

Once the monster is dead, it simply calculates which party has the highest sum of hostility. Solo players are counted as single player parties. The party with highest sum of hostility gets all the drops.

This system is still present on Bango KalOnline, however there are changed to few key monsters in the game.

### Changes to the drop distribution from bosses

To convince broader group of players to participate in weekly or hourly bosses, the logic behind drop distribution has been changed. Now **for each item, each party has a chance equal to % of hostility share** to get it.

Examples:

<figure><img src="/files/9u1QFnBV1kgLJlE7gfab" alt=""><figcaption><p>Hostility Distribution upon Boss Death</p></figcaption></figure>

Let's imagine there are 2 parties and 1 solo player.&#x20;

* solo player made 12% of total damage (hostility)
* party A made 56% of total damage (hostility) (sum of all party A players)
* party B made 32% of total damage (hostility) (sum of all party B players)

Each item has separate chance of being assigned to Party A, Party B or solo player.

* aggro party (tankers) have the highest chance for each of the item: 56%
* Party B has 32% for each of the items
* solo player has 12% for each of the items

As a result of this chance, it will be usually the case that multiple parties get some drops. However, it is still that tank (aggro) party get the most of the drops (depending how high was their advantage versus other parties).

Please note that even for low level characters there is slight chance to get a loot, because dealing low (but higher than 0) damage is also subject to item distribution!

For now it is only applicable to:

* Demon's Queen
* Ghost of Dragon (BK)
* Elemental Masters (MK)
* Dunamic and Cheios

### Drop Info Broadcasting

Once the boss is dead, everyone can see what has been looted. It is also possible to see who picked the items as seen on the image.

<figure><img src="/files/4842tdCQFaALmaQlvl60" alt=""><figcaption></figcaption></figure>

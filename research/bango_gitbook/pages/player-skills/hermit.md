> For the complete documentation index, see [llms.txt](https://bango-organization.gitbook.io/kalonline-2012-content/llms.txt). Markdown versions of documentation pages are available by appending `.md` to page URLs; this page is available as [Markdown](https://bango-organization.gitbook.io/kalonline-2012-content/player-skills/hermit.md).

# Hermit

## Lightning Summons

<div align="left"><figure><img src="/files/IJY9clW2N5vfsbJwZz7V" alt=""><figcaption></figcaption></figure></div>

#### Description

Striking the lightning to the selected object from the sky.

#### Level Limit

* G1 - 53 Lv.
* G2 - 57 Lv.

#### Required Condition

* has Lightning Blow G10

#### Mana Consumption

```
22 + SKILL_LEVEL * 4
```

#### Range

190

#### Attack Points

```
MAGIC_ATTACK + BETWEEN(
    MIN(
        450 + SKILL_LEVEL,
        20 * LIGHTNING_MASTERY + 3 * CHAR_LEVEL / 2 + 2 * SKILL_LEVEL * CHAR_INT / 14 + 320),
    MIN(
        700 + SKILL_LEVEL * 200,
        20 * LIGHTNING_MASTERY + 3 * CHAR_LEVEL / 2 + 7 * SKILL_LEVEL * CHAR_INT / 8 + 320)
)
```

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 formula was:

<pre><code>MAGIC_ATTACK + BETWEEN(
    MIN(
        450 + SKILL_LEVEL,
        20 * LIGHTNING_MASTERY + 3 * CHAR_LEVEL / 2 + 2 * SKILL_LEVEL * CHAR_INT / 14 + 320),
    MIN(
        700 + SKILL_LEVEL * 200,
        20 * LIGHTNING_MASTERY + 3 * CHAR_LEVEL / 2 + <a data-footnote-ref href="#user-content-fn-1">10 </a>* SKILL_LEVEL * CHAR_INT / <a data-footnote-ref href="#user-content-fn-2">4 </a>+ 320)
)
</code></pre>

{% endhint %}

#### Cast time

0.8 seconds

#### Cooldown time

0.6 seconds

***

## Hail

<div align="left"><figure><img src="/files/aFTJL1cjVBMN1UbfdyuC" alt=""><figcaption></figcaption></figure></div>

#### Description

Drop pieces of sharp ice from the sky.

#### Level Limit

* G1 - 51 Lv.
* G2 - 58 Lv.
* G3 - 64 Lv.
* G4 - 67 Lv.

#### Required Condition

* has Ice Magic G20

#### Mana Consumption

```
12 + SKILL_LEVEL * 4
```

#### Range

210

#### Attack Points

```
MAGIC_ATTACK + MIN(
    400 + SKILL_LEVEL * 150,
    (3 * CHAR_LEVEL / 2 + 10 * SKILL_LEVEL * CHAR_INT / 4) / 2 + 240
)
```

{% hint style="info" %}
&#x20;2012 settings, not available on this server:

```
MAGIC_ATTACK + MIN(
    (400 + SKILL_LEVEL * 150) * 1.3,
    (3 * CHAR_LEVEL / 2 + 5 * SKILL_LEVEL * CHAR_INT / 12 + 240) * 1.3
)
```

{% endhint %}

#### Cast time

1 second

#### Cooldown time

0.6 seconds

***

## Flame Bomb

<div align="left"><figure><img src="/files/fmM4J8yJ90Tr9BK2ZRqy" alt=""><figcaption></figcaption></figure></div>

#### Description

Explode and fire up the selected target.

#### Level Limit

* G1 - 52 Lv.
* G2 - 59 Lv.

#### Required Condition

* has Fire Magic G20

#### Mana Consumption

```
16 + SKILL_LEVEL * 4
```

#### Range

180

#### Attack Points

```
MAGIC_ATTACK + MIN(
    500 + SKILL_LEVEL * 150,
    3 * CHAR_LEVEL / 2 + 6 * SKILL_LEVEL * CHAR_INT / 12 + 380
)
```

{% hint style="info" %}
Modified to trust 2012 clientside config, oldschool 2004 formula was:

```
MAGIC_ATTACK + MIN(
    500 + SKILL_LEVEL * 150,
    (3 * CHAR_LEVEL / 2 + 10 * SKILL_LEVEL * CHAR_INT / 3) / 2 + 380
)
```

{% endhint %}

#### Cast time

1.3 seconds

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 setting was 1.2 seconds.
{% endhint %}

#### Cooldown time

0.6 seconds

***

## Cold Binding

<div align="left"><figure><img src="/files/0CV33nG7ADt6XcctXdKV" alt=""><figcaption></figcaption></figure></div>

#### Description

Freeze up to 5 enemies in the effective area with cold frost.

#### Level Limit

* G1 - 54 Lv.
* G2 - 58 Lv.
* G3 - 63 Lv.
* G4 - 68 Lv.

#### Required Condition

* has Frost G1

#### Mana Consumption

```
60 + SKILL_LEVEL * 6
```

#### Range

210

#### Freeze Time (Seconds)

```
6 + SKILL_LEVEL * 2
```

#### Cast time

1.2 seconds

#### Cooldown time

0.8 seconds

***

## Refining Weapon

<div align="left"><figure><img src="/files/vz7dmm1tEnON64rkZ9R8" alt=""><figcaption></figcaption></figure></div>

#### Description

Give additional Attack Point & Magic Attack Point on the selected target and its party for a while.

{% hint style="info" %}
This skill is changed to match 2012 settings so that effect is applied to entire party of a target in range.

It also re-applies the buff (cancels previous Refining Weapon buff).
{% endhint %}

#### Level Limit

* G1 - 50 Lv.
* G2 - 57 Lv.
* G3 - 62 Lv.
* G4 - 66 Lv
* G5 - 69 Lv..

#### Required Condition

None

#### Add Attack/Magic Attack

```
16 + SKILL_LEVEL * 8
```

#### Mana Consumption

```
50 + SKILL_LEVEL * 12
```

#### Target Range

100 (from caster)

#### Party Effect Range

80 (from target)

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 setting was effective on single target only.
{% endhint %}

#### Cast time

1.5 seconds

#### Cooldown time

5 seconds

***

## Chain Lightning

<div align="left"><figure><img src="/files/DbGs9U09im7HF6I4AUkm" alt=""><figcaption></figcaption></figure></div>

#### Description

Deliver the lightning effect to the selected target and the near the target.

#### Level Limit

* G1 - 59 Lv.

#### Required Condition

* has Lightning Blow G10

#### Mana Consumption

174

#### Range

190

#### Attack Points

```
MAGIC_ATTACK + BETWEEN(
    MIN(
        700,
        20 * LIGHTNING_MASTERY + 3 * CHAR_LEVEL / 2 + 7 * SKILL_LEVEL * CHAR_INT / 6 + 360),
    MIN(
        1000,
        20 * LIGHTNING_MASTERY + 3 * CHAR_LEVEL / 2 + 10 * SKILL_LEVEL * CHAR_INT / 8 + 700)
)
```

{% hint style="info" %}
2012 formula, not available on this server:

```
MAGIC_ATTACK + BETWEEN(
    MIN(
        1050,
        (20 * LIGHTNING_MASTERY + 3 * CHAR_LEVEL / 2 + 7 * SKILL_LEVEL * CHAR_INT / 6 + 360)) * 1.5,
    MIN(
        1500,
        (20 * LIGHTNING_MASTERY + 3 * CHAR_LEVEL / 2 + 10 * SKILL_LEVEL * CHAR_INT / 8 + 700)) * 1.5
)
```

{% endhint %}

#### Cast time

2.2 seconds

#### Cooldown time

0.3 seconds

***

## Thunder

<div align="left"><figure><img src="/files/emKKVGyHxUcitdQzG8My" alt=""><figcaption></figcaption></figure></div>

#### Description

Drop thunderbolt to the selected target.

#### Level Limit

* G1 - 63 Lv.
* G2 - 66 Lv.

#### Required Condition

* has Lightning Summons G2

#### Mana Consumption

```
30 + SKILL_LEVEL * 8
```

#### Range

190

#### Attack Points

```
MAGIC_ATTACK + BETWEEN(
    MIN(
        (456 + SKILL_LEVEL * 154),
        (20 * LIGHTNING_MASTERY + 3 * CHAR_LEVEL / 2 + (5 * CHAR_LEVEL * (3 * CHAR_INT / 2) / 6) + 360)),
    MIN(
        (900 + SKILL_LEVEL * 300),
        (20 * LIGHTNING_MASTERY + 3 * CHAR_LEVEL / 2 + (10 * CHAR_LEVEL * (3 * CHAR_INT / 2) / 4) + 700))
)
```

#### Cast time

2 second

#### Cooldown time

0.6 seconds

***

## Ice Restriction

<div align="left"><figure><img src="/files/dUufQfEAVc1bRVDI0Q8g" alt=""><figcaption></figcaption></figure></div>

#### Description

Call the ice to the selected target, give the damage to the nearby targets and reduce its moving speed.

#### Level Limit

* G1 - 56 Lv.

#### Required Condition

* has Splashy Ice G2

#### Mana Consumption

126

#### Range

190

#### Attack Points

```
MAGIC_ATTACK + MIN(
    500,
    3 * CHAR_LEVEL / 2 + (2 * SKILL_LEVEL * CHAR_INT / 12) + 480
)
```

#### Cast time

0.8 seconds

#### Cooldown time

0.6 seconds

***

## Explosion

<div align="left"><figure><img src="/files/rY7kbUHYwcc7VlrEmOZD" alt=""><figcaption></figcaption></figure></div>

#### Description

The selected target gets hot wind and it's exploded and burned.

#### Level Limit

* G1 - 62 Lv.
* G2 - 68 Lv.

{% hint style="info" %}
This is modified, oldschool setting was G2 - 64 Lv.
{% endhint %}

#### Required Condition

* has Flame Bomb G2

#### Mana Consumption

```
32 + SKILL_LEVEL * 4
```

#### Range

180

#### Attack Points

```
MAGIC_ATTACK + MIN(
    600 + SKILL_LEVEL * 300,
    3 * CHAR_LEVEL / 2 + (14 * SKILL_LEVEL * CHAR_INT / 6) + 380
)
```

{% hint style="info" %}
This is modified to match 2012 setting, oldschool formula was:

```
MAGIC_ATTACK + MIN(
    600 + SKILL_LEVEL * 300,
    (3 * CHAR_LEVEL / 2 + (14 * SKILL_LEVEL * CHAR_INT / 3)) / 2 + 580
)
```

{% endhint %}

#### Cast time

1.4 seconds

#### Cooldown time

0.6 seconds

***

## Explosive Burst

<div align="left"><figure><img src="/files/HK7FfKLAq6lrfsyTpRmp" alt=""><figcaption></figcaption></figure></div>

#### Description

Big explosion is made on the selected area. All enemies nearby get damages.

#### Level Limit

* G1 - 64 Lv.

#### Required Condition

* has Fire Blow G5

#### Mana Consumption

142

#### Range

180

#### Attack Points

```
MAGIC_ATTACK + MIN(
    900,
    6 * CHAR_LEVEL / 2 + (4 * SKILL_LEVEL * CHAR_INT / 10) + 580
)
```

{% hint style="info" %}
This is modified to match 2012 setting, oldschool formula was:

```
MAGIC_ATTACK + MIN(
    900,
    (6 * CHAR_LEVEL / 2 + (4 * SKILL_LEVEL * CHAR_INT / 5)) / 2 + 580
)
```

{% endhint %}

#### Cast time

1.8 seconds

#### Cooldown time

2.2 seconds

***

## Thunder Storm

<div align="left"><figure><img src="/files/mNgSujtRwG74qOuMPT8Y" alt=""><figcaption></figcaption></figure></div>

#### Description

Thunderbolts are droping for certain amount of time on the selected area. Attack every target in the area every 2 seconds for 16 seconds.

#### Level Limit

* G1 - 65 Lv.

#### Required Condition

* has Chain Lightning G1

#### Mana Consumption

352

#### Range

190

#### Attack Points

```
BETWEEN(
    0.6 * (20 * LIGHTNING_MASTERY + 3 * CHAR_LEVEL / 2 + 15 * SKILL_LEVEL * CHAR_INT / 12 + 360),
    0.6 * (20 * LIGHTNING_MASTERY + 3 * CHAR_LEVEL / 2 + 30 * SKILL_LEVEL * CHAR_INT / 8 + 700)
)
```

#### Cast time

2 seconds

{% hint style="info" %}
This is adjusted to match 2012 setting, oldschool setting was 4 seconds.
{% endhint %}

#### Cooldown time

2 minutes

{% hint style="info" %}
This is adjusted to match 2012 setting, oldschool setting was 3 minutes.
{% endhint %}

***

## Ice Storm

<div align="left"><figure><img src="/files/KH6sIO4D3gMflAIE09JI" alt=""><figcaption></figcaption></figure></div>

#### Description

Ice and snow are droping for certain amount of time on the selected area. Attack every target in the area every 2 seconds for 16 seconds.

#### Level Limit

* G1 - 65 Lv.

#### Required Condition

* has Ice Restriction G1

#### Mana Consumption

396

#### Range

190

#### Attack Points

```
0.6 * (3 * CHAR_LEVEL / 2 + 10 * SKILL_LEVEL * CHAR_INT / 8 + 240)
```

#### Cast time

2 seconds

{% hint style="info" %}
This is adjusted to match 2012 setting, oldschool setting was 4 seconds.
{% endhint %}

#### Cooldown time

2 minutes

{% hint style="info" %}
This is adjusted to match 2012 setting, oldschool setting was 3 minutes.
{% endhint %}

***

## Fire Storm

<div align="left"><figure><img src="/files/YfAImbfxdxOldxwT7BVs" alt=""><figcaption></figcaption></figure></div>

#### Description

Fire is droping for certain amount of time on the selected area. Attack every target in the area every 2 seconds for 16 seconds.

#### Level Limit

* G1 - 65 Lv.

#### Required Condition

* has Explosive Burst G1

#### Mana Consumption

327

#### Range

180

#### Attack Points

```
0.6 * (3 * CHAR_LEVEL / 2 + 14 * SKILL_LEVEL * CHAR_INT / 6 + 380)
```

#### Cast time

2 seconds

{% hint style="info" %}
This is adjusted to match 2012 setting, oldschool setting was 4 seconds.
{% endhint %}

#### Cooldown time

2 minutes

{% hint style="info" %}
This is adjusted to match 2012 setting, oldschool setting was 3 minutes.
{% endhint %}

***

## Life Extension

<div align="left"><figure><img src="/files/JK2GnBsPzQjFBjSQr5ik" alt=""><figcaption></figcaption></figure></div>

#### Description

Add more Health Points to your original HP forever.

Passive, automatically obtained.

#### Level Limit

* G1 - 50 Lv.
* G2 - 55 Lv.
* G3 - 60 Lv.
* G4 - 65 Lv.
* G5 - 70 Lv.

#### Required Condition

None

#### Health Increase %

```
14 + SKILL_LEVEL * 10
```

***

## Mana Circulation

<div align="left"><figure><img src="/files/LOdzeKVv2ITFo4zsGgaW" alt=""><figcaption></figcaption></figure></div>

#### Description

To facilitate the flow of inside energy to help the recovery of Mana.

Passive, automatically obtained.

#### Level Limit

* G1 - 50 Lv.

#### Required Condition

None

#### Mana Regeneration Per Second

2

[^1]: 7

[^2]: 8

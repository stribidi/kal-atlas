> For the complete documentation index, see [llms.txt](https://bango-organization.gitbook.io/kalonline-2012-content/llms.txt). Markdown versions of documentation pages are available by appending `.md` to page URLs; this page is available as [Markdown](https://bango-organization.gitbook.io/kalonline-2012-content/player-skills/expert-archer-ea.md).

# Expert Archer (EA)

## Focus Shot

<div align="left"><figure><img src="/files/OGqm6VP0Cs3n77kP59ZQ" alt=""><figcaption></figcaption></figure></div>

#### Description

Focus the target slowly for more accurate and powerful attack.

Attack Power is depend on the time you focus.

#### Level Limit

* G1 - 50 Lv.
* G2 - 56 Lv.
* G3 - 60 Lv.
* G4 - 66 Lv.
* G5 - 69 Lv.

#### Required Condition

None

#### Mana Consumption

```
25 + SKILL_LEVEL * 5
```

#### Range

```
WEAPON_RANGE + 60
```

Affected by Range Extension passive skill.

#### Attack Points

```
MIN(2000,
    IF(CHARGE_LEVEL, 1, PHYSICAL_ATTACK * (50  + 25 * SKILL_LEVEL + 50) / 90),
    IF(CHARGE_LEVEL, 2, PHYSICAL_ATTACK * (100 + 32 * SKILL_LEVEL + 50) / 90),
    IF(CHARGE_LEVEL, 3, PHYSICAL_ATTACK * (150 + 40 * SKILL_LEVEL + 50) / 90),
    IF(CHARGE_LEVEL, 4, PHYSICAL_ATTACK * (200 + 47 * SKILL_LEVEL + 50) / 90),
    IF(CHARGE_LEVEL, 5, PHYSICAL_ATTACK * (250 + 55 * SKILL_LEVEL + 50) / 90))
```

#### Additional Fatality Rate

```
SKILL_LEVEL + 5
```

#### On-Target Points

```
(SKILL_LEVEL + 1) / 2 + 2 * CHARGE_LEVEL - 1
```

#### Cast time

* 1 Lv. charge - 1 second
* 2 Lv. charge - 1.7 seconds
* 3 Lv. charge - 2.3 seconds
* 4 Lv. charge - 2.6 seconds
* 5 Lv. charge - 2.9 seconds

#### Cooldown time

None\ <br>

***

## Mysterious Arrow

<div align="left"><figure><img src="/files/bizJpkzUaodNua71xIAL" alt=""><figcaption></figcaption></figure></div>

#### Description

Shoot several arrows to the target.

When it hit the target, it explodes and the target gets continuous damage for 5 seconds.

#### Level Limit

* G1 - 57 Lv.
* G2 - 67 Lv.
* G3 - 70 Lv.

#### Required Condition

None

#### Mana Consumption

<pre><code><a data-footnote-ref href="#user-content-fn-1">31 </a>+ SKILL_LEVEL * 5
</code></pre>

{% hint style="info" %}
Modified to match 2012 setting, previously (in 2004) it was:

```
9 + SKILL_LEVEL * 5
```

{% endhint %}

#### Range

```
WEAPON_RANGE
```

Affected by Range Extension passive skill.

#### Attack Points

```
(SKILL_LEVEL + 2) * (PHYSICAL_ATTACK / 2)
```

#### Damage Over Time (5 waves)

```
PHYSICAL_ATTACK / 10
```

#### Debuff Time

5 seconds

#### Cast time

Instant

#### Cooldown time

5 seconds

***

## Lightning Resistance

<div align="left"><figure><img src="/files/1Coy1iaI01KADolRkSqn" alt=""><figcaption></figcaption></figure></div>

#### Description

Increase the resistance on Lightning.

#### Level Limit

* G1 - 52 Lv.
* G2 - 64 Lv.

#### Required Condition

None

#### Mana Consumption

```
42 + SKILL_LEVEL * 11
```

#### Lightning Resistance

```
10 + SKILL_LEVEL * 5
```

#### Buff Time

15 minutes

#### Cast time

Instant

#### Cooldown time

1 minute

***

## Ice Resistance

<div align="left"><figure><img src="/files/L2jyWh2nfxfLWAQyh6Cw" alt=""><figcaption></figcaption></figure></div>

#### Description

Increase the resistance on Ice.

#### Level Limit

* G1 - 52 Lv.
* G2 - 64 Lv.

#### Required Condition

None

#### Mana Consumption

```
42 + SKILL_LEVEL * 11
```

#### Ice Resistance

```
10 + SKILL_LEVEL * 5
```

#### Buff Time

15 minutes

#### Cast time

Instant

#### Cooldown time

1 minute

***

## Fire Resistance

<div align="left"><figure><img src="/files/iXL3L08VsnPXWeHKqFTt" alt=""><figcaption></figcaption></figure></div>

#### Description

Increase the resistance on Fire.

#### Level Limit

* G1 - 52 Lv.
* G2 - 64 Lv.

#### Required Condition

None

#### Mana Consumption

```
42 + SKILL_LEVEL * 11
```

#### Fire Resistance

```
10 + SKILL_LEVEL * 5
```

#### Buff Time

15 minutes

#### Cast time

Instant

#### Cooldown time

1 minute

***

## Curse Resistance

<div align="left"><figure><img src="/files/AUUPFBS0R6qGW6lata8K" alt=""><figcaption></figcaption></figure></div>

#### Description

Increase the resistance on Curse.

#### Level Limit

* G1 - 55 Lv.
* G2 - 65 Lv.

#### Required Condition

None

#### Mana Consumption

```
22 + SKILL_LEVEL * 14
```

#### Fire Resistance

```
10 + SKILL_LEVEL * 5
```

#### Buff Time

15 minutes

#### Cast time

Instant

#### Cooldown time

1 minute

***

## Non-Attribution Resistance

<div align="left"><figure><img src="/files/7wk9vyxK5r3fOYVMShhW" alt=""><figcaption></figcaption></figure></div>

#### Description

Increase the resistance on Non-Attribution.

#### Level Limit

* G1 - 56 Lv.
* G2 - 65 Lv.

#### Required Condition

None

#### Mana Consumption

```
22 + SKILL_LEVEL * 14
```

#### Fire Resistance

```
10 + SKILL_LEVEL * 5
```

#### Buff Time

15 minutes

#### Cast time

Instant

#### Cooldown time

1 minute

***

## Powerful Arrow of Silence

<div align="left"><figure><img src="/files/sKUM7BEKiYEKFUFMz4NC" alt=""><figcaption></figcaption></figure></div>

#### Description

Block the opponent's magic, and consume the target's MP for 10 seconds.

#### Level Limit

* G1 - 53 Lv.
* G2 - 63 Lv.

#### Required Condition

None

#### Mana Consumption

```
80 + SKILL_LEVEL * 20
```

#### Range

```
WEAPON_RANGE
```

Affected by Range Extension passive skill.

#### Target MP Decrease Over Time (10 waves)

```
70 * SKILL_LEVEL - 20
```

#### Debuff Time

10 seconds

#### Cast time

2 seconds

#### Cooldown time

40 seconds

***

## Emergency Escape

<div align="left"><figure><img src="/files/688aPEZEjClYt698IIv9" alt=""><figcaption></figcaption></figure></div>

#### Description

Run fastly to escape from the danger temporally. It effects on all your group members#nwho are near you.

#### Level Limit

* G1 - 59 Lv.

#### Required Condition

None

#### Mana Consumption

70

#### Range

64

#### Speed Increase

200

#### Debuff Time

10 seconds

#### Cast time

Instant

#### Cooldown time

15[^2] minutes

{% hint style="info" %}
Modified to match 2012 setting, previously (in 2004) it was:

```
30 minutes
```

{% endhint %}

***

## Range Extension

<div align="left"><figure><img src="/files/OSZ1QRdz0KunES9hw6KW" alt=""><figcaption></figcaption></figure></div>

#### Description

Attack longer distance than the weapon's effective distance.

#### Level Limit

* G1 - 51 Lv.
* G2 - 58 Lv.
* G3 - 67 Lv.

#### Required Condition

None

#### Add Range

```
SKILL_LEVEL * 20
```

***

## Perfect Evasion 2

<div align="left"><figure><img src="/files/nkesDkW5pfNu3HVqslev" alt=""><figcaption></figcaption></figure></div>

#### Description

Evade opponent's physical attack perfectly.

#### Level Limit

* G1 - 54 Lv.
* G2 - 62 Lv.
* G3 - 68 Lv.

#### Required Condition

Perfect Evasion G10

#### Add Evade Chance %

```
SKILL_LEVEL * 1
```

***

## Critical Hit

<div align="left"><figure><img src="/files/e03bqvjtJk165CXwYl3n" alt=""><figcaption></figcaption></figure></div>

#### Description

The power of attack is increased, and the percentage of activation remains same as 15%

#### Level Limit

* G1 - 61 Lv.

#### Add Fatal Damage %

+80%

#### Other

Fixed the bug that the effect stacked when repeadetely used Stone of Chance.

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

[^1]: 9

[^2]: 30

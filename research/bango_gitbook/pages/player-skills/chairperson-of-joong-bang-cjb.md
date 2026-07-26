> For the complete documentation index, see [llms.txt](https://bango-organization.gitbook.io/kalonline-2012-content/llms.txt). Markdown versions of documentation pages are available by appending `.md` to page URLs; this page is available as [Markdown](https://bango-organization.gitbook.io/kalonline-2012-content/player-skills/chairperson-of-joong-bang-cjb.md).

# Chairperson of Joong-Bang (CJB)

## Summons

<div align="left"><figure><img src="/files/saudJVzzDcBkhKZyD9yw" alt=""><figcaption></figcaption></figure></div>

#### Description

Revive one player who's not able to fight. Revived character will get only 50% of EXP loss. Revived character will be brought up to you. It can't be used on monsters & Hell.

#### Level Limit

* G1 - 50 Lv.
* G2 - 61 Lv.
* G3 - 68 Lv.

#### Required Condition

* has Revival G1

#### Mana Consumption

```
230 + 30 * SKILL_LEVEL
```

#### Range

```
128 + SKILL_LEVEL * 16
```

#### Cast time

```
3s - SKILL_LEVEL * 0.4s
```

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 setting was 1.8 seconds.
{% endhint %}

#### Cooldown time

5 seconds

***

## Hypnotism

<div align="left"><figure><img src="/files/hZFTJVCHuC3P5XnrG6Qo" alt=""><figcaption></figcaption></figure></div>

#### Description

Make the enemies who are in the effective area to fall in a sleep. Target can't do anything while it's under hypnosis but when it get attacked, the effectiveness of magic will be gone away.

#### Level Limit

* G1 - 51 Lv.
* G2 - 56 Lv.
* G3 - 61 Lv.
* G4 - 67 Lv.
* G5 - 70 Lv.

#### Required Condition

None

#### Mana Consumption

```
98 + SKILL_LEVEL * 4
```

#### Range

```
190 + SKILL_LEVEL * 10
```

#### Hypno Effect Time

```
4 + SKILL_LEVEL * 5
```

#### Cast time

```
2.5s - SKILL_LEVEL * 0.1s
```

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 setting was 2.4 seconds.
{% endhint %}

#### Cooldown time

0.6 seconds

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 setting was 6 seconds
{% endhint %}

***

## Purification

<div align="left"><figure><img src="/files/cgXng2gIGVY95pjd9aq3" alt=""><figcaption></figcaption></figure></div>

#### Description

Disable all debuffs of the selected target. Except the Revival Sequela. It can't be used on monsters.

#### Level Limit

* G1 - 50 Lv.

#### Required Condition

None

#### Mana Consumption

74

#### Range

170

#### Cast time

2 seconds

#### Cooldown time

5 seconds

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 setting was 15 seconds
{% endhint %}

***

## Cure 3

<div align="left"><figure><img src="/files/mNV6XQnEWzFlgb1gfo5Y" alt=""><figcaption></figcaption></figure></div>

#### Description

Recover the selected target's HP. The amount of HP recovery cannot exceed 1600. It can't be used on monsters.

#### Level Limit

* G1 - 51 Lv.
* G2 - 60 Lv.
* G3 - 66 Lv.

#### Required Condition

None

#### Mana Consumption

```
39 + 4 * SKILL_LEVEL
```

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 formula: `39 +` [`2` ](#user-content-fn-1)[^1]`* SKILL_LEVEL`
{% endhint %}

#### Range

190 (+40 if has Increase of Target Range skill)

#### Heal Amount

```
MIN(1600, 100 * SKILL_LEVEL + 11 * CHAR_WIS / 3 + 750 + RANDOM(0, 100))
```

{% hint style="info" %}
2012 settings, not used on this server:

```
MIN(3500, 100 * SKILL_LEVEL + 11 * CHAR_WIS / 3 + 750 + RANDOM(0, 100))
```

{% endhint %}

#### Cast time

1.5 seconds

#### Cooldown time

0.6 seconds

***

## Defense Improvement

<div align="left"><figure><img src="/files/cxHUVxkHdPmzwV1X6Fij" alt=""><figcaption></figcaption></figure></div>

#### Description

Increase the defense of selected target and its party members in range. It can't be used on monsters.

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 setting was effective on single target only.

It also re-applies the buff (cancels previous Refining Weapon buff).
{% endhint %}

#### Level Limit

* G1 - 53 Lv.
* G2 - 62 Lv.

#### Required Condition

None

#### Mana Consumption

```
64 + 31 * SKILL_LEVEL
```

#### Target Range

128 (from caster)

#### Party Effect Range

80 (from target)

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 setting was effective on single target only.
{% endhint %}

#### Add Defense

```
CLOSE RANGE: 5 + SKILL_LEVEL * 30
LONG RANGE: 5 + SKILL_LEVEL * 20
```

#### Cast time

2 seconds

#### Cooldown time

5 seconds

#### Lasting Time

30 minutes

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 setting was 10 minutes.
{% endhint %}

***

## Blessing of Strength

<div align="left"><figure><img src="/files/YlkdL7495GVt46Dmumhc" alt=""><figcaption></figcaption></figure></div>

#### Description

Increase the strength of selected target and its party members in range. It can't be used on monsters.

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 setting was effective on single target only.

It also re-applies the buff (cancels previous Refining Weapon buff).
{% endhint %}

#### Level Limit

* G1 - 54 Lv.
* G2 - 63 Lv.

#### Required Condition

None

#### Mana Consumption

```
41 + 32 * SKILL_LEVEL
```

#### Target Range

94 (from caster)

#### Party Effect Range

80 (from target)

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 setting was effective on single target only.
{% endhint %}

#### Add Strength

```
2 + SKILL_LEVEL * 6
```

#### Cast time

2 seconds

#### Cooldown time

5 seconds

#### Lasting Time

30 minutes

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 setting was 15 minutes.
{% endhint %}

***

## Blessing of Health

<div align="left"><figure><img src="/files/0mIqKER8zeyZVUqtwxM3" alt=""><figcaption></figcaption></figure></div>

#### Description

Increase the health of selected target and its party members in range. It can't be used on monsters.

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 setting was effective on single target only.

It also re-applies the buff (cancels previous Refining Weapon buff).
{% endhint %}

#### Level Limit

* G1 - 54 Lv.
* G2 - 64 Lv.

#### Required Condition

None

#### Mana Consumption

```
60 + 27 * SKILL_LEVEL
```

#### Target Range

94 (from caster)

#### Party Effect Range

80 (from target)

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 setting was effective on single target only.
{% endhint %}

#### Add Health

```
3 + SKILL_LEVEL * 8
```

#### Cast time

2 seconds

#### Cooldown time

5 seconds

#### Lasting Time

30 minutes

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 setting was 15 minutes.
{% endhint %}

***

## Blessing of Agility

<div align="left"><figure><img src="/files/1PcYzD9i1fBxAXKlXO9Y" alt=""><figcaption></figcaption></figure></div>

#### Description

Increase the agility of selected target and its party members in range. It can't be used on monsters.

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 setting was effective on single target only.

It also re-applies the buff (cancels previous Refining Weapon buff).
{% endhint %}

#### Level Limit

* G1 - 55 Lv.
* G2 - 64 Lv.

#### Required Condition

None

#### Mana Consumption

```
67 + 26 * SKILL_LEVEL
```

#### Target Range

94 (from caster)

#### Party Effect Range

80 (from target)

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 setting was effective on single target only.
{% endhint %}

#### Add Agility

```
3 + SKILL_LEVEL * 8
```

#### Cast time

2 seconds

#### Cooldown time

5 seconds

#### Lasting Time

30 minutes

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 setting was 15 minutes.
{% endhint %}

***

## Blessing of Intelligence

<div align="left"><figure><img src="/files/sbgiYcsCkA1BeXphR53s" alt=""><figcaption></figcaption></figure></div>

#### Description

Increase the intelligence of selected target and its party members in range. It can't be used on monsters.

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 setting was effective on single target only.

It also re-applies the buff (cancels previous Refining Weapon buff).
{% endhint %}

#### Level Limit

* G1 - 56 Lv.
* G2 - 65 Lv.

#### Required Condition

None

#### Mana Consumption

```
64 + 36 * SKILL_LEVEL
```

#### Target Range

94 (from caster)

#### Party Effect Range

80 (from target)

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 setting was effective on single target only.
{% endhint %}

#### Add Intelligence

```
2 + SKILL_LEVEL * 6
```

#### Cast time

2 seconds

#### Cooldown time

5 seconds

#### Lasting Time

30 minutes

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 setting was 15 minutes.
{% endhint %}

***

## Increase of Critical Hit

<div align="left"><figure><img src="/files/ALFfwq3yTOiKe32THAbD" alt=""><figcaption></figcaption></figure></div>

#### Description

Increase the appearance of Critical Hit of selected target and its party members in range. It can't be used on monsters.

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 setting was effective on single target only.

It also re-applies the buff (cancels previous Refining Weapon buff).
{% endhint %}

#### Level Limit

* G1 - 57 Lv.
* G2 - 66 Lv.

#### Required Condition

None

#### Mana Consumption

```
72 + 38 * SKILL_LEVEL
```

#### Target Range

94 (from caster)

#### Party Effect Range

80 (from target)

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 setting was effective on single target only.
{% endhint %}

#### Add Critical Chance %

```
2 + SKILL_LEVEL * 3
```

#### Cast time

2 seconds

#### Cooldown time

5 seconds

#### Lasting Time

30 minutes

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 setting was 15 minutes.
{% endhint %}

***

## Soul Destruction

<div align="left"><figure><img src="/files/hgtYdJaVMe2NrRRuVKXQ" alt=""><figcaption></figcaption></figure></div>

#### Description

Throw luminary to the selected target.

Single target attack skill.

#### Level Limit

* G1 - 52 Lv.
* G2 - 57 Lv.
* G3 - 62 Lv.
* G4 - 67 Lv.
* G5 - 72 Lv.

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 setting max G2 (52 Lv. / 63 Lv.)
{% endhint %}

#### Required Condition

None

#### Mana Consumption

```
18 + 22 * SKILL_LEVEL
```

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 formula was [`29`](#user-content-fn-2)[^2]`+ SKILL_LEVEL *`[`8`](#user-content-fn-3)[^3]
{% endhint %}

#### Range

150 (+50 if has Distance Control skill)

#### Attack Points

In both PVP and PVE:

```
MAGIC_ATTACK + ((CHAR_LEVEL * 9 / 2) + (CHAR_WIS / 2 * SKILL_LEVEL * 5)) * 0.5
```

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 formula was (for both PVP and PVE):

`MAGIC_ATTACK + MIN(200 * SKILL_LEVEL + 600, ((9 * CHAR_LEVEL / 2) + (5 * SKILL_LEVEL * CHAR_INT)) / 2)`
{% endhint %}

#### Cast time

0.7 seconds

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 setting was 1.2 seconds.
{% endhint %}

#### Cooldown time

0.6 seconds

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 setting was 6 seconds.
{% endhint %}

***

## Group Cure 2

<div align="left"><figure><img src="/files/7S0NRag0ujU8VcpDN27P" alt="group cure 2"><figcaption></figcaption></figure></div>

#### Description

Recover the health point of all the group members.

#### Level Limit

* G1 - 58 Lv.
* G2 - 67 Lv.

#### Required Condition

* has Group Cure G3

#### Mana Consumption

```
72 + 15 * SKILL_LEVEL
```

#### Range

128

#### Heal Amount

```
550 + RANDOM(0, 100)
```

#### Cast time

1.3 seconds

#### Cooldown time

0.6 seconds

***

## Perfect Cure

<div align="left"><figure><img src="/files/gA1I4DVXezWW4MLmBSiH" alt=""><figcaption></figcaption></figure></div>

#### Description

Recover the health of the selected targe instantly. It can't be used on monsters.

#### Level Limit

* G1 - 52 Lv.
* G2 - 62 Lv.
* G3 - 69 Lv.

#### Required Condition

* has Restore G1

#### Mana Consumption

```
190 + SKILL_LEVEL * 30
```

#### Recover % of Target Max Health

```
15 + SKILL_LEVEL * 20
```

#### Range

180

#### Cast time

0 seconds

#### Cooldown time

90 seconds

***

## Perfect Group Cure 2

<div align="left"><figure><img src="/files/ujJCq9dcDVwvMlxJkGpz" alt=""><figcaption></figcaption></figure></div>

#### Description

Recover the Health of your group memebers in the effective area. Recover 100% of Max HP of all group members instantly.

#### Level Limit

* G1 - 59 Lv.
* G2 - 69 Lv.

#### Required Condition

* has Group Cure 2 G1

#### Mana Consumption

```
400 + SKILL_LEVEL * 40
```

#### Range

128

#### Cast time

0 seconds

#### Cooldown time

15 minutes

***

## Perfect Healing

<div align="left"><figure><img src="/files/gA1I4DVXezWW4MLmBSiH" alt=""><figcaption></figcaption></figure></div>

#### Description

Recover 100% of HP of selected target. But, it takes a long tme to reactivate. It can't be used on monsters.

{% hint style="info" %}
The skill is completely glitched in leaked publicly available 2004 files, healing max 5-10% HP due to overflow. This server has it fixed.
{% endhint %}

#### Level Limit

* G1 - 68 Lv.

#### Required Condition

None

#### Mana Consumption

596

#### Range

210

#### Cast time

0 seconds

#### Cooldown time

10 minutes

{% hint style="info" %}
Modified to match 2012 settings, oldschool 2004 setting was 30 minutes.
{% endhint %}

***

## Amnesia

<div align="left"><figure><img src="/files/UDgxAQVmWUXRvTbvRaKK" alt=""><figcaption></figcaption></figure></div>

#### Description

Make the anger point of selected target to zero.

#### Level Limit

* G1 - 59 Lv.

#### Required Condition

None

#### Mana Consumption

50

#### Range

190

#### Cast time

1.5 seconds

#### Cooldown time

5 seconds

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

## Increase of Target Range

<div align="left"><figure><img src="/files/dAiIyF7StG2qDPxdwhEa" alt=""><figcaption></figcaption></figure></div>

#### Description

Increase the range of all kinds of single target cure skills (+40).

Works with Cure, Cure 2, Cure 3 and Restore skills.

Passive, manually obtained.

#### Level Limit

* G1 - 53 Lv.

#### Required Condition

None

***

## Distance Control

<div align="left"><figure><img src="/files/Ox2xK1wpRhuKRLO8zJgu" alt=""><figcaption></figcaption></figure></div>

#### Description

Increase the range of Soul Destruction (+50).

Passive, manually obtained.

#### Level Limit

* G1 - 58 Lv.

#### Required Condition

None

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

[^1]: 4

[^2]: 18

[^3]: 22

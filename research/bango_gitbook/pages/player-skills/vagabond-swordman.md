> For the complete documentation index, see [llms.txt](https://bango-organization.gitbook.io/kalonline-2012-content/llms.txt). Markdown versions of documentation pages are available by appending `.md` to page URLs; this page is available as [Markdown](https://bango-organization.gitbook.io/kalonline-2012-content/player-skills/vagabond-swordman.md).

# Vagabond Swordman

## Powerful Upward Slash

<div align="left"><figure><img src="/files/Itd3L9khrxZNRb4ZDDJO" alt=""><figcaption></figcaption></figure></div>

#### Description

After stabbing the weapon deeply in to the body, lifting up strongly. When making a hit, you get 1 Death Blow Point.

#### Level Limit

* G1 - 50 Lv.
* G2 - 57 Lv.
* G3 - 63 Lv.
* G4 - 68 Lv.

#### Required Condition

None

#### Mana Consumption

```
24 + SKILL_LEVEL * 2
```

#### Range

Inherited from weapon

#### Attack Points

```
PHYSICAL_ATTACK + PHYSICAL_ATTACK * (10 * SKILL_LEVEL + 100) / 80
```

{% hint style="info" %}
Effectively it means that base physical attack is increased by:

* G1 +37%
* G2 +50%
* G3 +62%
* G4 +75%
  {% endhint %}

#### On-Target Points

+10

#### Cast time

Instant

#### Cooldown time

4.6 seconds

***

## Brutal Attack

<div align="left"><figure><img src="/files/XFcvMp9KDO4RqZYvX6NV" alt=""><figcaption></figcaption></figure></div>

#### Description

By using the Death Blow Points, making a Brutal Attack to the enemy. Death Blow Point is needed. Damage increases depending on the Death Blow Points.

#### Level Limit

* G1 - 53 Lv.
* G2 - 56 Lv.
* G3 - 63 Lv.
* G4 - 67 Lv.
* G5 - 70 Lv.

#### Required Condition

None

#### Mana Consumption

```
12 + SKILL_LEVEL * 3
```

#### Range

Inherited from weapon

#### Attack Points

```
PHYSICAL_ATTACK + 
    45 +
    PHYSICAL_ATTACK * (20 * DEATH_BLOW + 2 * SKILL_LEVEL + 8) / 50 +
    5 * DEATH_BLOW +
    SKILL_LEVEL * (5 * DEATH_BLOW + 25)
```

{% hint style="info" %}
Effectively it means that base physical attack is increased by:

* **G1**: +120 points and also +220% base attack when fully charged, +80 points and also +60% with low charge
* **G2**: +170 points and also +225% base attack when fully charged, +110 points and also +64% with low charge
* **G3**: +220 points and also +228% base attack when fully charged, +140 points and also +68% with low charge
* **G4**: +270 points and also +232% base attack when fully charged, +170 points and also +72% with low charge
* **G5**: +320 points and also +236% base attack when fully charged, +200 points and also +76% with low charge
  {% endhint %}

{% hint style="info" %}
2012 setting, not used on this server:

```
    2 * (45 +
          PHYSICAL_ATTACK * (20 * DEATH_BLOW + 2 * SKILL_LEVEL + 8) / 50 +
          5 * DEATH_BLOW +
          SKILL_LEVEL * (5 * DEATH_BLOW + 25))
```

{% endhint %}

#### On-Target Points

+10

#### Cast time

Instant

#### Cooldown time

0.7 seconds

***

## Half Swing

<div align="left"><figure><img src="/files/4M9twct4bAPS8uIl6NbF" alt=""><figcaption></figcaption></figure></div>

#### Description

Swing a weapon and attack the front of 180 degree enemies. You must equip two handed sword. You get a Death Blow Point if you hit any enemy.

#### Level Limit

* G1 - 54 Lv.
* G2 - 58 Lv.
* G3 - 62 Lv.
* G4 - 66 Lv.
* G5 - 69 Lv.

#### Required Condition

None

#### Mana Consumption

```
49 + SKILL_LEVEL * 9
```

#### Range

Inherited from weapon

#### Attack Points

```
PHYSICAL_ATTACK + PHYSICAL_ATTACK * 10 * SKILL_LEVEL / 100
```

{% hint style="info" %}
Effectively it means that base physical attack is increased by:

* **G1**: +10%
* **G2:** +20%
* **G3:** +30%
* **G4:** +40%
* **G5:** +50%

2012 setting, not available on this server:

<pre><code>PHYSICAL_ATTACK + PHYSICAL_ATTACK * 2<a data-footnote-ref href="#user-content-fn-1">0 </a>* SKILL_LEVEL / 100
</code></pre>

{% endhint %}

#### On-Target Points

Not based on OTP, never misses

#### Cast time

Instant

#### Cooldown time

5 seconds

{% hint style="info" %}
Modified to match 2012 formula, oldschool setting was 10 seconds.
{% endhint %}

***

## Berserk

<div align="left"><figure><img src="/files/VUuSHiqsqZIiVIbpEVZT" alt=""><figcaption></figcaption></figure></div>

#### Description

Offensive power increases but Defensive power decreases.

#### Level Limit

* G1 - 53 Lv.
* G2 - 56 Lv.
* G3 - 59 Lv.
* G4 - 62 Lv.
* G5 - 65 Lv.
* G6 - 70 Lv.

#### Required Condition

None

#### Mana Consumption

```
200 + SKILL_LEVEL * 15
```

#### Attack Points

```
5 + SKILL_LEVEL * 10
```

{% hint style="info" %}
Effectively it means that base physical attack is increased by:

* **G1**: +15%
* **G2:** +25%
* **G3:** +35%
* **G4:** +45%
* **G5:** +55%
* **G6:** +65%

Modified to match 2012 setting, previous 2004 formula was:

```
5 + SKILL_LEVEL * 6
```

{% endhint %}

#### Defense Points

```
-(6 + SKILL_LEVEL * 2)
```

{% hint style="info" %}
Effectively it means that caster defense is decreased by:

* **G1**: -8%
* **G2:** -10%
* **G3:** -12%
* **G4:** -14%
* **G5:** -16%
* **G6:** -18%

Modified to match 2012 setting, previous 2004 formula was:

```
-(3 + SKILL_LEVEL * 2)
```

{% endhint %}

#### Buff Time

1 minute

#### Cast time

Instant

#### Cooldown time

3 minutes

{% hint style="info" %}
Modified to match 2012 formula, oldschool setting was 10 minutes.
{% endhint %}

***

## Rush

<div align="left"><figure><img src="/files/GdZTUVSQvdEGyjOtpYNW" alt=""><figcaption></figcaption></figure></div>

#### Description

Rushing to the enemy and enemy gets stiff instantly. But distance must be more than 60.

#### Level Limit

* G1 - 52 Lv.
* G2 - 62 Lv.

#### Required Condition

None

#### Mana Consumption

```
46 + SKILL_LEVEL * 4
```

#### Range

```
60 + SKILL_LEVEL * 20
```

#### Stun Time

```
1 + SKILL_LEVEL
```

{% hint style="info" %}
Effectively it means that base physical attack is increased by:

* **G1**: 2 seconds
* **G2:** 3 seconds
  {% endhint %}

#### Cooldown time

```
14s - SKILL_LEVEL * 2
```

{% hint style="info" %}
Effectively it means that cooldown is:

* **G1**: 12 seconds
* **G2:** 10 seconds
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

## Parry

<div align="left"><figure><img src="/files/97xvCyCf9Io9EqURdEtX" alt=""><figcaption></figcaption></figure></div>

#### Description

By using your weapon, you can block the enemy's attack. However, it is harder to block than by using shield. Two Hand Sword must be equipped.

Passive, manually obtained.

{% hint style="info" %}
Modified an effect in game to indicate when parry is applied - "Blocking" indicator.
{% endhint %}

#### Level Limit

* G1 - 50 Lv.

#### Required Condition

None

***

## Increase of Critical Hit

<div align="left"><figure><img src="/files/e03bqvjtJk165CXwYl3n" alt=""><figcaption></figcaption></figure></div>

#### Description

Increase the damage of Critical Hit.

Passive, manually obtained.

#### Level Limit

* G1 - 61 Lv.

#### Required Condition

* has Critical Hit G15

#### Add Fatal Damage %

+20%

#### Other

Fixed the bug that the effect stacked when repeadetely used Stone of Chance.

[^1]: 10

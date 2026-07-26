> For the complete documentation index, see [llms.txt](https://bango-organization.gitbook.io/kalonline-2012-content/llms.txt). Markdown versions of documentation pages are available by appending `.md` to page URLs; this page is available as [Markdown](https://bango-organization.gitbook.io/kalonline-2012-content/player-skills/imperial-commander-ic.md).

# Imperial Commander (IC)

## Life Absorption

<div align="left"><figure><img src="/files/To020x50SLcT1rY4XyPO" alt=""><figcaption></figcaption></figure></div>

#### Description

Reduce the target's HP and absorb some part of the HP.

Leaves 1 HP to the target.

Critical hit and explosive blow not applicable.

Ignores target defence.

#### Level Limit

* G1 - 50 Lv.
* G2 - 57 Lv.
* G3 - 66 Lv.

#### Required Condition

None

#### Mana Consumption

```
20 + SKILL_LEVEL * 6
```

#### Range

160

#### Attack Points (PVE)

<pre><code>PHYSICAL_ATTACK * (<a data-footnote-ref href="#user-content-fn-1">60 </a>* SKILL_LEVEL + <a data-footnote-ref href="#user-content-fn-2">60</a>) / 50
</code></pre>

{% hint style="info" %}
Modified to match 2012 setting, previously it was:

```
PHYSICAL_ATTACK * (40 * SKILL_LEVEL + 50) / 50
```

{% endhint %}

#### Attack Points (PVP)

```
PHYSICAL_ATTACK * (40 * SKILL_LEVEL + 50) / 50
```

#### Health Point Regeneration

```
FINAL_DAMAGE * (10 * SKILL_LEVEL + 20) / 50
```

{% hint style="info" %}
Effectively it means that heal depends on final damage and heals % of it:

* G1 60%
* G2 80%
* G3 100%
  {% endhint %}

#### On-Target Points

+5

#### Cast time

Instant

#### Cooldown time

6 seconds

***

## Pain

<div align="left"><figure><img src="/files/AyXMxgDM9Tgj6yI2tGlj" alt=""><figcaption></figcaption></figure></div>

#### Description

Give mental pain to the selected target continuously.

Deals 30 waves of damage overtime (every second)

#### Level Limit

* G1 - 51 Lv.
* G2 - 56 Lv.
* G3 - 62 Lv.
* G4 - 68 Lv.

#### Required Condition

None

#### Mana Consumption

```
40 + SKILL_LEVEL * 8
```

#### Range

180

#### Single Wave Damage

```
MIN(
  PHYSICAL_ATTACK * (150 * SKILL_LEVEL + 100) / 600,
  150)
```

{% hint style="info" %}
Non elemental resistance decreases this value.
{% endhint %}

#### Cast time

1.5s

#### Cooldown time

30 seconds

***

## Speed of Attack Reducer

<div align="left"><figure><img src="/files/q1ZWnpX3nS39bxU1mEs2" alt=""><figcaption></figcaption></figure></div>

#### Description

Reduce the target's speed of physical attack for a while.

#### Level Limit

* G1 - 52 Lv.
* G2 - 61 Lv.

#### Required Condition

None

#### Mana Consumption

20

#### Range

180

#### Lasting time

15 seconds

#### Attack speed decrease

```
SKILL_LEVEL * 30
```

#### Cast time

Instant

#### Cooldown time

30 seconds

***

## Sight Interruption

<div align="left"><figure><img src="/files/EIJGNjImMArQjhtcLcJA" alt=""><figcaption></figcaption></figure></div>

#### Description

Reduce the opponent's movement instantly by 50%.

#### Level Limit

* G1 - 53 Lv.
* G2 - 58 Lv.
* G3 - 69 Lv.

#### Required Condition

None

#### Mana Consumption

<pre><code><strong>57 + SKILL_LEVEL * 11
</strong></code></pre>

#### Range

Inherited from weapon

#### Lasting time

<pre><code><strong>SKILL_LEVEL * 8
</strong></code></pre>

#### Cast time

1 second

#### Cooldown time

5 seconds

***

## Decrease of Target Range

<div align="left"><figure><img src="/files/JBVURlkkCFgV5F0l1Di5" alt=""><figcaption></figcaption></figure></div>

#### Description

Decrease 50% of the range of selected target.

Applicable only to archers.

#### Level Limit

* G1 - 52 Lv.

#### Required Condition

None

#### Mana Consumption

50

#### Range

200

#### Lasting time

15 seconds

#### Cast time

Instant

#### Cooldown time

30 seconds

***

## MP Vaporization

<div align="left"><figure><img src="/files/UeimNRggcZRY44ZTF9qk" alt=""><figcaption></figcaption></figure></div>

#### Description

Vaporize the target's MP for certain amount of time.

#### Level Limit

* G1 - 53 Lv.
* G2 - 65 Lv.

#### Required Condition

None

#### Mana Consumption

<pre><code><strong>40 + SKILL_LEVEL * 16
</strong></code></pre>

#### Total enemy mana decrease over time

<pre><code><strong>100 + SKILL_LEVEL * 250
</strong></code></pre>

#### Range

150

#### Lasting time

10 seconds

#### Cast time

2.4 seconds

#### Cooldown time

30 seconds

***

## Curse of Critical Hit

<div align="left"><figure><img src="/files/ZXvQsf9OeM0FBYRG2Bv6" alt=""><figcaption></figcaption></figure></div>

#### Description

Decrease the activation percentage of Cirtical Hit temporally.

#### Level Limit

* G1 - 54 Lv.
* G2 - 67 Lv.

#### Required Condition

None

#### Mana Consumption

26

#### Range

200

#### Lasting time

<pre><code><strong>50 + SKILL_LEVEL * 20
</strong></code></pre>

#### Critical chance percentage decrease

<pre><code><strong>25 + SKILL_LEVEL * 25
</strong></code></pre>

#### Cast time

Instant

#### Cooldown time

1 minute

***

## Curse of Strength

<div align="left"><figure><img src="/files/LQgeoPqyGRGtazpaeTGJ" alt=""><figcaption></figcaption></figure></div>

#### Description

Decrease the target's strength temporally.

#### Level Limit

* G1 - 53 Lv.
* G2 - 63 Lv.

#### Required Condition

None

#### Mana Consumption

38

#### Range

190

#### Lasting time

<pre><code><strong>50 + SKILL_LEVEL * 20
</strong></code></pre>

#### Strength decrease

<pre><code><strong>SKILL_LEVEL * 24
</strong></code></pre>

#### Cast time

Instant

#### Cooldown time

1 minute

***

## Curse of Health

<div align="left"><figure><img src="/files/bpV9l3TGs4nj57eohXGY" alt=""><figcaption></figcaption></figure></div>

#### Description

Decrease the target's health temporally.

#### Level Limit

* G1 - 56 Lv.
* G2 - 63 Lv.

#### Required Condition

None

#### Mana Consumption

38

#### Range

190

#### Lasting time

<pre><code><strong>50 + SKILL_LEVEL * 20
</strong></code></pre>

#### Health decrease

<pre><code><strong>SKILL_LEVEL * 12
</strong></code></pre>

#### Cast time

Instant

#### Cooldown time

1 minute

***

## Curse of Agility

<div align="left"><figure><img src="/files/ge7CislgXDnP8Jfrq3Dw" alt=""><figcaption></figcaption></figure></div>

#### Description

Decrease the target's Agility temporally.

#### Level Limit

* G1 - 56 Lv.
* G2 - 64 Lv.

#### Required Condition

None

#### Mana Consumption

42

#### Range

200

#### Lasting time

<pre><code><strong>50 + SKILL_LEVEL * 20
</strong></code></pre>

#### Agility decrease

<pre><code><strong>SKILL_LEVEL * 20
</strong></code></pre>

#### Cast time

Instant

#### Cooldown time

1 minute

***

## Curse of Intelligence

<div align="left"><figure><img src="/files/2jbOeqJ9dW3BgX4dXdA1" alt=""><figcaption></figcaption></figure></div>

#### Description

Decrease the target's Intelligence temporally.

#### Level Limit

* G1 - 57 Lv.
* G2 - 64 Lv.

#### Required Condition

None

#### Mana Consumption

42

#### Range

200

#### Lasting time

<pre><code><strong>50 + SKILL_LEVEL * 20
</strong></code></pre>

#### Intelligence decrease

<pre><code><strong>SKILL_LEVEL * 24
</strong></code></pre>

#### Cast time

Instant

#### Cooldown time

1 minute

***

## Curse of Wisdom

<div align="left"><figure><img src="/files/BPbEhQZKrkOyUwqPwtUf" alt=""><figcaption></figcaption></figure></div>

#### Description

Decrease the target's Wisdom temporally.

#### Level Limit

* G1 - 58 Lv.
* G2 - 66 Lv.

#### Required Condition

None

#### Mana Consumption

38

#### Range

200

#### Lasting time

<pre><code><strong>50 + SKILL_LEVEL * 20
</strong></code></pre>

#### Wisdom decrease

<pre><code><strong>SKILL_LEVEL * 16
</strong></code></pre>

#### Cast time

Instant

#### Cooldown time

1 minute

***

## Curse of Defense

<div align="left"><figure><img src="/files/PryV6S7hqy6qZ4eM9FfN" alt=""><figcaption></figcaption></figure></div>

#### Description

Decrease the target's Defense temporally.

#### Level Limit

* G1 - 59 Lv.
* G2 - 67 Lv.

#### Required Condition

None

#### Mana Consumption

83

#### Range

180

#### Lasting time

<pre><code><strong>30 + SKILL_LEVEL * 10
</strong></code></pre>

#### Short Range Defense decrease

<pre><code><strong>4 + SKILL_LEVEL * 8
</strong></code></pre>

#### Long Range Defense decrease

<pre><code><strong>2 + SKILL_LEVEL * 6
</strong></code></pre>

#### Cast time

Instant

#### Cooldown time

1 minute

***

## Poison Cloud

<div align="left"><figure><img src="/files/Eb9Upd1C1D6jU5tmPmPN" alt=""><figcaption></figcaption></figure></div>

#### Description

Spread the poison cloud and give continous damage to the all player in the poison cloud.

Poison cloud stays for 12 seconds.

#### Level Limit

* G1 - 59 Lv.
* G2 - 70 Lv.

#### Required Condition

None

#### Mana Consumption

```
100 + SKILL_LEVEL * 16
```

#### Range

200

#### Single Wave Damage

```
PHYSICAL_ATTACK * (200 * SKILL_LEVEL + 50) / 1000
```

{% hint style="info" %}
Effectively it means that single wave deals % of base attack:

* G1 25%
* G2 45%
  {% endhint %}

#### Cast time

2 seconds

#### Cooldown time

3 minutes

***

## Loss of Confidence

<div align="left"><figure><img src="/files/pDe0XJBtW752AJdVBiQz" alt=""><figcaption></figcaption></figure></div>

#### Description

Decrease 50% of target's On-Target Point temporally.

#### Level Limit

* G1 - 61 Lv.

#### Required Condition

None

#### Mana Consumption

98

#### Range

90

#### Lasting time

15 seconds

#### Cast time

Instant

#### Cooldown time

30 seconds

***

## Sight Blockade

<div align="left"><figure><img src="/files/adq33YJP7uum2cG8SSUi" alt=""><figcaption></figcaption></figure></div>

#### Description

Block the target's sight and make the target blind.

#### Level Limit

* G1 - 62 Lv.

#### Required Condition

None

#### Mana Consumption

100

#### Range

170

#### Lasting time

10 seconds

#### Cast time

1.8s

#### Cooldown time

30 seconds

***

## Buff Remover

<div align="left"><figure><img src="/files/mENFAwo5hi89Sw6yLnUL" alt=""><figcaption></figcaption></figure></div>

#### Description

Disable all the buffs from the target.

#### Level Limit

* G1 - 63 Lv.

#### Required Condition

None

#### Mana Consumption

68

#### Range

200

#### Cast time

2.3s

#### Cooldown time

15 seconds

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

[^1]: 40

[^2]: 50

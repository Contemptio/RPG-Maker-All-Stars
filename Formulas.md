# Formulas

## Auto-attack damage.

k is a scaling factor. Initial thought is that k = 0.1, so that damage dealt at the start is roughly 1/10th of maximum health.

> <pre>D := (2 * a.STR - b.def) * k;        // k = 0.1 currently.</pre>

## Critical hit chance.

While it is statically modified by weapon type and PC class, it is also increased by Luck (LUK). There will be something that counteracts it, some kind of "Hardness"-variable, but currently it is simply counteracted by the target's own Luck. The innate chance of a critical hit is C_i = 5%, and CH_MIN is the minimum allowed critical hit chance (curently 1%).

> <pre>PC_CH := (a.LUK - b.LUK) / 100;        // PC Critical Hit.</pre>

> <pre>PC_CH <= 0 ? CH = CH_MIN : 5 + PC_CH;  // Ensures minimum of CH_MIN %.</pre>

## Health

Health is a particularly straight-forward statistic and most other formulas are born from how they interact with health. It is therefore set to be 10 * L * k_h, where L is level and k_h ([1,10]) is the pertinent class' scaling factor. 
  This means that a level 1 character has between 10-100 HP and a level 100 character has between 1000-9999 HP. A class' starting hp is 10 * k_h and its HP at max level is 1000 * k_h.
  It is possible that this will be reconsidered, given that health-increasing items could be ineffective for level 100-characters with k_h = 10, albeit this might not be an issue.

> <pre>HP := 10 * L * k_h</pre>

### Classes' HP scaling factors

| Class   | k_h |
|:--------|:---:|
|Barbarian|  9  |
|Ranger   |  6  |
|Rogue    |  4  |
|Shaman   |  6  |

## Mana

Mana works along the same reasoning as health, it's just scaled down by a factor 10.

> <pre>MP := L * k_m</pre>

### Classes' MP scaling factors

| Class   | k_m |
|:--------|:---:|
|Barbarian|  3  |
|Ranger   |  4  |
|Rogue    |  5  |
|Shaman   |  7  |

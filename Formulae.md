# Formulae
## Damage and Healing
### Auto-attack damage

k is a scaling factor. Initial thought is that k = 0.1, so that damage dealt at the start is roughly 1/10th of maximum health.

> <pre>D := (2 * a.VIG - b.STA) * k;        // k = 0.1 currently.</pre>

### General ability formula
As abilities can be given very varied effects from their formulas being directly customizable, many will not use the structure described below. It should, however, be the go-to formula for generic or simple abilities.
  Ability resolution is determined by several variables, as well as whether the ability is magical or physical in nature. Both magical and physical offensive abilities generally have the same formulae structure, however.
  Both of the aggressor's and defender's involved statistics can be scaled with a constant factor, e for efficiency and m for mitigation, and the entire result is then scaled by its own factor k. It is highly recommended that for most "bread-and-butter" abilities that e > 2 * m so that in most encounters the abilities aren't nullified. The factor k depends on the magnitude of the ability, as well as the factors e and m.
  The entire formula can of course be adjusted up or down with the flat modifier B but this should be avoided in most cases since if used frivolously it might inhibit the scaling in the entire game.

> <pre>E := k * (e * a.STAT - m * b.STAT) + B;</pre>

## Statistics Formulae
### Health

Health is a particularly straight-forward statistic and most other formulae are born from how they interact with health. It is therefore set to be 10 * L * k_h, where L is level and k_h ([1,10]) is the pertinent class' scaling factor. 
  This means that a level 1 character has between 10-100 HP and a level 100 character has between 1000-9999 HP. A class' starting hp is 10 * k_h and its HP at max level is 1000 * k_h.
  It is possible that this will be reconsidered, given that health-increasing items could be ineffective for level 100-characters with k_h = 10, albeit this might not be an issue.

> <pre>HP := 10 * L * k_h;</pre>


### Mana

Mana works along the same reasoning as health, it's just scaled down by a factor 10.

> <pre>MP := L * k_m;</pre>

### Agility
#### Action recovery rate
TBW.

#### Critical hit chance

While it is statically modified by weapon type and PC class, it is also increased by Luck (LUK). There will be something that counteracts it, some kind of "Hardness"-variable, but currently it is simply counteracted by the target's own Luck. The innate chance of a critical hit is C_i = 5%, and CH_MIN is the minimum allowed critical hit chance (curently 1%).

> <pre>PC_CH := (a.LUK - b.LUK) / 100;        // PC Critical Hit.</pre>

> <pre>PC_CH <= 0 ? CH = CH_MIN : 5 + PC_CH;  // Ensures minimum of CH_MIN %.</pre>

### Dexterity
#### Hit chance
In order to make hit chance a relevant statistic, it needs to be varied from encounter to encounte based on the opponent's evasion chance. Hit chance is calculated based on the aggressor's dexterity vs. the defender's dexterity. The minum hit chance at any time is 25%, whereas the maximum hit chance can reach 100%. This means that the discrepancy between dexterity values will generate a hit chance addition between 0-75% units.

> <pre> DEX_dm = 
> <pre> HC = B_H + DEX_dm * k_hc = 100;</pre>
> <pre> k_hc = (100 - B_H) / DEX_dm;</pre>

Currently,

> <pre>B_H = 25, Dex_dm = 50; => k_hc = (100 - 25) / 50 = 1.5;

Which means the current hit chance formula is:

> <pre>HC = 25 + 1.5 * (a.

#### Evasion
TBW.

### Spirit
#### Buff rate
TBW.

### Stamina
#### Targeted rate
TBW.

### Vigour
#### Guard amount
TBW.

### Willpower
#### Magic evasion
TBW.

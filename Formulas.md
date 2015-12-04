# Formulas

## Auto-attack damage.

k is a scaling factor. Initial thought is that k = 0.1, so that damage dealt at the start is roughly 1/10th of maximum health.

> <pre>D := (2 * a.STR - b.def) * k;        // k = 0.1 currently.</pre>

## Critical hit chance.

While it is statically modified by weapon type and PC class, it is also increased by Luck (LUK). There will be something that counteracts it, some kind of "Hardness"-variable, but currently it is simply counteracted by the target's own Luck. The innate chance of a critical hit is C_i = 5%.

> <pre>PC_CH := (a.LUK - b.LUK) / 100;      // PC Critical Hit.</pre>

> <pre>PC_CH <= 0 ? CH = 5 : 5 + PC_CH;     // Ensures minimum of 5%.</pre>

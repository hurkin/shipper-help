# Explanation of Rounding

**Question:** when I convert the total pounds to short tons (ST) or metric tons (MT),
the result differs from the total on the report. Why?

**Answer:** each row's ST or MT is rounded, and the report adds up the rounded
values. It doesn't recalculate the total from the total pounds. Both totals can't
match every time. This is arithmetic, not a fault.

Shipper keeps the **column total** accurate: the total is always the sum of the rows
shown. Shipping lines and banks have asked for this repeatedly, because the rows
and the total on a document must agree.

## Example

| Container | Pounds | MT (rounded to 3 places) |
|---|---|---|
| 1 | 40,101 | 18.190 |
| 2 | 40,101 | 18.190 |
| 3 | 40,101 | 18.190 |
| **Total** | **120,303** | **54.570** |

Each container is 18.1895 MT, which rounds up to 18.190, so the rows add up to
54.570. The total pounds, 120,303, converts to 54.569 MT.

## A detailed example

Five containers, converted to metric tons at 2,204.6341 pounds per MT, rounded to 4
and to 3 places:

| Pounds | MT, 4 places | MT, 3 places |
|---|---|---|
| 50,000 | 22.6795 | 22.680 |
| 50,100 | 22.7249 | 22.725 |
| 50,240 | 22.7884 | 22.788 |
| 50,300 | 22.8156 | 22.816 |
| 50,400 | 22.8609 | 22.861 |
| **Column total:** 251,040 | **113.8693** | **113.870** |
| **Calculated from 251,040 lbs** | 113.8692 | 113.869 |
| **Difference** | 0.0001 | 0.001 |

The column total is what the report shows.

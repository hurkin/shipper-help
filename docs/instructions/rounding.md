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

# Grower Deposits

Record a deposit paid to a grower outside Shipper (for example, a check written in
your accounting system) against their purchase contract. Linking a bill to a
contract is done in ShipperXL Desktop.

You need from accounting: the check number, amount, payee and date paid.

1. Open **Bills** and click **Add New**.
2. Choose the seller that matches the payee. Your company is the buyer.
3. In **Agreement**, enter the purchase contract number. If a sales agreement has
   the same number, Shipper asks which one you mean. Pick the purchase contract.
4. Enter *Deposit* in **Memo** and save to get the bill number.
5. On **Items**, add a line with item *Deposit*. The bill total stays at zero.
6. On **Dates and Terms**, set **Bill Date** to the date paid and **Terms** to
   *Prepaid*.
7. On **Payments**, enter the check amount, payment date (the date paid),
   **Reference 1** (the check number) and method *Check*.
8. Save and close.

Run **Agreement Summary** for the purchase contract to check the deposit shows. It
lists two lines: the zero-amount bill and the check.

If you picked the sales agreement by mistake: clear the agreement number, save and
close, reopen the bill, and enter the number again.

See also: [Bills](../context/IV03.md).

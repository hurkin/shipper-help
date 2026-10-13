# Automated Credit Memos or Work Orders

Shipper can create a credit memo (or a work order) automatically when an invoice is
completed. This takes two things:

1. **A price breakdown on the sales order line.** Open the line, go to **Variable
   Costs**, and add the amount for the item to credit (for example, a claim item).
   Mark it **Auto Bill**.

   ![[auto-bill-cost.png]]

2. **A scheduled job.** Email support to set up the *Automated Credit Memo* or
   *Automated Work Order* job for your database.

Once both are in place, marking an invoice **Completed** creates the credit memo (or
work order) for each marked breakdown row.

## Good to know

- It can take up to 10 minutes after the invoice is completed.
- It runs once per invoice. Changing the invoice or the breakdown afterwards does
  not update the credit memo.
- In the web app, **Auto Bill** shows only on purchase lines. Mark sales lines in
  ShipperXL Desktop.

See also: [Scheduled Jobs](../context/G014.md), [Credit Memos](../context/IV05.md).

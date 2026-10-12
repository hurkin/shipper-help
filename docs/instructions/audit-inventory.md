# Audit and Reconcile Inventory

- **Check levels:** run a balance report such as **Inventory by SKU, Location**, or
  use **Inventory > Balance**.
- **Check daily activity:** run **Inventory Transactions**. This helps most when
  many people or mobile scanners are recording inventory.
- **Look at one SKU:** open it in **Lists > SKUs**. The **Ledger** tab lists every
  transaction with running raw, processed and weight balances.
- **Move inventory:** use [Move Inventory](move-inventory.md).
- **Correct inventory:** fix the row on the cargo or work order it belongs to, or add
  an [inventory adjustment](../context/I012.md) in ShipperXL Desktop.

## Physical counts

Use **Inventory > Physical Inventory** to record what you counted at a point in
time:

1. Set **Checked** to the date and time of the count, and narrow it by work zone,
   location owner, location or SKU.
2. Click **Rebuild** to fill the worksheet with what Shipper says is on hand as of
   that time.
3. Enter the counted raw and processed quantities, add rows for anything found
   that wasn't listed, and remove rows that weren't found.
4. Save.

Counts don't change inventory. Compare them with reports such as **Physical
Inventory** and **Physical Inventory Cost Variance**, then correct the inventory
where it is wrong.

See also: [Physical Inventory](../context/I011.md), [Inventory Basics](inventory-basics.md).

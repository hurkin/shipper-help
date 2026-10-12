# Move Inventory to Another SKU

Do this when product was received under the wrong SKU. It takes the inventory off
the old SKU and puts it, with the same tags, on a new cargo under the right SKU.
The barcode and SKU on an inventory row can only be changed in ShipperXL Desktop,
so these steps use the desktop app.

1. Open the original cargo and note its inventory: each tag, location and balance.
2. Add a deducting row for each location. For example, if Barn A holds 48, add a
   row of -48 at Barn A. Don't save yet.
3. Create a new cargo.
4. Add the inventory you noted in step 1, with the same tags, under the right SKU.
5. Put the new cargo on the purchase contract or order line, if it has one.
6. Save and close the new cargo.
7. Go back to the original cargo and remove the tag barcode from each of its
   inventory rows.
8. Save and close the original cargo.

Date the new rows after the deductions, so the balance never shows the product in
both SKUs at once.

See also: [Inventory Basics](inventory-basics.md), [Cargo](../context/B003.md).

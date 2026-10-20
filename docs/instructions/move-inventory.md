# Move Inventory

Use **Inventory > Move** to move inventory from where it is to a new location.

1. Choose the **To Location**. Every line goes there unless you give it its own.
2. Build the list. You can add:
   - **A tag:** scan or type it. It moves whole, from wherever it is.
   - **A SKU:** pick it to see its balance in every location, then choose how much
     raw and processed to take from each.
   - **A location:** pick it to see every SKU there, and choose the same way.
3. If the move happened earlier, enter it in **Transaction Date**. Leave it blank
   for now.
4. Click **Move**.

![[move-inventory.png|300]]

## Good to know

- Every line is checked before anything moves. If one line fails, nothing moves,
  and the failing lines show why (for example, not enough on hand, or the same from
  and to location).
- A move writes two rows: one out of the old location and one into the new
  location a second later. Both are dated with the Transaction Date, or now.
- Tags are faster and safer than SKUs. A barcode scanner works in the tag field.
- If you are catching up on paperwork, enter the Transaction Date, and check that
  nothing was shipped from the old location after it.

See also: [Move Inventory](../context/I010.md), [Move Inventory to Another SKU](move-to-another-sku.md).

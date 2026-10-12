# Create a Quick Sale

Use a quick sale when you sell product straight from your yard to a walk-in
customer and need to weigh, load and invoice in one visit. The **Quick Sale**
screen is in ShipperXL Desktop. It creates an ordinary sales order (marked with the
source *QuickSale*), an outbound cargo and its scale ticket together.

## Steps

1. Open **Quick Sale** and choose the buyer.
2. Enter the line: the item or SKU sold and the price.
3. Tick the cargo option to record the load, then weigh the vehicle in on the scale
   ticket, or read the weight from the scale.
4. While the customer loads, the record can stay open or be saved and reopened.
5. When the customer returns, weigh out to complete the scale ticket.
6. On the inventory section, deduct the SKU from its location (a negative raw
   quantity).
7. Save, then click **Create Invoice**. The invoice opens. Print or email it.

> **Screenshot placeholder:** the Quick Sale screen with a buyer, one line and a completed scale ticket. (save as `images/quick-sale.png`)

## Good to know

- **Create Invoice** is available only once the cargo is included and only until an
  invoice exists.
- You can also create a purchase contract for the product from the same screen.
  That needs a booking (shipment) number.

## Doing the same in the web app

There is no quick sale screen in the web app. Use the same records instead:

1. Create the [sales order](sales-orders.md).
2. In **Outbound > Outbound Cargo**, create a cargo, add its scale ticket, put the
   order's line on its **Fulfillment** tab with a fulfilled quantity, and deduct
   the inventory on its **Inventory** tab.
3. Open the sales order and click **Create Invoice**.

See also: [Sales Orders](../context/A004.md), [Cargo](../context/B003.md),
[Quick Sale](../context/A009.md).

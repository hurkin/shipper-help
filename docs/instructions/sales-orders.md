# Create a Sales Order

1. Go to **Outbound > Sales Orders** and search first, to make sure the order
   doesn't already exist.
2. Click **New** and choose the customer. If the customer is missing, the lookup
   offers to create it.
3. Click **Create**. Shipper gives the order its number, makes your company the
   seller and you its sales agent, and adds your default terms.
4. On **General**, fill in what you know: ship-to, references, dates and memo. You
   can save at any point and finish later.
5. On **Line Items**, add a line for every item you are selling:
   - Choose the **Item**. A **SKU** is often needed too. Create it in
     **Lists > SKUs** if it doesn't exist. It doesn't need a purchase contract
     first.
   - Enter the **Quantity Ordered** and the **Unit Type** (Each or Container).
   - The **Sales Amount** fills in from your price list when one matches. You can
     overwrite it.
6. If the sale already has a booking, open the line, go to **Assignments**, and
   assign it to the booking with a quantity and work zone.
7. Click **Save**.
8. Use **Reports** to print the **Agreement** report and send it to your customer.

## Good to know

- An order can be drawn from a sales contract. Pick the contract on **General**,
  then pick the contract line on each order line. Fulfillment on the order then
  counts towards the contract.
- A new order doesn't appear in the Sales Orders grid until it has at least one
  line.
- To turn a quote into an order, open the quote and use **Copy To**.

## Reassign a line to another agreement

1. Find where the line is used: on a cargo's or work order's **Fulfillment** tab.
2. Set the old line's Assigned and Fulfilled to 0. Then click **Add line item**,
   pick the line from the other agreement, and enter its quantities.
3. Save.

See also: [Sales Orders](../context/A004.md), [Quick Sale](quick-sale.md),
[Create Invoices](create-invoices.md).

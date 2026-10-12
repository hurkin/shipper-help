# Create Invoices

You can create an invoice from a **sales order** or from a **booking**. Either way,
Shipper builds the invoice from what has been fulfilled and saves it straight away.

| From | Lines come from | Use when |
|---|---|---|
| **Sales order** (Create Invoice button) | That order's fulfilled lines | You invoice per order |
| **Booking** (Invoices tab) | Every sales order and contract fulfilled on the booking or its cargo | You invoice per booking |

## Steps

1. Save any changes first. The buttons are disabled while there are unsaved edits.
2. On a sales order, click **Create Invoice**. On a booking, open **Invoices** and
   click **Create Invoice with Item Descriptions** or **Create Invoice with
   Contents Descriptions**.
3. If an invoice already exists, Shipper names it and asks whether to create
   another.
4. The new invoice opens. Check it, change what you need, and save.
5. Use **Reports** on the invoice to print the **Bill** or **Commercial Invoice**.

## How the lines are built

- Each fulfillment makes one line. Its item column shows the cargo number, work
  order number or scale ticket number it came from.
- If the order line is priced per container, the quantity is 1. Otherwise it is the
  cargo's contents quantity, the work order's quantity, or the fulfilled quantity.
- If the cargo has a scale ticket, its net weight goes in the secondary quantity.
- The description is the item's short description plus the line's customer SKU.
  With **Contents Descriptions**, a cargo line uses the cargo's contents description
  instead.
- Price, unit and references come from the order line.
- Finished work orders on the booking can add lines too, when the order line has a
  work order template marked to include on the bill.

## Good to know

- Nothing fulfilled means nothing to invoice. Shipper says so and creates nothing.
- The invoice date is today. Terms come from the order, then the customer, then the
  first terms set up.
- A new invoice goes into your invoice starting queues.
- A booking linked to a letter of credit links its invoice to that letter of
  credit.
- A wrong invoice can be deleted as long as it isn't posted and has no payments.

See also: [Invoices](../context/IV01.md), [Explanation of Rounding](rounding.md).

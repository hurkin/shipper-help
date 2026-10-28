# Accounting Integration

ShipperXL can connect to your accounting package, so you don't enter the same
invoices and bills twice. It works with:

- [QuickBooks Online](https://qbo.intuit.com)
- [Zoho Books](https://books.zoho.com)
- Using another? Let us know.

Still on QuickBooks Desktop? See [QuickBooks Service](quickbooks-service.md).

## What it does

- Copies invoices from Shipper to your accounting package.
- Copies bills from Shipper to your accounting package.
- Copies payments from your accounting package back to Shipper.
- Copies or updates the customers, vendors and items on those invoices and bills.

## Set it up

Email support@shipperxl.com to have it set up for your database. It is quick.

Then fill in its section, and the account names Shipper posts with, in **Admin >
Settings** on the **Accounting** tab. See [Settings](../context/settings.md).

## How accounting codes are chosen

Each bill and invoice line with an item gets an accounting item number, class and
account. Bills and credits get an expense account, invoices an income account.
They are worked out when the line is created, by Create Bills, Create Invoices or
Create Bill, and each time a bill or line is saved. A later step wins over an
earlier one:

1. **The item's** external item number, class and account, where the line has none
   yet. Changing a line's item clears its codes first, so the new item's are used.
2. **Class from fulfillment** (invoices made from a sales order only): the first
   fulfillment of the line whose processor, work center or work zone has an
   external class, taken in that order.
3. **Class from the work zone:** the line's work zone, if it has an external class.
   The work zone comes from the line's work orders, else the fulfillment, scale or
   assignment of its cargo or agreement line, else the booking's cargo.
4. **Item overrides:** an item's accounting overrides that match the line's work
   zone, or the seller's country or region, replace each code they set.
5. **The default account** in **Admin > Settings**, under **QuickBooks Online**:
   **Expense Account** for bills and **Income Account** for invoices, fills an
   account that is still empty.

A bill line's description also starts with its work zone, such as *Ellensburg:
Squeeze Loading*.

## Related

[Create Invoices](create-invoices.md) ·
[Scheduled Job: Payment Posted](payment-posted-job.md) ·
[Scheduled Jobs](../context/G014.md)

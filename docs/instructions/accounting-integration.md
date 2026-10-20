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

Then set the account codes Shipper posts with in **Admin > Settings**, on the
**Accounting** tab. See [Settings](../context/settings.md).

## How accounting codes are chosen

When an invoice is created from a booking, each line's accounting item number,
class and accounts are worked out in this order. A later step wins over an earlier
one:

1. **The item's** external item number, class, income account and expense account.
2. **Class from fulfillment:** the first fulfillment of the line whose processor,
   work center or work zone has an external class, taken in that order.
3. **Class from the work zone:** the line's work zone, if it has an external class.
   The work zone comes from the line's fulfillment, else the scale of the cargo that
   fulfilled it, else its assignment, else the booking's cargo.
4. **Item overrides:** an item's accounting overrides that match the line's work
   zone, or the seller's country or region, replace each code they set.
5. **The default income account** in **Admin > Settings** fills an income account
   that is still empty.

## Related

[Create Invoices](create-invoices.md) ·
[Scheduled Job: Payment Posted](payment-posted-job.md) ·
[Scheduled Jobs](../context/G014.md)

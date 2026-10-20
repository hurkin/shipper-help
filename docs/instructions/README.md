# Instructions

Start with [How Shipper Works](how-shipper-works.md) to see how the records connect,
then [Getting Started](getting-started.md). [See Who Changed a Record](record-history.md)
explains a record's History.

## Day to day

- [Create a Sales Order](sales-orders.md)
- [Create a Quick Sale](quick-sale.md)
- [Create a Booking](bookings.md)
- [Enter a Purchase Contract](purchase-contracts.md)
- [Work Orders and the Scheduler](work-orders.md)
- [Receive Inventory](receive-inventory.md)
- [Move Inventory](move-inventory.md)
- [Ship Cargo](ship-cargo.md)
- [Move Cargo to Another Booking](move-cargo.md)
- [Complete a Booking](complete-a-booking.md)
- [Create Invoices](create-invoices.md)
- [Prepare Documentation](documentation.md)
- [Queues (Workflow)](queues.md)

## Inventory

- [Inventory Basics](inventory-basics.md)
- [Traceability](traceability.md)
- [Audit and Reconcile Inventory](audit-inventory.md)
- [Move Inventory to Another SKU](move-to-another-sku.md)

## More scenarios

- [Reserve Inventory with a Sales Contract](reserve-by-sales-contract.md)
- [Enter a Claim](claims.md)
- [Grower Deposits](grower-deposits.md)
- [Automated Credit Memos or Work Orders](automated-credit-memos.md)
- [Record Customer Visits and Other Inspections](inspections.md)
- [Scheduled Job: Payment Posted](payment-posted-job.md)
- [Explanation of Rounding](rounding.md)
- [Create Custom Reports](custom-reports.md), with [Power BI](power-bi.md) or
  [Report Builder](report-builder.md)
- [ShipperXL APIs](api.md)

See also
[Using the ShipperXL Mobile App with the Kiosk](https://docs.google.com/document/d/1lbXtoBH1YqVAT-fk8ntrYfVBp4zB6iSobUoi1-1ZAIU/edit?usp=sharing).

## Editions

Some features come only with the Pro or Enterprise edition:

- **Pro:** [reserving inventory with a sales contract](reserve-by-sales-contract.md),
  [carrier service contracts](../context/B009.md), [cost lists](../context/I005.md),
  [inventory adjustments](../context/I012.md),
  [letters of credit](../context/IV07.md), [bulk edit bookings](../context/S028.md),
  [terms templates](../context/A008.md),
  [scheduled jobs such as Payment Posted](payment-posted-job.md),
  [custom reports](custom-reports.md) and [assets](../context/T001.md).
- **Enterprise:** [customer visits and inspections](inspections.md),
  [claims](claims.md), [grower deposits](grower-deposits.md),
  [automated credit memos or work orders](automated-credit-memos.md),
  [purchase orders](../context/A002.md), [sales quotes](../context/A006.md),
  [Create Bills](../context/W005.md), [bills](../context/IV03.md),
  [price lists](../context/I006.md), [physical inventory](../context/I011.md), the
  [Supplier Performance](../context/R200.md) report, Power BI's semantic model, and
  direct database access.

Some quick answers:

- **Transfer inventory by truck to another location:** use work orders.
- **Add work orders to an invoice:** create the invoice from the sales order.
- **Kick out bales when the SKU is known:** move them to a kick-out location.
- **Kick out bales when the SKU isn't known:** move them to a kick-out SKU.
- **Sell chaff:** use a quick sale.

## Install and set up

- [Implementation Checklist](implementation-checklist.md)
- [Set Up a New Database](new-database.md)
- [Hardware and Supplies](hardware.md)
- [User Accounts](user-accounts.md)
- [Email Attachments into Shipper](email-attachments.md)
- [Accounting Integration](accounting-integration.md), or the
  [QuickBooks Service](quickbooks-service.md) for QuickBooks Desktop
- [MailChimp Integration](mailchimp.md)
- [Example Documents](example-documents.md)
- [Install ShipperXL Desktop](install-desktop.md)
- [Install ShipperXL Mobile](install-mobile.md)
- [Using ShipperXL Mobile](mobile-app.md)
- [Install the Kiosk](install-kiosk.md)
- [Using the Kiosk](kiosk.md)
- [Label Printer Setup](label-printer.md)
- [Test Versions](test-versions.md)
- [Billing](billing.md)

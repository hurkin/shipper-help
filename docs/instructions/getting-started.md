# Getting Started

## Before you start: items and SKUs

You need an item for every product and service involved in buying, processing,
shipping and selling, and a SKU for every lot of product you hold.

For example, a hay exporter might set up:

| Code | Kind | What it is |
|---|---|---|
| 3ALF | Product item (raw) | 3rd Cutting Alfalfa |
| ALFSLV | Product item (processed) | Compressed Alfalfa in Sleeve |
| PCOMM | Service item | Purchasing commission |
| BASIN2EBURG | Service item | Flatbed delivery from the Basin to Ellensburg |
| SLVPRESS | Service item | Press into sleeve |
| EBURG2SEA | Service item | Container delivery from Ellensburg to Seattle |
| A123 | SKU | Grower "A", stack 123 |

So SKU A123 is received via BASIN2EBURG, commissioned via PCOMM, pressed from 3ALF
into ALFSLV via SLVPRESS, and shipped via EBURG2SEA.

Things to know when setting these up:

- An item is either a product or a service, and that can't be changed after it is
  saved.
- A SKU belongs to one item and has one raw inventory unit (such as a 3x4 bale).
  If a lot comes in two unit types, use two SKUs.
- Once an item has SKUs, its unit classes are locked.

Read [How Shipper Works](how-shipper-works.md) for how these records connect.

## Basic functions

| Question | Where to go |
|---|---|
| What am I selling? | [Create a Sales Order](sales-orders.md) or a [Quick Sale](quick-sale.md) |
| Is there an ocean booking? | [Create a Booking](bookings.md) |
| What am I buying? | [Enter a Purchase Contract](purchase-contracts.md) |
| What work am I doing? | [Work Orders and the Scheduler](work-orders.md) |
| Receiving inventory? | [Receive Inventory](receive-inventory.md), [Inventory Basics](inventory-basics.md) and [Traceability](traceability.md). See [Using the Kiosk](kiosk.md) for self-service at the scale. |
| Moving inventory? | [Move Inventory](move-inventory.md) or [Move Inventory to Another SKU](move-to-another-sku.md) |
| Shipping inventory? | [Ship Cargo](ship-cargo.md) or [Move Cargo to Another Booking](move-cargo.md) |
| Wrapping up? | [Complete a Booking](complete-a-booking.md) |
| Sending an invoice? | [Create Invoices](create-invoices.md) |
| Sending documents? | [Prepare Documentation](documentation.md) |

## Getting around the web app

- The menu is grouped by stage: **Inbound**, **Processing**, **Outbound**,
  **Inventory**, **Documentation** and **Lists**, with **Reports** and **Admin** at
  the bottom.
- Lookups start searching after you type a few characters. If nothing matches and
  you can add records of that kind, the lookup offers to create one.
- Grids remember their filters and search text until you close the browser tab.
- A record page shows **Unsaved changes** while you have edits. Leaving the page,
  refreshing or signing out asks first.
- The **?** button on each screen opens help for that screen.
- **History**, at the far right of a record's **Save** row, shows who changed the
  record and its lines, and what they changed. See
  [See Who Changed a Record](record-history.md).

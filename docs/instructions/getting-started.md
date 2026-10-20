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
- **Pictures are public.** JPG and PNG attachments are stored where anyone with
  their link can see them, so documents and reports can show them. Other files are
  private.
- In ShipperXL Desktop, lists that rarely change (such as categories, commodities
  and container types) are cached. After changing one, press **F9** to reload it.
- **History**, at the far right of a record's **Save** row, shows who changed the
  record and its lines, and what they changed. See
  [See Who Changed a Record](record-history.md).

## Companies and contacts

[Companies and Contacts](../context/G008.md) holds everyone you deal with. A contact
(a person) can belong to several companies, and a company can have many addresses
and categories, such as customer, supplier and carrier.

- Changes to a company or contact show on everything you do from then on. They
  don't change documents already printed or sent.
- If a business changes its name, rename it rather than adding a new one. All its
  past records follow it.

## Save typing

- **Copy To** makes a new agreement from an existing one, with its parties, terms
  and lines. For example, copy a purchase contract to a purchase order for one
  delivery against it. See [Sales Orders](../context/A004.md).
- **Clone** copies an item, cost list, asset or work order to start a new one.
- **Auto Work Orders** on a purchase or sales agreement create the same work
  orders, with the same rates and services, on every cargo its lines are assigned
  to. See [Work Orders and the Scheduler](work-orders.md).
- [Import Data](../context/G012.md), in ShipperXL Desktop, loads companies, items,
  bookings or cargo from a CSV file, such as one exported from QuickBooks.

## Next

New to ShipperXL? Work through the
[Implementation Checklist](implementation-checklist.md) and
[Set Up a New Database](new-database.md).

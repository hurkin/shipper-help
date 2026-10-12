# Inventory Basics

## The numbers

| Number | Meaning |
|---|---|
| **Ordered** | The quantity on an agreement line. Buy in bales, sell in containers. |
| **Assigned** | The part of an ordered quantity planned onto a booking (the same or less than ordered). |
| **Fulfilled** | The part actually delivered by a cargo or work order. |
| **Raw** | Inventory in raw units, such as bales. Negative removes, positive adds. |
| **Processed** | Inventory in processed units, such as sleeves. Negative removes, positive adds. |

Most systems would move product from SKU A to SKU B when it is processed. Shipper
keeps the same SKU and moves it from raw to processed, so a processed product can
always be traced to its source.

## The rules

- A row counts only when it has a **date and time** and a **location**.
- Balances are worked out by date and time, so record events in the order they
  happened.
- Each SKU has one raw unit. It can't change once the SKU has inventory.
- Weights come from inbound scale tickets. A row deducted by tag uses that tag's
  weight. A row deducted by SKU uses the SKU's average weight of everything received
  up to that time.

## Product coming in

- **A. Bought on a purchase contract and stocked.** The cargo fulfills the contract
  line and adds raw inventory to the SKU (positive). Fulfillment is usually in
  bales.
- **B. Received with no purchase agreement**, for example for custom pressing. The
  cargo adds raw inventory to the SKU, with no fulfillment.
- **C. Bought but never stocked**, as in a back-to-back trade. The cargo fulfills
  the contract line with no inventory and no SKU. Use the line's reference to find
  it. Fulfillment is usually in containers.

## Product going out

- **A. Processed straight into a container.** The cargo fulfills the sales order and
  removes raw inventory (negative). Fulfillment is usually in containers.
- **B. Processed ahead of the container**, for a particular order. A work order
  removes raw inventory and adds processed inventory. When the container arrives,
  it is loaded from processed inventory (negative) and fulfills the sales order.
- **C. Back-to-back**, like incoming C. Usually there are two fulfillments on one
  container: one for the purchase and one for the sale.
- **D. Shipped straight from the supplier.** The cargo's movement type is both
  inbound and outbound (a direct ship). It fulfills both the purchase (usually
  bales) and the sale (usually containers), both positive.

When you process for someone else, the item sold is a service (pressing) rather
than a product. How much of the documentation you do depends on how the work is
split with the processor.

See also: [Traceability](traceability.md), [Audit and Reconcile Inventory](audit-inventory.md),
[SKUs](../context/I004.md).

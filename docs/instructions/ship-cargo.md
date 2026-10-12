# Ship Cargo

An outbound load is a cargo with movement type **Outbound**: usually a container on
a booking.

## Check whether the load is planned

Go to **Outbound > Outbound Cargo** and look at **Incomplete**. Containers added to
a booking are already here. Search by booking or container number.

## Record the load

1. Open the existing cargo, or click **New** and choose the container type.
2. On **General**, enter the **Container Number** (for a container, Shipper checks
   its check digit), the seal, and the exact booking number under **Shipment**.
3. Under **Processor Timeline**, enter **Received**. Don't enter **Loaded** yet if
   the driver still has to weigh out.
4. On **Scale Ticket**, choose the scale and capture or enter the weights.
5. On **Fulfillment**, make sure the sales line is there and **Fulfilled** is 1 (one
   container). Use **Add line item** if it is missing.
6. On **Work Orders**, add or finish the loading work.
7. On **Inventory**, take the product off inventory. Scan each tag to deduct its
   whole balance, or pick a SKU and source location to deduct what is there.
8. On **Contents**, click **Copy from inventory** or **Copy from order** to list what
   the container holds for the documents.
9. Enter **Loaded** when loading is finished. Save, then print the **Cargo Bill of
   Lading** or **Scale Weight Ticket** from **Reports**.

> **Screenshot placeholder:** the outbound cargo Inventory tab after scanning tags, showing negative rows. (save as `images/outbound-inventory.png`)

## Good to know

- Deductions are dated with **Loaded**, or **Delivered to Carrier** if there is no
  load time yet.
- Scanning a tag with nothing left on it asks before deducting.
- If the booking is posted, its cargo is read-only.
- With scale integration, don't finish **Loaded** or the work orders until the
  driver comes back for the second weight.

## Shipping by scanning

**Outbound > Ship Inventory** takes inventory out against a work order without
opening the cargo. Choose the work order, scan tags (each goes whole) or pick a SKU
and choose how much to take from each location, then click **Ship**. The rows are
recorded on the work order's cargo. Shipping starts the work order if it hadn't started.

See also: [Outbound Cargo](../context/B003.md), [Ship Inventory](../context/M05.md),
[Move Cargo to Another Booking](move-cargo.md).

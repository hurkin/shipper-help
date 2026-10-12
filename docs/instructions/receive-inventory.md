# Receive Inventory

An inbound load is a cargo with movement type **Inbound**. It records the truck,
its weights, the purchase line it fulfills and the inventory tags it brings in.

## Check whether the load is expected

Go to **Inbound > Inbound Cargo** and look at **Incomplete**. If the delivery was
planned, its cargo (or work order) is already there. Search by SKU, manifest or
cargo number. If a search finds nothing, Shipper looks across all cargo and tells
you why each match was outside your view.

## Record the load

1. Open the existing cargo, or click **New**. A new cargo takes the next cargo
   number. Choose its container type (for example, flatbed trailer).
2. On **General**, enter the manifest. Under **Processor Timeline**, enter the
   **Received** date and time, and **Unloaded** once the truck is unloaded.
3. On **Scale Ticket**, choose the scale and add the ticket. Enter or capture the
   gross and tare weights, and the driver in **Driver**.
4. On **Inventory**, type the SKU (or the supplier's SKU) and click **Find**. Shipper
   finds the purchase line and puts it on the cargo. If several lines match, pick
   one.
5. On **Fulfillment**, enter the number of units received (for example, bales) in
   **Fulfilled**.
6. Back on **Inventory**, enter how many tags to print and, if you know it, the
   receipt location. Click **Add tags**. The fulfilled quantity is split evenly
   across the tags. For example, 8 tags for 448 bales gives 56 bales each.
7. On **Work Orders**, add or finish the work done on the load (trucking,
   unloading).
8. Save, then use **Reports** for the tags, inspection report or scale weight
   ticket.

> **Screenshot placeholder:** the cargo Inventory tab after Add tags, showing the tag rows with SKU, quantity and location. (save as `images/inbound-tags.png`)

## Good to know

- **A tag with no location isn't in inventory yet.** It waits until it is received:
  give it a location here, or scan it in **Inbound > Receive Inventory**.
- Inventory rows are dated with the **Unloaded** time, or **Received** if there is
  no unload time yet.
- The unit weight of everything on the load comes from its scale ticket: net weight
  divided by the units received. Change the weights later and every row from the
  load is recalculated.
- A cargo can carry up to 99 tags.
- With scale integration, the driver weighs in at the kiosk. Find the driver's
  cargo here when they return to finish the unload time and work orders. See
  [Using the Kiosk](kiosk.md).

## Receiving by scanning

**Inbound > Receive Inventory** is the quick way to bring in tags that were
printed earlier:

1. Choose the **To Location** for every line that has no location of its own.
2. Scan a work order or cargo to list all its tags not yet received, or scan tags
   one at a time.
3. Click **Receive**. Every line is checked first. If any line fails, nothing is
   received and the failing lines are marked.

Receiving sets the cargo's **Received** (and, for inbound cargo, **Unloaded**) time
if it was empty, and starts the work order if it hadn't started.

See also: [Inbound Cargo](../context/B003.md),
[Receive Inventory](../context/M01.md), [Inventory Basics](inventory-basics.md).

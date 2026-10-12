# Using ShipperXL Mobile

ShipperXL Mobile records inventory by scanning: receiving, moving, processing and
shipping. The main menu shows only the screens your roles allow. See
[Install ShipperXL Mobile](install-mobile.md) to get started.

> **Screenshot placeholder:** the mobile app's main menu. (save as `images/mobile-menu.png`)

## ADD, then DONE

On every screen, press **ADD** once a line is filled in, then **DONE** to save to
Shipper. A line you didn't **ADD** isn't saved. Lines you added aren't saved until
you press **DONE**.

If any line fails when you press **DONE**, nothing is saved and the app shows why.
Fix or remove the line and try again.

## Tags

- **An inventory tag** (block tag) is a serial number for one block of product. It
  traces back to the inbound load and every move since. It has one quantity and
  one location at all times. Moving it moves all of it.
- **A SKU tag** stands for the SKU as a whole, not a particular load. When you use
  one, you also enter the location and quantity.

> **Screenshot placeholder:** an inventory tag beside a SKU tag. (save as `images/mobile-tags.png`)

## Work orders

Every printed work order has a barcode you can scan. There are three kinds:

- **Inbound:** tied to an inbound cargo. Its tags can be printed before the load
  arrives.
- **Processing:** only a work type, such as *Press*, with no cargo. Used for
  staging or backstocking.
- **Shipment:** tied to an outbound cargo, such as delivering a container to the
  port.

## The screens

| Screen | What it does |
|---|---|
| [Receive](../context/M01.md) | Scan tags, the location and the quantity received. SKU tags also need a work order. |
| [Move](../context/M02.md) | Scan tags and the new location. SKU tags also need the from location and quantity. |
| [Process](../context/M04.md) | Turn raw product into processed product before the container arrives. |
| [Return](../context/M03.md) | Put leftover product back into inventory after processing. |
| [Ship](../context/M05.md) | Take product out of inventory as it is loaded. |
| [Inventory](../context/M06.md) | Look up what is on hand by tag, SKU, location or work order. |
| [Inbound Inspection](../context/M08.md) | Record a quality check on an inbound load. |
| [Send Pictures](../context/M09.md) | Attach photos to a cargo or SKU. |
| [My Work Orders](../context/M11.md) | See work orders to do. |

## Process and Ship: enter it before ADD

On **Process** and **Ship**, enter the processed quantity and choose whether to
finish the work order **before** you press **ADD**. Enter one processed value for
the whole load. For 896 units, enter 896 once, not eight lines of 112.

## Two ways to process

1. **Process and ship at once.** One work order, tied to the outbound cargo. Use
   **Ship**, entering both the raw product taken and the processed quantity.
2. **Process ahead (staging).** Two work orders. The first has a work type such as
   *Press* and can be scheduled in advance. Use **Process** with it to turn raw
   product into processed product in a staging location. The second work order is
   tied to the outbound cargo. Use **Ship** with it to ship from processed
   inventory.

## Settings

With a device that has a built-in scanner, such as a Zebra TC25, turn off the
camera **Scan** buttons in **Settings**. They are on by default.

## Related

[Install ShipperXL Mobile](install-mobile.md) · [Inventory Basics](inventory-basics.md) ·
[Receive Inventory](receive-inventory.md) · [Ship Cargo](ship-cargo.md)

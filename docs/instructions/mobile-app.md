# Using ShipperXL Mobile

ShipperXL Mobile records inventory by scanning: receiving, moving, processing and
shipping. The main menu shows only the screens your roles allow. See
[Install ShipperXL Mobile](install-mobile.md) to get started.

![[mobile-menu.png|300]]

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

An inventory tag (left) shows its serial number, cargo and SKU. A SKU tag (right)
shows the item and SKU.

![[mobile-block-tag.png|200]] ![[mobile-sku-tag.png|200]]

## Work orders

Every printed work order has a barcode you can scan. There are three kinds:

- **Inbound:** tied to an inbound cargo. Its tags can be printed before the load
  arrives.
- **Processing:** only a work type, such as *Press*, with no cargo. Used for
  staging or backstocking.
- **Shipment:** tied to an outbound cargo, such as delivering a container to the
  port.

![[mobile-work-order-barcode.png|200]]

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

### Receive

With inventory tags, scan each tag, the location you put it in, and the quantity
received. With SKU tags, also scan the work order the product came in on.

![[mobile-receive.png|200]] ![[mobile-receive-sku.png|200]]

### Move

With inventory tags, scan the tags and the new location. With SKU tags, also enter
the **From** location and the raw or processed quantity. Watch for errors: you
can't move more than is there.

![[mobile-move.png|200]] ![[mobile-move-sku.png|200]]

### Process

Scan product out of raw inventory and into processed inventory, to ship later.
A SKU tag also needs the **From** location and the raw quantity.

![[mobile-process.png|200]] ![[mobile-process-sku.png|200]]

### Return

Put product back after processing. For example, a tag had 56 bales, 50 were used,
and 6 go back. The return is tied to the tag's last work order. A SKU tag also
needs the **From** location.

![[mobile-return.png|200]] ![[mobile-return-sku.png|200]]

### Ship

Scan product out of inventory as it is loaded, converting it to processed product
at the same time if it wasn't processed earlier. Staged product usually has no
identifiable tags, so ship it by SKU from its location. To convert raw to processed
as you ship, enter both quantities.

![[mobile-ship.png|200]] ![[mobile-ship-sku.png|200]]

### Inventory and Inbound Inspection

**Inventory** looks up what is on hand: scan a SKU tag, inventory tag, location or
work order barcode, or type a SKU, location or work order number. **Inbound
Inspection** records a check on an inbound load: scan any of its tags, or its work
order.

![[mobile-inventory.png|200]] ![[mobile-inspection.png|200]]

### Send Pictures

Scan a SKU, inventory tag or work order, take pictures, and press **SAVE**. The
pictures are attached to the cargo or SKU. Current versions of the app upload up to
3 pictures at a time directly. Older versions send them by email, which needs
[email attachments](email-attachments.md) set up and an email app on the device:
when asked which app to share with, choose your email app and **ALWAYS**.

![[mobile-send-pictures.png|200]] ![[mobile-share-gmail.png|200]]

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

- **Show camera-based scan buttons:** with a device that has a built-in scanner,
  such as a Zebra TC27, turn these off. They are on by default.
- **Inspection after receive:** opens Inbound Inspection after each receipt.
- **Send Pictures after ship:** opens Send Pictures after each shipment.

![[mobile-settings.png|200]]

If you chose the wrong app to share pictures with, reset the choice. On Android, go
to **Settings > Apps**, open the menu and choose **Reset app preferences**.

![[mobile-reset-preferences.png|200]]

## Related

[Install ShipperXL Mobile](install-mobile.md) · [Inventory Basics](inventory-basics.md) ·
[Receive Inventory](receive-inventory.md) · [Ship Cargo](ship-cargo.md)

# Using the ShipperXL Kiosk

The kiosk connects to a truck scale and reads weights automatically, so nobody
copies weights from a paper ticket:

- Inbound trucks enter their truck number or work order.
- On return, they weigh out and print a weight ticket.
- Container loading is done by scanning work orders, which are timestamped
  automatically.
- With one or two cameras on the scale, a picture is taken with each weight and
  attached to the scale ticket.

See [Install the Kiosk](install-kiosk.md) for hardware and setup.

> **Screenshot placeholder:** the kiosk's main screen. (save as `images/kiosk-home.png`)

## Weighing

The weight and picture recorded when you press **RECORD** are what is on screen at
that moment. The weight turns green when it is stable. Wind or movement on the
scale makes it change, so press **RECORD** only while the weight is green.

## Inbound load with a prepared work order

1. Enter or scan the work order number.
2. Enter the manifest number and the number of bales.
3. Record the weight. Tags print on the kiosk's label printer.
4. **Unload.**
5. Enter or scan the work order number again.
6. Record the weight, or print the ticket.

## Inbound load with pre-printed tags

1. Enter the truck number.
2. Scan one of the pre-printed tags.
3. Record the weight.
4. **Unload.**
5. Enter the truck number again.
6. Record the weight, or print the ticket.

## Outbound load with a work order

1. Enter or scan the work order number.
2. Record the weight.
3. **Load the product.**
4. Enter or scan the work order number again.
5. Record the weight, or print the ticket.

## Short scales (multi-weight)

A scale too short for a whole truck can take several weights per pass. Turn on
**Multi Weight** for the scale in **Admin > Scales**. Then press **RECORD** for the
first weight, **RECORD** for the second, and **DONE**.

## Image checking

Shipper checks pictures uploaded to scale tickets. When a picture doesn't match the
ticket, the scale ticket shows it. To be told when this happens, set up a scheduled
job. See [Scheduled Jobs](../context/G014.md).

## In the web app

The cargo's **Scale Ticket** tab shows the kiosk's live weight and picture while a
truck is on the scale. The reading updates every few seconds and is marked out of
date after about a minute and a half without a new reading. Click **Capture** to put
the weight on the ticket: the first capture is the gross, the second the tare. If
the second weight is heavier, Shipper swaps them, because the truck was weighed
empty first.

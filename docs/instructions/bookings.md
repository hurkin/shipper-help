# Create a Booking

A booking is a reservation with a carrier. In Shipper, *booking* and *shipment*
mean the same record. The booking number from the shipline is its identifier.

1. Go to **Processing > Bookings** and search for the booking number first.
2. Click **New**. Enter the booking number and choose the carrier.
   - Leave the number blank to take the next number from the booking number scheme.
3. Click **Create**, then fill in the **General** tab:
   - The four legs: **IPI** (place of receipt), **POL** (port of loading),
     **POD** (port of discharge) and **DLV** (place of delivery), each with its
     planned and actual dates. The arrows over the legs show the days from one
     leg to the next, in red if the dates are out of order.
   - Vessel, voyage, container class and type, and quantity.
4. On **Freight**, enter the shipper and forwarder, the cut-off dates (cargo due,
   documents due, earliest pickup and so on) and the bill of lading number.
5. On **Fulfillment**, use **Add line item** to put each sales line (and purchase
   line, for back-to-back trades) on the booking, and enter the assigned
   quantities.
6. Click **Save**.

![[booking-general.png]]

## Starting from another booking

For a booking much like an existing one, open that booking and click **Clone**.
Enter the new booking number (or leave it blank for the next number) and click
**Clone**. The new booking has the same parties, ports, dates and sea details, but
no bill of lading, vessel, voyage, references, lines or cargo. Enter those, then
save.

## Adding containers

On **Freight**, click **Add cargo** for each container. Enter the container number
(or leave it blank for the next cargo number) and the container type.

Each new cargo picks up the booking's lines. A sales line priced per container is
marked fulfilled with 1. Every other line is put on the cargo with a quantity of 0
for you to fill in.

## Watching the shipline

Tick **Watch Shipline for changes** to have Shipper follow the booking with the
carrier. There is a small fee per booking watched.

- Changes are applied as soon as they arrive: vessel, voyage, ports, sail and
  arrival dates, carrier status, and each container's type and carrier dates.
- A note on the booking lists what changed.
- The booking is put into your remote-changes queue (or moved back to the top of
  it), so someone can review it.
- Once the shipline service has picked up the booking, the box can't be unticked.

See also: [Bookings](../context/B008.md), [Ship Cargo](ship-cargo.md),
[Complete a Booking](complete-a-booking.md).

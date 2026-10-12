# Move Cargo to Another Booking

Use this when a booking is split or a container rolls to another booking.

1. Make sure the new booking exists. If you are splitting a booking, create the
   second booking first.
2. Open the container's cargo.
3. On **General**, change **Shipment** to the new booking number. Don't save yet.
4. On **Fulfillment**, if the container fulfills lines of the old booking, set
   those lines' Assigned and Fulfilled to 0. Then use **Add line item** to add the
   new booking's lines and enter their quantities.
5. Save.

A cargo with no lines of its own shows its booking's lines on the Fulfillment tab,
with blank quantities.

See also: [Cargo](../context/B003.md), [Bookings](../context/B008.md).
